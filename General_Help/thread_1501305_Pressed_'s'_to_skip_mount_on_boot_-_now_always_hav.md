---
title: "Pressed 's' to skip mount on boot - now always have to mount manually"
date: 2010-06-04
forum: General Help
---

### Post by infinitejones on 2010-06-04
I was fiddling around with /etc/fstab and on re-boot I got a message during boot-up telling me there was an error - I pressed 's' to skip, everything booted fine, and I've now fixed /etc/fstab.

However... now it skips mounting my NFS mounts every time I boot. Not the end of the world, and easily fixed with a quick 'sudo mount -a', but it's a bit annoying.

How can I go back to auto-mounting on boot?

---

### Post by IndieRockSteve on 2010-06-05
bump!
this is ***ridiculously*** annoying and a huuuuge regression. I was planning on running 10.04 but now if there is no way to stop this from happening I'm going to go back to 9.10

---

### Post by sdowney717 on 2010-06-05
you could create an executable script file with that line in it and put this into startup programs.

you might just be able to add the command in here also.

---

### Post by IndieRockSteve on 2010-06-05
> **sdowney717 said:**
> you could create an executable script file with that line in it and put this into startup programs.

you might just be able to add the command in here also.

no, I should not have to. fstab is where one has traditionally, for quite a while now, placed filesystem mounting information. It worked in 9.10 and works in every other distribution I've seen, this is a bug, or an omission on the part of Ubuntu with no seeming way to fix it.

I think it's time to go back to 9.10, way too many issues with 10.04 that make the system a pita to use.

---

### Post by sdowney717 on 2010-06-05
sounds like you already made up your mind.
I thought fstab was deprecated in some fashion now.

---

### Post by infinitejones on 2010-06-06
So it sounds like this is a "feature" then, and not just me being unable to find the setting somewhere?

---

### Post by Elfy on 2010-06-06
What does it say on boot when you try and boot with the nfs in fstab? Are you sure you fixed fstab?

Not a feature as far as I know - mine mount fine here.

---

### Post by infinitejones on 2010-06-07
It doesn't say anything - it just gets on and boots. 

But once everything's started, I have to do sudo mount -a to mount two remote NFS mounts and /var/backup, which is on a separate ext4 partition of the same hard drive (and don't worry, that's not my only backup location!)

---

