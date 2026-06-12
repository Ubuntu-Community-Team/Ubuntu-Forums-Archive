---
title: "Is there a way we can make ubuntu to use the classic su instead of sudo?"
date: 2012-05-05
forum: General Help
---

### Post by deepaknet on 2012-05-05
This is a related thread to [http://ubuntuforums.org/showthread.php?p=11909901#post11909901](http://ubuntuforums.org/showthread.php?p=11909901#post11909901).

I was just wondering if it is possible to use the old su style and escape to # shell instead of the new style sudo?

---

### Post by hawkmage on 2012-05-05
What are you trying to do?  You can still use su.  

Using su requires you to know the password of the user you are trying to run as.  

Using sudo you normally need to only know your own password.

---

### Post by HereInOz on 2012-05-05
This may not be an answer to your question, but you are able to invoke a su scenario by entering

sudo su

enter your password and that will put you into a superuser situation in the terminal.

---

### Post by deepaknet on 2012-05-05
HereinOz: Thank you. I think that precisely matches the classic su mode.

---

### Post by lisati on 2012-05-05
Have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by hawkmage on 2012-05-05
> **deepaknet said:**
> HereinOz: Thank you. I think that precisely matches the classic su mode.
"sudo su" is not the classic su mode.  

The only user that has ever been able to run su without a password is root.

---

