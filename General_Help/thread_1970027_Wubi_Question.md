---
title: "Wubi Question"
date: 2012-04-30
forum: General Help
---

### Post by Skregzilla on 2012-04-30
I downloaded Wubi to use 11.10 and decided to remove it. So far, I have used the EasyBCD program to remove the bootloader as well as going through command prompt and deleting it by its {GUID}. 

Now I am not sure how to get back the hard drive space that 11.10 used up. Any help would be greatly appreciated, thanks.

---

### Post by bcbc on 2012-04-30
Wubi comes with it's own uninstaller. It's in Control Panel, Add/remove programs under the entry "Ubuntu".

Or you can run: \ubuntu\uninstall-ubuntu.exe

But now that you've manually edited the BCD it will fail (fixed for 12.04, but your uninstaller will be 11.10 so it fails). So [keep going manually]("https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F") is what I'd suggest.

The hard drive space will be freed up when you remove \ubuntu

---

### Post by Frogs Hair on 2012-04-30
If there is nothing in control panel/programs open c programs and in in the Ubuntu folder you'll find the un-installer which has an Ubuntu logo. This happened to a friend when he wanted to install 12.04 on win 7. It's no a bad idea to run defrag after removal.

---

### Post by Skregzilla on 2012-04-30
Neither does it exist in program files or program files x86. I've also tried following the manual uninstallation and it does not exist in my registry.

---

### Post by bcbc on 2012-04-30
All the hard drive space is in the \ubuntu folder (on the 'drive' you installed on, usually C:\ubuntu). Deleting this will free up the space... unless you had some corruption problems, in which case Windows sometimes recovers the corrupted root.disk to a special recovery folder (that is hidden by default): *\found.000*. 

So if you're removed \ubuntu and still don't have the space returned, you can look there. Running chkdsk is not a bad idea if you suspect corruption.

---

