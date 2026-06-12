---
title: "any way to see if updates are unstable?"
date: 2012-08-16
forum: General Help
---

### Post by LLCoolJeff on 2012-08-16
for example I think there were just some updates issued today, because I am showing 32 updates in the update manager.

I am worried about one of these eventually causing a system crash, does this sort of thing happen? Should I shy away from installing updates unless I need them? is there any way to see beforehand if they will cause instability?

I'm pretty new to linux in general so all of these issues are new to me, and I do not know what to expect...

Thanks for the help

---

### Post by Vaphell on 2012-08-16
in general you should update, that's how bugs and security holes are fixed. Updates going bad unfortunately happen from time to time, usually related to kernel or graphics stack, especially proprietary drivers coming from nvidia and amd which often don't match the version of the server managing gfx stuff - botched resolution, no acceleration and even text-only mode do happen.

If you want to be relatively safe you need to scan the list of packages to update/install and if you see anything kernel/linux or xorg/<gfx-vendor> related, wait few days. If there are complains on forums, wait few days.
You can uncheck packages in update manager, so you can upgrade non-essential programs that don't endanger stability of the system right off the bat but leave core stuff on hold.

---

### Post by LLCoolJeff on 2012-08-16
ok thanks for the reply. that pretty much answers my question...If the worst case were to happen, does ubuntu have any kind of recovery "go back in time" feature in the bootloader or anything?

---

### Post by codemaniac on 2012-08-16
> **LLCoolJeff said:**
> ok thanks for the reply. that pretty much answers my question...If the worst case were to happen, does ubuntu have any kind of recovery "go back in time" feature in the bootloader or anything?

'Clonezilla Live' enables a user to clone a single computer's storage  media, or a single partition on the media, to a separate medium device.  The cloned data can be saved as an image-file or as a duplicated copy of  the data. The data can be saved to locally attached storage device, an ssh server, a samba server or an NFS file-share. The clone file can then be used to restore the original when needed.[]("http://en.wikipedia.org/wiki/Clonezilla#cite_note-4")

[http://clonezilla.org/clonezilla-live.php](http://clonezilla.org/clonezilla-live.php)

---

### Post by QIII on 2012-08-16
A caveat:

Partial Upgrades are often the quickest way of ***borking*** your system.

***Don't do partial upgrades*** if you don't want to take a chance on learning more than you would like to on a machine you are using for every day use..  Wait a day and see if the dependency issues and such are addressed in the repos.

---

### Post by LLCoolJeff on 2012-08-17
> **QIII said:**
> A caveat:

Partial Upgrades are often the quickest way of ***borking*** your system.

***Don't do partial upgrades*** if you don't want to take a chance on learning more than you would like to on a machine you are using for every day use..  Wait a day and see if the dependency issues and such are addressed in the repos.

ok and where would I look to see these isues and the repos? it may be obvious but this is all new to me...

Thanks

---

### Post by QIII on 2012-08-17
If you are using the Update Manager, you will see something to the effect that "These packages are not going to be installed" and the Manager will ask you if you want to do a partial.  You don't.

If you do it from the terminal, you will see a message something like "These packages will be held back" followed by a list.

The way you check to see if it is resolved is just to try again later and see if you're still being told it's a partial.

This often occurs for a few hours when there is a kernel update

This is the "new to Ubuntu" version of what to do.  For now.  Patience.

---

### Post by walker195 on 2012-08-17
most updates only get better and are safe you only get a bad one every now and then

---

### Post by Scott Harrison on 2012-08-17
> **walker195 said:**
> most updates only get better and are safe you only get a bad one every now and then
This is true but for an inexperienced user, this can be quite distressing.

For example, I am running a proprietary Nvidia display driver on my Inspiron 7720. I performed an update recently without paying too much attention, upon reboot, my laptop had reverted to 800x600 graphics. I was able to quickly fix this (I'm a computer technician) and reminded myself to check updates more closely for installing.

On the other hand, my girlfriend (who uses Ubuntu) could have done the same and been stressed that she'd broken her system, just by installing updates.

I'm not saying that Canonical should change the way they organise updates to cater to Nvidia, however, some sort of warning in the Update Manager would not go astray.

---

### Post by mastablasta on 2012-08-17
another option is to mark only security updates. those are safe.
 
Linux Mint has a nice organisation where you can quickly review problematic uipdates and chose to install safe ones only. i still dont' understand why cannonical doesn't have a similar thing.

---

### Post by Scott Harrison on 2012-08-17
> **mastablasta said:**
> another option is to mark only security updates. those are safe.
 
Linux Mint has a nice organisation where you can quickly review problematic uipdates and chose to install safe ones only. i still dont' understand why cannonical doesn't have a similar thing.
This would be a good solution. Even something to improve the situation where I have to go through each update and "untick" what I don't want.

---

