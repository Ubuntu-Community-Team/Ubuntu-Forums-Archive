---
title: "Rsync --exclude rules for system backup"
date: 2012-09-17
forum: General Help
---

### Post by cogset on 2012-09-17
I must admit,I thought this was going to be way easier:after backing up my system with a tar of my / directory with all the exclusions suggested here [https://help.ubuntu.com/community/BackupYourSystem/TAR](https://help.ubuntu.com/community/BackupYourSystem/TAR)[URL="https://help.ubuntu.com/community/BackupYourSystem/TAR"]
[/URL] I was suggested that rsync also may  be worth trying,so I had a go at backing up again with rsync trying to append the same exclusions as with tar,namely 
```
/proc /sys /lost+found /mnt /media /dev
```well it apparently doesn't work the same way ](*,),I keep getting some of these directories in the dry run test of rsync:can someone please point out what I'm doing wrong?

---

### Post by SlugSlug on 2012-09-17
each folder needs the --exclude eg

--exclude /proc --exclude /tmp



take a look at back in time - its a good backup util :)

---

### Post by Habitual on 2012-09-17
SlugSlug is correct, Here's a working example.
```
rsync -avz . /run/media/jj/Keepers --exclude ".cache/" --exclude "VirtualBox VMs/" --stats --delete
``` HTH!

---

### Post by bodhi.zazen on 2012-09-17
FWIW, this question is answered on the Ubuntu wiki 

[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)

---

### Post by Slim Odds on 2012-09-17
If you have a lot of exclusions, it's much better (and easier) to use the --*exclude-from* option and create a file that contains all of the exclusions.

---

### Post by bodhi.zazen on 2012-09-17
> **slim odds said:**
> if you have a lot of exclusions, it's much better (and easier) to use the --*exclude-from* option and create a file that contains all of the exclusions.

+1

---

### Post by cogset on 2012-09-18
Thank you all for the replies (especially the tip about the  --exclude-from option,very interesting):yes,I had a look at the wiki  before asking but-as far as the exclude option goes-it doesn't look very  accurate to me,as I've found no evidence of the quotation marks that  are apparently needed to make it work.
I kinda thought it was just the same as the --exclude option of tar,but  there it works without quotes,in rsync I couldn't make it work.

EDIT:later  on,searching for useful tips,I've came across this line > A lot of users  do mistake when specifing path. This path should be relative to source  directory in this webpage [http://supportex.net/2011/07/exceptions-copying-directory-rsync/](http://supportex.net/2011/07/exceptions-copying-directory-rsync/) ,it may sound all too obvious but IMHO adding this simple remark to the wiki page would make things a lot easier for newbies like me.

---

