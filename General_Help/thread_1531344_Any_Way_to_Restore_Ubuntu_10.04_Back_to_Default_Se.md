---
title: "Any Way to Restore Ubuntu 10.04 Back to Default Settings?"
date: 2010-07-14
forum: General Help
---

### Post by Volfan94 on 2010-07-14
Hey guys, I was watching a video on YouTube about how to make Ubuntu 10.04 look and feel like Mac OSX. I thought it looked pretty cool, so I followed the video step by step. It involved downloading a file called Mac4Lin from Sourceforge.net and a few steps involved the use of the terminal. I thought I would like the new look and everything, but I actually like the default Lucid Lynx look better. Is there any way to restore everything back to defaults?

---

### Post by Volfan94 on 2010-07-14
Can anyone possibly help?

---

### Post by borth92 on 2010-07-14
open terminal and type:
**rm -rf .gnome .gnome2 .gconf .gconfd .metacity**

---

### Post by Volfan94 on 2010-07-14
> **borth92 said:**
> open terminal and type:
**rm -rf .gnome .gnome2 .gconf .gconfd .metacity**

Will this uninstall my programs or will it simply change the look of Ubuntu?

---

### Post by borth92 on 2010-07-14
This should just reset the settings, you should not lose any files or programs, because it is reconfiguring the gnome and metacity files, which are the files that make the desktop look how it does

---

### Post by Volfan94 on 2010-07-15
> **borth92 said:**
> open terminal and type:
**rm -rf .gnome .gnome2 .gconf .gconfd .metacity**

That didn't do anything.

---

### Post by Rubi1200 on 2010-07-15
Try using Synaptic to remove the packages but just be careful that you don't remove anything needed for other programs to work.

You can also try searching and/or asking for help on the project's help page:

[http://sourceforge.net/projects/mac4lin/forums/forum/730185](http://sourceforge.net/projects/mac4lin/forums/forum/730185)

---

### Post by Rubi1200 on 2010-07-15
> **borth92 said:**
> open terminal and type:
**rm -rf .gnome .gnome2 .gconf .gconfd .metacity**

This is quite a "harsh" way of resetting things.

> These commands are "safe" in that they reset your settings, but note that it's pretty harsh. It'll reset all of your GNOME settings and the settings of any GNOME applications that you've used (including your Pidgin/Empathy user accounts and so on). 

I'd recommend doing something like

 	Code:
 	mv .gnome .gnome_backup 
for each mentioned directory, that way if you later figure out you didn't want to do this, you can reverse the mv command and restore a backup.
 originally mentioned by jdong (Ubuntu admin)

---

### Post by borth92 on 2010-07-15
> **Rubi1200 said:**
> This is quite a "harsh" way of resetting things.

 originally mentioned by jdong (Ubuntu admin)

don't you need to set up the backup manually ahead of time?

---

