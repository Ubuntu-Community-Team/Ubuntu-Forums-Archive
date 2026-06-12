---
title: "Windows convert curious about ubuntu recovery options"
date: 2011-04-20
forum: General Help
---

### Post by groogrux on 2011-04-20
Hi, I have recently started using ubuntu 10.10 as my primary operating system (coming from Windoze 7) and I love it so far.  As with any operating system, its good to know how to repair/restore your system if something goes wrong.  With Windows, I knew the basics of going into safe mode, using system restore, etc.  What are the recovery options for Ubuntu?  I noticed the extra options in GRUB (recovery, memtest, etc) but I wasn't sure exactly what they did.  Are there some terminal commands that are good to know to repair common problems?  

Sorry for the block of text.  I suppose the main thing I'm asking is what are the general steps to take to diagnose/fix a problem if I encounter one with Ubuntu?  thank you very much!

---

### Post by bodhi.zazen on 2011-04-20
That is a very broad question and of course it sort of depends on the problem. It takes some time to learn to problem solve in any OS, in linux I find the command line is most helpful.

You run a command in the command line and interpret the error message. Of course some error messages are more difficult then others.

If (when) you need assistance, post any error messages you get here.

---

### Post by groogrux on 2011-04-20
Yeah, I figured there wouldn't be an all powerful solution. I guess what I want to know is what are a few good terminal commands to know if ubuntu won't boot up.  Also, should I be using the recovery entry in GRUB or just use the LiveCD? Thanks for the fast response.

---

### Post by tredegar on 2011-04-20
So far, linux seems to be working for you. Good, because it has worked for me for _years_.

If you run into problems, come here, accurately describe what went wrong, and you'll get help.

If you know you are "playing with fire", or about to try commands when you know you are out of your depth, then please take a backup first, or it'll be a reinstall and maybe data lost.

Just apply common sense and you will be OK.

Have fun.

---

### Post by r-senior on 2011-04-20
Like many others I always use a separate /home partition (in fact I tend to use separate physical disks) because it's then quite simple to reinstall if things go bad. As long as you have a recent backup of /home, you are pretty much covered for losing your disks or messing things up. Makes upgrading easier too.

---

### Post by groogrux on 2011-04-20
Thanks for all of your replies.  I value the information greatly. I've been very happy with my linux experience so far.  Never thought I'd actually like the command line, but i love it now haha.  The one mistake I made was not separating my /home and / partitions.  Do they have to be on separate partitions entirely or just under the same extended partition?

---

### Post by BertN45 on 2011-04-20
In the stone age somebody decided that 4 partitions and 1 MB of memory was enough for a PC. To overcome the problem they have invented the extended partition, that allows to have more additional logical partitions as part of the extended partition. Windows still makes a difference between Primary and Extended partition, but for Linux it is largely the same. So yes you can use the extended partition.

A tool for the recovery is of course your live-cd from that you can always repair your installation and you have the full Gui and all terminal commands at your disposal..

---

### Post by Mark Phelps on 2011-04-21
> **groogrux said:**
> ...With Windows, I knew the basics of going into safe mode, using system restore, etc.

Just so you know ... there is no builtin System Restore capability in Ubuntu.  (Some will say this a GOOD thing!).

You're expected to do backups of you later want to do roll-back to a previous state.

Also, when you do an OS upgrade (like upgrade to 11.04 from 10.10), there is no roll-back capability there, either. Once again, you're expected to do your own backups.

---

### Post by mastablasta on 2011-04-21
^^ bah who needs those restore points anyway :-P

---

### Post by Frogs Hair on 2011-04-21
I use Back in Time  from the software center to take snapshots of my home folder . System restore is nice, but learning to be thoughtful about what you are doing on your computer is better .

---

### Post by bodhi.zazen on 2011-04-21
I would echo the good advice of using a separate /home or data partition. That way you can re-install without loosing data.

When problems occur , new users often re-install, takes 10-20 minutes.

Over time, as you gain experience, you will not need to re-install as much.

The recovery mode in linux is basically a root shell (administrative access) without a graphical interface. You then run commands to investigate and restore your system. It is most often used when, for some reason either X (the graphical interface) fails, there are problems logging in or switching to root, or hardware problems.

Again I highly advise you learn to use the command line and read the man pages.

[http://linuxcommand.org/](http://linuxcommand.org/)

---

### Post by groogrux on 2011-04-21
I've been learning as I go with the command line (using apt-get, and other basic commands).  The next step I suppose is to learn some diagnostic commands.  Thanks for the advice everyone.

---

### Post by ezsit on 2011-04-21
Look into a program called remastersys - this program will create a live DVD from your installed system and work as a recovery tool, very handy. 

I will also stress the importance of using a separate partition for /home, this makes upgrading and reinstalling a breeze as long as you remember NOT to format your /home directory when reinstalling or upgrading.

Lastly, get familiar with Unix style file permissions and using commands like chown and chmod and how they work on files, directories, and mount points. Use the man command, like: **man chmod** to get the manual page for the command chmod. Eventhough manual pages may seem intimidating, they are very handy.

---

### Post by nothingspecial on 2011-04-21
Here is an excellent, well documented **one-line** back up script.

Read all the comments because you will get errors that don't matter.

Also, it is supposed to be run on one line. The web-page has formatted it into multiple lines.

[http://openubuntu.com/index.php/topic,671.0.html](http://openubuntu.com/index.php/topic,671.0.html)

---

### Post by groogrux on 2011-04-21
I'll be sure to do that.  I was intimidated by the "manually partition" option when first installing Ubuntu.  Now I see the benefits to it.  I may reinstall in order to optimize my system.  Thanks again.

P.S. Nice quote ezsit.  Morrison is the man.

---

