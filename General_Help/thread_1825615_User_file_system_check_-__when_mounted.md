---
title: "User file system check -  when mounted??"
date: 2011-08-15
forum: General Help
---

### Post by candtalan on 2011-08-15
A non techie friend has helped an even less techie friend by contacting me by email to discuss an ailing laptop.

A few emails were exchanged, with more details, and it was not looking good because it seemed that suddenly the CD drive was not responding, nor any USB devices, the wireless icon was gone, but Ubuntu still seemed to work (for now), with wired ethernet also working. 

I was struggling to think of what could be done, with the favourite routes of Live CD and Live USB apparently gone.

After a few more hours - another email:
'It's now working! After so many reboots it checked disc for errors and repaired itself! Is there some way of doing that when needed anyway?'

A 'miracle'!
Much kudos for the boot up file system checks!

And now my question:
I see there is 'Disk Utility', and this would presumably fit the bill, but how does it do checks and repair when the damaged file system is being run, and is currently *mounted*? I thought utilities like fsck(?) could only be run on unmounted file systems?

Have I misunderstood the disk utility fs check repair function? And anyway, what might be a good answer to my (nontechie) friend's question 'After so many reboots it checked disc for errors and repaired itself! Is there some way of doing that when needed anyway?'

Comments appreciated  tia

For the record: (quote) It is a toshiba EA60-155 Model number PSA67E-00300C8J. He put in extra ram to install ubuntu. He thinks he may have deleted something! There is a 'trash' file on his USB drive with loads of stuff in it and he doesn't know how or why but because it won't now read the drive on her laptop we cant replace it! (end quote)

---

### Post by Bachstelze on 2011-08-15
YOU SHOULD NEVER FSCK A MOUNTED FILESYSTEM!

If you try, it will display a warning similar to the one above, but  a reminder never hurts. One way to force a fsck is by creating a file named forcefsck at the root of the filesystem you want to check (e.g. [font=monospace]sudo touch /forcefsck[/font], and rebooting.

---

### Post by candtalan on 2011-08-15
Thanks. For myself, I would unmount first. However, I am searching for a good answer to guide my non techie friend.... hoping of course to avoid any mention of a terminal.  Is there something useful for this is in the grub boot up menu 'recovery mode'?

---

### Post by candtalan on 2011-08-15
I see in Ubuntu 11.04 that after choosing the startup Grub menu line 'Recovery Mode', there is in fact an entry for 'fsck' (at reboot) in the recovery menu, which is really good, and would answer my problem. However, my non techie friend is currently using Ubuntu 10.04.x and I see in this version the recovery mode menu entries do not include this useful entry. 

However I think I will offer that to my friend and say that all they have to do in that recovery mode is to 
1) choose 'Drop to root shell prompt'
2) tab key (to highlight OK)
3) type
shutdown  -rF  now
(then hit return key)(note spaces, and lower case r and upper case F)
4) reboot as normal. The file system check will be forced during the reboot, probably without any display of activity.

Note 1: (as administrator)
'shutdown -rF now' causes actions:
shutdown immediate, reboot, force filesystem check at restart
Note 2: The file system check is NOT carried out while the file system is mounted. The use of the Recovery Menu facility means that the check is set to be done at the next startup, before the filesystem is 'mounted'.

---

