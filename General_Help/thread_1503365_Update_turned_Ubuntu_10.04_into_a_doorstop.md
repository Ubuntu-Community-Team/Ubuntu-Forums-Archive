---
title: "Update turned Ubuntu 10.04 into a doorstop"
date: 2010-06-06
forum: General Help
---

### Post by cas007 on 2010-06-06
I am kinda fed up with the a**holes who provide updates, whathaveyou. I just want to have a machine that works. And I am spending more bloody time fixing stupid problems on this system than I ever did in 20 years of using Windows. Yeah, go ahead and say that I flame. I sure as hell do when I'm mad as hell with those that purport to say that Ubuntu is for everyone.

So here is the problem ... I allowed an auto update to go ahead on my mums's machine (952 files of it!!!!!), and received this error on reboot:

 There is a problem with the configuration server (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)

There was also a fatal error an the mail notification module and also a gnome power management fault (can't remember the exact wording). This caused the system to fail to boot into any operational mode.

I have tried all sorts of things like pressing the SHIFT key to access the menu for previous installs (didn't work either), trying to edit the /temp folder permissions using 1777 chmod (the person failed to say though HOW to do that, as do most posts that also FAIL to tell the exact steps of doing something) which I could not do even when I got to the folder using a 10.04 boot CD as it said 'You do not have permission to change these values'. Really stupid to be locked out of a machine that no one else but my mum and me use at home. (Don't you people get that this is just STUPIDITY or plain old ARROGANCE on the part of the developers/programmers to treat us like dumbasses?). We should have the option to lock ourselves out of our own machines in the setup screen.

Anyway, can anyone see themselves getting past my angry post and actually providing some pointers? 

And another reason for the anger is that I DO NOT HAVE TIME FOR THIS sort of stuff to be happening all the time. I have just come out of installing Hplip-3.10.5-1 (which was NOT available as a bona fide upgrade so had to get it direct from Debian) to get an HP 3310 printer going :mad: which took two days or more. Before that it was trying to get a Canon MP130 to work, and the woes go on. Been thinking of ditching this Ubuntu but have emails etc on it that would take just too much work to get off/backup and start from scratch.:mad::mad::mad:

---

### Post by Smart Viking on 2010-06-06
Hey, i don't know if it would actually work to open permissions to the /tmp folder(i assume you mean the /tmp folder), but to do that you would use this command:

sudo chmod 777 /tmp

---

### Post by cas007 on 2010-06-06
Dear Smart VIking,

First of all thank you very much for replying to my angst. It is much appreciated.

Ok, now to your post. How do I do what you suggest?

I am running off the Install/Boot CD of Ubuntu 10.04 and in the terminal window it has ubuntu@ubuntu: ~$

I have tried going to the physical folder but it says 'No such file or directory'. Any more ideas? By the way the suggestion you gave I have seen elsewhere and is what I was doing. Here is what the info says about the '1':

1777 implies read/write/execute for everyone on the system. However, when applied to a directory the '1' prefix implies that only the directory owner and group are able to rename and delete files. This is important in a multi-user environment where many users have open files in /tmp.
 
SO that is why I was doing 1777. If that is incorrect please advise.

PS. And you were correct, it was the /tmp folder.

---

### Post by arvevans on 2010-06-06
Ubuntu upgrades have become so bullet-proof that I have discontinued doing double-backups prior to upgrading.  Several prior, and the latest, upgrades all worked flawlessly for me.  My machines get a pretty rigorous workout with three computers (web server and 2 desktops) linked via NFS, so robustness is required and regularly achieved during upgrades of all three machines each time there is a new distribution release.

To more directly answer your posting:
[LIST=1]
[*]Did you follow the recommendations and do a backup of /usr prior to doing the upgrade?  If you have a backup, you can reload and re-install the backup so you won't lose anything.
[*]Did you download and try the upgrade release via a bootable CD to see that all your hardware was capable of running the new release, prior to doing the upgrade?  For those with hardware that is outside the usual standards, this should probably be a first step prior to committing to any upgrade.
[*]Have you posted a non-inflammatory request for help resolving this issue prior to flaming the developers?
[/LIST]

It should be possible to walk this person through the necessary steps to help recover the problem system, and to make it run with the latest Ubuntu release.  The situation though is that I am old and grouchy (have been administering UNIX and Linux systems since 1979) and thus not inclined to support those who post flames and abuse of the ones who might be able to help them.   Maybe someone else will want to help this individual, but I am going fishing and will not be thinking about Linux during that time.

Good Luck.

---

### Post by cas007 on 2010-06-06
I did an UPDATE not an upgrade. Two different things.

10.04 has been running since 7th May 2010, without any problems (apart from not running a Canon MP130).

I did not do a backup of /usr. Why would I? After all Ubuntu is for 'Everyone' and 'Everyone' (me being in that category) sure as hell wouldn't know that a backup is required before updating to 'dodgy' updates. 

I did not make a bootable CD of the update because that is not an option that I was aware of, nor does any 'window' come up and offer it to me. And when the update window comes up all I see are the buttons 'Apply' or 'ignore'(?) can't remember exactly which buttons there are. I know 'Apply' is one of them but the other one I am not sure about.

---

### Post by 4Orbs on 2010-06-06
I can't imagine how you might have gotten 952 updates on an Ubuntu install that's less than a month old unless your Mom has been installing lots and lots of stuff. But it sounds to me like your root partition ran out of room during the update process. I can't offer any advice on how to fix the current installation, but if you choose to do a fresh installation of Ubuntu I would recommend making the root partition several GB larger than it is currently.

---

### Post by cas007 on 2010-06-06
My mums HD (Hard Disk) is a 400GB one. It has 333GB left on it. Can't imagine how it has run out of space. I have been thinking of re-installing Ubuntu but don't know where to find the emails folder (Evolution email program).

When attempting to re-install from the CD the options given were two instead of the four that 9.10 had. That is what I was looking for; the 'more options' option. It wasn't there. So I decided to cancel the install but before I did the partition info showed the full 399GB being used. No separate root partition.

---

### Post by 4Orbs on 2010-06-06
Did you install Ubuntu inside Windows by using the WUBI installer? Did you install Ubuntu by giving it the entire hard drive space for just the root partition and swap? Did you install it by creating separate partitions for / and /home and swap?

Since you have the Ubuntu live cd in hand, you can see the status of your hard drive by booting into the live cd and choose "Try Ubuntu without changing anything" and once you are in the desktop of the live cd, open System>> Administration>> Partition Mgr (gparted) and have a look at the representation of the hard drive. If the root (/) partition has plenty of unused GB, then my theory is incorrect and hopefully one of the Ubuntu guru's will come along with a suitable fix.

---

### Post by cas007 on 2010-06-06
Ubuntu has been installed on 3 partitions (of the whole hard drive) without any Windows partitions, as it was not done through Windows. The partitions as shown through the GParted program is:

Partition **File System **** Mount Point ********* Size ***** Used *** Flags

/dev/sda1 *** ext4 ******* /media/xxxx ****** 371.21GB * 19.91GB * Boot
/dev/sda2 *** extended ********************* 1.39GB   --     
/dev/sda5 *** linux-swap ******************** 1.39GB   --     

So the only extra partition that is being used is linux-swap, or so I think. Hope this answers your questions. The mount point is in this format because the CD is running the machine at the moment.

---

### Post by 4Orbs on 2010-06-06
I'm really hoping someone else will post a REAL solution. I think your emails can be easily recovered by using the live cd, but I have never used the live cd for recovery so I don't know the commands to make it work. The live cd doesn't just automatically hook up to the file system on the hard drive... you need to mount the hdd partition to the live cd in order to access those folders. That's probably why you weren't able to affect any permissions changes. If you become impatient waiting for someone else to help... I'll be happy to tell you what I would do as a desperate last resort. I would make a second installation of Ubuntu while leaving the existing Ubuntu untouched. Then I would use this new Ubuntu install to access the folders of the existing old install and recover the emails by copying them from the old /home/Mom's-folder/.evolution folder (not sure where the emails are actually stashed though) to the new Ubuntu then save them to a cd or thumb drive or something equivalent. Once those important files are somewhere safe, you'd be free to wipe the hard drive and do a new install of any system you might prefer.

If you decide to try a second Ubuntu installation... when you reach the partitioning portion of the install process choose the option to "Manually Specify" the partitions, then shrink the existing Ubuntu partition down by maybe 20 GB or so, then create a new partition on that 20 GB unallocated space and do the new installation there. This whole process is a convoluted and cheesy way of salvaging those emails. It would be much wiser to just wait for someone to help you in using the live cd to recover the emails.

I'll continue watching this thread if you would like me to elaborate in any way. Best of luck.

---

### Post by cas007 on 2010-06-06
Thank you 4Orbs.

Its already 2am here in the UK, and I suspect that I will have to do as you suggested. I will install beside the old installation and then recover the emails and any other docs through the new install.

I really wish that the folks who create these updates would really watch what they are doing. It is really bad PR amongst other things. Makes people walk away from a still promising system. Yes, it has a long way to go before becoming used by many more people.

But thanks for your help.

---

### Post by 4Orbs on 2010-06-06
Believe me... most of us here have experienced the same frustration and anger at some point. Problem is, from what I understand, the Ubuntu developers seldom even look at these forums. We're all just Ubuntu users trying to help other Ubuntu users. Hope you get things working well tomorrow.

EDIT: You still might run into permission issues when trying to copy files from the old install to the new. But if that happens, it should be easy to overcome. I'll be back.

---

### Post by cas007 on 2010-06-11
Ok. Everything has been setup and is running ok. I copied some of the files from the old evolution folder and found that the folder structure from the old install came back and so did the contacts database (which is not copied over, even though one checks the box to do so, so was done by hand). For the future all updates have been disabled. Thanks for everyones help.

---

