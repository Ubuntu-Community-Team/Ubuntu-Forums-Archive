---
title: "General configuration questions"
date: 2011-02-06
forum: General Help
---

### Post by ctracy on 2011-02-06
First of all I'm using Lubunu, but I think the answers to these questions will be the same for any variant (even an unofficial one like Lubuntu) of Ubuntu.

I've installed Lubuntu to an external USB hard drive so I can take it with me.

I have 3 questions.

When my system boots it tries to mount a disk partition that is not there. How do I stop it from doing this?

The system tries to check the disk every time I boot. How do I set this to something more reasonable?

My graphical login has session options such as other desktops. Is there a way I can set up an option in this that will let me boot into the console?

Thanks.

---

### Post by dcstar on 2011-02-07
> **ctracy said:**
> First of all I'm using Lubunu, but I think the answers to these questions will be the same for any variant (even an unofficial one like Lubuntu) of Ubuntu.

I've installed Lubuntu to an external USB hard drive so I can take it with me.

I have 3 questions.

[LIST=1]
[*]When my system boots it tries to mount a disk partition that is not there. How do I stop it from doing this?

[*]The system tries to check the disk every time I boot. How do I set this to something more reasonable?

[*]My graphical login has session options such as other desktops. Is there a way I can set up an option in this that will let me boot into the console?
[/LIST]

Thanks.

[LIST=1]
[*]Edit the /etc/fstab file
[*]Only "Dirty" disks are attempted to be checked every time - see if this is related to issue #1.
[*]You can search out options to boot to a command prompt in the forum or on the Internet.
[/LIST]

---

