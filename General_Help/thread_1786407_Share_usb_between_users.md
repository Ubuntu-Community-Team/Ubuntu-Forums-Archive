---
title: "Share usb between users"
date: 2011-06-19
forum: General Help
---

### Post by JuanitoMint on 2011-06-19
Hi there I've been looking for a solution to this but haven't found any,here is the scenario my wife and I share the same pc and both have our fast usb stick (thumb drive or usb drive) with our mail and pidgin profiles in it so it's portable, but only one user can mount the usb devices at a time, if I plug my then udev seems to restart and mount both usb drives to me and my wife get disconnected 
1. solution may be to have the system mount the usb drives instead the active user (don't know howto)
 

any ideas??? this could be a common scenario where 2 users with active sessions want to share a usb drive.

Thanks in advance.
Juan

---

### Post by idoitprone on 2011-06-19
Great a permission problem....


I will say a few things about your problem. Since you are using a fat filesystem in that usb, am i correct? Fat do not understand linux permissions. To hack this problem once mounted, the usb gives full permission to the user that mounts it. This is a problem as other users cannot use the same usb, since it only allows the user to have execute, write, and read. I can suggest a couple of solutions but it not really that helpful and you may need someone else

First solution, add both of you to the storage group and change the permissions, so all storage groups users can use the usb.

Second solution, change the mount permission so everyone can modify the usb

Note: the first solution is more secure

I do not know how to write udev rules right now, i can might research it and tell you what to do, but i feeling lazy right now

---

