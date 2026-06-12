---
title: "corrupted files in ubuntu lucid"
date: 2010-08-07
forum: General Help
---

### Post by 2xd on 2010-08-07
hi all

I'm running dual boot with Vista and Ubuntu Lucid Lynx.

for few days i was running Ubuntu only, downloaded some files and created some directories.
few minutes ago, i switched to Vista to see something and i wanted to burn some of the files i downloaded using Ubuntu but couldn't find those folders.

i thought maybe its related to different file system or something so i switched back to Ubuntu and surprise !!! my folders are not there, instead i got a file, of unknown type with the same name as the folder had !!!
in another folder case it's was an image (some print screen of my browser screen - Mozilla) and again with the name of what was the folder !!!

first - what the hall had happened ?
second - can i recover my data somehow ???

any fast answer will be much appreciated 

thanks ahead

---

### Post by Mark Phelps on 2010-08-07
When you downloaded the files, did you download them to your Vista filesystem?  If so, did you manually do a clean dismount of the filesystem before you rebooted?

If the answer to the first is Yes, and the second is NO, the files never actually got written to the filesystem.

It's a really BAD idea to mount a Vista or Win7 filesystem read/write because of the unclean shutdown risks associated with doing so.

If you downloaded the files to your Linux filesystem ... then sorry, don't know whey they're not there.

---

### Post by 2xd on 2010-08-07
well oops...

yep I did downloaded them to my Vista file-system and no I do not know what  is a "manually clean dismount of the file-system"

do you mean i need to dismount the media from /media/ ?

---

### Post by 2xd on 2010-08-07
well I've tried what you said but maybe I didnt get it right:
I've downloaded something into vista file-system, **UNMOUNTED** the media and rebooted into Vista - no files !

?

---

### Post by cavalier911 on 2010-08-07
Do you have an entry in ubuntu's /etc/fstab to mount the vista ntfs partition with ntfs-3g with the proper options?

---

### Post by 2xd on 2010-08-07
sorry but i'm kind of newbe in linux so i dont really know what you talking about, i'll love to learn if you could elaborate a little...

thanks.

---

### Post by cavalier911 on 2010-08-07
Thread #6 is a mini tutorial I did for a new linux user on creating an /etc/fstab entry to automount a windows partition

[http://ubuntuforums.org/showthread.php?t=1529824](http://ubuntuforums.org/showthread.php?t=1529824)

---

### Post by 2xd on 2010-08-08
hi cavalier911, thanks for the link and for the post behind it !

i did every thing you said in that post #6 and gained an auto mount for my FileSystem. that is by itself was worth all the trouble :)

but anyway, my problem is still there... even after restarting, i created a new Directory, unmounted the driver saftly.. and in Vista there were still nothing !!!

what can i do next ?

---

