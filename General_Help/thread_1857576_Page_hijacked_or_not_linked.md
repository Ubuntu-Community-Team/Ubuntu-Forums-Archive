---
title: "Page hijacked or not linked"
date: 2011-10-10
forum: General Help
---

### Post by weezyrider on 2011-10-10
Trying to straighten out a DVD error, finally find some appropriate files that were asked for. Clicked on multiverse.list and got this. Are you guys into pediatric medicine now?????

[I]Overview

Purpose

The goal of the Pediatric Perioperative Cardiac Arrest (POCA) Registry is to collect a large set of cases of cardiac arrests and deaths of pediatric patients during the administration of or recovery from anesthesia in order to investigate the possible relationship of anesthesia to these incidents.[/I]
That's a big help with my problem which might lead to ADULT cardiac arrest!!!

---

### Post by drs305 on 2011-10-10
The text you quoted was in a repository file called multiverse.list? 

Which distro/release are you using? Any idea how the contents made it into the file?

---

### Post by weezyrider on 2011-10-10
Yes, it was under multiverse.list. I'm using Meerkat. I am trying to get the DVD player to work, and the printed out the instructions from the multimedia forum. I think the multiverse download or whatever itself was buggered. Now synaptic, update, etc. don't work.

It doesn't look like a normal hijack

In fact, searching under multiverse, most of the files look buggered. I''d have to send a screen shot.

I'm still confused with syntax, so I just changed the distro and the  commands for universe to multiverse

---

### Post by weezyrider on 2011-10-10
Here's the error message. I've got a red circle with a minus sign in it on the menu bar.


E: Type '<html><!--' is not known on line 1 in source list /etc/apt/sources.list.d/multiverse.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

Report where?

---

### Post by weezyrider on 2011-10-10
How do I get this mess off the computer? I don't feel like reinstalling and hunting for everything again.

---

### Post by drs305 on 2011-10-10
I'd just delete the entire /etc/apt/sources.list.d/multiverse.list file. It's not one you need. You can use nautilus as root to remove/move it.
```

gksu nautilus /etc/apt/sources.list.d/
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by weezyrider on 2011-10-10
Doesn't work
gksu nautilus /etc/apt/sources.list.d/
sudo apt-get update
sudo apt-get upgrade
(nautilus:1984): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
eedesktop.ConsoleKit.Manager.GeneralError: Unable to lookup session information for process '1984'

---

### Post by weezyrider on 2011-10-10
I feel that this mess is getting out of hand. Nothing wants to work, so how do I back up stuff so I don't have to start from scratch? I can't even redownload anything as update manager ISN"T WORKING!!!

---

### Post by drs305 on 2011-10-10
> **weezyrider said:**
> I feel that this mess is getting out of hand. Nothing wants to work, so how do I back up stuff so I don't have to start from scratch? I can't even redownload anything as update manager ISN"T WORKING!!!

Can you open Software Sources either by command line or via Synaptic > Settings Repositories or Ubuntu Software Center > Settings or via terminal: gksu software-properties-gtk 

In the Other Software (Third Party) tab, untick everything. In the Ubuntu Software tab, untick Multiverse, then press CLOSE.

If that doesn't work you can move the /etc/apt/sources.list.d folder elsewhere, and move the /etc/apt/sources.list somewhere else and generate a new one from this site:
[http://repogen.simplylinux.ch/]("http://repogen.simplylinux.ch/")

---

### Post by weezyrider on 2011-10-10
> **drs305 said:**
> Can you open Software Sources either by command line or via Synaptic > Settings Repositories or Ubuntu Software Center > Settings or via terminal: gksu software-properties-gtk 

In the Other Software (Third Party) tab, untick everything. In the Ubuntu Software tab, untick Multiverse, then press CLOSE.

If that doesn't work you can move the /etc/apt/sources.list.d folder elsewhere, and move the /etc/apt/sources.list somewhere else and generate a new one from this site:
[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

 Nope, it's just plain stuck! Like I said, I've got this stupid red circle with a minus sign in it, and if I tell it to update, open anything, all I get is a little box that says CLOSE.  I tried using the safe mode to fix. I've been reading install screens for years (even windows) so I can read that fast. There's files that safe mode can't find.

---

### Post by weezyrider on 2011-10-10
I can't delete the files - No permission.  I can't move them, can't check anything. Can get online, use other programs, but this is making me so dratted mad that I'm ready to toss the computer.  I thought Linux was supposed to avoid this behavior. 
I didn't type in a url, used a command in terminal, Ubuntu went to the site.

I need to get the stupid DVD player/recorder going!

---

### Post by drs305 on 2011-10-10
Have you lost admin privileges (can you run any root commands)?
How about "sudo blkid" ?

If not, check these two items:
1. 
```
cat /etc/hosts
```
One of the entries should be:
> 127.0.1.1  <your computer's hostname>
Example: 127.0.1.1 mydell
There should be nothing appended to the end of your hostname

```
groups
```
If you don't see "admin" among the returns, reboot to the recovery mode, drop to a root shell, and add yourself to the 'admin' group.
```

adduser <yourusername> admin
```
Example: adduser drs305 admin

From the root shell, you can also open nano to edit /etc/hosts if the hostname is missing or corrupted.
```
nano /etc/hosts
```
After making the change, CTRL-x, Y to save.

---

### Post by weezyrider on 2011-10-11
admin is there, and there is nothing after computer name as you said.

---

### Post by jazzon on 2011-10-11
from a command prompt:
```
sudo mv /etc/apt/sources.list.d/multiverse.list ~/Desktop/
```

should solve and move the folder to your Desktop.  DOnt delete it as you may have stumbled upon a security issue that someone will contact you about.  Probably here.

---

### Post by jazzon on 2011-10-11
how did the multiverse.list file get to that folder?  Did you save it from a web site and put it there?

---

### Post by weezyrider on 2011-10-11
There's a tutorial in the multimedia section. It said to get multiverse. I replaced the commands for universe with multiverse and my distro. Ubuntu went and got it.

---

### Post by weezyrider on 2011-10-11
Didn't solve the problem. It says no such file or directory but a search for multiverse brings it up.

---

### Post by weezyrider on 2011-10-11
I've got a screen shot of the directory. How do I post it? I don;t feel like using FLICKR.

---

### Post by weezyrider on 2011-10-11
> **jazzon said:**
> from a command prompt:
```
sudo mv /etc/apt/sources.list.d/multiverse.list ~/Desktop/
```

should solve and move the folder to your Desktop.  DOnt delete it as you may have stumbled upon a security issue that someone will contact you about.  Probably here.

Doesn't work. Says no such file. I posted a pic of what comes up on a search. If that's a junk file, and Ubuntu doesn't see it, I should be able to delete it. Nope. If you want the file, you are welcome to it. Do I have to worry about identity theft?

---

### Post by weezyrider on 2011-10-11
It might have worked. Took it a while to do so. Did not move it on command. The file is now in the desktop folder. I can now open Synaptic, etc. Should I back this file up on a USB stick or something?

---

### Post by jazzon on 2011-10-11
please do for the moment ... i wanna check a fwew things.  Also can you post a link to the tutorial you were following.

And also do this

```
sudo apt-get update
```
email me the file at aragornnrogara at yahoo.com

---

### Post by weezyrider on 2011-10-11
I think this is the thread link
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
I printed out all 30+ pages It's what I printed from, not sure about 766683

Sent from my Yahoo acct.

---

### Post by egalvan on 2011-10-11
I just finished "upgrading" an IBM ThinkPad T60P from XP to Natty.
ran all the updates, then decided to check this problem you have.

following this tutorial that you cited..

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

after finishing, i popped in a DVD *"Hitman Unrated"*,
and VLC popped up and proceeded to play it perfectly.
The same thing happened the other times I've used that (excellent)
tutorial, BTW (I've been using it since Hardy days no less)

I did not have to substitute "natty" for anything,
so I'm not sure where you did so.,.
also, you say **It said to get multiverse**,
yet I read **click multiverse**.

Perhaps you used a different tutorial?
perhaps you mis-stepped somewhere?

---

### Post by weezyrider on 2011-10-12
This is the beginning of the tutorial. And since the links to be copied are for Karmic -----[B]


Here's the start: IMPORTANT: If you haven't already, you need to enable the Medibuntu repository. *The first command below is compatible with any version of Ubuntu, but the manual instructions are aimed at Ubuntu 9.10 Karmic Koala users, so if you are using a different version of Ubuntu, you will have to edit the sources accordingly.*[/B]* =*

I'm using Maverick. And I found out the DVD won't play due to the format recorded. 
I'm going to have to find a codec that will let me experiment with whatever form of DVIX Toshiba is using. The DVD plays on all the other DVD players in the house. Just not the computer players.

I couldn't click multiverse. It didn't turn up even in a search. It wasn't in Synaptic. So I tried to install it.

---

### Post by egalvan on 2011-10-17
> **weezyrider said:**
> This is the beginning of the tutorial. And since the links to be copied are for Karmic -----[B]


Here's the start: IMPORTANT: If you haven't already, you need to enable the Medibuntu repository. *[COLOR="Red"]The first command below is compatible with any version of Ubuntu[/COLOR], but the manual instructions are aimed at Ubuntu 9.10 Karmic Koala users, so if you are using a different version of Ubuntu, you will have to edit the sources accordingly.*[/B]* =*

I'm using Maverick. And I found out the DVD won't play due to the format recorded. 
I'm going to have to find a codec that will let me experiment with whatever form of DVIX Toshiba is using. The DVD plays on all the other DVD players in the house. Just not the computer players.

**I couldn't click multiverse. It didn't turn up even in a search. It wasn't in Synaptic. So I tried to install it.**


Multiverse isnt something you "install"... its a "repository" that you access..

Under Synaptic, go to the "repository" tab, and choose the one called "multiverse"

its definition is
"software restricted by copyright or legal issues"

And the tutorial you cited had Medibuntu installed in a way that was release-agnostic...
at the very start... [COLOR="Red"]IN RED[/COLOR]
The "manual commands " it cites are only used if the first set does not work,,,
again, i've never had that first set of commands fail to properly set up Medibuntu.

its worked for me ever since 8.04 Hardy Heron...

---

