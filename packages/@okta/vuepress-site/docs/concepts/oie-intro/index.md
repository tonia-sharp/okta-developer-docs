---
title: Okta Identity Engine overview
meta:
  - name: description
    content: Find out more about Okta's Identity Engine authentication flow, what developer features it unlocks, and how to use it.
---
# Okta Identity Engine

<ApiLifecycle access="ie" />

Okta Identity Engine enables you to customize your Okta experience and implement flexible identity use cases. This means shifting from predefined behaviors to a platform that offers customizable building blocks for dynamic, app-based configurations.

For administrator information about implementing Identity Engine, see [Get started](https://help.okta.com/okta_help.htm?type=oie&id=ext-get-started-oie).

> **Note:** As of March 1, 2022, Identity Engine supersedes Okta Engine for new customers. Okta Engine is now referred to as Okta Classic Engine. Existing Classic Engine customers can upgrade to Identity Engine. See the [Identity Engine upgrade overview](/docs/guides/oie-upgrade-overview/) for more information on upgrading. Okta documentation reflects use cases for Identity Engine and indicates when a feature is only available for Identity Engine users. Previous functionality is still supported; see  [Okta Classic Engine](/guides/archive-overview/). To determine your Okta version, see [Identify your Okta solution](https://help.okta.com/okta_help.htm?type=oie&id=ext-oie-version).

## Supported authentication deployment models

Identity Engine supports the following authentication deployment models:

* **Okta-hosted (redirect) Sign-In Widget**: Use the redirect (Okta-hosted) Sign-In Widget to authenticate your users, then redirect back to your app. This is the recommended approach as it's the most secure and fastest to implement.
* **Embedded Sign-In Widget**: Embed the Sign-In Widget into your own code base to handle the authentication on your servers. This provides a balance between complexity and customization.
* **Embedded SDK-driven sign-in flow**: Use our SDKs to create a completely custom authentication experience. This option is the most complex and leaves you with the most responsibility, but offers the most control.

The following topics provide more detailed information:

* [Okta deployment models — redirect vs. embedded](/docs/concepts/redirect-vs-embedded/)
* [Sign users in](/docs/guides/sign-in-overview/)

## Identity Engine customization features

Identity Engine includes the following customization features:

* App context in email templates
* Sign-on policies
* App intent links
* CAPTCHA
* Interaction code grant type

> **Note:** Previous functionality is still supported, including Classic Engine org, v1 API, and SDKs. See [Okta Classic Engine](https://developer.okta.com/docs/guides/archive-overview/). To determine your Okta version, see [Identify your Okta solution](https://help.okta.com/okta_help.htm?type=oie&id=ext-oie-version).

### **App context in email templates**

You can use app context variables in email templates, enabling you to dynamically customize email style and content based on the app from which the email notification is sent. You can use variables for the app ID, app name, and app label.

See [Customize email notifications | Okta Developer](/docs/guides/custom-email/main/#use-vtl-variables).

### **Sign-on policies**

With sign-on policies, Identity Engine enables you to create flexible apps that can change their authentication methods without you needing to alter a line of code.

You can restrict access based on a number of conditions such as user and group membership, device, location, or time. You can also require more secure authentication steps for access to sensitive applications, such as confirmation of a push notification to a mobile device or re-authentication through an SMS one-time passcode.

You can create global policies that determine access to Okta as well as additional authentication policies that provide extra steps. You can share these authentication policies between apps.

See the following detailed documentation:

* [Configure a global session policy and authentication policies](/docs/guides/configure-signon-policy/)

* [Authentication policies](https://help.okta.com/okta_help.htm?type=oie&id=ext-about-asop)

* [Policies (high-level concept)](/docs/concepts/policies/)
 
### **App intent links**

You use app intent links to initiate a sign-in flow to an application. Both Identity Provider and Service Provider-initiated flows are supported.

Example app intent link for a SAML application:
`http://${yourOktaDomain}/app/mysamlapp_1/${appInstanceID}/sso/saml`

With Identity Engine, your app intent links host the Sign-In Widget which optimizes the sign-in process and enables you to use a common rate limit group and apply policies.

When unauthenticated users attempt to access an app, they’re no longer redirected to a centralized sign-in page. Instead, the hosted Sign-In Widget evaluates the global session policy, authentication policy, and all other policies relevant to the sign-in experience.

### CAPTCHA support

Identity Engine offers registration, sign-in, and account recovery integration of the two market-leading CAPTCHA services: hCAPTCHA and reCAPTCHA.
> **Note:** CAPTCHA is not available when using an SDK.

See [CAPTCHAs](/docs/api/openapi/okta-management/management/tag/CAPTCHA/).

### Interaction code grant type for embedded authentication

The Interaction Code grant type is an extension of the OAuth 2.0 and OpenID Connect (OIDC) standards that you can use to manage user interactions. Use the Interaction Code grant for native, SPA, and web client apps that you want to interact directly with the user and mediate between the user and the authorization server, instead of using a [browser-based redirect](https://developer.okta.com/docs/concepts/redirect-vs-embedded/) to hand off the authentication experience.

The Interaction Code grant type enables you to manage user interactions with the authorization server directly using a client ID, as well as a Proof Key for Code Exchange (PKCE), to keep the flow secure.

See [Implement authorization by Interaction Code grant type](/docs/guides/implement-grant-type/interactioncode/main/).

## SDKs and sample apps

Identity Engine includes multiple SDKs and sample apps to show you how to implement the authentication flows.

The following topics provide detailed information and examples:
* [Languages and SDKs | Okta Developer](/code/)
* [Download and set up the SDK, Sign-In Widget, and sample apps | Okta Developer](/docs/guides/oie-embedded-common-download-setup-app/)
