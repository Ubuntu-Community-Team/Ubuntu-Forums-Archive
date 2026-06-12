---
title: "Intentionally corrput LUKS key"
date: 2012-04-13
forum: General Help
---

### Post by Darris on 2012-04-13
I've had a LUKS system corrupt on me once (no biggie, I had everything backed up), it just happened when my battery died and when I turned it back on, my password wouldn't work.
I don't know whether that's a reliable way to always corrupt a LUKS key but I'm curious.
Do you guys know? I like the idea of someone demanding your password and you being able to honestly say "... I don't know what it is anymore... I can give you my old password?" :p
Mainly I want to know to figure out what causes the corruption for curiosity's sake.

---

### Post by Darris on 2012-04-27
bump

---

### Post by Herman on 2012-04-27
It's the same as any other file system. If the operating system is shut down in the middle of a disk write and the kernel didn't get time to finish writing the data to disk and update the file system metadata to match the data then the file system is said to be corrupted.

You can (most times) recover a corrupted LUKS encrypted file system the same as any other file system, by running a file system check. You just need an auxiliary Ubuntu installation in another partition or in another disk, (such as a USB if you like), or a Ubuntu Live CD. See post #8 in the following linked thread, [http://ubuntuforums.org/showthread.php?t=1777611](http://ubuntuforums.org/showthread.php?t=1777611)

Another thing that might be useful to know about LUKS encrypted partitions is that the LUKS 'Header' contains something called a 'salt', without which the LUKS file system cannot be decrypted, so it can be a good idea to make a backup of the LUKS header. I think (from memory it's just the first two sectors), and keep it somewhere safe and secure. Conversely, that's the part you might want to be able to destroy in a hurry if you get paranoid about somebody being able to crack your passphrase and gain access. 
There is a pretty good explanation including the commands you might want to use in the  [Official LUKS web site]("http://code.google.com/p/cryptsetup/"), especially see [FrequentlyAskedQuestions]("http://code.google.com/p/cryptsetup/wiki/FrequentlyAskedQuestions").

---

### Post by Darris on 2012-09-21
I know it's late, but that was very helpful, thank you.

---

