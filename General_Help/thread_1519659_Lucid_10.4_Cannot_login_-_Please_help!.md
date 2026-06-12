---
title: "Lucid 10.4 Cannot login - Please help!"
date: 2010-06-28
forum: General Help
---

### Post by jc1234 on 2010-06-28
Hello,

I previously had ubuntu 9.11 (Karmic) installed and a couple weeks ago upgraded to 10.4 (Lucid). Upgrade went smoothly, everythig was working fine.
Today I did an update using update package manager, and rebooted.
The system starts up, the login screen is displayed, and it prompts me for my password.
I enter my password, the screen goes blank for a few minutes, then returns to the login screen!.

NOTE: Its not incorrect password, as when I enter incorrect password I get a message telling me so.

When I press ctrl-alt-f1, I can login to terminal window OK.



Can anyone help me please?

Thankyou.

---

### Post by yperionas on 2010-08-13
Try here with the solutions given and give me your feedback. I am having the same problem but haven't managed yet to go through it.

That would be #10 here: [http://kubuntuforums.net/forums/inde...opic=3099811.0]("http://kubuntuforums.net/forums/index.php?topic=3099811.0")

---

### Post by gabouel on 2010-09-24
I am having the same issue.
It seems that there may be several different causes to this problem.

Here is what I tried so far (not in this order):
[LIST]
[*] log to failsafe session => nogo
[*] log to failsafe from recovery => nogo
[*] sudo dpkg-reconfigure gdm => nogo
[*] sudo spkg-reconfigure gnome-* => nogo
[*] sudo apt-get remove --purge gdm; sudo apt-get install gdm => nogo
[*] Recovery mode > Root shell > /etc/init.d/gdm start => nogo
[*] cd ~;chown -R <user>:<user> * => nogo
[/LIST]
**I finally managed to get a workaround** but I am not very happy with it:

[LIST=1]
[*] edit /etc/X11/Xwrapper.config and change allow_users from "console" to "anybody"
[*] From terminal (CTRL + ALT + F1 on gdm): sudo apt-get remove --purge gdm
[*] reboot
[*] logon and type startx start gnome.
[/LIST]
But I guess it can help.

Note: One of the reasons why I am not happy with this method is that I cannot use xset from the shelf. I get the message 'xset:  unable to open display ""'. To make it work, I have to set the DISPLAY var to :0.0 (in ~/.profile for instance).

To me, it looks like something is going wrong between gdm and X but I cannot figure out what is really wrong and how to fix it.

I really hope that some clever people will find a solution for this. Reinstalling my system is just not an option for me.

---

