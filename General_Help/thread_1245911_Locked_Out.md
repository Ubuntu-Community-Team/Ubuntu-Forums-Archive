---
title: "Locked Out"
date: 2009-08-21
forum: General Help
---

### Post by marshcaptain on 2009-08-21
I have just reinstalled Ubuntu after it crashed and refused to boot but now I can not log in. Somehow my password and username which not too long ago I wrote and accepted, has now become useless and Ubuntu is refusing me access.

I have tried using the recovery console and changed my password but it refuses me access to change my username. It says command prompt not recognise every time and my password works only sometimes. 

I would like some help before I jump ship and leave Linux. Thank you.

---

### Post by SkippoGuangiacomo on 2009-08-21
Might it be that you forgot the password you typed, or that you had accidentally capslock on and now it's probably impossible to recover the password?

Given that you just re-installed ubuntu and that a brand new re-install will take you approx 40 min would it be a possibility for you to re-install and pay attention when you type in user name and password.

I say this because I had the same accident last week, I do not know how to change password but reinstalling making sure that I did type what I wanted for password worked... 

I hope this helps.

---

### Post by gdoc on 2009-08-21
Hi,
If you press esc when your computer is loading it will open the grub menu. Then select restore. Then open terminal with root. Then type ls /home/. Your user name should show up. Type passwd username. You will now have the option to enter your new password. 
Hope this helps!

G

---

### Post by imogenisabelle on 2009-09-15
Hi, I have the same problem and have gone to various tutorials but no GRUB screen comes up when I start up. I have a Dell Mini Inspiron 9 and when I hold down the ESC key for long enough I get the Boot Menu (options are: Hard Drive, USB Storage, CD/DVD/CD-RW, Removable Devices and Network Boot).

On my Dell startup screen it says: Press 2 for Setup, press 0 for Boot Menu, and when I press 2 I get the PhoenixBIOS Setup Utility (tabs are: Main, Advanced, Security, Boot and Exit. There is an option of "Set User Password" on Security, but it is in grey so not highlightable...

Any help would be much appreciated! Feel like a complete idiot for forgetting it in the first place!

---

