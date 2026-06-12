---
title: "E-mail recovery from failed upgrade!"
date: 2011-05-29
forum: General Help
---

### Post by trlrider on 2011-05-29
Hello,
My name is Louis, and new to the group!

While I have been using Fedora on my machine and Ubuntu on the wifes computer for some time, I am by no means a power user.  While I have some experience with the command line in Fedora, In Ubuntu it is nill!

The system at issue was a Ubuntu 10.10 which was running fine, until the attempted upgrade to 11.04.

What has happened!

Attempted an upgrade using the built software manager from 10.10 to 11.04.  Somewhere along the process after the install started, was close to finish the best I can tell, something in the PC failed, causing a power failure.

Subsequent attempts to recover the system showed failure to mount the drive.

Installed the harddrive in another tower, and was able to complete a fresh 11.04 install on a separate partition.  

The original partition appears to be intact and all data still on the drive, as I have been able to manually copy most of the files over to the new partition.

What I cannot figure out, is how to recover the e-mails from the previous version of Evolution to the new one in 11.04.  

Also missing is the Favourites files from Firefox!

How do I recover the e-mail files from the old partition?

How do I recover the favourites folders from the old partition?

Attempts to utilize import and recover functions built in have resulted in total frustration.

Thank you,

Louis

---

### Post by dFlyer on 2011-05-29
If you know the command line with fedora than you know the command line with ubuntu. The main different is fedora uses rpm for it packages and su for root. Ubuntu uses deb for it packages and sudo for root. I know this isn't helping much, but I believe evolution in 10.10 saved it mail in a folder in your home directory .evolution and 11.04 saves it in .gconf/apps/evolutions also in your home folder.

---

### Post by trlrider on 2011-05-29
dFlyer,
Thanks, for the location of the files!  That was my biggest problem, not knowing where Evolution saved them.
Although, copying those did not solve the problem with the missing e-mails.  I am still missing something somewhere!

On another note, you did get me on the correct path to find and restore the missing favourites in Firefox.

One issue down, one to go!

Thanks,

Louis

---

