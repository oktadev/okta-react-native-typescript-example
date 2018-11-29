# Okta React Native Typescript Example

This app shows how to use React Native 0.57+ with Typescript (i.e. Babel 7), using React Native App Auth for OAuth 2.0 authentication (Okta) and react-test-renderer for testing.

**NOTE**: This has only been tested on Android.

Please read [Build a React Native Application and Authenticate with OAuth 2.0](https://developer.okta.com/blog/2018/11/29/build-test-react-native-typescript-oauth2) to see how this app was created.

**Prerequisites:** [Node.js](https://nodejs.org/) and Android Studio.

> [Okta](https://developer.okta.com/) has Authentication and User Management APIs that reduce development time with instant-on, scalable user infrastructure. Okta's intuitive API and expert support make it easy for developers to authenticate, manage, and secure users and roles in any application.

* [Getting Started](#getting-started)
* [Links](#links)
* [Help](#help)
* [License](#license)

## Getting Started

To install this example application, run the following commands:

```bash
git clone https://github.com/oktadeveloper/okta-react-native-typescript-example.git
cd okta-react-native-typescript-example
```

This will get a copy of the project installed locally.

### Create Native Application in Okta

Before you can run this React Native example, you'll need an application to authorize against. If you don't have an Okta Developer account, [get one today](https://developer.okta.com/signup/)!

Log in to your Okta Developer account and navigate to **Applications** > **Add Application**. Click **Native** and click the **Next** button. Give the app a name you’ll remember (e.g., `React Native`), select `Refresh Token` as a grant type, in addition to the default `Authorization Code`. Copy the **Login redirect URI** (e.g., `com.oktapreview.dev-123456:/callback`) and save it somewhere. You'll need this value when configuring your app.

Click **Done** and you should see a client ID next screen. Copy and save this value as well. 

### Specify Your Issuer, Client ID, and Redirect URI

Open `src/App.tsx` and change the `config` to match your authentication parameters. 

```tsx
const config = {
  issuer: 'https://{yourOktaDomain}/oauth2/default',
  clientId: '{yourClientId}',
  redirectUrl: '{yourReversedOktaDomain}:/callback',
  additionalParameters: {},
  scopes: ['openid', 'profile', 'email', 'offline_access']
}
```

Similarly for the `manifestPlaceholders` section of `android/app/build.gradle`.

```groovy
manifestPlaceholders = [
    appAuthRedirectScheme: '{yourReversedOktaDomain}'
]
```

### Run the App

First run the following command to install the dependencies.

```bash
yarn
```

Then run the following command to deploy to an Android emulator or connected device.

```bash
react-native run-android
```

## Links

This example uses the following libraries:

* [React Native App Auth](https://github.com/FormidableLabs/react-native-app-auth)

## Help

Please post any questions as comments on [this repo's blog post](https://developer.okta.com/blog/2018/11/29/build-test-react-native-typescript-oauth2), or visit our [Okta Developer Forums](https://devforum.okta.com/). You can also email developers@okta.com if would like to create a support ticket.

## License

Apache 2.0, see [LICENSE](LICENSE).
