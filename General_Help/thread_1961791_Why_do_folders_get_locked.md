---
title: "Why do folders get locked?"
date: 2012-04-19
forum: General Help
---

### Post by carmenin87 on 2012-04-19
Could someone take a look at this image of one of my folders:

[http://tinypic.com/r/2me3fwn/5](http://tinypic.com/r/2me3fwn/5)

Why do my folders get locked like this with no permissions.  In this instance, Dropbox automatically created the folder but in other cases, I've created a folder over the network and the same problem occurs.

Also, how can I easily delete these locked folders?  When I right click, delete, I get permission denied.

---

### Post by ammofreak on 2012-04-19
Hi ):P _Here is what I do_: open terminal ([COLOR="Red"]Ctrl+Alt+t[/COLOR]), type in *sudo -i*, hit Enter key, type in password (Enter key), & finally, type in  *gksudo nautilus* (Enter key). Nautilus opens up with root privileges. You can now go to any folder & delete it. Also by right-clicking on any folder, open Properties, then Permissions, you should be able to set permissions too.;)

PS: folder permissions are set depending on where the folder(s) is/are saved. For example, anything saved in /home/ will be accessible. However, anything saved in File System will need root privileges for security reasons.

---

### Post by carmenin87 on 2012-04-20
> **ammofreak said:**
> PS: folder permissions are set depending on where the folder(s) is/are saved. For example, anything saved in /home/ will be accessible. However, anything saved in File System will need root privileges for security reasons.

Thanks, just before I saw your response, I found the below command which worked as well:

sudo chown -R yourname directory

In terms of why they get locked, does that mean that the "desktop" is not part of the /home/ folder?

This morning, just before I left the house for the day, I started copying files from a Win 7 machine to a folder on desktop on the Ubuntu machine and I can see it is locked as well.

---

### Post by Roasted on 2012-04-20
How exactly are you copying files to/from your drive when they get locked? Not Dropbox in particular, but over the network instances. Explain what you're doing step by step so it can paint a more thorough picture and maybe we can help isolate the cause.

---

### Post by mastablasta on 2012-04-20
> **carmenin87 said:**
> Thanks, just before I saw your response, I found the below command which worked as well:

sudo chown -R yourname directory

In terms of why they get locked, does that mean that the "desktop" is not part of the /home/ folder?

This morning, just before I left the house for the day, I started copying files from a Win 7 machine to a folder on desktop on the Ubuntu machine and I can see it is locked as well.

they get locked for you because they are owned (created) by another user. using sudo you have temporary accesss to folders from all users.

chown is htere to change folder/file propperties

---

### Post by raja.genupula on 2012-04-20
> **mastablasta said:**
> they get locked for you because they are owned (created) by another user. using sudo you have temporary accesss to folders from all users.

chown is htere to change folder/file propperties

Yeah for more information you can use this as reference [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by carmenin87 on 2012-04-20
@Roasted - In terms of the steps, on the Windows 7 machine, I right click a folder and select copy.  I then click on run and type \\10.1.1.2\share and press enter

At this point, I paste the files and the copy process begins.

I move files across my home network from one Windows workstation to another all of the time and don't have this issue.

It is only when I copy files to an Ubuntu workstation using this method that I have this issue.

Is there no way to prevent this problem?  Running that command I listed below isn't hard, but it is an unnecessary step, at least I think so.

Thank you

---

### Post by Roasted on 2012-04-23
Oh, you're moving the files under Dropbox. I'm not sure how Dropbox manages to copy the files. If you utilize Samba on the local network, Samba can mimic the same user as long as you log in as that user.

For example, say your Ubuntu machine is up and your user is Frank. If Samba is set up, and Frank is added as a Samba user, you pushing files from Win7 to Ubuntu will come across as owned by Frank.

---

