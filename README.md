# instagram clone version 3 ๐๐๐

instagram clone project(BACKEND)

# we don't need to graphql-yoga anymore , apollo๊ฐ ์ด์  ์ง์์ ์ ํด์ค

# eslint and prettier setting

- https://velog.io/@das01063/VSCode%EC%97%90%EC%84%9C-ESLint%EC%99%80-Prettier-TypeScript-%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0

# ESLint ํธํ

npm i -D eslint-config-prettier eslint-plugin-prettier

- eslint-config-prettier๋ Prettier์ ์ถฉ๋๋๋ ESLint ๊ท์น๋ค์ ๋ฌด์ํ๋ ์ค์ ์ด๊ณ , eslint-plugin-prettier๋ Prettier๋ฅผ ์ฌ์ฉํด ํฌ๋งทํ์ ํ๋๋ก ESLint ๊ท์น์ ์ถ๊ฐํ๋ ํ๋ฌ๊ทธ์ธ์๋๋ค. (์ถ์ฒ: Prettier - Integrating with Linters)

# prettierrc.json ๋ด์ฉ

```
{
    "printWidth": 80,			// ํ ์ค์ ๋ผ์ธ ์
    "tabWidth": 2,			// tab์ ๋๋น
    "useTabs": false,			// tab ์ฌ์ฉ ์ฌ๋ถ
    "semi": true,				// ; ์ฌ์ฉ ์ฌ๋ถ
    "singleQuote": true,			// 'string' ์ฌ์ฉ ์ฌ๋ถ
    "quoteProps": "consistent",		// ๊ฐ์ฒด property์ ๋ฐ์ดํ ์ฌ๋ถ
    "trailingComma": "es5",		// ๋์ , ์ฌ์ฉ ์ฌ๋ถ
    "bracketSpacing": true,		// Object literal์ ๋์ด์ฐ๊ธฐ ์ฌ์ฉ ์ฌ๋ถ (ex: { foo: bar })
    "arrowParens": "always",		// ํจ์์์ ์ธ์์ ๊ดํธ ์ฌ์ฉ ์ฌ๋ถ (ex: (x) => y)
    "endOfLine": "lf"			// ๋ผ์ธ ์๋ฉ ์ง์ 
  }
```

# eslintrc.json ๋ด์ฉ

```
{
  ...
  "extends": [
    "eslint:recommended",
    "plugin:@typescript-eslint/eslint-recommended",
    "plugin:@typescript-eslint/recommended",
    "plugin:@typescript-eslint/recommended-requiring-type-checking",
    "plugin:prettier/recommended",
    "prettier/@typescript-eslint"
  ],
  ...
}
```

# apollo-server graphql install

- https://github.com/apollographql ์ฐธ๊ณ 

# nodemon ์ค์น ํ nodemon์ ์ด์ฉํ์ฌ ์๋ฒ ์คํ

# issue!! - import ๋ฌธ์ผ๋ก ๋ฐ๊พธ์ด์ ๋ผ์ด๋ธ๋ฌ๋ฆฌ๋ฅผ ์ฌ์ฉํ๊ณ  ์ถ์๋

1. way one

```
(node:32191) Warning: To load an ES module, set "type": "module" in the package.json or use the .mjs extension.
(Use `node --trace-warnings ...` to show where the warning was created)
/Users/nohsangwoo/Desktop/reactClass/instaclone/server.js:1
```

๋ผ๋ ์๋ฌ๊ฐ ๋ํ๋จ (๊ธฐ๋ณธ์ ์ผ๋ก es ๋ชจ๋์ด ์๋๊ธฐ๋๋ฌธ)

- ์๋ฌ์ ๋ด์ฉ๋๋ก package.json์ "type": "module" ์ด๋ ์ต์ ์ถ๊ฐ ๊ทธ๋ผ ์ด์์์

2. way two
   ์ ๋ฐฉ์์ node๋ฒ์ ผ์ด ๋ฎ์๊ฒฝ์ฐ ์ฌ์ฉํ ์ ์์์ง๋ ๋ชจ๋ฆ ๋ฐ๋ผ์ babel์ ์ด์ฉํ์ฌ trade off๋ฅผ ์์ ๋ฒ๋ฆด๊บผ์

- "type": "module" ์ค์ ์ ๋ค์ ์์ ์ค
- babel ์ฌ์ฉ (javascript ์ปดํ์ผ๋ฌ)
  ์ง์์ํ๋ ์ ๋ฒ์ ผ ์๋ฐ์คํฌ๋ฆฝํธ ๋ฌธ๋ฒ์ ๊ตฌ๋ฒ์ ผ์์๋ ๊ตฌ๋ํ ์์๊ฒ ์ปดํ์ผ ํด์ฃผ๋ ๊ธฐ๋ฅ
  https://babeljs.io/setup#installation ์ฐธ๊ณ 

- npm install --save-dev @babel/core
- npm install @babel/preset-env --save-dev
- root๊ฒฝ๋ก์ babel.config.json ํ์ผ ์์ฑ ํ ๊ณต์๋ฌธ์์ ์๋ ์ธํ ์ต์ ๋ณต์ฌ ๋ถ์ฌ๋ฃ๊ธฐ

```
{
  "presets": ["@babel/preset-env"]
}
```

- package.json ์

```
    "dev": "nodemon --exec babel-node server"

```

- npm install @babel/node --save-dev
  (์ฝ์์์ jsํ์ผ์ ์คํ์์ผ์ฃผ๋ ๊ธฐ๋ฅ)
- @babel/preset-env
  (์ด๋ค ๋ฒ์ ผ์์๋  ์ต์  ์๋ฐ์คํฌ๋ฆฝํธ ๋ฌธ๋ฒ์ ์ฌ์ฉํ  ์ ์๊ฒ ํด์ค)
  ์ด์  node๊ฐ ๋์ ๋ฒ์ ผ์ด๋  ๋ฎ์ ๋ฒ์ ผ์ด๋  ํด์ํด์ ์คํ ํด์ค

# prisma ์ค์น

- https://www.prisma.io/

1. npm install prisma -D
2. npx prisma init
3. ์ด๋ ๊ฒ ํ๋ฉด root ๊ฒฝ๋ก์ prisma/schema.prisma ํ์ผ์ด๋ .envํ์ผ ๋ง๋ค์ด์ง
   (๊ธฐ๋ณธ์ ์ผ๋ก postgresql์ธํ ๋ฐฉ๋ฒ์ ์์๋ก ๋ง๋ค์ด์ ธ์์)

# schema.prisma ํ์ผ์ ๋ฐ์ดํฐ๋ฒ ์ด์ค ๋ชจ๋ธ ๊ตฌํ

# migrate๋ก ์งํ

<!-- npx prisma migrate dev --name add-profile --> 2021.04.11์ผ ๊ธฐ์ค ์ฌ๊ธฐ์ --name add-profile์ ์ ์ธ

- npx prisma migrate dev
  (์ด๋ .env์ postgresql์ ํ์ํ์ ๋ณด๋ฅผ ์ ์๋ ฅํ๋ค./์ฌ์ฉ์์ด๋ฆ ๋น๋ฒ ํฌํธ๋ฒํธ ๋ฑ๋ฑ..)
- ์ ๋จ๊ณ๋ฅผ ์ ๋ฐ๋ฅธ๋ค๋ฉด shema.prisma์์ ์ง์ ํ model์ด ๋ฐ์ดํฐ๋ฒ ์ด์ค์ ๋๊ธฐํ๋จ(์ฐ๋์ด ์๋ฃ๋จ)

# typeDef์ schema์ model๋ด์ฉ์ ์๋์ผ๋ก syncํด์ค์ผํจ

(์ด๋ sync์ ์์ ์ฃผ์์ฌํญ)

- typeDef
  typeDef์์ table์ ์ ์ํ ๋ ๊ธฐ๋ณธ์ ์ผ๋ก optinal์์ฑ์ด๊ธฐ๋๋ฌธ์ require์ธ ๊ฒฝ์ฐ๋ !๋ฅผ ๋ถ์ฌ์ค์ผํจ
- schema.prisma
  schema์์ model์ ์ํ ๋ ๊ธฐ๋ณธ์ ์ผ๋ก require์์ฑ์ด๊ธฐ์
  optional์ธ ๊ฒฝ์ฐ๋ ?๋ฅผ ๋ถ์ฌ์ค์ผํจ
- ์ ๋๊ฐ์ ์ฐจ์ด๋ฅผ ์ธ์ํ๊ณ  ๋ชจ๋ธ๊ณผ ํ์์ ์ ์ํ๋ค

# prisma studio

- npx prisma studio ๋ก ์คํ (package.json์ ์ถ๊ฐ)

- https://www.prisma.io/docs/concepts/components/prisma-studio
  postico ๊ฐ์๊ฑด๋ฐ prisma์ ์ต์ ํ๋ ๋ฐ์ดํฐ๋ฒ ์ด์ค ์๊ฐํ ํ๋ก๊ทธ๋จ

# ํ์ผ์ ๋ถํ ํ๊ธฐ์ํด graphql-tools ๋ผ์ด๋ธ๋ฌ๋ฆฌ ์ฌ์ฉ

- npm install graphql-tools@latest
  (๋ถํ ๋ ํ์ผ์ ํ๊ณณ์ ๋ชจ์์ ๋ก๋ํ๊ธฐ์ํ ์์)
- https://www.graphql-tools.com/docs/schema-merging
  (๋ถํ ๋ schema๋ค์ ๋ชจ์์ฃผ๋ ๊ธฐ๋ฅ)

# apply to dotenv

- npm install dovenv

# BFORE start clone coding

- prismaํ์ผ๊ณผ , Movie์ ๊ด๋ จ๋ typeDefs, resolversํ์ผ์ ์ญ์  ๋ฐ database๋ฅผ ์ญ์  ํ ์ฒ์๋ถํฐ ๋ค์ ์์ํ๊ฒ ์ธํํด๋ 
- ๋ํ ๋ค์ instaclone๋ฐ์ดํฐ๋ฒ ์ด์ค๋ฅผ ๋ค์ ์์ฑํด์ค

# USER MODULE

## User:

- [x] Create Account
- [x] See Profile
- [x] Login
- [x] Edit Profile
- [x] Follow User
- [x] Unfollow User
- [x] See Followers w/ Pagination
- [x] See Following w/ Pagination
- [x] Computed Fields
- [x] Search Users

## Photos

- [ ] See Photo
- [ ] Upload Photo
- [ ] Edit Photo
- [ ] Like / Unlike Photo
- [ ] See Photo Likes
- [ ] See Feed
- [ ] Search Photos
- [ ] See Hashtags
- [ ] Comments
- [ ] Comment on Photo
- [ ] Edit Comment
- [ ] Delete Comment

# 4.0 createAccount part one

- npx prisma init

# 4.2 bcrypt createAccount part two

- hashing password
- npm install bcrypt

# 4.3 createAccount part three

- createAccount ๊ธฐ๋ฅ ๊ตฌํ

# 4.4 login

- npm install jsonwebtoken

1. find username
2. compare password
3. return jsonwebtoken

# 4.9 http header์์ mutaion์ด๋ query๋ฑ์์ ์ธ์๋ก ๋ฐ์์ค๋ ๋ฐฉ๋ฒ

# 4.10 context์์ request์ response๋ฅผ ์ฌ์ฉํ๋ ๋ฐฉ๋ฒ

# 4.13 currying ๊ฐ๋ ์ตํ๊ธฐ

# 4.14 apollo-server๊ฐ ์ ๊ณตํ๋ api๋ฑ์ ์ฌ์ฉํ๊ธฐ์ํด schemaํ์ ๋ณ๊ฒฝ

# graphql client altair

https://altair.sirmuel.design/features

# 4.16

altair์ฌ์ฉํ์ฌ fileuload์์ createStream ์ฌ์ฉ์ ์๊ธฐ๋ ๋ฒ๊ทธ ํด๊ฒฐ๋ฒ

```
 "resolutions": {
    "fs-capacitor": "^6.2.0",
    "graphql-upload": "^11.0.0"
  }
```

- script ์ ์ถ๊ฐ
  npx npm-force-resolutions

# 4.17 upload part four

- process.cwd()

current working directory
ํ์ฌ ํ๋ก์ ํธ์ root๊ฒฝ๋ก

# graphql server๋ฅผ apollo server์์ express๋ก ๋ณ๊ฒฝํ์ฌ ๋๋ ค๋ฒ๋ฆฌ๊ธฐ

- npm install apollo-server-express
- npm install express
- npm install morgan

# 4.20 self-referencing relationship

# 4.20 unfollow user

# include ๋ฅผ ์ด์ฉํ์ฌ ๋์์ ์ปฌ๋ผ์ด ๋ค๋ฅธ ์ฌ์ฉ์์ ๊ด๊ณ๊ฐ ์๋ค๋ฉด ํด๋น ์ ๋ณด๋ฅผ ๊ฐ์ ธ์ค๋๋ก ํด์ค

# 4.23 Followers Pagination part One - offset Pagenation

- https://www.prisma.io/docs/concepts/components/prisma-client/pagination#offset-pagination
- where์ ์คํผ๋ ์ดํฐ๋ก some,every,none์ ์ฌ์ฉํ ์์์

```
const followers = await client.user.findMany({
  where:{
    some:{   <--- ์ฌ์ฉ๋ฒ
      username:username
    }
  }
})
```

- some : ์ ๊ณตํ๋ ๊ฒ์์ด์ ์ผ๋ถ๋ผ๋ ํฌํจ๋๋ค๋ฉด ๊ฒฐ๊ณผ๊ฐ์ ํฌํจํ์ฌ ๋ฐํ
- every : ์กฐ๊ฑด์ ์๋ฒฝํ๊ฒ ๋ถํฉํ๋ ๊ฒฐ๊ณผ๊ฐ๋ง ๋ฐํ
- none : ์กฐ๊ฑด์ ๋ถํฉํ๋ ๊ฐ์ ์ ์ธํ ๊ฒฐ๊ณผ๊ฐ์ ๋ฐํ(like a omit)

# 4.24 followers pagination part two

- select๋ก ๊ฒ์์ ๋ถ๋ฌ์ค๋ ๋ฐ์ดํฐํ๋๋ฅผ ์ ํ๊ฐ๋ฅ

```
  const ok = await client.user.findUnique({
        where: { username },
        select: { id: true },
      });
```

- username์ผ๋ก ๊ฒ์ํ ๊ฒฐ๊ณผ์ค id์ ๋ด์ฉ๋ง ํํฐ๋ง ํ์ฌ ๊ฐ์ ธ์ด(์ปฌ๋ผ์ pick type๊ณผ ๊ฐ์)

# 4.25 following pagination part one - cursur pagination

- https://www.prisma.io/docs/concepts/components/prisma-client/pagination#cursor-based-pagination

# 4.26 Computed Fields part One

- ๋ฐ์ดํฐ๋ฒ ์ด์ค์ ์กด์ฌํ์ง ์์ง๋ง ๋ฌด์์ธ๊ฐ ๊ณ์ฐํด์ ์ ๊ณตํด์ฃผ๋ ๊ฐ

- root arguement ์ฌ์ฉ๋ฒ
  ์์ parent๊ฐ ์กด์ฌํ๋ค๋ฉด ํด๋นparent์ ๊ฐ

# 4.27 isMe computed field

# 4.28 isFollowing computed field

- seeProfile๋ก ๊ฒ์ํ ์ ์ ๊ฐ (๋ก๊ทธ์ธ๋)๋ด๊ฐ followingํ ๋์์ธ์ง ๊ตฌ๋ถํด์ฃผ๋ ํ๋

# 4.29 searching users

- startsWith
  ํค์๋๊ฐ ์์๋๋ ๋ถ๋ถ๊ณผ ๊ฐ๋ค๋ฉด ๊ฒ์๋จ
  ex)
  term: noh // -- ๊ฒ์์ด
  nohsangwoo // ๊ฒ์๋จ
  sangwoonoh // ๊ฒ์์๋จ

```
client.user.findMany({
        where: {
          username: {
            startsWith: keyword.toLowerCase(),
          },
        },
      }),
```

# Photos

- [x] Upload Photo (Parse #)
- [x] See Photo
- [x] See Hashtag
- [x] Search Photos
- [x] Edit Photo
- [ ] Like / Unlike Photo
- [ ] See Photo Likes
- [ ] See Feed
- [ ] Comments
- [ ] Comment on Photo
- [ ] Edit Comment
- [ ] Delete Comment

# 6.0 Photos Model

# 6.2 Upload Photo part One

- setting basic form

# 6.3 Upload Photo part Two

- https://www.regexpal.com/
  ์ ๊ท ํํ์ ๋์
  (match)ํจ์๋ฅผ ์ฌ์ฉํ์ฌ ์ ๊ทํํ์์ ์ฌ์ฉํ์ฌ ๋ฐฐ์ด๋ก ํน์  ๋จ์ด๋ฅผ ์ถ์ถํ์ฌ ๋ฐฐ์ด๋ก ๋ฐํํจ

# 6.5 seePhoto

# 6.6 seeHashtag

- Photo - user
  ์ด photo์ ์ฐ๊ฒฐ๋ ํ๋์ user๋ฅผ ๊ฒ์

- Photo - hashtags
  ์ด photo id๋ฅผ ๊ฐ์ง๊ณ ์๋ ๋ชจ๋  hashtag๋ฅผ ๊ฒ์

- Hashtag - photos
  ํด์ ํ๊ทธ์์ hashtag์ id๋ฅผ ๊ฐ์ง๊ณ ์๋ photo๋ค์ ๊ฒ์
- hashtag - totalPhotos.count
  ํด์ ํ๊ทธ ์์ ํด๋น ํ๊ทธ๋ฅผ ๊ฐ์ง๊ณ ์๋ ๋ชจ๋  photo ์ ์๋ฅผ ๊ฒ์
- seeHashtag
  hashtag ์ด๋ฆ์ผ๋ก ํ๋์ hashtag๋ฅผ ๊ฒ์

# update

npm i --save-dev prisma โ
npm i @prisma/client
