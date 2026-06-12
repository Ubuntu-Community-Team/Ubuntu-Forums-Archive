---
title: "No automatic updates?"
date: 2010-05-17
forum: General Help
---

### Post by oshirowanen on 2010-05-17
Dear Community,

I have Ubuntu 10.04 64 bit installed on a test machine as I do not want to replace my installations of Ubuntu 8.04 32 bit until I know for sure that Ubuntu 10.04 64 bit is working properly.

I've been using my test setup for a few weeks now and I just realized that I have not been receiving any automated daily notifications of available updates.  So I thought to myself, maybe there are no updates yet...

I tried

sudo aptitude update
sudo aptitude full-upgrade

and it came up with many available updates...

I checked

system > administration > software sources > updates

and "Check for updates" is checked and it already has "Daily" in the dropdown box.

So my question is, why am I not been notified about any updated available?

I am getting the same problem when I install Ubuntu 10.04 64 bit via VirtualBox.  I have not tried the 32 bit version yet.

---

### Post by plucky on 2010-05-17
From the [Release Notes](http://www.ubuntu.com/getubuntu/releasenotes/1004) and has been the same since Jaunty.

> **Change in notifications of available updates**

Ubuntu 10.04 LTS launches update-manager directly to handle package updates, instead of displaying a notification icon in the GNOME panel. Users are notified of security updates on a daily basis, but for updates that are not security-related, users will only be prompted once a week.   

Users who wish to continue receiving update notifications in the previous manner can restore the earlier behavior using the following command:   

gconftool -s --type bool /apps/update-notifier/auto_launch false

(This change was made in Ubuntu 9.04.)   

Good Luck

---

### Post by oshirowanen on 2010-05-17
Ah IC,  But the update-manager has not automatically appeared ever since I installed 10.04 when it was released.

---

### Post by jubilee33 on 2010-05-17
> **oshirowanen said:**
> Ah IC,  But the update-manager has not automatically appeared ever since I installed 10.04 when it was released.

My two 64bit computers have the same problem.  I do believe I have seen other posts talking about the update manager not showing up on 64bit 10.04 systems.  It's a reported bug.  You can do a bit search around the forum.  I don't remember if there's a workaround, however, except for launching the update manager by yourself or updating through the terminal.  Sorry I can't be of more help.

---

### Post by oshirowanen on 2010-05-17
> **jubilee33 said:**
> My two 64bit computers have the same problem.  I do believe I have seen other posts talking about the update manager not showing up on 64bit 10.04 systems.  It's a reported bug.  You can do a bit search around the forum.  I don't remember if there's a workaround, however, except for launching the update manager by yourself or updating through the terminal.  Sorry I can't be of more help.

Thanks, that's all I wanted to know, i.e. it's a reported bug.  I'll do some searching, hopefully it will be fixed by 10.04.1.

---

