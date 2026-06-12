---
title: "ubuntu requiring entering pw in pre-startup for every mounted network share"
date: 2006-05-01
forum: General Help
---

### Post by kupajava on 2006-05-01
Heres a new question for ya,  After modifying my /etc/fstab to mount win2k3 server shares (I had to use cifs instead of smbfs, still not sure why smbfs wouldnt work) the OS requires me to imput my PW (client pw) for each share during bootup.  This happens after the brown ubuntu startup checklist and before the gui logon.  It makes me enter the PW 5 times (one for each share) at this time.  During the brown startup screen the checklist ticks off each line as ok and then breaks into a white text screen where I can see all of the startup lines and says it needs a pw to mount network shares.  When I give it the pw it goes to the next share and asks again until each share is mounted, then goes into the gui and asks for the normal login.  Anyone know how I can circumvent this?  Thanks!

---

### Post by miscreant on 2006-05-01
It looks like, from this link [http://lists.olug.org/pipermail/olug/2004-November/015520.html](http://lists.olug.org/pipermail/olug/2004-November/015520.html) that you need to create a credentials file like you need to do for smbfs.

Basically you just put your username and password into a file like this:

username = myusername
password = mypassword

and then add the following to the options for your fstab entry:

credentials=/path/to/credentials/file

I did this for my smb shares and it works fine, looks like it's essentially the same process for cifs.

Hope this helps.

miscreant

---

### Post by kupajava on 2006-05-01
already have it.  here is my fstab (locations replaced)

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
//server/share /mnt/share cifs defaults,uid=1000,gid=1000,credentials=/etc/cifspw,umask=777 0 0
//server/share2 /mnt/share2 cifs defaults,uid=1000,gid=1000,credentials=/etc/cifspw,umask=777 0 0
//server/share3 /mnt/share3 cifs defaults,uid=1000,gid=1000,credentials=/etc/cifspw,umask=777 0 0
//server/share4 /mnt/share4 cifs defaults,uid=1000,gid=1000,credentials=/etc/cifspw,umask=777 0 0
//server/share5 /media/share5 cifs defaults,uid=1000,gid=1000,credentials=/etc/cifspw,umask=777 0 0

The problem (feature) happens before the GUI loads and asks me for my pw (no username so I assume its my Linux user account pw, not win) for each of the share mounts, i.e. I have to put in my pw 5 times before my GUI comes up.  any ideas?

---

### Post by kupajava on 2006-05-02
Anyone have any ideas about this?  If I could enter my password once in my fstab instead of 5 times somewhere in my bootup it would be great.  Theoretically, if I could get this to run as root in bootup or even put in a credentials file for my linux login like the one already there for the windows side, that would work I suppose.  Anything?

---

