---
title: "help with grub install script"
date: 2010-07-30
forum: General Help
---

### Post by qdub on 2010-07-30
I'm working on a script that will install grub and I'm running into a couple of issues:
 
1. this is on a raid0 and my plan is to get the raid info from /dev/mapper and store that variable in an answer file which will then be used to provide the input for the grub command. My problem is that I can't remember how to tell the grub command to get it's input from the answer file (been years since I did this).
 
2. After the script configures the /target directory I have to chroot into it, which basically stops the script. I've done a lot of searching on how to get around this but haven't found a very good solution so far. Any ideas?
 
In case anyone is wondering, I'm stuck with grub1 since my raid volume names contain underscores which grub2 doesn't like.
 
Thanks.

---

### Post by prodigy_ on 2010-07-30
Grub legacy doesn't like to be installed on raid volumes. In fact, I'm not even sure it's possible.

Are you certain that underscores are the actual problem? My devices in /dev/mapper have those too but Grub2 doesn't mind.

---

### Post by qdub on 2010-07-30
Thanks for the reply.
 
You're correct in that grub legacy doesn't like raid devices, but you can get legacy working via manual grub install. I uncheck install grub in advanced options at the install summary, then choose keep testing at the prompt and go in and mount the raid volume with / into /target etc.. (I can throw in the rest if you're interested).
 
I'm pretty sure it's the underscores since grub2 seems to cut the volume names off at the first underscore and I've read posts where people were having the same issues. It seems to depend on the type of controller for some reason.

---

