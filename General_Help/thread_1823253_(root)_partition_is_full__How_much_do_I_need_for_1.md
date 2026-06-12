---
title: "/ (root) partition is full?  How much do I need for 10.04"
date: 2011-08-11
forum: General Help
---

### Post by Dngrsone on 2011-08-11
I am running 10.04 desktop AMD64 on an HP G72 dual-boot with Win7.

Currently, I have 29.5GB allocated to / with a separate /home partition @ 40GB.

My / partition is getting full.  As in 2.3GB free.

I would have sworn my last install only had 20GB for the / partition...

Anyhow, what size should I have?

---

### Post by MG&amp;TL on 2011-08-11
Unless I've got something seriously wrong in my head here, it depends how many programs you install, 'cos they're in /usr/bin, right?

So if you've got more programs, or one monster one you didn't have in previous install, there you have it. I think.

You could try extending the / into the /Home partition. Backup your data first though. Typically I barely use any /Home. But that's me.

---

### Post by cgroza on 2011-08-11
Maybe your apt cache is getting too big.
Try running these commands to clear the apt cache:
```

sudo apt-get update
sudo apt-get clean
sudo apt-get autoclean

```

---

### Post by Dngrsone on 2011-08-11
Hrm... the only two I can think of are Docky and Google Chrome...

... and Banshee.

I'll have to check on that.


Thanks for the quick answer!

I'll have to come back to this later because I had to boot Win to transfer my backup file to LAN storage.

Dang!  Now that I think about it, I pulled that 9.8GB backup file out of / and my free space did not increase.


I'm beginning to wonder if I have some form of malware in Ubuntu.

Thanks, cgroza, I will try that, too.

---

### Post by MG&amp;TL on 2011-08-11
go 'gksu nautilus' in a terminal, navigate to / and see what's taking the space. Just don't delete anything!

---

### Post by pqwoerituytrueiwoq on 2011-08-11
clean out some log files i have seen some balloon to multiple gigs that was on 9.04 and printer related though you can use [bleachbit]("apt:bleachbit") to clean stuff

---

### Post by Dngrsone on 2011-08-11
Bleachbit helped me recover some 10GB of space!  Thanks to pqwoerituytrueiwoq for that.

I did the clean, autoclean, scrubbed some 2GB of logs, the entire /usr folder is only 3GB.

Thank you for the help, guys!

---

### Post by pqwoerituytrueiwoq on 2011-08-11
still looks over sized to me my 10.04 install uses a mere ~5.5gb
did you install some large games?

---

### Post by Dngrsone on 2011-08-11
In addition to the games that came with the install, I have Minecraft (which resides on the separate /home partition, no?) and I recently started messing around with Angry Birds.

I haven't added a lot of programs or anything-- Banshee, Docky, the GIMP, Palm OS devices, Simple Backup... I have local install of WordPress but that doesn't take even a gig of space in /var/www... though mysql has recently started giving me problems.  [IMG]http://i230.photobucket.com/albums/ee303/Dngrs_1/argh.gif[/IMG]

---

### Post by pqwoerituytrueiwoq on 2011-08-11
is your database in /var/www a few gigs?
wondering where ~4-5 gb is coming from

---

### Post by idoitprone on 2011-08-11
```
df -h
```

?

```
du -hd 1 /
```

?

---

### Post by Dngrsone on 2011-08-11
The mysql database isn't in /var/www... that whole folder is 2.2MB.

Oh... found it! There was a 6.4GB tar archive in /var/mysql folder.

It was part of my backup from a couple months ago when I was trying to recover my local WordPress blog.

The system doesn't register the additional space right away, though, huh?

---

### Post by cgroza on 2011-08-11
In the future, if you want to see what branches of your filesystem are taking up the most space, Ubuntu includes an application called Baobab for this task. I think they call it Disk Usage Analyzer.

---

### Post by bjarkih on 2011-08-22
Hi, I'm having a similar problem.  I'm running natty amd64 and this is the first time the root partition has (almost) filled up.  I've had several Ubuntu systems running for the last two years and this is a first time occurrence.

output of df -h :

```
root@*******:/# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             4.6G  4.4G   43M 100% /
none                  1.7G  724K  1.7G   1% /dev
none                  1.7G  124K  1.7G   1% /dev/shm
none                  1.7G  436K  1.7G   1% /var/run
none                  1.7G  4.0K  1.7G   1% /var/lock
/dev/sdb1             299G  155G  144G  52% /media/sdb1
/dev/sda7             3.7G   72M  3.5G   3% /tmp
/dev/sda1             184M   68M  107M  39% /boot
/dev/sda8             3.7G  565M  3.0G  16% /var
/dev/sda9             898G  255G  598G  30% /home
```

---

### Post by oldfred on 2011-08-22
For standard desktops I do not recommend separate system partitions so you can share any free space. Otherwise you have to plan system size for every partition.

I normally suggest 10 to 20GB for / with everything included, but I have a somewhat larger drive and use 25GB for all my / that I have.

Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

---

### Post by Wim Sturkenboom on 2011-08-22
> **bjarkih said:**
> Hi, I'm having a similar problem.  I'm running natty amd64 and this is the first time the root partition has (almost) filled up.  I've had several Ubuntu systems running for the last two years and this is a first time occurrence.
Did you follow the suggestions in this thread to see what eats the space?

If you reboot regularly, the below will not apply. Else it might

*_df_* reports different from _*du*_. If you delete a file that is in use by a program, *df* will not see that while *du* will. *df* will only see it once you close the program that has the file in use. You can check for this type of files with the _*lsof*_ command.

```

fortyfourgalena@desktop-01:~/Desktop$ **lsof |grep deleted**
nautilus  2170 fortyfourgalena   21r      REG                8,9    64296    3558940 /home/fortyfourgalena/.local/share/gvfs-metadata/home (deleted)
nautilus  2170 fortyfourgalena   22w      REG                8,9    32768    3558941 /home/fortyfourgalena/.local/share/gvfs-metadata/home-bf7d2b87.log (deleted)
indicator 2225 fortyfourgalena   20w      REG                8,9    64296    3559232 /home/fortyfourgalena/.local/share/gvfs-metadata/home (deleted)
indicator 2225 fortyfourgalena   21r      REG                8,9    32768    3559244 /home/fortyfourgalena/.local/share/gvfs-metadata/home-d056db1e.log (deleted)
gnome-ter 2615 fortyfourgalena   22u      REG                8,7     2446    1232223 /tmp/vteG56S0V (deleted)
gnome-ter 2615 fortyfourgalena   23u      REG                8,7      304    1232228 /tmp/vteV86S0V (deleted)
gnome-ter 2615 fortyfourgalena   24u      REG                8,7     1952    1232229 /tmp/vte1Z720V (deleted)
fortyfourgalena@desktop-01:~/Desktop$ 

```

---

### Post by Dngrsone on 2011-08-22
I ran into the problem again just recently-- I had a misconfigured plugin in a local WordPress install that generated 11GB of error logs in Apache2 in the space of a couple minutes.

I saw what was happening and was able to reboot the machine in safe mode and was able to delete the logs so I could start Ubuntu again correctly.

---

### Post by Wim Sturkenboom on 2011-08-23
Time to consider to move /var to a dedicated partition ;)
And to move your database out of /var if applicable and you have not done so yet.

---

### Post by Dngrsone on 2011-08-23
Time for me to get a larger hard drive... [IMG]http://i230.photobucket.com/albums/ee303/Dngrs_1/argh.gif[/IMG]

---

