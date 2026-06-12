---
title: "Encrypted home does not decrypt/automount on login"
date: 2011-09-28
forum: General Help
---

### Post by anlag on 2011-09-28
I'm running 11.04 with Unity on my laptop, and using an encrypted home folder. During the past couple of months, it's occasionally happened that I'd log into my system and be faced with the default icons, complaints from Nautilus, Dropbox etc, all evidently indicating my home folder was unavailable since it hadn't been automatically decrypted on login. I'd just log out and log back in again and it would work. This happened perhaps once in every 20-30 logins, at a wild estimate, so it didn't seem like an urgent thing to spend time sorting out.

Tonight the problem is worse. I've logged back in multiple times to no avail, the decryption simply doesn't happen and I can't access my home. I've got the auto-generated passphrase at the office so I suppose I can do a manual recovery and if need be reinstallation tomorrow, but before I dig into that (and I'd really rather not spend that time right now) I thought I'd ask if anyone has a better solution. What could be causing this problem? What can I do to fix it?

Thanks in advance.

---

### Post by anlag on 2011-09-29
No ideas? I'd consider disk error, but I've seen no other such indications at all. Is it perhaps simply that the home directory encryption mechanism is not very stable and this can occasionally happen? That being the case or not, is there really no way I can restore the automatic mounting of the encrypted content on login?

---

### Post by anlag on 2011-09-29
OK, so I believe I've managed to mount my encrypted home directory, but there are still big problems. Many of the directories in the mounted home directory are showing up double. A simple ls in it, will show folders like Documents, Pictures, Videos and Downloads literally show up twice in the listing. Other directories, like Dropbox and some custom ones I've created myself, only show up once and I can access the contents of those. This is however not the case with the doubles. If I try to go into, or look inside, for example Documents, I find it to be empty. The same goes for all the double ones, making me unable to still access the vast majority of my important data. I speculated earlier whether it could be it was mounting on top of the empty default unencrypted home directory, but I've tried doing it also in a newly created home dir, from a live USB boot. And finding the same result.

Anyone have any idea or suggestion whatsoever? This is getting extremely frustrating and I've not the slightest idea left. I don't even know how having identical directories in the same place is even possible.

---

### Post by drsaamah on 2011-11-06
Did you ever find a solution for this?  I have the exact same problem.  Does anyone know how to fix this?  The ecryptfs-recover-private command will just copy the /home/.ecryptfs/username/.Private directory without actually decrypting the files in there. Is there an application to decrypt these manually, and what information is needed to do so?  Any help is appreciated.

---

### Post by anlag on 2011-11-06
Yes, I did indeed manage to resolve the problem after pulling an all-nighter trying things, and getting some key help from the friendly people in #ecryptfs on the [OFTC IRC network](irc://irc.oftc.net:6667). I meant to get back here and post the solution, but had spent so much time trying to get it working that that ended up postponed... until now!

I'll start by saying I don't know what caused the problem in the first place, any more than that for some reason the automatic decryption of the home directory failed in such a way that the system could not read it, and instead created a default home directory setup with directories like Documents, Music, etc. Again for reasons that are unclear to me, these directories ended up inside the encrypted directory, but in an unencrypted form. So in the directory /home/.ecryptfs/anlag/.Private I had, in addition to all my previous home directory contents - in encrypted form - also a few mostly empty default directories - in unencrypted form. Then when I mounted the ecryptfs volume, they both showed up side by side, so I had duplicates of Documents, Music, etc and could only access the empty ones since apparently they took higher priority.

The solution for me was to simply remove the duplicate directories from /home/.ecryptfs/anlag/.Private after which I could mount and access all my data perfectly fine. Now to be on the safe side, I'll make the point also that you should make sure to have backups every step of the way. Ideally a backup of the entire /home, just in case. And in any case, making sure that when removing those duplicate directories that nothing is lost. I simply moved them off to a flash drive or some such, but however you do it, be careful and don't lose your stuff.

For reference I'll also include a log of my chat in #ecryptfs, since I was helped through various other steps along the way that may be helpful to others encountering these or similar problems:

[http://pastebin.com/937YU03H](http://pastebin.com/937YU03H)

Finally, for the problem you're encountering, it sounds to me like there is a problem with the way you use ecryptfs-recover-private, but I don't know if I can be of much more help than that. However when I was working on this, I used both ecryptfs-recover-private and the more lengthy procedure described for manual decryption on the [Ubuntu help pages](https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering_Your_Data_Manually), and they both equally well decrypted my data. 

If I were to guess, I'd say you might not have added your passphrase correctly, or if you might have changed the password for the user in question, that could cause problems too. Either way, if ecryptfs-recover-private doesn't do it for you, you can also try the more manual way I linked above, and make sure you get it right with which keyring signature goes where. If you're still unsuccessful, you can always try going to ask the developers/helpers in that IRC channel as well.

Best of luck!

---

### Post by drsaamah on 2011-11-07
Thank you for the response!  It does sound like your problem is the same issue I'm having.  As soon as I get access to my external hard drive I'll try this out.  Thanks a ton!

---

### Post by caravaggisto on 2012-03-26
> **anlag said:**
> Yes, I did indeed manage to resolve the problem after pulling an all-nighter trying things, and getting some key help from the friendly people in #ecryptfs on the [OFTC IRC network]("irc://irc.oftc.net:6667"). I meant to get back here and post the solution, but had spent so much time trying to get it working that that ended up postponed... until now!

I'll start by saying I don't know what caused the problem in the first place, any more than that for some reason the automatic decryption of the home directory failed in such a way that the system could not read it, and instead created a default home directory setup with directories like Documents, Music, etc. Again for reasons that are unclear to me, these directories ended up inside the encrypted directory, but in an unencrypted form. So in the directory /home/.ecryptfs/anlag/.Private I had, in addition to all my previous home directory contents - in encrypted form - also a few mostly empty default directories - in unencrypted form. Then when I mounted the ecryptfs volume, they both showed up side by side, so I had duplicates of Documents, Music, etc and could only access the empty ones since apparently they took higher priority.

The solution for me was to simply remove the duplicate directories from /home/.ecryptfs/anlag/.Private after which I could mount and access all my data perfectly fine. Now to be on the safe side, I'll make the point also that you should make sure to have backups every step of the way. Ideally a backup of the entire /home, just in case. And in any case, making sure that when removing those duplicate directories that nothing is lost. I simply moved them off to a flash drive or some such, but however you do it, be careful and don't lose your stuff.

For reference I'll also include a log of my chat in #ecryptfs, since I was helped through various other steps along the way that may be helpful to others encountering these or similar problems:

[http://pastebin.com/937YU03H](http://pastebin.com/937YU03H)

Finally, for the problem you're encountering, it sounds to me like there is a problem with the way you use ecryptfs-recover-private, but I don't know if I can be of much more help than that. However when I was working on this, I used both ecryptfs-recover-private and the more lengthy procedure described for manual decryption on the [Ubuntu help pages]("https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering_Your_Data_Manually"), and they both equally well decrypted my data. 

If I were to guess, I'd say you might not have added your passphrase correctly, or if you might have changed the password for the user in question, that could cause problems too. Either way, if ecryptfs-recover-private doesn't do it for you, you can also try the more manual way I linked above, and make sure you get it right with which keyring signature goes where. If you're still unsuccessful, you can always try going to ask the developers/helpers in that IRC channel as well.

Best of luck!

Thanks so much for sharing your fix! Question, though: what method did you take with backing up your home folder? Mine is on its own partition. But, when I boot up with a live USB ubuntu, the mount point for the /home partition is in /media/mumble_jumblexxxxxxxxxxx . As a a result, all symbolic links (notably, the ones made by ecryptfs!) are broken. My best guess as a solution to this is to re-mount the /home partition (containing the encrypted contents) to a new mount point (namely, `/home` on the live USB booted system). But, I'm nervous that I'll screw something up. What a lugubrious fate - to lose my data when trying to back it up...! 

For those who have found this page and have the same issue (your home folder is encrypted all of a sudden, or Ubuntu no longer automatically mounts your home folder anymore), check out these links:


[LIST=1]
[*][http://askubuntu.com/questions/62581/identical-folders-in-home-directory-after-decryption-of-home-directory-failed](http://askubuntu.com/questions/62581/identical-folders-in-home-directory-after-decryption-of-home-directory-failed)
[*][http://serverfault.com/questions/160277/ubuntu-how-to-decrypt-home-directory-swap-basically-everything-without-reins](http://serverfault.com/questions/160277/ubuntu-how-to-decrypt-home-directory-swap-basically-everything-without-reins)
[*][http://askubuntu.com/questions/38336/how-do-i-recover-my-data-from-an-encrypted-home-directory](http://askubuntu.com/questions/38336/how-do-i-recover-my-data-from-an-encrypted-home-directory)
[*][http://ubuntuforums.org/showthread.php?t=1580999](http://ubuntuforums.org/showthread.php?t=1580999) (which itself has a plethora of links in the first post)
[*][http://askubuntu.com/questions/115497/encrypted-home-directory-not-auto-mounting](http://askubuntu.com/questions/115497/encrypted-home-directory-not-auto-mounting)
[/LIST]
Update: good news, I managed to decrypt my /home/username folder by using "ecryptfs-recover-private" when booted via a live ubuntu USB stick. But, I now have the same issue as anlag with duplicate folders. It looks like the pairs of each folder come from (1) my encrypted user folder and (2) new defaults made by ubuntu when I logged in and my home folder had failed to mount / decrypt. I conclude this is the case because, when I was logged in and everything looked like the defaults (and all my data was missing / encrypted), I downloaded an Ubuntu ISO file into the Downloads folder. Now, I can see that the duplicate Downloads folder, right next to my decrypted one, contains that ISO file. The other Downloads folder presumably contains the downloads from my normal user folder.

Sorry if this is unclear to whoever is reading... Due to the nature of the problem - with all its homonymous folders, partitions and mount points - it's difficult to be specific without also sounding redundant and verbose.

---

### Post by lodp on 2012-07-31
First off, a great **big thanks to anlag**, who posted his solution here, despite receiving no help himself in his original three posts here. You saved me a great deal of nail-biting over potentially lost files.

I had the exact same problem. Encrypted home wouldn't mount a couple of days ago, so when I logged in I got a "vanilla" KDE session, with the default folders and config files being created in my /home/lodp dir, just as anlag described above. For example, the .kde dir, and the .firefox dir (because I had used firefox in the "vanilla" session).

I then made the mistake of mounting the encrypted home manually from within that session, using "ecryptfs-mount-private". 

Just as anlag described, my /home/lodp folder ended up with 2 identical versions of those user space folders (2x .kde, 2x .firefox, etc.), all of which contained not the original encrypted data, but the fresh data created in the vanilla session.

Following anlag's lead, I unmounted the enrypted home ("ecryptfs-unmount-private"), created a new user equipped with sudo rights, logged in as that, and from there removed everything from the /home/.ecryptfs/lodp/.Private folder that wasn't encrypted (i.e. didn't start with "ECRYPTFS_FNEK..."). 

The next time I logged with my regular user, the encrypted home mounted fine, and all the data was accessible. 

I AM curious as to what originally kept the encrypted home from being mounted. All this was quite a scary, and I'd rather not go through it again. This was the first time it happened to me

Also, how do you manually mount your encrypted home from a default/empty kde/unity/gnome session without ending up with all those duplicates?

---

### Post by mcsmith on 2013-01-09
I have also experienced this problem, twice in the last 10 weeks, using 12.04.

I was able to recover both times by moving the duplicated files in my home directory to a "mystery/<date>" directory.  Fortunately, the "first" of the duplicate directory pairs has always been the from the virgin environment setup, so mv moves them out of the way and leaves the real directories in place.

Curiously, the directories that were duplicated in the two incidents were not the same.

I wish someone was able to identify the root cause of the problem.  It diminishes my confidence in encrypted home directories.

---

### Post by drew870mitchell on 2013-02-10
Huge thanks to **anlag**, I ran into this and fixed it thanks to his IRC chat pastebin.  Shamelessly bumping since this happened after

```
sudo apt-get dist-upgrade
reboot
```

so there may be a few other people experiencing it recently as well.

---

