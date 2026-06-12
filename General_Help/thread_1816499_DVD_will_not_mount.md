---
title: "DVD will not mount"
date: 2011-08-02
forum: General Help
---

### Post by SirWeazel on 2011-08-02
Commercial DVD will not mount, so i'm unable to even play it.  If i put a blank cd or dvd in the drive it will mount those ok.  But when i put a movie dvd in the drive, my drive stays lit and nothing happens.

With the dvd in the drive, i cannot see the dvd drive in nautilus or "computer."  I can however view the drive with disk utility.

Any other media i put into the drive it will read and automount, but a store movie dvd doesn't mount at all.

I've installed ubuntu restricted extras, medibuntu repo with libdvdcss2 and i've also ran sudo apt-get install libdvdcss2 && sudo /usr/share/doc/libdvdread4/./install-css.sh and anything else i could find that i thought might work.

I'm running ubuntu 11.04 32bit on asus a8n32-sli deluxe motherboard with a plextor PX-755SA sata dvd burner.  I've installed ubuntu 11.04 on other laptops, and have not had a hard time at all enabling dvd playback. I usually just add the medibuntu repos and install libdvdcss with it.

I'm about to format and try again, any help soon would be helpful before i start my reinstall to see if that fixes the problem.

---

### Post by mc4man on 2011-08-02
Bit of a real  longshot -  put an audio cd in the drive, let it be seen, eject. Then put a dvd video disk in. Does it mount?

Also  - dvd video disks don't actually have to be mounted to be played.
You could try something like vlc with this command (assumes drive is normally /dev/sr0, adjust if needed
sudo lshw -C disk 
will show /dev/ links
```
vlc dvd:///dev/sr0
```

---

### Post by SirWeazel on 2011-08-02
Thanks for the reply, but after much frustration, i decided to try reinstalling one more time. The first time i removed all my other hard drives before installing, and this time i'm installing with my drives attached to see if that had anything to do with the problem.  I'm just hoping it doesn't erase my data off of my data drive.

I did try putting other media in the drive, and then putting the dvd in the drive, but nothing. Now i'm just holding my breath to make sure it doesn't mess with with other drives during the install. I've been working on my computer for the last couple days, and i've reached a boiling point where now i'll probably do something stupid.  Thanks again, i'll update this thread after my install takes hold.

---

### Post by mc4man on 2011-08-02
Only mentioning because I have an old, (but never used) plextor 712A that suffers from a rare bug. It first was seen in fiesty, then disappeared until natty.

The only way I can get a com. dvd disk to mount is to first insert an audio cd (and only an audio cd will work
Then the drive is good until a reboot
(absolute nonsense, but true

Otherwise, if you can't resolve,  I assure you that dvd disks are playable without mounting - do it all the time

---

### Post by SirWeazel on 2011-08-02
I didn't try with an audio cd... And now i did something super stupid... I just lost everything i had on my data drive.  I told the installer to isntall to sdb drive, and it installed to sdc.... so now i have to copys of ubuntu on 2 drives, and all my stuff is gone!  Oh how fun.  And i'll find out here in  minute if it mounts the dvd.

---

### Post by SirWeazel on 2011-08-02
So after a fresh install, it still doesn't mount the dvd.  I think you are right on the plextor drive issue. (i didn't have any problems with ubuntu 9.10) Do you know if this is reported or being worked on?

Edit: Took me awhile to find an audio cd, but that did the trick. That is just plain stupid. Is this a bug that needs to be reported?

---

### Post by SirWeazel on 2011-10-04
I'm going to mark this as solved. For anyone else reading this. There is some type of problem with plextor drives. (the audio cd trick works that mc4man mentioned above). Also check out this thread [http://ubuntuforums.org/showthread.php?p=11110732#post11110732](http://ubuntuforums.org/showthread.php?p=11110732#post11110732)

mc4man, in another thread/post you mentioned still having this problem with 11.10 beta. Since the final is about to be released in a couple days, can you report back if you still have this problem with the final/latest updates?

---

