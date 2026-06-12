---
title: "Backup to NAS options"
date: 2012-03-29
forum: General Help
---

### Post by nick_a_louse on 2012-03-29
I've been doing some research; here is the current set-up and what I am trying to achieve.  I'm still relatively nieve where Ubuntu is concerned - my server is nice and reliable but I've now started to try and expand it's capabilities.

It's running Ubuntu server 11.10 with a 3 disk software raid-5 (and separate OS drive).

Whilst nothing on the box is commercial, I want to improve my contingency for certain part of the data (almost 100GB of photos and documents).  I've got the original RAW data on DVDs, but it would be a massive pain to reconstruct everything (and they only have a limited lifespan)

Now, before I had this box, I had an old single drive NAS box.  It can be accessed via samba or ftp.  It can also be connected using USB, but the point is I want it separated from the main box using the internal LAN.

It is quite an old device (Icy-box NAS900) and runs an older version of samba (2.X I think?).  Trying to mount it using symbolic links doesn't work; I believe it needs smbfs rather than CIFS.  Presumably I could install smbfs on the server, but would that cause issues in the future if I updated / upgraded (since it is no longer supported)?

I then thought I'd look at ftp.  I saw 'curlftpfs, but one of the pages I encountered said it was no longer supported (and had bugs).  Can anyone confirm the status of this project and the reliability?

Finally, there was the option of something like rsync. From what I understand however, it backs up to an archive.  I was hoping to avoid archives (even though they add extra protection); I just wanted to copy new and modified files to the ftp.  Can this be done or is there another tool that'll do what I want?

Apologies for the long post, but I hope I've painted a complete pictures.

Looking forward to some advice; thank you in advance!

Nick

---

### Post by nick_a_louse on 2012-03-29
Damn it - accidentally prefixed this with 'lubuntu'.  Anyone know how to change it? 'Forum help' doesn't say.

---

### Post by papibe on 2012-03-29
Hi nick_a_louse. Welcome to the forums!

If I understand correctly your main concern is to get your files from your old NAS to the new Ubuntu server? Here are a some thoughts: 

**smbfs**
You are correct: the protocol is no longer preferred, but cifs instead. The new package is called cifs-utils. A little note though, smbfs still exists as a package but underneath is cifs-utils (check it [here]("http://packages.ubuntu.com/oneiric/smbfs")).

**rsync**
You have a misconception here. Rsync mirrors a source to a destination (may be you are thinking of 'tar'?). I believe the confusion may lay on the use of the the typical '-a' option that is read as 'archive', but not in the sense of tar's archiving. It is just a shortcut for several useful options (like recursive, preserve permissions, etc).

I hope that points you in the right direction, and tell us if you need more help on the matter.

Regards.

---

### Post by CharlesA on 2012-03-29
> **nick_a_louse said:**
> Damn it - accidentally prefixed this with 'lubuntu'.  Anyone know how to change it? 'Forum help' doesn't say.
Fixed the prefix for you.

Do you want to still use the only NAS box or are you trying to transfer the data from that box to the new one?

EDIT: I couldn't find an english user guide, but I did find a page on newegg about it:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16817714032](http://www.newegg.com/Product/Product.aspx?Item=N82E16817714032)

It sounds.. nasty.

---

### Post by nick_a_louse on 2012-03-30
Hi guys, thanks for replying.

I was actually trying to duplication certain files _to_ the NAS, from the server.  Whilst the server has a level of redundancy, I wanted to use the NAS as an additional backup. Redundancy doesn't help if someone steals the box...

Yes, the NAS is a bit old, slow and nasty, but it has some custom firmware on it from a guy in France which at least makes the interface at least work properly!  Tried a buffalo terastation before build my Ubuntu box and it didn't seem to offer anything significantly extra for the money.

Papibe; now that you've clarified the use of rsync, I'll give it a whirl.  I was indeed confused by the -a parameter.  With the possibility of incremental backups, I assumed that by default it operated like a tape backup.

I'll let you know how I get on and mark the thread as solved when appropriate.

Thanks,

Nick

---

