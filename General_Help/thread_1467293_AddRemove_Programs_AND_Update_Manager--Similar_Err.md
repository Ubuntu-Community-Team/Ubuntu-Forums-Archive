---
title: "Add/Remove Programs AND Update Manager--Similar Error."
date: 2010-04-30
forum: General Help
---

### Post by zuko1234 on 2010-04-30
In both of these areas, when I actually go to "Install" the things, whether it be adding or removing programs, or doing the Update Manager, I get the same error as soon as I click "Install," and it fails to install any selected programs/updates.

Here is the following error:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I have not been able to find this "sudo dpkg" file to manually run, or have failed to find help elsewhere.  Sorry I'm not as good with this as I should be, as it's probably a very simple error that will make me feel blonde.

Any help is greatly appreciated--Thanks in advance!

---

### Post by jmszr on 2010-04-30
zuko1234,

To fix your problem you need to Copy and Paste this command in the terminal (Applications > Accessories > Terminal) :

```
sudo dpkg --configure -a
``` 
 

Press Enter and then type your password when prompted (it won't be visible-security) and press Enter.

That should do it.

---

### Post by zuko1234 on 2010-05-01
Thank you so much, jmszr! Problem completely fixed. So I'm guessing the Terminal is pretty much like the Command Prompt in Windows?

Thanks a lot, got everything going now. :D

---

