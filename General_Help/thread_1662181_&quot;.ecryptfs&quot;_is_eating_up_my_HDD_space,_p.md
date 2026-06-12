---
title: "&quot;.ecryptfs&quot; is eating up my HDD space, please help!"
date: 2011-01-07
forum: General Help
---

### Post by Th3Professor on 2011-01-07
When I installed the system I went ahead and added the private/ecryptfs feature.

However, I have never actively (or at least "awaringly") used it. I don't know if it is being used passively or if it contains any of my important data that I cannot already otherwise access.

There is also a problem with space constantly reducing. I'm losing HDD space and I'm not aware of what is causing it. I've tried clearing caches, tmp, things like that, disabling internet, not running applications that would tend to eat at the hard drives. But no luck. And the space free is being very weird. A few days ago I had 700M remaining on my "/" partition (it's a 19G (almost 20G) partition), then a day later I had several gigs free but I did nothing, then another day later it was back to 800M or 700M free. Something very fishy is going on here.

Regardless, my focus on this thread is that dang ".ecryptfs".

Can I get rid of it *without* losing data?

Disk usage analyzer, partition with a little over 19G:
/home is using 20G ...somehow... (and on a 19G partition?!) weird.
The main user account home is using 9.7G ...the ".ecryptfs" is using 10.2G.

I really do not want that 10.2G to be used just for the sake of some shady ecrypt feature.

Please help. Thanks!

Edit - That partition is now down to 260M free! It's going fast. Please help soon. Thank you!

---

### Post by Th3Professor on 2011-01-07
Is anyone able to help please? I'm down to 180M free and it's getting lower.

---

### Post by cipherboy_loc on 2011-01-07
Do you know IF it is mounted?


```
sudo mount
```

to tell you if it is mounted.





Cipherboy

---

### Post by Th3Professor on 2011-01-07
> **cipherboy_loc said:**
> Do you know IF it is mounted?


```
sudo mount
```to tell you if it is mounted.





Cipherboy


Hi thank you for replying. Yes it is mounted. Auto mounted, I think.


```
/home/username/.Private on /home/username type ecryptfs (ecryptfs_sig={omitted})
```

Edit - I'm down to only 78M free now! AAAAAAAAACK!

---

### Post by Th3Professor on 2011-01-07
I now only have 38M free. Someone please help?

---

### Post by Th3Professor on 2011-01-07
I was down to only 3 megs free... nobody responded so I just deleted everything in /tmp as a quick-fix. That did not solve the problem though. Of a 19+ gig partition there is a lot of it missing for no known reason and something is actually constantly eating it all up. And it's happening at a fast rate. I'd like to take the "ecryptfs" out of the system entirely, it is an absolute waste even having that. Someone please help. Thanks!

---

### Post by psusi on 2011-01-07
It's everything in your home directory.  Go clean it up.

---

### Post by Th3Professor on 2011-01-07
> **psusi said:**
> It's everything in your home directory.  Go clean it up.

No. It's not. I've checked. If I'm missing something please let me know, I'll check something specific if I missed something.

/home is only using 2G. (2.6G)

It's a 19+ gig partition.

It is something else... not /home.

Anyway...

Here's an update.

I rebooted. On logging back in df = 7.4G. Miraculous. Right? Right, well, then the screen started freaking out (totally different issue, an nvidia problem I haven't been able to resolve) so I logged out (to reset GUI issue) but didn't reboot then I logged back in and then df = 8.2G. This happened the other day. I went from almost 0M to 8G free, then back down to almost 0M free, and here I am again back up to 8G. So something's auto-clearing, and I need to find out what and where, and how to limit how much space it takes. Anybody?

(the /home taking up 2G was *before* I rebooted/relogged on, so it's not /home related)

---

### Post by psusi on 2011-01-07
You originally said /home was using 20g, now you say 2.  Which is it?

---

### Post by Th3Professor on 2011-01-07
Just caught that... it's 2G.

The issue is 2-fold...

1. I need to get rid of .ecryptfs, I'm not even actively using it for one, and it is more of a problem than anything else.

2. I need to find out what's eating up HDD space, regardless of ecryptfs involvement, but what could be doing it? (Something happening during reboot auto-cleans, I just don't know what, or how to limit the space taken up by whatever is causing it)

---

### Post by psusi on 2011-01-07
Where is this .ecryptfs and how big is it?  According to your output from mount, your home directory is encrypted and stored in .Private, which is what other users will see if they look in your home directory when you are not logged in.

---

### Post by cipherboy_loc on 2011-01-07
> **Th3Professor said:**
> 
1. I need to get rid of .ecryptfs, I'm not even actively using it for one, and it is more of a problem than anything else.

To remove it:
[https://help.ubuntu.com/community/EncryptedPrivateDirectory#How%20to%20Remove%20an%20Encrypted%20Private%20Directory%20Setup](https://help.ubuntu.com/community/EncryptedPrivateDirectory#How%20to%20Remove%20an%20Encrypted%20Private%20Directory%20Setup)

I would recommend copying your /home to an external drive (cp /home -prv /media/external/drive) and the directions posted above.


> **Th3Professor said:**
> 
2. I need to find out what's eating up HDD space, regardless of ecryptfs involvement, but what could be doing it? (Something happening during reboot auto-cleans, I just don't know what, or how to limit the space taken up by whatever is causing it)

Run the Disk Usage Analyzer (Applications -> Accessories -> Disk Usage Analyzer on Ubuntu 10.10) on / after removing the .ecryptfs (make sure you reboot) and see what it tells you (screenshot please?). 

If it still fluctuates after removing ecryptfs, I don't know what it would be. I was thinking it might be something about it being a circular mount (A file ~/.ecrypfs mounted as ~/), but that is just a wild guess. 



Cipherboy

---

### Post by Th3Professor on 2011-01-08
> **cipherboy_loc said:**
> To remove it:
[https://help.ubuntu.com/community/EncryptedPrivateDirectory#How%20to%20Remove%20an%20Encrypted%20Private%20Directory%20Setup]("https://help.ubuntu.com/community/EncryptedPrivateDirectory#How%20to%20Remove%20an%20Encrypted%20Private%20Directory%20Setup")

I would recommend copying your /home to an external drive (cp /home -prv /media/external/drive) and the directions posted above.




Run the Disk Usage Analyzer (Applications -> Accessories -> Disk Usage Analyzer on Ubuntu 10.10) on / after removing the .ecryptfs (make sure you reboot) and see what it tells you (screenshot please?). 

If it still fluctuates after removing ecryptfs, I don't know what it would be. I was thinking it might be something about it being a circular mount (A file ~/.ecrypfs mounted as ~/), but that is just a wild guess. 



Cipherboy

RE: 1st thing, before I go in and rm -rf things, will deleting .ecryptfs, .Private, Private also delete any files that I actually awaringly/actively (or otherwise) use?

Edit - I don't know if that ecryptfs nonsense has any actual "active" use or if it's entirely a passive/background thing, though I have never done anything with it.

---

### Post by Jerry N on 2011-01-08
If it was me I would quit messing with it, do a complete re-install, and reload my data files from my backup.  You do have a backup of your data files don't you?

Jerry

---

### Post by Th3Professor on 2011-01-08
complete reinstall? No. Not gonna happen. Well, not soon. I have a little over 3 **terabytes** of data to sift through, back up, etc. ...so, it'll be a while before I do a fresh system install, and it won't be reinstall, it'll be install of the most recent system (current one is a year old or so, which is fine for now).

Also, I'm not "messing" with it. I'm actually doing the exact opposite because I am not sure just yet what needs to be done.

Going to have to go another route.

---

### Post by cipherboy_loc on 2011-01-08
What is the output of:


```
ls -hAl --recursive ~/.ecryptfs ~/.Private ~/Private
```

Run it once on a fresh boot, and once after running for a while (AKA when your low on disk space). This should give us some idea on what is taking up so much room.


Cipherboy

---

### Post by Th3Professor on 2011-02-03
Okay it's doing it again, space being eaten up.

Doing "ls" (recursive) on the home user .ecryptfs brought this up:
/home/user/.ecryptfs -> /home/.ecryptfs/user/.ecryptfs

Also, when ecryptfs was added on system install it did not auto-add a "Private" directory. I manually added one to see if that'd make a difference but nil.

I am currently at 0 (zero) gigs of free space on / (root directory), with space analyzer showing .ecryptfs as taking up the majority of it, 75% (10gigs). So, it's back to the .ecryptfs problem eating space again.

"du -hs" on /home/.ecryptfs = 10G

More specifically, the 10gigs are in /home/ecryptfs/user/.Private

(So it looks like ".Private" was auto-created instead of "Private")

There's no sense in doing a "ls -lAhR" on that directory, it lists *many* files with the encrypted file names, so there's no deciphering which means what.

This really all boils down to getting rid of .ecryptfs.

However, I require 2x the HDD space to get rid of it, at least from the howto pages I've seen so far. I can't do that when there is 0 (zero) free space.

---

### Post by psusi on 2011-02-03
Look at everything ELSE in your home directory.  That is what is encrypted and stored in .ecryptfs.

---

### Post by Th3Professor on 2011-02-03
I just did a reboot and that spared me 740megs.

RE: home dir, so if I move non-encrypted files out of / partition and into my non-root partition that'll do the trick? I'd still like to get rid of ecryptfs entirely, it's just a pain, and I don't know if I'll be able to create 2x free space to do so.

Edit - I just did a "du -hs ~/*" and there's nothing taking up that much space. The "Documents" folder has about 400megs of files, that's it. Everything else = tiny files.

Edit2 - I just did a "du -hs ." and it brings up 9.4G of space used.

I'm going to try this from someone left in an reply:
> [https://help.ubuntu.com/community/En...ectory%20Setup]("https://help.ubuntu.com/community/EncryptedPrivateDirectory#How%20to%20Remove%20an%20Encrypted%20Private%20Directory%20Setup")

I would recommend copying your /home to an external drive (cp /home -prv /media/external/drive) and the directions posted above.Edit3 - 

Regarding:

> **How to Remove an Encrypted Private Directory Setup**

 Perhaps an Encrypted Private Directory is not for you.  To remove this setup: 

[LIST=1]
[*]Ensure that you have moved **all** relevant data out of your ~/Private directory
[*]Unmount your encrypted private directory
[LIST]
[*] $ ecryptfs-umount-private
[/LIST]
 
[*]Make ~/Private writable again
[LIST]
[*] $ chmod 700 ~/Private
[/LIST]
 
[*]Remove ~/Private, ~/.Private, ~/.ecryptfs (**Note: THIS IS VERY PERMANENT**)
[LIST]
[*] $ rm -rf ~/Private ~/.Private ~/.ecryptfs
[/LIST]
 
[*]Uninstall the utilities
[LIST]
[*] $ sudo apt-get remove ecryptfs-utils libecryptfs0
[/LIST]
 
[/LIST]
How am I to move all relevant data from ~/Private when I manually created Private but never put anything in it?
I suspect it means ".Private" instead of "Private", in which case, all of those files are encrypted. How do I know which files are relevant if they're all encrypted?
The steps provided above don't seem like they apply directly to me considering the ecryptfs, as auto-installed, on the system never had a "~/Private" in the beginning.
What do I do to get rid of the ecryptfs stuff since that's the case? (I don't know if I have any important data that's encrypted, nor how to find out.)

Also, I suspect some of this problem (or the majority) might be related to cache. It seems like some applications are set to accept unlimited cache or a high amount of space of cache, which is very odd. During the copy process from ~ to external drive (it's going right now, still) a lot of ".macromedia" went by, then it held on at xsession log for a while, then a lot of ".thumbnails" went by. It's in the middle of the copy process now, so I'm not sure if there will be any/many other file/folders that particularly stand out as perhaps taking up more files or maybe more space. (edit- lots of .mozilla (seamonkey and firefox), and I'm going to assume there was a lot of google chrome as well) (edit- okay now it's going through and copying all of the encrypted files over, I'd guess that'll be the rest of it; still not sure what to do with the whole rm -rf Private .Private .ecryptfs stuff (followed by apt-get remove ecryptfs stuff) since I am currently unaware of how to check to see what encrypted files I need to preserve) anybody?

Okay no more edits to this post. Thank you anyone/everyone for helping!

Cheers!

P.S.- okay one more edit and that'll be it: the copying of files just spat out one that said "file too large to copy" (the ext.dr. uses a windows fs I think), and it was an encrypted file, so I have no idea if I'm going to end up losing critical data now from the encryptfs stuff unless there's a way to find out what all the encryptfs files/folders are unencrypted. ...okay that's all for now. thanks all!

---

### Post by Th3Professor on 2011-02-04
Bump... for the questions in my previous message.

---

### Post by ubuntu27 on 2011-02-04
I don't know the solution nor what is causing the loss of free space.

But, I recommend you to take a look at your hidden trash directory. Many files might be accumulating in it. (I once discovered that I had 10GB or more files in the hidden trash!) 

Take a look at these threads:

[Purpose of home/.trash-0 ???]("http://ubuntuforums.org/showthread.php?t=1665747")

[Purpose of /root/.local/share/Trash/expunged ?]("http://ubuntuforums.org/showthread.php?t=1490072")


Also, you might be interested in reading [HOWTO: Cleaning up all those unnecessary junk files]("http://ubuntuforums.org/showthread.php?t=140920")


Good luck!

---

### Post by Th3Professor on 2011-02-04
Thank you for those links. I went ahead and went through the steps provided in those threads. It didn't really solve the issue here, only cleaned out a few megs at best, though I'm glad to know about that stuff.

Has anyone else (who is reading this) dealt with ecryptfs before or perhaps familiar with the workings of it?

How do I know which files are relevant (for backing up prior to deleting ecryptfs stuff) if they're all encrypted?

What do I do to get rid of the ecryptfs stuff considering I don't know if I have any important data encrypted in the ecryptfs folder(s)?

(And I don't know how to find out if I have any important encrypted data.)

Does the ".macromedia" folder hold anything critical? Or ".thumbnails"? Perhaps the xsession log file?

After that there's the cache for firefox, chrome, and seamonkey, which I thought I've cleared out (and I used autoclean also) but there's still a gradually-diminishing HDD issue going on, even when I just let the computer set and actively do "nothing".

---

### Post by Stephen Morgan on 2011-02-05
ecryptfs encrypts the contents of your ~/ directory, then on login mounts it so that it can be decrypted on the fly to allow you access. The encrypted files are the same as the unencrypted files in ~/, or should be. Therefore if you have all the "unencrypted" files from ~/ backed up it should be safe to delete .Private and the rest and uninstall ecryptfs.   I've not done that, so I suppose it might leave you unable to decrypt and access the files in ~/, in which case simply copy them back over from your back up.    If you want to maintain the ability to encrypt directories you could just create a new user account in System>Administration>Users and Groups, making sure not to select 'ecnrypt home folder', or whatever the option is. That might also stop any other programme which might be starting on log in and filling your hdd with crap, if it's not ecryptfs.  on edit:   I've just done a `sudo ls` on the ~/ of another user on my system, with an ecryptfsed ~/, this is what comes up:    ```
grim@07:08:31:~/$ sudo ls /home/sysadminbk/  [sudo] password for grim: Access-Your-Private-Data.desktop README.txt  grim@07:12:00:~/$ sudo cat /home/sysadminbk/README.txt  THIS DIRECTORY HAS BEEN UNMOUNTED TO PROTECT YOUR DATA. From the graphical desktop, click on:  Access Your Private Data or From the command line, run:  ecryptfs-mount-private 
```    That's what your ~/ would look like without ecryptfs, all the files which to you seem to be unencrypted in ~/ are in fact encrypted in ~/.Private and being decrypted by ecryptfs as you use them, therefore your backup ought to be unencrypted.

---

### Post by Stephen Morgan on 2011-02-05
I seem to have somehow broken the formatting on that last post, and I've had second thoughts, so here's how I would get rid of ecryptfs:  first, create a new user account with administrative privileges in system>admin>users and groups, unticking the encrypted home folder option.  2) logout as olduser, in as newuser, assuming you've got everything other than the encrypted directory backed up 3) delete /home/olduser 4) uninstall ecryptfs 5) mkdir /home/olduser 6) copy the backedup files back into /home/olduser,  7) chown olduser --recursive /home/olduser 8) logout as newuser, back in as olduser to make sure everything works 9) feel free to remove ~/.Private  That ought to do the job, but I doubt ecryptfs is what's taking up all your space, ecryptfs should only encrypt the files  in your home folder, which is why df -h shows the same figures as the partition /home is on, ecryptfs is specifically designed to vary in size according to the amount of data stored on it. Therefore I would recommend that, after the above, continue running as newuser to see if you get the same problem, and then do the same as the reincarnated olduser, see if ti does the same thing.

---

### Post by Th3Professor on 2011-02-06
I just came across this page:
[http://virtually-a-machine.blogspot.com/2010/08/howto-disable-ecryptfs.html](http://virtually-a-machine.blogspot.com/2010/08/howto-disable-ecryptfs.html)

Those steps you listed have similarities.

My only concern is what someone said in the 2nd comment on that page: that at least 50% free space is required. I have 0% free.

Edit -

I've heard other mention of ecryptfs basically just being a duplicate of the space I'm already using, only as encrypted files, mirroring the normal files, like in /home/user.

So I did a check on disk usage in /home/user and the following files or folders come up as taking up the most space:

.config = 750mb
.thumbails = 600mb
Documents = 460mb
Downloads = 125mb
.mozilla = 100mb

Everything else is under 100mb, and significantly so, and all of the remaining things (separate from the 5 listed above) total about 400mb.

Adding those numbers up and it's about 2.5gigs.

However, /home/user (in disk usage analyzer) says 8.9gigs are being used.

So the big question is: where are the 6.4gigs coming from?

Edit 2 -

Here's a more detailed look at some of those files/folders that are unrelated to the mysterious missing 6.4gigs:

.config = 750mb = ~/.config/google-chrome/Default (and ./History type folders and a Thumbnails folder) (safe to delete contents of directory?)
.thumbails = 600mb = ~/.thumbnails/normal = a bunch of ".png" files (safe to delete those files?)
Documents = 460mb (documents, I am not deleting those files)
Downloads = 125mb (just 125mb, no need to delete those files)
.mozilla = 100mb = ~/.mozilla/firefox (80mb) and ~/.seamonkey (20mb) (anything in those directories safe to delete?)

It'll help to know what I can delete from those folders but it unfortunately doesn't solve the 6.4gigs, other than the connection with the ecryptfs.

---

### Post by cipherboy_loc on 2011-02-06
It is safe to delete ~/.thumbnails, its just a bunch of your photos resized to smaller format (128x128 or so). About the others, I don't know.

Cipherboy

---

### Post by ubuntu27 on 2011-02-06
I use encryptfs to encrypt my ~/ as well. But, i do not have these problems. Very weird. I am also losing space, but that is because I keep saving lots of GB worth of videos. ><;

I recommend you to use [BleachBit]("http://bleachbit.sourceforge.net"), a application that free-up disk space and safeguard your privacy.
It is in the repository, so you can just install it with

```
sudo apt-get install bleachbit
```

Also, some other cleaning-up tools are mentioned in this site: [Cleaning up a Ubuntu GNU/Linux system]("http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html")

---

### Post by Th3Professor on 2011-02-06
Wow that bleachbit is great! Should be called bleachb!tch ;) lol ...good stuff. I managed to clear out 1gig. That leaves 5.4gigs of mysteriously-eaten-up HDD space. It's not a solid solution for those 5gigs but it's one step closer.

---

### Post by sportykev on 2012-11-21
Hate to bring this up from the dead.  I too am experiencing this ecryptfs bloat.  It tends to grow extremely large 50gb+ when I leave any Flash objects open under Chrome overnight.  How to stop this from happening?!

---

### Post by wildmanne39 on 2012-11-21
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

