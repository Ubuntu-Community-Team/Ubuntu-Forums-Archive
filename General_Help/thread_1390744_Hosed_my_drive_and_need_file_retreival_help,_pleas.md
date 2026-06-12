---
title: "Hosed my drive and need file retreival help, please!"
date: 2010-01-26
forum: General Help
---

### Post by zami on 2010-01-26
Hose my drive and need file retreival help, please!

Skipping over how I get into this predicament... 

I have booted from the LiveCD, and I can see my entire Ubuntu partition is intact.  I have *one* file I need from this entire partion.  I can see the directory, but I don't have "permission" to do anything with it.

Can someone please tell me how I can get this directory?  I've got an external hard drive I can copy it too, I just need permissions.

Permissions say
"
Owner: 1000-user #1000
Group: 1000
Others:
SELinux context: unknown
Last changed: unkown
You are not the owner, so you cannot change these permissions.
"

Please tell me I can bully my way into there somehow!
If it makes any difference I do have the root password that directory would have been locked with.  (Actually I'm confused why this directory is locked and so many others aren't - it's just a folder that sat on my desktop.)

Thanks

-zami

---

### Post by t4thfavor on 2010-01-26
sudo cp -a mydir /myExternaldir

you will get it all sudo is for Super User Do so you will be allowed to do anything, even it it's bad.

Be careful. and you will get the files you need.

---

### Post by zami on 2010-01-26
> **t4thfavor said:**
> sudo cp -a mydir /myExternaldir

you will get it all sudo is for Super User Do so you will be allowed to do anything, even it it's bad.

Be careful. and you will get the files you need.
PERFECT!!

Thank you, thank you, thank you!!

For kicks... check out the oddball location that file was in

/media/37267ebd-77e3-46b4-93a5-e219b439e313/home/laura/Desktop/Duncan

it used to just be /home/Desktop/Duncan

Now I feel free to tinker with recovering the drive or wiping it clean - it was just one file holding me back.  (Everything else is backed up.)

Thank you!!

:guitar:

-zami

---

### Post by t4thfavor on 2010-01-26
That big string is the UUID of the mounted drive. Its a unique key for identifying that drive on your syetem. 

the /media is the default location where the ubuntu distro mounts external media. 

Make sure the files got onto the removable as with the livecd you will lost them at reboot if you only copy them to the home dir.

---

### Post by zami on 2010-01-26
> **t4thfavor said:**
> That big string is the UUID of the mounted drive. Its a unique key for identifying that drive on your syetem. 

the /media is the default location where the ubuntu distro mounts external media. 

Make sure the files got onto the removable as with the livecd you will lost them at reboot if you only copy them to the home dir.

Thanks!  I'm familiar with finding things mounted under /media, but that long string of gibberish threw me.  What was really odd was other items that had been sitting side by side with that folder did *not* have a UUID (thank you, going to have to look that up) in their location, and didn't have "locks".  Just the one directory I wanted to get something from.  

Anyhow, that was a fantastic last ditch save-my-file command and it worked great, and I'm back to a nice fresh dual-booting install.  (With a day of updates ahead of me.)  No files lost.  :D

Thanks again!

-zami

---

