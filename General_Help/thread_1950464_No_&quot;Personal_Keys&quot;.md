---
title: "No &quot;Personal Keys&quot;"
date: 2012-03-31
forum: General Help
---

### Post by cbennett926 on 2012-03-31
Hello,

I just did my first full install of Ubuntu, but have been using it for a while, since 10.04, and for some reason under "Passwords and Keys" I do not have any personal keys. Any help?

---

### Post by nickajeglin on 2012-03-31
Those keys are used to log in to remote machines, if you aren't doing so, you don't have any need of a key. If you were expecting keys to be there, and they went missing, I'm not entirely sure what to tell you.

---

### Post by cbennett926 on 2012-03-31
On Launchpad.net in order to sign ubuntu's code of coduct it asks for an OpenPGP key which is found under personal keys, and I do not have anything in there.

---

### Post by nickajeglin on 2012-03-31
I don't have ubuntu in front of me at this moment, so the help I can offer is limited, but you will almost certainly have to generate a new key. You should be able to do this from the passwords and keys dialog.

```
Step 1: Open Passwords and Encryption Keys.

Step 2: Select File > New, select PGP Key and then follow the on-screen instructions.

Now you'll see your new key listed in the Passwords and Encryption Keys tool.
```

I copied those instructions from here: [https://help.launchpad.net/YourAccount/ImportingYourPGPKey](https://help.launchpad.net/YourAccount/ImportingYourPGPKey)

You may have already seen that. 

Also useful is this page: [https://help.ubuntu.com/community/GnuPrivacyGuardHowto](https://help.ubuntu.com/community/GnuPrivacyGuardHowto)

There is a section on how to generate a pgp key, with a variety of methods listed, just in case you have any trouble with the passwords and keys manager.

Good luck!

---

### Post by cbennett926 on 2012-03-31
> **nickajeglin said:**
> I don't have ubuntu in front of me at this moment, so the help I can offer is limited, but you will almost certainly have to generate a new key. You should be able to do this from the passwords and keys dialog.

```
Step 1: Open Passwords and Encryption Keys.

Step 2: Select File > New, select PGP Key and then follow the on-screen instructions.

Now you'll see your new key listed in the Passwords and Encryption Keys tool.
```I copied those instructions from here: [https://help.launchpad.net/YourAccount/ImportingYourPGPKey](https://help.launchpad.net/YourAccount/ImportingYourPGPKey)

You may have already seen that. 

Also useful is this page: [https://help.ubuntu.com/community/GnuPrivacyGuardHowto](https://help.ubuntu.com/community/GnuPrivacyGuardHowto)

There is a section on how to generate a pgp key, with a variety of methods listed, just in case you have any trouble with the passwords and keys manager.

Good luck!

Now I just feel silly, I didn't even try using the file menu's and what not! Thank you!!

---

### Post by nickajeglin on 2012-03-31
No problem :D Glad I could help!

---

