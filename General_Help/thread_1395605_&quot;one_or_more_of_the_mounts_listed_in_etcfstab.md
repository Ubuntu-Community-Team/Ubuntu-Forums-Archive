---
title: "&quot;one or more of the mounts listed in /etc/fstab cannot yet be mounted&quot; message"
date: 2010-02-01
forum: General Help
---

### Post by LonelyAppleHater on 2010-02-01
Hi all,

I just wanted to help someone out that might be having the same problem I had.

I'm running 9.10 on my netbook.  Home, Root, and swap all encrypted using the alternate installer.  

It was running absolutely fantastic until I started getting some strange messages on boot saying "superblock is dated in the future" or something like that, and then said it fixed it.  So I ignored it.

Then, it was trying to perform fsck on my partitions, but stopped at my encrypted home with the "one or more of the mounts listed in /etc/fstab cannot yet be mounted, waiting for /dev/mapper/vg-vghome" (my encrypted home directory).  

Some posts would say that it would just continue after that message, but for me it didn't.  

I tried a couple of things some posts suggested such as changing the last column in /etc/fstab (the <pass> column) to 0 in my entries to try to pass the fsck, but no go.  Then I tried to change the UUID's to the corresponding /dev/sdxx in /etc/fstab and the UUID in my /etc/crypttab to /dev/sda5 (where my encrypted root, home, and swap reside), but that still didn't work.  I did a blkid and vg-vghome was not listed with a UUID.  

BUT, the one for my encrypted root was there, telling me that it just stopped mounting at vg-vghome.  So, I know that everything was decrypted successfully, I just had a problematic home volume.  So, I figured what the heck and just do a mount -t ext4 /dev/mapper/vg-vghome /home.  

Not only could I see my home dir, but I did a control-D do resume the script, and gdm came right up!  The only thing messed up I could see was my panel had dockbarx missing.  No biggie.  Now, I restored the original /etc/fstab file, rebooted, and now fsck could do it's thing and I'm back to normal again!  fsck did find a couple of bad inodes and cleared them.  Weird, cuz when fsck did that I logged in and found out a couple of applets on my panel reset.  Everything else was fine.

I just thought I pass this along and give this suggestion in case they're stuck like I was with that dreadful message.  I'm happy I didn't have to reinstall from scratch again.  I was blaming Ubuntu, ext4, encrypting my drives, etc. for the problem.  :)

Now I'm off to back up my home.  Hope this helped someone.

---

