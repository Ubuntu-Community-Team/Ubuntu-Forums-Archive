---
title: "Eclipse Menus Not Appearing in Ubuntu 10.10 Netbook Edition"
date: 2010-10-16
forum: General Help
---

### Post by mpwoodward on 2010-10-16
Hi there--I just installed Ubuntu 10.10 netbook edition on an Asus 1000HE netbook, and overall it's really nice.

I'm a developer so I downloaded the latest Eclipse (meaning downloaded from eclipse.org; didn't install via apt-get) and fired it up. It launches fine, but the entire top menu bar (File, Edit, Source, Refactor, etc.) doesn't show up. All that appears is a "File" menu and the only option there is "Close." I tried resizing the window to see if maybe they were just hidden but that didn't help.

Picture's worth 1000 words of course:
[http://dl.dropbox.com/u/151780/eclipse_menu_issue.png](http://dl.dropbox.com/u/151780/eclipse_menu_issue.png)

Any ideas? This netbook isn't what I develop on every day by any means, but it's really handy when I travel so it's kind of important that Eclipse works.

Thanks for an excellent release!

---

### Post by kerry_s on 2010-10-16
when you add something new, you need to log out & back in, for it to show in the menu.

---

### Post by mpwoodward on 2010-10-16
Thanks, I'll give that a shot, but just so it's clear it's not that Eclipse isn't showing up *in* a menu, it's that the *menus in eclipse* aren't showing up. :-) Just wanted to make sure that's clear.

---

### Post by mpwoodward on 2010-10-17
No luck with restarting. My suspicion is that maybe the Unity stuff doesn't play nicely with Eclipse, but since I know nothing of the technical details that's just a hunch. A workaround would be great.

---

### Post by cu_ on 2010-10-17
I have the same problem.  It is quite frustrating really.  I thought it was because I "upgraded" from 10.04.  I spent the whole afternoon installing 10.10 fresh and still no menus in eclipse.

OP, please post if you had any luck.

---

### Post by dotsha on 2010-10-18
The workaround here worked for me:

[https://bugs.launchpad.net/ubuntu/+source/appmenu-gtk/+bug/659931](https://bugs.launchpad.net/ubuntu/+source/appmenu-gtk/+bug/659931)

i.e. start eclipse as follows:

UBUNTU_MENUPROXY= /usr/local/eclipse/eclipse

All on one line, space after the equals, with the last part pointing to where your eclipse executable is.

---

### Post by mpwoodward on 2010-10-18
Excellent! Thanks so much for the response. Giving it a shot now. If I don't reply again, that means it worked. ;-)

Thanks!

---

### Post by mpwoodward on 2010-10-18
I lied--want to let you know this did work like a champ, so thanks for the info!

---

### Post by myron317 on 2010-10-22
Alright, so I will preface this that I am a noob at the finer details of linux.  I am having this problem and when attempting to execute the command listed above, I get a no such file or directory error.  I have attempted to google this, but am honestly not entirely sure where to start.  Any suggestions would be appreciated.  Thanks!

---

### Post by retr0virus on 2010-10-25
> **myron317 said:**
> Alright, so I will preface this that I am a noob at the finer details of linux.  I am having this problem and when attempting to execute the command listed above, I get a no such file or directory error.  I have attempted to google this, but am honestly not entirely sure where to start.  Any suggestions would be appreciated.  Thanks!
The path /usr/local/eclipse/eclipse does only exist if the package were installed in that directory and does not exists if you unpacked the downloaded .tar.gz in your home directory or somewhere else. How do you start eclipse?

With the right path after UBUNTU_MENUPROXY= the workaround worked for me. But I hope they fix it soon...

---

### Post by satyapd on 2011-07-08
> **myron317 said:**
> Alright, so I will preface this that I am a noob at the finer details of linux.  I am having this problem and when attempting to execute the command listed above, I get a no such file or directory error.  I have attempted to google this, but am honestly not entirely sure where to start.  Any suggestions would be appreciated.  Thanks!

Try this. It worked for me.
---
export UBUNTU_MENUPROXY=/home/satya/eclipse/eclipse
Here, /home/satya/eclipse folder contains my executable file 'eclipse'.

---

