---
title: "booting problems"
date: 2010-06-26
forum: General Help
---

### Post by kat4568 on 2010-06-26
I am new to Ubuntu, I have Ubuntu on a Dell 420 Work Station, which I am hoping to make as a Linux only computer.
I have loaded and played a little with Ubuntu.
Today I went to log on again and now I have an open boot loop. All I'm getting is a login window, I add my password and it loop back to the login window.
What can I do to fix this problem?
Thanks, Ken

---

### Post by hansdown on 2010-06-26
Welcome to the forum kat4568.

If your login window is like this screenshot, you have to enter your username, hit enter, then your password, and enter again.


If your login window shows your username, either left click it, and enter your password, then enter, or hit enter, then password, then hit enter.

---

### Post by kat4568 on 2010-06-26
Thanks hansdown,
No that didn't work. The Ubuntu login is displayed, after loging in, the Ubuntu logo shifts to the right then back to the login window.

---

### Post by hansdown on 2010-06-26
> **kat4568 said:**
> Thanks hansdown,
No that didn't work. The Ubuntu login is displayed, after loging in, the Ubuntu logo shifts to the right then back to the login window.

Hold tight kat4568.

Someone should be able to help.

Could you please post your make and model of computer, and which version of ubuntu you are using?

---

### Post by Leppie on 2010-06-26
at the login screen press the keys CTRL+ALT+F2 together to drop to a terminal.
login with your  normal account, then rename the .gconf directory:
```
mv .gconf .old-gconf
```
type the exit command to logoff:
```
exit
```
then press ALT+F7 to return to the graphical interface and try to log in.

if you can login, you will no longer have your personalized settings.

---

### Post by kat4568 on 2010-06-27
Thanks for your help, I'm still trying to get around this boot problem.
Hansdown, my Dell is an old model, It's a 420 Workstation, P-III 798 Omhz, 640 mb ram, 320 GB hd, Chipset Inter i840, BIO's A14.
I am looking at buying another computer, what computer seems to work best with Ubuntu?
Thanks,
Ken

---

### Post by dragos240 on 2010-06-27
Actually, it looks to me like you may have an issue with gnome. Push the select session button, and hit failsafe terminal, login, if it logs in, try reinstalling gnome.

---

### Post by hansdown on 2010-06-27
> **kat4568 said:**
> Thanks for your help, I'm still trying to get around this boot problem.
Hansdown, my Dell is an old model, It's a 420 Workstation, P-III 798 Omhz, 640 mb ram, 320 GB hd, Chipset Inter i840, BIO's A14.
I am looking at buying another computer, what computer seems to work best with Ubuntu?
Thanks,
Ken

My last few computers all have intel graphics, which seem to work very well.

I tend to stay away from ati, amd.

Nvidia used to work well, but sometimes need tweaking.

---

### Post by kat4568 on 2010-06-28
Well, I seemed to have solved to Ubuntu booting problem by switching to Mint 8. For some reason, and I'm not knocking Ubuntu. Later I will reinstall Ubuntu and dual boot the 2 programs.
Thanks for your help,
Ken

---

