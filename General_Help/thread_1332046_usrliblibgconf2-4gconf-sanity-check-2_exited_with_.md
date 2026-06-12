---
title: "/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with error status 256"
date: 2009-11-19
forum: General Help
---

### Post by daveb_za on 2009-11-19
**Hey: first post here, linux n00b, thanks in advance for any help. Kind of long explanation follows but I'm not really sure what my problem is, so I kind of threw out everything that I thought was relevant. Here goes:**
 
**I'm trying to login into my clean install of Karmic, and after sorting out my Nvidia graphics card issues, when the GNOME desktop starts up it shows a warning that my desktop doesn't have battery power levels configured (I have a desktop, though, no battery), and then this message pops up:**
 
**/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with error status 256**
 
**I can't login to the desktop sessions at all, even with a newly created user created through the command line, who should have all the permissions. **
 
**My system is a dual boot with vista home basic, and I had karmic installed through WUBI initially, but I didn't have much joy with it. I removed that, and used the live CD installer to give me the 32-bit version (it's all I can run on my system). I have however been able to get the Live CD sessions working perfectly - after quite a lot of fiddling- and I can still boot in through the Live Cd and inspect the file system of my installed Karmic while in these sessions. **
 
**I've been fiddling with this problem for a week now, and checked the other threads in this forum. No joy. **
 
**What I've been able to see from using the live cd (and nano in the command line of my Karmic install) to inspect my /etc/gconf/gconf.xml.system directory is that this directory is empty. There are no files in it, and I think this may be the problem. **
 
**What I've been trying to do so far has mainly revolved around **
 
**chmod 755 /etc/gconf/gconf.xml.system**
 
**I've also tried some chown commands. Much of what I've tried has com from[COLOR=blue] [/COLOR][[COLOR=blue]this thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1147553").**
 
**I've tried to modify the directory in nano, but it's empty. **
 
**I'm a total n00b at this, and any help would be greatly appreciated. I'm not sure what's relevant, so if you need any more info about this issue, let me know. **
 
**I'm also happy re-installing Karmic, or downgrading to Jaunty, if that would help - but I'd need to be told how to do this, as my previous experience with Ubuntu has been through WUBI (a Hardy Heron install).**

---

### Post by daveb_za on 2009-11-21
So, still having this issue. I have run a dist-upgrade, though, and now I'm noticing that when I log into the system through the command line, I'm getting this message:

No directory, logging in with HOME=/
-bash:cannot create temp file for here-document: no space left on device.

I still haev loads of space on my hard disk, but I resized for a dual boot using the guided partition method when I installed Karmic. it gave me an 8.5 gb install, and since this was default I thought this would be fine.

I've created new users, and tried to login with them, but nothing gets past the Sanity error. And now I'm starting to feel the effects on my own sanity, I think...

Again, thanks in advance for any relplies to this.

---

### Post by daveb_za on 2009-11-23
Bump. And also, would it be easier to re-install, possibly even going for an olde Ubuntu version, over this installation? Would that wreck my master boot record, and give me issues at startup?

---

### Post by daveb_za on 2009-11-24
Solved. I reinstalled Hardy over this partition. But thanks for all the help guys, scintillating dialogue.

---

### Post by tomverweij on 2009-12-19
Hi,

Maybe it makes you happy that I encountered the same symptoms.
I'm testing 9.10 on a older laptop and got notice earlier that diskspace was low.
I'm guessing this has something to do with how I installed on this test system (leaving a large partition unused).
So now I'm reinstalling using all diskspace available.
Anyway, nice word "scintillating".

Cheers
Tom

---

### Post by jayarajk on 2010-10-19
Did anything with /tmp....
The following worked for me..
chmod 1777 /tmp

---

