---
title: "Looking for Boot Sequence start-to-finish resources"
date: 2009-09-28
forum: General Help
---

### Post by narnie on 2009-09-28
Hello,

I have been looking for resources that would hold my hand through through the Ubuntu boot process, from grub -> initially booting the kernel -> gdm (and how that starts the gnome {or whichever WM} environment) -> Gnome startup

I found many older resources from earlier versions of Ubuntu, but much has changed.

I would like to understand this more, but I started on this task in hopes of trying to figure out how the ecryptfs is automatically mounted on Private. Where is it in which script?

I would like to stop that behaviour and have it _**ME**_ who decides when to mount it, esp if I might be away from my computer and forget to unmount it and then another root user could see my "Privates" hehe.

I have tried running ecryptfs-umount-private at gnome-session startup, but for some reason when running it as a startup application, it leaves the tokens in the keyring and all one has to do is click on "Access your Private..." and there you are. If you then umount it, the keyring is cleared as it should be. I'd rather not have it mounted in the first place (I'll be posting this question on the security forum).

Any tutorials on the Ubuntu boot process (not how to speed it up or anything like that, just stock step-by-step how it boots and what it calls) would be much appreciated.

Yours,
Narnie

---

### Post by narnie on 2009-09-28
> **narnie said:**
> 
I would like to understand this more, but I started on this task in hopes of trying to figure out how the ecryptfs is automatically mounted on Private. Where is it in which script?

I would like to stop that behaviour and have it _**ME**_ who decides when to mount it, esp if I might be away from my computer and forget to unmount it and then another root user could see my "Privates" hehe.

I have tried running ecryptfs-umount-private at gnome-session startup, but for some reason when running it as a startup application, it leaves the tokens in the keyring and all one has to do is click on "Access your Private..." and there you are. If you then umount it, the keyring is cleared as it should be. I'd rather not have it mounted in the first place (I'll be posting this question on the security forum).



I was able to find a way to do this for those intersted. See thread:
[http://ubuntuforums.org/showthread.php?p=8018769#post8018769]("http://ubuntuforums.org/showthread.php?p=8018769#post8018769")

For the solution for the automounting problem on a system level.

Narnie

---

### Post by narnie on 2009-10-04
Does this mean there aren't any or no one knows or are keeping it all to themselves?

---

