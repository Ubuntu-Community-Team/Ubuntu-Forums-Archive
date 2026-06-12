---
title: "Ubuntu 11.10- freezes on load"
date: 2011-10-16
forum: General Help
---

### Post by keelx on 2011-10-16
I'm not sure if it is actually freezing, or just taking a really long time to load, but here's what's happening:
I installed ubuntu 11.10 from the update manager, and now, when I restart the computer, it shows a blank purple screen, then the splash screen for about a second, and then goes black, with all the loading messages and what not. It stops in different places each time, but after some loading messages, it just stops loading. The text and everything is still there, it is just either inactive or frozen. It won't let me type anything, because it is still in the loading up phase, and there is no mouse. How do I get out of this and fix this and keep it from happening again?

Just for information, the message it freezes on most of the time is this, however it varies:

start: Unknown job: S90binfmt-support

---

### Post by espenore on 2011-10-17
I have a similar problem. Ubuntu 11.10 stops at the same spot every time I try to boot, before the logon-dialog-window appears:

sh: Can't open /home/lokalespen/apache-tomcat-6.0.29/bin/startup.sh

Now it is not important to me to get Tomcat up and running now, so I wonder if there are any magic buttons I can use to get Ubuntu to start without trying to start tomcat (and other possible problem-generators)?

Espen Ore

---

### Post by JackNBox on 2011-10-17
Add me to the list of people with this problem.  Upgraded from 11.04 to 11.10.  The upgrade seemed to go fine, rebooted when prompted and now I get to the Ubuntu logo and it just hangs.  Can not even figure out how to even get to the recovery mode.  This is my work computer and I am dead in the water.  Grrr.

---

### Post by forkmantis on 2011-10-17
I had this issue this morning before work.  I didn't have much time, but I tried CTRL-ALT-F6 to see if I could get to a terminal.  I could not.

Once I got to work, out of curiosity, I tried ssh-ing into my machine.  It worked.  I tried:

> sudo apt-get upgrade

I got some error, which I don't remember specifically, but it suggested trying something to the effect of "sudo dpkg -a" (forgive me for not remembering exactly, but I was at work and wasn't really expecting any of this to work, so I didn't take notes)

After running the command, I was able to continue the upgrade.  After the upgrade completed, I did a

> sudo shutdown -r now

When I got home, I was happy to be greeted by a login screen.

---

### Post by irongiant14 on 2011-10-21
Any other ideas for those of us without SSH installed?

---

### Post by kubilay@xanadu on 2011-10-22
Same problem here I chose to upgrade my Dell E6500 laptop from 11.04 to 11.10 and bammm! Black screen with the message:
[B]
start: Unknown job: S90binfmt-support 
* Checking batter state...[/B]

and just hangs there! phew!

Anyone can help?

Thank you!

---

