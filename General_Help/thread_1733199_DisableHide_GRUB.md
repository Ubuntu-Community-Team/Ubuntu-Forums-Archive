---
title: "Disable/Hide GRUB"
date: 2011-04-19
forum: General Help
---

### Post by Mangler13 on 2011-04-19
Alright, so I have kind of a strange request I've been Googling forums for a bit now and haven't found anything so I decided to post. 

I am currently running a dual boot Windows 7 and Ubuntu 10.10 environment and was wondering if there is a way to disable/hide the GRUB menu when my computer is booting. Ideally, I would like to attach a key binding to it instead should I want to see the GRUB menu and change which OS to boot up. So basically, without pressing the key binding while the BIOS is loading it will just boot to whatever is first on my grub menu.

Is there a way to do this?

---

### Post by yetiman64 on 2011-04-19
> **Mangler13 said:**
> Alright, so I have kind of a strange request I've been Googling forums for a bit now and haven't found anything so I decided to post. 

I am currently running a dual boot Windows 7 and Ubuntu 10.10 environment and was wondering if there is a way to disable/hide the GRUB menu when my computer is booting. Ideally, I would like to attach a key binding to it instead should I want to see the GRUB menu and change which OS to boot up. So basically, without pressing the key binding while the BIOS is loading it will just boot to whatever is first on my grub menu.

Is there a way to do this?

Yes, edit /etc/default/grub using the command
```
gksu gedit /etc/default/grub
```and change the line,
> #GRUB_HIDDEN_TIMEOUT=0to> GRUB_HIDDEN_TIMEOUT=0You can reduce the grub timeout setting "GRUB_TIMEOUT=" if you wish, but please **do not** set it to 0 if Windows is set as the default boot. Doing so will stop you booting into Ubuntu and it is Ubuntu that controls grub (do you see the potential for trouble ?). 3 is a good low setting to set for "GRUB_TIMEOUT=" while still allowing you time to hit the **SHIFT key** to bring up the grub screen (the key binding you ask about in your post)

To make your settings work you must issue the command in terminal
```
sudo update-grub
```Check this post for a good example [http://ubuntuforums.org/showpost.php?p=9351135&postcount=3](http://ubuntuforums.org/showpost.php?p=9351135&postcount=3).

---

