---
title: "How do I make /home functional on another drive?"
date: 2010-04-19
forum: General Help
---

### Post by swright007 on 2010-04-19
I have Ubuntu 9.10 set up on a 40 GIG HD.  For upgrade purposes I would like to copy my /home directory to another directory.  That way I can completely wipe my operating system without losing my programs.  Can someone show me an easy way of doing this... ALSO once done, after I installed the, say, next upgraded operating system how would I tell it to look to the other hard drive for it's /home directory?

                                        Thank you, 
                                       Scott Wright

---

### Post by mikewhatever on 2010-04-19
Use rsync, <rsynk -av /home/$USER /destination_folder>.
If you want to have a separate home directory, choose Advanced/Manual at the partitioning stage, and specify the mount points for root and home.

---

### Post by darolu on 2010-04-19
If you want to use the other drive as your home, you'll have to edit your fstab file to meke it mount at /home

---

### Post by swright007 on 2010-04-20
SO basically, if I want it to work that way, I need to wipe everything and just set it up AS such to begin with. There is no way around that.  If that is the case, then my original premise for setting it up that way wouldn't work the way I intended.

---

### Post by dcstar on 2010-04-20
> **swright007 said:**
> SO basically, if I want it to work that way, I need to wipe everything and just set it up AS such to begin with. There is no way around that.  If that is the case, then my original premise for setting it up that way wouldn't work the way I intended.

No.

There are numerous HOWTOs on setting up a separate /home partition, please search them out.

---

### Post by swright007 on 2010-04-20
I apologize if I seemed ungrateful.  There are parts on Linux that are still new to me.  The idea that all devices are seen as one directory stucture, where as with Windows there are drive letters and so forth, is a bit confusing to deal with. 
     I believe there is a better way than everything being on one hard drive and I think it is within my grasp with this operating system.  I will continue searching for a "complete" tutorial.   The ones I have bumped into are flawed and have you copying things to directories you haven't created yet, and so forth.   
     Thank you all for your help. Please forgive my newness to this. I was literally just asking clarification. 

                                          Scott

---

### Post by john newbuntu on 2010-04-20
If you do not have an additional disk or partition, you need to create that first to house your /home filesystem.  Once that is done, go through those tutorials as mentioned by the posters above.  Here are 2 examples:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
[http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/](http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/)


A very brief summary of those are as follows:
1. Create a new ext4 partition using liveCD to host /home. Lets call it /dev/sda7
2. Boot using a liveCD.  Mount this partition as /mnt/newhome using commands:
      # sudo mkdir /mnt/newhome
      # sudo mount -t ext4 /dev/sda7 /mnt/newhome
3. Mount your current Ubuntu partition containing /home and copy files from current home to new.
      You can use any method - cp, tar, cpio, rsync etc.  But make sure that it is a perfect clone.
      # cd /home/
      # sudo find . -depth -print0 | sudo cpio --null --sparse –-preserve-modification-time -pvd /mnt/newhome/
4. Unmount new home and make way for new home
      # sudo umount /mnt/newhome
      # sudo mv /home /old_home
5. Recreate /home directory
      # sudo mkdir /home
6. Make a copy of /etc/fstab.  Edit /etc/fstab and add:
      /dev/sda7 /home ext4 nodev,nosuid 0 2
7. Adjust permissions on the /mnt/newhome
Reboot and check if everything is ok for a couple of days.  If ok, delete /old_home.


When you install a newer/next version of OS, use manual partitioning and point the /home directory properly to the new /home directory but DO NOT FORMAT the /home directory.  That should do it mostly do it.  You may have to do some fine tuning if some app configuration has changed.  But those are mostly minor.

---

### Post by mikewhatever on 2010-04-20
> **swright007 said:**
> SO basically, if I want it to work that way, I need to wipe everything and just set it up AS such to begin with. There is no way around that.  If that is the case, then my original premise for setting it up that way wouldn't work the way I intended.

I was under impression that you wanted to wipe the system clean, and start over with a separate home partition. Is that not the case? I forgot to mention, that you can't keep the installed programs when reinstalling the system, just settings and data, which are in the home directory.

---

### Post by swright007 on 2010-04-20
Is there a way to log in as "root" from the livedisk?   I  tried changing roots password and logging in, but it didn't seem to work.

                                   Scott

---

