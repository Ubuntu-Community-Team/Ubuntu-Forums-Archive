---
title: "Blank Screen after gnome-shell install, cannot logon"
date: 2011-11-30
forum: General Help
---

### Post by chesl73 on 2011-11-30
Hi all,
 
I've got myself in a bit of a jam, I'm hoping someone can help me.
I have Ubuntu 11.10, I have a single user setup and the user is set to auto logon.
I then decided I'd like to install and try out the gnome-shell so I installed it which worked fine and then I logged out from my one and only user and at the logon screen I then selected to use the newly installed gnome-shell. 
When I then logged on, all I can now see is my desktop background image and nothing else, I can right-click and see the context menu to create a new folder but that's it. I cannot see or do anything. I've tried ctrl-alt-T to bring up a terminal window but nothing. 
I'm now in a loop I can't get out of. I can't logout again and all I can do is reboot which then automatically logs me in using the gnome-shell again and I'm back where I started.
Does anyone have any ideas how I can break this cycle? I tried going into recovery mode and running sudo apt-get remove gnome-shell but I just got some errors. 
 
Any suggestions would be appreciated.
 
Thanks

---

### Post by Liova99 on 2011-11-30
I Don't know where is your problem, the best you can do is try with a Live CD or USB to log in and back up your data,then wait 1 day maby someone helps you out or reinstall the system.... The bad think of linux is that you dont have a restore system like on windows, and if you make a big miskeke it's some time hard to solve it. 
If you don't Like Unity, beter try Gnome 3 and install Shell extenssions like botom panel. see on youtube there is a lot of videos. Sorry thut i can't help you...

---

### Post by chesl73 on 2011-12-02
Anyone?

---

### Post by j1mst1x on 2011-12-06
Hey,

Try getting a remote terminal from another computer over ssh and then enter the command:

sudo /usr/lib/lightdm/lightdm-set-defaults -s ubuntu

That should reset your auto-login to unity and then reset the computer. Hopefully this will regain you normal logon to your computer.  

Command was found in this article: [http://www.addictivetips.com/ubuntu-linux-tips/how-to-auto-login-to-gnome-in-ubuntu-11-10-tip/](http://www.addictivetips.com/ubuntu-linux-tips/how-to-auto-login-to-gnome-in-ubuntu-11-10-tip/) 

Hope I'm not to late,

-j1mst1x

---

