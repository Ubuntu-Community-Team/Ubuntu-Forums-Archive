---
title: "is there any alternative to &quot;startupmanager&quot; that works in ubuntu 11.04?"
date: 2011-07-22
forum: General Help
---

### Post by dmdevotee on 2011-07-22
I did a fresh installation of ubuntu 11.04 desktop and i installed the package "startupmanager" to change boot option. This software doesn't work for me now, but when i tried it in ubuntu 10.10 it worked.

is there an alternative to that software? thanks

---

### Post by flipper T on 2011-07-22
what are you trying to do ?

in what way does startup manager not work anymore ?

ps works fine for me in 11.04

---

### Post by Frogs Hair on 2011-07-22
For changing my login screen background screen and greeter icon I use Ubuntu Tweak . For changing my _Plymouth_ splash screen I use Zorin Splash Manager. I did not have success using startup manger in 10.04 , so I have never installed it since . If it still works thats great.

---

### Post by drs305 on 2011-07-22
Try Grub Customizer. Click the link in my signature line. It was written for Grub2, has been updated to work with Grub 1.99 and submenus, and is very versatile.

If you need to manually edit Grub 1.99, see these threads:
[Grub 1.99 Submenus]("http://ubuntuforums.org/showthread.php?p=10720316#post10720316")
[Grub 2 Drop-In Backgrounds & Font Selection]("http://ubuntuforums.org/showthread.php?t=1739412")

---

### Post by dmdevotee on 2011-07-22
> **drs305 said:**
> Try Grub Customizer. Click the link in my signature line. It was written for Grub2, has been updated to work with Grub 1.99 and submenus, and is very versatile.

If you need to manually edit Grub 1.99, see these threads:
[Grub 1.99 Submenus]("http://ubuntuforums.org/showthread.php?p=10720316#post10720316")
[Grub 2 Drop-In Backgrounds & Font Selection]("http://ubuntuforums.org/showthread.php?t=1739412")


thanks. the package grup-pc is installed but i can't find how to execute it. thanks

---

### Post by drs305 on 2011-07-22
> **dmdevotee said:**
> thanks. the package grup-pc is installed but i can't find how to execute it. thanks

grub-pc is Grub 2, which should be installed on your system unless you overrode the defaults. You can see what version of Grub 2 you are using from the Grub menu (at the top) or by running "grub-install -v".

You shouldn't really need to run the 'grub-pc' package unless you are trying to install G2 for the first time.

The command most often employed by the user of Grub 2 is:
```
sudo update-grub
```
This lets G2 update the main configuration file (the Grub menu you see at boot). You have to run this command any time you make changes to the grub configuration settings.

If you need or want to learn more about Grub 2, check out the links in my signature line. "Basics" covers most of what you would normally need, "Tasks" provides much less detail but covers how to tweak the main things that a user might desire.

The good news is that Grub Customizer can probably make the changes you need and you don't have to learn about Grub 2. You can learn about Grub Customizer from the "Customizer" link in my signature line.

---

