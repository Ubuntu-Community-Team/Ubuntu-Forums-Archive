---
title: "Computer performing badly the last couple days"
date: 2012-03-13
forum: General Help
---

### Post by webcomm on 2012-03-13
I have a 1 1/2 year old laptop, originally with Windows XP.  I run Ubuntu with wubi.  I started using Ubuntu last summer.  The computer performed beautifully until yesterday.  

The last couple days it's been horrible, starting yesterday morning.  I don't know what to do.  Clearly this may not be an Ubuntu problem at all.  I just don't know where to begin looking for the problem.  The fan is going on every 10 seconds.  Yesterday I was doing a lot of image editing with gimp, and the computer froze up three times.  There was nothing I could do except unplug it and pull the battery out.  I figured it just couldn't handle image editing well.  But today I have done very little image editing and it is still performing badly.  At times it is more or less normal, but then will get bogged down for no apparent reason and I can barely move the mouse pointer across the screen.  

I have not installed any new software, though today there were an unusually large amount of updates to download and install.  

In a similar situation, what would you look at first?

The computer has 2 gigs of RAM.  Intel Core 2 Duo T5670 @ 1.80GHz x 2.

I am in the middle of a project so getting a new computer and moving everything to the new computer is not a great option, and I would hate to give up on a computer all the sudden when it is only 1 1/2 years old.

Perhaps I could try resetting the gnome settings?  Not sure what I'm talking about there... just vaguely aware that I can somehow reset the desktop.

A separate ongoing issue I've had (and I have another thread open in the forum) is that I can't turn on "mirror displays" lately.  It won't stay on.  I mention that here in case it might be related.

Thank you

---

### Post by Sylos on 2012-03-13
Hello there.

Im dont know all that much about anything BUT I've seen a few laptops run slow just because of blocked fans/vents causing overheating. This will either cause the CPU to throttle back (hence slow down) of the heat will build up impeding the operation of the machine, or eventually lead to shutdown or burn out (never seen a burn out though). 

Anyhow, in the absence of any other advice I can give it may be worth checking your vents and seeing if the machine is just clogged.

Cheers

---

### Post by Diametric on 2012-03-13
Are you running both XP and Ubuntu?

Also, run this from your home directory in the output and post the results:

```
df -h
```

Good luck!

---

### Post by webcomm on 2012-03-13
Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0             15G   13G  1.3G  91% /
udev                  991M  4.0K  991M   1% /dev
tmpfs                 400M  964K  399M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                 1000M  1.2M  999M   1% /run/shm
/dev/sda2              68G   58G   11G  85% /host

Meanwhile I'm trying to figure out how to get the bottom cover off the computer to look for dust.  It's a Dell Vostro 1510 laptop.

---

### Post by LinuxFan999 on 2012-03-13
> **webcomm said:**
> Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0             15G   13G  1.3G  91% /
udev                  991M  4.0K  991M   1% /dev
tmpfs                 400M  964K  399M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                 1000M  1.2M  999M   1% /run/shm
/dev/sda2              68G   58G   11G  85% /host

Meanwhile I'm trying to figure out how to get the bottom cover off the computer to look for dust.  It's a Dell Vostro 1510 laptop.
I would also recommend cleaning the root partition, since I noticed that it is nearly full.

---

### Post by webcomm on 2012-03-13
I got the bottom cover off the laptop and found a pretty significant clump of dust inside the fan.  After restarting, the fan is still coming on pretty often but perhaps not running as long each time.  Really, I'm not sure if I simply started noticing the fan more because the computer was not running well.  It can't hurt to have that clump of dust out of there.

As for the partition being nearly full, there is actually a lot more room on the hard drive that I am currently not able to use.   A couple weekends ago, I shrunk the windows partition but then could not figure out how to create a new partition with the free space.  I was hoping to create a partition where I could install Ubuntu and thus not have to use wubi anymore.  I followed the instructions I found here: [http://jamesmcdonald.id.au/it-tips/gnu-linux/linux-tools/shrink-your-windows-xp-ntfs-partition-to-half-size-and-install-linux-while-keeping-the-nt-bootloader](http://jamesmcdonald.id.au/it-tips/gnu-linux/linux-tools/shrink-your-windows-xp-ntfs-partition-to-half-size-and-install-linux-while-keeping-the-nt-bootloader)
I got to step #11 but did not know what to do at that point.  Step #11 mentions deleting the old partition, but I never had any intention of deleting the windows partition.  I just wanted to shrink it.  I don't know if the attempt at re-partitioning is a factor in my recent problems.

ps -- Not sure if it's just my imagination, but the fan does seem to be running less frequently now with that dust clump removed.

---

### Post by electrojustin on 2012-03-13
Perhaps run an application to monitor temperatures? I've found Screenlets work rather nicely. Also, perhaps run system monitor to check RAM usage and CPU load to see if there's anything out of the ordinary. Is there anything you might have done in the last couple of days that might have triggered this, perhaps an update or new software?
 
By the way, as for getting stuck on that tutorial on how to resize partitions, it might be easier to install gparted on an ubuntu livecd (though I must warn that resizing windows partitions doesn't always go very well-I would make backups and not plan on doing anything important with the computer for a day or two).

---

### Post by webcomm on 2012-03-14
I don't think it's a temperature issue.  My fan is no longer coming on very often, but the system is still freezing up regularly.  I have had to unplug and pull the battery out twice today.

At times the computer works great.  It will work great for an hour or so, then get bogged down quite suddenly.

As for running system monitor, that's impossible when the system is frozen.  Opening the terminal is impossible... or the terminal opens, but then hangs.  At such times, CTRL+ALT+t will not open the terminal.  So there is no way to run the system monitor when I most need to.  When I'm having these problems, I can barely move the mouse pointer.  I move my mouse, and 15 seconds later the pointer moves a few millimeters, if at all.

I am getting quite a few "unresponsive script" errors in Firefox at times.  At least a few each day the last three days.  So I wonder if there could be an issue with FF that is complicating things, or perhaps the script errors are not the cause but just another effect.

I still think the display issue may be related.  That is, not being able to turn on "mirror displays".  I just have a hunch that it could be that my system is having trouble dealing with complicated graphics and the problem may be related to whatever is preventing me from turning on "mirror displays".

Basically, I have no clue how to diagnose.  Just theories that are hard to test.  

I don't think it has anything to do with the partition, since I shrunk the partition more than a week ago but have only been having problems with the computer the last three days.  I used the computer very intensively last week and had no problems.

PS -- I have now reset the gnome settings to defaults and also deleted some FireFox addons.  I'll see if any of that helps.

---

### Post by oldfred on 2012-03-14
As mentioned above your NTFS partition looks full. NTFS works best with 30% free, starts to slow at 20% free and just about stops working at 10% free. You are at 15%.

Do you have 4 primary partitions? Most Windows 7 laptops are set up that way, so even if you make free space you cannot create more partitions.

Mentions HP but applies to most portables.
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

---

### Post by webcomm on 2012-03-15
oldfred,
Thanks for those guidelines for free space.  I was able to create a new ext3 partition and I installed Ubuntu in it.  I have a bit more research to do to see how to boot into the new partition.  Then I'll be able to delete the wubi install from the windows partition and have plenty of free space in both.

---

### Post by Helen McCall on 2012-03-18
I would recommend looking at your log files - especially syslog and dmesg to see if there have been any important error messages wihcih might account for the slowing of your system. The things you might look out for are I/O errors and similar hardware problems which might have been cause by the high temperatures.

Monitor those logfiles to make sure you are not still getting such errors - if they persist you might have permanent hardware damage.

---

