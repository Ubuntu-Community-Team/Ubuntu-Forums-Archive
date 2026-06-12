---
title: "Windows not showing up in the boot screen"
date: 2011-08-16
forum: General Help
---

### Post by chromefourfour on 2011-08-16
I installed wubi to try ubuntu out. It didn't show up in the windows boot manager, so I manually went to startup options and changed the default os from windows to ubuntu, trough right clicking My Computer, and going into the "advanced" tab. Now I don't know how to revert back to windows because this does not have a "My Computer". Any help would be appreciated, thanks in advance :). My os is windows XP professional, by the way.

---

### Post by chromefourfour on 2011-08-16
Can anyone help?

---

### Post by garvinrick4 on 2011-08-16
Try installing 
```
sudo apt-get install startupmanager
```Open the app and
See if you can set Windows as default.
#Should have given you a way to select windows or ubuntu at boot.
I know where you changed from windows to ubuntu.
Never did change that did not know it would take away the boot menu.
If does not work this will kick the thread up to front. 

##By the way you can see Windows drives in Ubuntu file system in WUBI in host
open the file system the open host and there windows be.

## By the way put WUBI in your title from now on and usually users by the name of "bcbc" or "rubi1200"
will chime in. They are the resident WUBI experts around here, can ask them also. I know rubi1200 and
he is glad to help any user.

---

### Post by chromefourfour on 2011-08-16
Thanks for you reply. I've already tried doing that though startupmanager, but it does not show up there. All my windows files are in host so I should be able to switch back.
Is there not a wubi at the front of this thread? I'm pretty sure i can see one

---

### Post by garvinrick4 on 2011-08-16
> Is there not a wubi at the front of this thread?Sorry, there is a [wubi]. 

                                                  > Thanks for you reply. I've already tried doing that though startupmanager, but it does not show up thereyea, figured that was only in grub2 on a partition install but just in case gave the thread a bump.
See you have a duplicate thread going also and bcbc is there he should get you going. Have a nice day.

---

### Post by Mark Phelps on 2011-08-16
If you start pressing F8 as soon as you boot, that should force the display of a selection screen in Windows, in which you can then change the default back to Windows.

---

