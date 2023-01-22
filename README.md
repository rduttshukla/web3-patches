# What is this?

This is CRA installation with a patch to resolve compilation issues due to missing libraries when using some web3 libraries. That may occour in the cases where you're using a verson of a web3 library such as `@web3/react` not supported for React v18.

# How to use this?

Follow the following instructions to apply the patch

1. Take a backup of your code by using git or other means. 
2. Clone this repository to your system and copy the `patches` directory from the cloned repository to your project's root.
3. In your project, install `patch-package` using `npm i patch-package`.
4. Add a `postinstall` script in your `package.json` like this:
```
...
	"scripts": {
		...
		"postinstall": "patch-package"
	},
...
```

5. Add the dev dependencies from this repository's `package.json` to your project:

```
...
	"devDependencies": {
		...
		"assert": "^2.0.0",
		"buffer": "^6.0.3",
		"crypto-browserify": "^3.12.0",
		"patch-package": "^6.5.0",
		"process": "^0.11.10",
		"stream-browserify": "^3.0.0",
		"url": "^0.11.0"
	}
...
```

6. Do a `npm i` again which will install your dependencies as well as apply the patch.
7. If you have already installed the dependencies, run `npx patch-package` to only apply the patch.

# Notes

1. I have tested the patch only on `react-scripts` 5.0.0 and 5.0.1 but they should work on any `react-scripts` ^5.0.0 release. 
2. Edit the version number of the patch file included in the `patches` directory, if you're using a version of `react-scripts`  other than 5.0.1.
