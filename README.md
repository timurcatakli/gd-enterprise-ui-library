## Introduction

`gd-enterprise-ui-library` is an all-in-one tool to create and publish a high-quality component library, taking care of tedious setup and ensuring best practices.

## What's Inside

- ⚛️ React, with TypeScript by default

- 📦 Tsup for building and bundling

- 🤖 GitHub Actions for publishing to npm and testing

- 📕 Storybook v7 running on Vite for instant HMR

- ⚡ Vite playground dev server

- 🦋 Changesets for versioning

- 🧪 Vitest for testing

- 🕵️‍♂️ Eslint for linting

- 💅 Prettier for formatting

## 🚀 Publishing

Once the GitHub Action has been triggered, it will create a PR that will publish the library to npm. Once the PR has been merged, library will be published to npm!

## 📦 Bundling

Project uses [tsup][] for bundling.

Everything project uses is hot-swappable. Meaning, if you don't want to use tsup as a bundler for whatever reason you can easily change it to your favourite bundler. Change the `build` scripts in `package.json` to whatever you want.

You can edit the `tsup.config.ts` file to your liking.

For example, if you wanted to enable code-splitting and minify the code your config would look like this:

```ts
// tsup.config.ts

export default defineConfig({
  // ...
  splitting: true,
  minify: true,
});
```

## 📕 Storybook

[Storybook][] has been preconfigured to run on Vite, which means that you get instant HMR when developing your components. This is a huge productivity boost when developing components.

To start storybook run:

```sh
npm run storybook
```

Project utilises version 7 of Storybook, which means that you can use the new Component Story Format (CSF) to write your stories.

Check out the [official documentation][] for more information on how to make the most out of the awesome features that Storybook provides.

## ⚡ Vite Dev Server

Each project is preconfigured with a [Vite][] dev server that can be started by running:

```sh
npm run dev
```

This has been provided for those that like to create components in a playground rather than a storybook-first approach.

## 🦋 Changesets

[Changesets][] are used to version your library, and publish it to npm.

To create a changesets run:

```sh
npx changeset
```

Commit the generated changelog to trigger the GitHub Action mentioned [below](#-github-actions).

The files that you commit alongside the generated changeset log are the changes that will be referenced in the release notes. This means you can commit the changeset log by itself to just trigger the publish without referencing the exact files.

## 🤖 GitHub Actions

There are two actions provided out of the box located in the `.github/workflows` folder.

`main.yml`:

- This action is run on all branches.
- It runs linting, tests, and typechecking.
- It runs typechecking, and performs a build to make sure it can be built safely.

`publish.yml`

- This action is run on the `main` branch
- If there is a changeset that was committed, a PR is created that when merged will automatically publish that version to npm.
- If a publishing PR already exists, the changes are added to that release PR.

## 🧪 Testing

There are several approaches to testing components that have been provided out of the box.

### Vitest

[Vitest][] is a testing framework that is built on top of Vite. It is a great choice for testing components, as it provides a fast and easy way to test components. It's mainly used to test the functionality of components, rather than the visual aspects, however it can be used for both.

To run the tests, run:

```sh
npm run test
```

### Storybook Tests

The recommended way to run storybook tests is to use the [Chromatic][] integration. This is a service that allows you to run visual regression tests on your components.

The setup steps can be found [here][chromatic-setup].

Once that has been set up, you can use the Storybook play function to run integration tests on your components. See the [official documentation][storybook-play-functions] for more information.

## License

This project is licensed under the terms of the MIT license.

[npm-token]: https://docs.npmjs.com/creating-and-viewing-access-tokens#creating-access-tokens
[github-secrets]: https://docs.github.com/en/actions/security-guides/encrypted-secrets#creating-encrypted-secrets-for-a-repository
[tsup]: https://tsup.egoist.dev/
[storybook]: https://storybook.js.org/
[official documentation]: https://storybook.js.org/docs/7.0/react/get-started/introduction
[vite]: https://vitejs.dev/
[changesets]: https://github.com/changesets/changesets
[vitest]: https://vitest.dev/
[chromatic-setup]: https://storybook.js.org/docs/7.0/react/writing-tests/visual-testing#setup-chromatic-addon
[storybook-play-functions]: https://storybook.js.org/docs/7.0/react/writing-tests/interaction-testing
[tailwindcss]: https://tailwindcss.com/
[chakraui]: https://chakra-ui.com/
[ant design]: https://ant.design/
[emotion]: https://emotion.sh/
[styled components]: https://styled-components.com/
[material ui]: https://material-ui.com/
[chromatic]: https://www.chromatic.com/

[new-project-issue]: https://github.com/moishinetzer/PBandJ/issues/new?title=[Example%20Project]:%20&body=Please%20add%20this%20project%20that%20was%20created%20with%20PBandJ%20to%20the%20README:
