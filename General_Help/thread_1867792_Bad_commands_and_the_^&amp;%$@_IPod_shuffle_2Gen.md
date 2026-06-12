---
title: "Bad commands and the ^&amp;%$@ IPod shuffle 2Gen"
date: 2011-10-23
forum: General Help
---

### Post by Smithie on 2011-10-23
[FONT=Verdana][SIZE=2]So, I've been trying to get my IPod Shuffle to work for a few days now, and decided to try the rebuild_db.py system recommended here:

[http://www.wiredrevolution.com/guides/sync-your-ipod-shuffle-with-linux](http://www.wiredrevolution.com/guides/sync-your-ipod-shuffle-with-linux)

No joy.  So I started to follow the instructions in the "rebuild_db.py won’t execute" troubleshooting section.  Everything was going fine until I bumped into this command line:

$ sudo mount /dev/sdb /media/my_ipod -o umask=0000

At first /dev/sbd was said to not exist.  Which I believe is correct  I have a dev/sda drive.  My bootable drive is /dev/sda1.

I tried $ sudo mount /dev/sda /media/my_ipod -o umask=0000 but the drive was busy, so I figured I needed to specify and I tried $ sudo mount /dev/sda1 /media/my_ipod -o umask=0000[/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT][FONT=Verdana][SIZE=2]
This seems to have renamed my bootable drive as "my-ipod" and moved it to my desktop.  Annoying, and I don't know how to undo this action.

So, a) how do I undo this screw-up, and b) does any one know what I did wrong and how I can get this &$@% Apple product to work.....

Thanks!!
[/SIZE][/FONT]

---

### Post by Smithie on 2011-10-23
Just in case anyone else bumps into this kind of problem, here's how I ended up resolving it.  Again, using the instructions at [http://www.wiredrevolution.com/guides/sync-your-ipod-shuffle-with-linux](http://www.wiredrevolution.com/guides/sync-your-ipod-shuffle-with-linux) under the "rebuild_db.py won't execute" section, I made the following tweeks:

First, I just unmounted the bad directory I had created and restarted the system.  My data and boot are on separate partitions, so, low risk even though I was just guessing this would solve my first problem.  It did.

Next, I did a ```
 cat /etc/mtab 
``` in order to find the right path for the ipod volume.  Mine was /dev/sdg.  This mounted the IPod again just as the instructions said it would.

Lastly, the final line of code on that website did not work for me.  I had to change it to ```
 sudo /media/my_ipod/rebuild_db.py
```.  I don't know if that is a mistake on the website or not, but doing this worked for me.  The gtkpod system still does not work for me, and neither does Banshee, but I was able to load all my mp3s into a new folder on the Ipod, execute the rebuild_db.py, and I have mobile music once again.  A bit of a pain when I want to switch out music, as the entire process of unmounting, creating a new directory with broader permission, and then executing the python script must be gone through all over again, but it works nonetheless.

---

