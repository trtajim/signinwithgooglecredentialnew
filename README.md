# 🔐 Google Sign-In (Firebase + Credential Manager Setup Guide)

Google has updated its authentication policies and libraries, so the login system must now be implemented through a new channel.  
Unfortunately, the official documentation is still limited — so this guide will walk you through the full setup **step-by-step in an easy way**.

---

## ⚙️ Step 1: Firebase Project Creation and Setup

1. **Create a Firebase Project** in the [Firebase Console](https://console.firebase.google.com/).
2. **Add your Android app** to the project.
3. While adding the app, **include your SHA-1 key** in the form.
   - You can find your SHA-1 key in **Android Studio → Gradle → Tasks → signingReport**.
   - 🔸 **This step is mandatory.**
4. Follow the Firebase documentation and **add the Firebase BoM dependencies** to your project.
   - Skip adding the `google-services.json` file for now — you’ll add it later.

---

## 🔧 Step 2: Enable Firebase Authentication and Set It Up in Your Project

1. In your **Firebase Console**, go to **Authentication → Sign-in method**.
   - Select **Google** as the provider and **enable it**.
2. Add the following dependency to your `build.gradle` file:

   ```gradle
   implementation("com.google.firebase:firebase-auth")
   ```

   Since you’re already using the **Firebase BoM**, there’s no need to specify a version.

3. After this step, you’ll receive a new `google-services.json` file.
   - Place it inside your project folder:

     ```
     app/
       └── google-services.json
     ```

---

## 🔑 Step 3: Google Credential Manager Setup

1. Visit the [official Credential Manager guide](https://developer.android.com/identity/sign-in/credential-manager-siwg) and add the required dependencies.

   The versions may vary, but here’s an example setup:

   ```gradle
   implementation "androidx.credentials:credentials:1.6.0-beta01"
   implementation "androidx.credentials:credentials-play-services-auth:1.6.0-beta01"
   implementation "com.google.android.libraries.identity.googleid:googleid:<latest-version>"
   ```

   Replace `<latest-version>` with the current version.  
   For example, in my case, it was:

   ```gradle
   implementation "com.google.android.libraries.identity.googleid:googleid:1.1.1"
   ```

2. Sync your project and proceed with the Java implementation as shown below.
   - Since both **Firebase** and **Credential Manager** are library-based integrations, just follow the code structure properly — there’s nothing complex to understand.
   - Note: As of now, Google hasn’t provided official **Java documentation** for this process, so refer to this guide’s example code instead.

---

## ✅ Summary

- You’ve connected Firebase and enabled Google Sign-In via the new Credential Manager system.  
- The old Google Sign-In method is deprecated, so this setup ensures future compatibility.  
- Follow this guide closely — no additional configuration is required.

---

**Author:** *TR Tajim*  
**Note:** This guide focuses only on the **new Google Sign-In flow** using **Firebase + Credential Manager** with **Java**.
