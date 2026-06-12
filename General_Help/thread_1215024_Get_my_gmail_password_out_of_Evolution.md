---
title: "Get my gmail password out of Evolution"
date: 2009-07-16
forum: General Help
---

### Post by legalguy on 2009-07-16
I set up Evolution Mail ver 2.26.1 to access my gmail account.  It works fine but now forgot my password.  How do I look it up in Evolution?

---

### Post by michy99 on 2009-07-16
When you set up your gmail account you should have set up a security question in case you forgot your password. Go to the gmail site and at the login page there will be something to click for 'I forgot my password' or something like that.

Here is the password recovery page for gmail:

[https://www.google.com/accounts/ForgotPasswd?service=mail&fpOnly=1](https://www.google.com/accounts/ForgotPasswd?service=mail&fpOnly=1)

---

### Post by legalguy on 2009-07-16
I'd rather get it out of Evolution...it's got to be in there somewhere...

---

### Post by michy99 on 2009-07-16
In that case, you're on your own.

---

### Post by mcduck on 2009-07-16
Evolution stores it's passwords in Gnome's keyring, so you can use the keyring manager to check the password.

To do that first open the Keyring Manager (Applications/Accessories/Passwords and Encryption Keys). Go to Passwords-tab and click the "Passwords:login"-keyring to show the keys. You should find your gmail account there, right-click it and select "Properties". You can now view the password on the Key-tab of that properties window.

---

### Post by legalguy on 2009-07-16
mcduck, you rock!  That was it.  Turned out I wrote it down wrong.

I've tried to read up on keyrings before (to add 3rd party software sources and use launchpad.net) but never found much documentation on it.

Thanks again...and i've learned to count the beans of whoever responds....

---

