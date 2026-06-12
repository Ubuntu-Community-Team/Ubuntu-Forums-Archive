---
title: "System Backup"
date: 2011-07-26
forum: General Help
---

### Post by Golvmopp on 2011-07-26
Hello

I tried searching the forum for an existing thread, but I couldn't really find anything. Maybe I'm just bad at searching. :P

I'm running Ubuntu 10.03, and I want to backup my software when I play around with other operating systems. I'm thinking about trying different O/S, such as Mandriva, FreeBSD, Slackware etc. to see what I think of them. 
But I think I'll stay with Ubuntu, I've used it for a while, gotten familiar with it, and am really satisfied with it.
I've got an external drive on 1TB, that I want to use to backup my important files in Ubuntu, so that I can make a new installation of Ubuntu in the future, and the just move the files back to the computer to get it as I have it now.

How is this best done? :-k

---

### Post by DrScum on 2011-07-26
Check out NS-Backup [http://nsbackup.sourceforge.net/](http://nsbackup.sourceforge.net/)

another option is Peazip, an archiving tool [http://www.peazip.org/](http://www.peazip.org/)

lastly I suggest to create an image of your system partition using clonezilla [http://clonezilla.org/](http://clonezilla.org/)

Another idea would be the following:
create two partitions on your harddrive (using Gparted for example) hold your ubuntu system on one of them and use the other one for testing other operating systems. The same approach works of course if you install a second harddrive.

---

### Post by seawolf167 on 2011-07-26
I highly suggest imaging you drive with [Clonezilla ]("http://www.clonezilla.org")as a backup every once and a while. Makes it painless to restore if something catastrophic goes wrong. Other backup ideas can be read about [here ]("https://help.ubuntu.com/community/BackupYourSystem")(like rsync, sbackup, etc.)

---

### Post by Manyette on 2011-07-26
I too would second the suggestion to use Clonezilla.  It will give you a bare metal backup that can restore everything you now have.

---

