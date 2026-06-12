---
title: "Linux ignoring Windows NTFS permissions &amp; security settings?"
date: 2010-04-26
forum: General Help
---

### Post by Rebelli0us on 2010-04-26
I have NTFS-protected directories under Windows. However under Linux, even though I'm not logged in as a Super-User, Ubuntu cheerfully mounts all NTFS partitions on this machine and EVERY computer on my home network. This gives my GUESTS complete access to all machines connected to my network: Nautilus -> Windows Network -> Workgroup -> Clicking on any computer Name gives access to windows' administrative shares C$, D$, etc. I've always known that Linux ignores Windows security, but... what is the solution?

---

### Post by oleink on 2010-04-26
go to your partition and type:
sudo chmod o-wx ______________
in the __________ type the name of the partition

---

### Post by oleink on 2010-04-26
Or if you're in media and looking at your windows partition and that is the only thing in your current directory you can just type:
sudo chmod o-wx *

---

### Post by mcduck on 2010-04-26
> **Rebelli0us said:**
> I have NTFS-protected directories under Windows. However under Linux, even though I'm not logged in as a Super-User, Ubuntu cheerfully mounts all NTFS partitions on this machine and EVERY computer on my home network. This gives my GUESTS complete access to all machines connected to my network: Nautilus -> Windows Network -> Workgroup -> Clicking on any computer Name gives access to windows' administrative shares C$, D$, etc. I've always known that Linux ignores Windows security, but... what is the solution?

Configure your Windows partition in /etc/fstab, and you'll be able to set it to mount with whatever permissions you want.

If you're not familiar with using fstab, here's a nice HowTo: [http://ubuntuforums.org/showthread.php?t=283131]("http://ubuntuforums.org/showthread.php?t=283131")

(trying to use chmod, as suggested in above post, is not going to do anything. NTFS doesn't understand ownerships & permissions as they are used on Unix/Linux systems, so the permissions are set for the whole partition at the time when it's mounted.)

---

### Post by Rebelli0us on 2010-04-26
Thanks, “chmod” and “fstab” looks much too technical. Assuming these commands work, what’s to prevent a GUEST user from using the same commands to acquire privileged access to machines on my home network?

---

### Post by Helkaluin on 2010-04-26
Once you've set up default mount permissions in fstab you should be safe. By default the fstab config file has permissions of write only by root.

---

### Post by Rebelli0us on 2010-04-26
Heloooo... what's to prevent a GUEST from plugging-in their own UN-configured laptop or booting any Windows machine on my home network with a Linux desktop CD??

---

### Post by bodhi.zazen on 2010-04-26
> **Rebelli0us said:**
> Thanks, “chmod” and “fstab” looks much too technical. Assuming these commands work, what’s to prevent a GUEST user from using the same commands to acquire privileged access to machines on my home network?

These things can only be set by root see

[RootSudo - Community Ubuntu Documentation]("https://help.ubuntu.com/community/RootSudo") 

The guest account does not have root (sudo) access.

If you give a guest access to your account and your password, then yes they can do what they want.

---

### Post by jerome1232 on 2010-04-26
> **Rebelli0us said:**
> Heloooo... what's to prevent a GUEST from plugging-in their own UN-configured laptop or booting any Windows machine on my home network with a Linux desktop CD??

If your shares don't require authentication then why do they need the linux cd, they could do the same from any Windows computer.

If you want some control on your network, a) don't share your entire drives, and b) require authentication for the shares.

---

### Post by Mark Phelps on 2010-04-26
> **Rebelli0us said:**
> Heloooo... what's to prevent a GUEST from plugging-in their own UN-configured laptop or booting any Windows machine on my home network with a Linux desktop CD??

If they have physical access to your network and/or machines, you're relying on encryption and/or account restrictions.

Also, you don't need a Linux CD; there are a host of other downloadable CDs out there that will not only grant access, they will allow the user to reset your machine userid/password combos.

If you really want to be paranoid, envision the case where you're at work all day, no-one is in your "home" to protect your stuff, someone gains entry, and has hours to remove your drives, copy them to other drives, restore the drives, and leave the place as they found it.

Once physical security has been compromised, anything other security is merely an inconvenience.

---

### Post by oleink on 2010-04-27
> **Rebelli0us said:**
> Thanks, “chmod” and “fstab” looks much too technical. Assuming these commands work, what’s to prevent a GUEST user from using the same commands to acquire privileged access to machines on my home network?

Well the way chmod works is it changes access rights (chmod: change mode) It will allow you to block others from accessing via terminal commands without being in your root name or being the main account holder for windows

---

### Post by jerome1232 on 2010-04-27
> **oleink said:**
> Well the way chmod works is it changes access rights (chmod: change mode) It will allow you to block others from accessing via terminal commands without being in your root name or being the main account holder for windows

chmod doesn't work for Microsoft filesystems. Permissions are set for the entire drive at mount time. (via fstab if your mounting it at boot time)

---

### Post by oleink on 2010-04-27
> **jerome1232 said:**
> chmod doesn't work for Microsoft filesystems. Permissions are set for the entire drive at mount time. (via fstab if your mounting it at boot time)

Actually sir they do.  They're just Linux permissions given.  Which means he only has to change 2 things instead of typing out the full dos commands

---

### Post by bodhi.zazen on 2010-04-27
> **oleink said:**
> Actually sir they do.  They're just Linux permissions given.  Which means he only has to change 2 things instead of typing out the full dos commands

No, chown and chmod will not work on a FAT or NTFS partition. No, they are not "just linux permissions given", it is more complex then that.

Here is a detailed explanation :

[http://www.tuxera.com/community/ntfs-3g-advanced/ownership-and-permissions/](http://www.tuxera.com/community/ntfs-3g-advanced/ownership-and-permissions/)

And for the reading impaired, skip to the very bottom of the page :

> User mapping features required for devices which may be plugged into  multiple Windows or Linux systems are not available yet, with the  exception of the single user default mapping.With FAT and NTFS you set ownership and permissions at the time of mounting, using uid=xxx,gid=yyy,umask=zzz. You can have some finer grained control with dmask an dfmask.

See : [man mount]("http://linux.die.net/man/8/mount")

---

### Post by oleink on 2010-04-27
> **bodhi.zazen said:**
> No, chown and chmod will not work on a FAT or NTFS partition. No, they are not "just linux permissions given", it is more complex then that.

Here is a detailed explanation :

[http://www.tuxera.com/community/ntfs-3g-advanced/ownership-and-permissions/](http://www.tuxera.com/community/ntfs-3g-advanced/ownership-and-permissions/)

And for the reading impaired, skip to the very bottom of the page :

With FAT and NTFS you set ownership and permissions at the time of mounting, using uid=xxx,gid=yyy,umask=zzz. You can have some finer grained control with dmask an dfmask.

See : [man mount]("http://linux.die.net/man/8/mount")

Correct but there is a way around that you can set permissions to the actually windows software and not just the partitioned space.  That is why there is AWRXYZM and a few more DOS commands for the same purpose.  They're used and effect our ability to do anything to them in linux too

---

### Post by ccw127 on 2010-04-27
Regardless, Mark above is totally 110 percent correct. Once physical security is compromised, all bets are off. There is nothing stopping anyone from walking in with a linux (or other) boot device, and browsing to there hearts content (among other things).

First thing that jumps to mind is encryption. You can take a look at something like truecrypt to encrypt the drives (or parts of). Then if someone mounts any drive without the key, its all just random garbage they see.

---

### Post by oleink on 2010-04-27
> **ccw127 said:**
> Regardless, Mark above is totally 110 percent correct. Once physical security is compromised, all bets are off. There is nothing stopping anyone from walking in with a linux (or other) boot device, and browsing to there hearts content (among other things).

First thing that jumps to mind is encryption. You can take a look at something like truecrypt to encrypt the drives (or parts of). Then if someone mounts any drive without the key, its all just random garbage they see.

I didn't say that I just said thats a type of security

---

### Post by ccw127 on 2010-04-27
Wasn't agreeing/ disagreeing with permission talk, just saying it doesn't really matter in this situation. The people he is worried about have physical access.

Chris

---

### Post by dcstar on 2010-04-28
> **ccw127 said:**
> Wasn't agreeing/ disagreeing with permission talk, just saying it doesn't really matter in this situation. The people he is worried about have physical access.


The solution remains the same: **Do not** have Shares and/or permissions on the shared files wide open.

Implement the security that is available and the security will work.

All this complaining is like saying that I have an open safe in my home and if people get through my front door they can access it.... der!

When I do a Nautilus -> Windows Network -> Workgroup -> from another Ubuntu machine on my network, all I get are the print$ share and the share I have specifically set up - my mounted Windows NTFS drive is not there because **I have not shared it**.

---

