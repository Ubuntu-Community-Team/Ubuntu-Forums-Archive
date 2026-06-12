---
title: "Ubuntu 11.10 won't install. Black screen"
date: 2012-02-18
forum: General Help
---

### Post by PomPWNius on 2012-02-18
I have been trying to install Ubuntu 11.10 on my new Lenovo laptop.  The specs are
 CPU - AMD A-8 3500M
GPU - AMD Radeon HD 6620G
4gb RAM
Currently on WIndows 7 64 bit (YUCK)
 So I put the 32bit Ubuntu 11.10 onto a cd-r, and booted it.  I got to  the menu screen and hit Install. Screen eventually turned off, so I  looked around on the internet and found I have to use the nomodeset  option.  I did, and it worked.  Ubuntu installed and then it said  something like "Installation successful, you must reboot now". So I did  and the screen went to the grub menu. I hit the first option and the  screen went all purple, then turned off again.  So once again I looked  around on the internet and found I have to edit the first option in the  grub menu and change the "quit splash" to "nomodeset".  So I did that  and the screen said loading, please wait. I waited like a half hour and  then everything dissapeared and the screen went black.  The backlight  stayed on though this time.  What do I have to do? I have been dying to  get ubuntu on this laptop, windows sucks so much.

---

### Post by Paddy Landau on 2012-02-19
I'm sorry, I don't know exactly what is happening, but as no one else has answered you I'll tell what I would try.

You are installing 32-bit Ubuntu. Try the 64-bit version; 4Gb RAM is plenty to run Ubuntu 64-bit.

I can't guarantee that this will make a difference, but give it a bash.

Does the Live CD work when you choose "Try Ubuntu"?

---

