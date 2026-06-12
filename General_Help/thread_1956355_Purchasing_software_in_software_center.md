---
title: "Purchasing software in software center"
date: 2012-04-10
forum: General Help
---

### Post by Runthantrip on 2012-04-10
[SIZE=2]Hello, 
   I have been a long time reader of this forum and I first want to thank all you wonderful people that have helped me with so many problems. I am running Ubuntu 11.10, and I have no complaints. This is the first problem that I could not find an answer to: I was trying to purchase software in the software center, but then software center crashes. I click buy, the screen shows[/SIZE] "connecting to payment center"  for about a half a minute then software  center closes. I have tried reinstalling the software center, but the  problem prosists.  I know that it is not a problem with my Internet  connection, because I am using it to write this post. I have looked in  my system log and found the same message every time this happens. the  message is as follows:

[COLOR=#000000][FONT=Ubuntu]  [/FONT][/COLOR][CENTER][SIZE=2][CENTER][COLOR=#000000][FONT=Ubuntu]'Apr 10 19:56:42  kernel: [781666.789811] software-center[23558]: segfault at bfe60000 ip 0359f1f3 sp bfe5bae0 error 6 in libwebkitgtk-3.0.so.0.7.3[24dc000+142c000]'[/FONT][/COLOR][/CENTER]
[/SIZE][LEFT][SIZE=2]
 Any ideas why this is happening? I recently updated the kernel and ran into some video card issues that I corrected, but is there any chance that the kernel update could be causing this problem? I also would like to thank everybody for their help in advance.[/SIZE]
[/LEFT]
[/CENTER]

---

### Post by Runthantrip on 2012-04-15
no ideas yet huh?

---

### Post by Paqman on 2012-04-15
Looks like a problem with webkit, which is a browser engine that Software Centre must be using to do the purchase process.

Since you can make it crash predictably what I suggest is that you temporarily enable the automated crash handler, apport. Open a terminal and paste this in:
```
sudo service apport start force_start=1
```
Then go through the purchase process until you get your crash. Apport should pop up and allow you to file a bug, and it will append all the technical details that the package maintainers will need to fix it. If there is already a bug report, apport will direct you to it, and you can mark it as "affects me too", which will bump it's priority up. There may be details of a workaround in the bug comments, so have a read.

You'll need a Launchpad account to file the bug.

---

### Post by Runthantrip on 2012-04-15
> Then go through the purchase process until you get your crash. Apport should pop up and allow you to file a bug, and it will append all the technical details that the package maintainers will need to fix it. If there is already a bug report, apport will direct you to it, and you can mark it as "affects me too", which will bump it's priority up. There may be details of a workaround in the bug comments, so have a read.

You'll need a Launchpad account to file the bug.

I tried this but apport never popped up.

---

### Post by Runthantrip on 2012-04-16
I still need some help with this one.

---

### Post by ubuntu27 on 2012-04-16
I never had problem purchasing thigns from Software Centre.
Perhaps there is some misconfiguration or corruption...

First, open the Terminal, and then run Software Centre from it by typing

```
software-center
```
and do what you were trying to do.

Copy and paste everything that shows in there here.

-------------------------------
Now, let's try our luck by deleting some config files. 
Warning: This will delete your configuration files, which means that it will "restore" your user configuration to the default. (Your personal changes or settings gets lost)


1) Open Nautilus (The file browser)
2) Make hidden files visible by going to
View menu-----> Show hidden files.  Or you could just tap Ctrl+H

3) Delete the following files:

.gconf
.local
.cache
.config

4) Log Out

5) Login again

6) Open Software Centre from the terminal again, and try to do what you wanted to do. If any error or crash occurs, copy and paste here.


Good luck!

---

### Post by Runthantrip on 2012-04-16
ok, So i followed the above steps. this is what is returned in the terminal.

>  software-center
2012-04-16 22:23:07,691 - softwarecenter.ui.gtk3.em - INFO - EM's: 17 15 21
2012-04-16 22:23:22,360 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2012-04-16 22:23:22,839 - softwarecenter.ui.gtk3.utils - INFO - Softwarecenter style provider for ambiance Gtk theme: /usr/share/software-center/ui/gtk3/css/softwarecenter.css
2012-04-16 22:23:43,559 - softwarecenter.ui.gtk3.app - INFO - software-center-agent finished with status 0
Segmentation fault
still confused... :(

The segmentation fault appears just after software center closes. also there is still no crash report from apport.

---

### Post by Runthantrip on 2012-04-16
At a loss for anything else to do I thought maybe the ubuntu-sso-client was not up to date so I: ```
 Sudo apt-get update ubuntu-sso-client
``` terminal returned sso was already up to date. I then removed the sso and software-center completely.```
sudo apt-get remove ubuntu-sso-client 
 sudo apt-get install ubuntu-sso-client 
apt-get install software-center
```  after reinstalling both the problem still is unresolved.

---

### Post by ubuntu27 on 2012-04-17
Create a new user account at

System Settings--------> User Accounts


Let's see if it works with a new user. Since you are installing programs, make sure that the new user has the ability to be an administrator.

---

### Post by Runthantrip on 2012-04-18
I set up a new user account and I still come up with the same errors. I know have set-up an account to buy software. I have bought software before. maybe I could set-up a new account, but I don't remember how to. Also, can it be set up on the Internet, and not through software center.

---

### Post by ubuntu27 on 2012-04-18
I hope that someone more knowledgeable than me will hope in.


I don't know what else to suggest you do except to an OS reinstall.
Since, Ubuntu 12.04 is just around the corner, you might want to install that. 


By the way, does the crash or error occur no matter what product you try to buy? And which product/package is it?

---

### Post by Runthantrip on 2012-04-22
The crash has happened no matter which product I try to buy, I have tried to buy three different games. steel sky, uplink, and a third who's name I forget. I think I will wait for 12.04 to roll out before I attempt an OS install. i want to thank you for helping to the extent of your knowledge. I'm  sure it is a simple fix that I would have never thought of.

---

### Post by mutex023 on 2012-04-23
Can you see if there is an upgrade for "libwebkitgtk" available in Synaptic Package Manager ? If so right click the libwebkitgtk package in synaptic and click 'Upgrade' and hit apply.

---

