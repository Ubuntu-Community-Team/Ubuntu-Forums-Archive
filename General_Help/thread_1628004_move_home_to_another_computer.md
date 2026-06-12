---
title: "move home to another computer"
date: 2010-11-22
forum: General Help
---

### Post by Odyssey1942 on 2010-11-22
I have just put together a new computer using an Intel i3-550 64 bit processor, and installed Windows (first), then Ubunutu 10.04. A separate /home partition was created. The hdd in this computer is formatted ext4.

Now I want to move my /home partition from my old 8.04 computer (32 bit, formatted ext3) which also has a separate /home partition. 

Both are connected to a lan, but so far I have not been able to connect from one to the other.

I have done lots of googling on this and am astonished at the apparent complexity involved. There seem to be issues involving whether or not the /home partition in the old computer is in use, user permissions, and I don't know what all else.

Assuming that neither the ext3 on the old and ext4 on the new, nor the 32 bit on the old and the 64 bit on the new are not issues, how do I go about moving the /home from the old to the new? If possible, I would like to use a GUI rather than the command line, but if it is necessary to use the command line, please specify where one needs to be located in the file hierarchy in order to give the designated commands. I am not very knowledgeable about using the terminal.

Also, I am a noob (probably apparent) so step-by-step instructions will be very helpful.

Thanks in advance.

---

### Post by Silent Warrior on 2010-11-22
I'd say the easiest way is to just run back and forth with a USB-stick, but... Have you tried Giver? Maybe install aMule on both machines, bundling the /home to transfer into one single .tar.bz2 or whatever, sharing, and downloading from the other machine? Similar, but using decentralised bittorrenting?

---

### Post by Odyssey1942 on 2010-11-22
Would that really be the easiest way? I am no fan of Windoze, but there it is simply a drag and drop, or a copy and paste.

Having read many of the multitude of posts asking how to move a /home directory to a new partition, or to a new hdd inside the same box, and how complicated and convoluted the directions are, I am amazed that the Ubuntu community has not yet agreed on a unified methodology for command line, never mind a GUI solution.

So if it is to be sneakernet, does this solve the permissions issue, and the "in use" issue? And does one copy the entire existing /home directory and paste it into a USB stick, then reverse the process on the new machine? 

Or does one create a tarball and unzip it on the target machine? If the latter, where should the new tarball be created? Can it go directly onto a DVD (if not too big) or a USB stick, then unzipped directly into the new /home partition. Sorry for these elemental questions, but I warned you that I am a noob.

---

### Post by Irony on 2010-11-22
> **Odyssey1942 said:**
> I am no fan of Windoze, but there it is simply a drag and drop, or a copy and paste.
Yes, just drag and drop the Documents, Pictures etc folders to an external drive and then drag and drop the contents into the respective folders on the new install.

---

### Post by SeijiSensei on 2010-11-22
> **Odyssey1942 said:**
> Both are connected to a lan, but so far I have not been able to connect from one to the other.

Can you use "ping ip.addr.other.computer" and get a response?  I'm not sure what you mean by "connect".  If they both can ping the other's IP address, they're connected.

Next, I'd use "sudo apt-get install rsync" on both machines. rsync is an excellent network file-transfer tool. 

On the 8.10 machine, type "sudo nano /etc/rsyncd.conf" and enter the following:

```

[home]
path = /home
uid = root
gid = root

```

then save the file with Ctrl-X followed by Yes.  Finally on the 8.10 machine, run the command "sudo rsync --daemon".

Now on the new machine, you should first create a new directory into which you'll place the stuff from the 8.10.  I'd advise against simply overwriting the new /home directory since the configuration files in the two directories can be very different.  I'd do this:

```

sudo mkdir /oldhome
sudo cd /oldhome
sudo rsync -av ip.addr.old.machine::home .

```

(The two colons are deliberate.) This should copy the entire contents of the remote home directory into /oldhome on the new machine.  If you want more help with rsync, take a look at its "man" page with the command "man rsync".  There are some useful examples near the bottom.

---

### Post by Odyssey1942 on 2010-11-22
Sounds good, but just want to be sure that we have specifically addressed these two issues:

"So if it is to be sneakernet, does this solve the permissions issue, and the file "in use" issue?"

Are you familiar with these two issues where copy and paste or drag and drop are concerned?

---

### Post by oldfred on 2010-11-22
If you use a sneakernet flash drive you will have to reformat to a linux file system to preserve permissions and ownership. Typical flash drives have FAT32 and will not have rights for Linux.

If you have to correct permissions after the fact, see this link. Commands are summarized at the end.

Sometimes there are dmrc errors or permission errors and this has how to correct them:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

---

### Post by Odyssey1942 on 2010-11-23
OK, apologies for the quiet period, but I am just getting up again from a bout with severe allergies. I think I now have everything I need to get started with moving the folder over to the new machine.

My wife and I are off shortly to visit our daughter over Thanksgiving and I am using this computer (the old one) right up until departure. So I will await our return early next week to actually remove the old drive and plug it into the new computer.

Many thanks to all who have contributed so far. Will appreciate any further input in the meantime if anyone thinks of anything relevant.

I will advise results after the event (or during if it goes pear-shaped.)

---

### Post by C.S.Cameron on 2010-11-23
Stick your old HDD in the new computer and copy the /home partition using gparted while booted from a Live CD or Live USB.

---

### Post by nl4m on 2010-11-23
Boot the the LiveCD, mount the new hard drive, mount the old hard drive and type in:
```
sudo cp -a /(path you used for the old hard drive)/home /(path you used to mount the new hard drive)
```

---

### Post by galvatron408 on 2010-11-23
since you said you are really new, then I would say, plug in a USB flash drive and drag and drop. (like someone else pointed out)

---

### Post by Odyssey1942 on 2010-12-04
I am back now from our travels and had a chance to do a lot of googling/reading while away.

After reading the above suggestions, and lots more of googled up discussion, I finally went with:

ssh server
rsync from old computer across the lan to 
a new directory in /home (called /oldhome) on the new computer.

So far this seem to work well and copied 13.92GB of user and hidden folders in less than one hour.

From /oldhome, I will copy all the user files into /home, and as I think possibly helpful, may copy hidden files as well. Any suggestions on which might be needed would be much appreciated.

A big part of my decision had to do with so many comments about the possibility of a GUI alternative mucking up the files in one way or another. Hard for me to understand why this should be, but I listen attentively.

Thanks for all the guidance.

---

### Post by Silent Warrior on 2010-12-04
What you want to watch out for copying the .-files and -directories is configurations that doesn't match. Avoid copying any .desktop-file - they're usually links to some installed piece of software, in which the by far best 'copy' is to just install the app from the new environment - and be careful of what bits of .gnome2, .kde, .config and .local you copy. There are several configuration items you don't want to overwrite. It usually won't be difficult restoring normality, but it's an embarrassment one might as well avoid. .mozilla will contain your browser-stuff (if you're using Firefox) - cookies, log-in things, form-data, cache, extensions - it's up to you if you want it. I think the rest is perfectly safe.
Do you have anything installed in .wine?

---

### Post by Odyssey1942 on 2010-12-05
Have never installed wine as I have an older Windoze desktop beside the linux machine for the few times I need it.

The only .file in my desktop is 

/home/robert/Desktop/.d..png (curious that there are two periods between the "d" and the "png"?)

which is described as a "png image" file

There is also only one .folder, which is .config. 

In .config, there are the following folders:

compiz
gnome-session
google-chrome
gtk-2.0
menus
totem
tracker 

and two files:

user-dirs.dirs
user-dirs.locale

This applies only to my desktop, not to other folders in my personal /home directory. (There are 45 hidden folders, plus 27 hidden files there.) Do you see any issues with the hidden files and folders listed above, without regard to hidden folders/files other than in my /desktop?

Thanks.

---

### Post by Silent Warrior on 2010-12-05
I was referring to the .-folders immediately in your /home. It looks like you can safely not back-up your .config-folder, though. You might want to wait for a second opinion, but all you stand to lose are links to menu-items - which should be set when their packages are installed, compiz-settings - which you'll have made anew on the other system, GTK-theme and appearance-settings - which you'll have already set on the other system; the pattern should be the same for the folders in .config.
Folders in .local are something you might want to be careful with, though I'm quite sure anything you fail to copy over that you maybe should have will be regenerated to some default with no pain to speak of, or you likely already have everything set up as needed. I think Banshee's ratings and Library-information are stored here, for instance - as well as applications installed in Wine (which you don't have; I spotted that).

Besides that, I seriously doubt you'll run into any issues. Just think long and hard if you're given a prompt to overwrite something - likely, you'll want to keep what's on the newer system, but there might just be an exception lurking somewhere.

---

### Post by Odyssey1942 on 2010-12-06
SW, thanks for that. 

This appears to have been a long term, continuing learning exercise. The new machine is happy as a clam, runs Chrome lightning fast.

However, the old machine is now wobbly. I upgraded it from 9.04 to 9.10, then to 10.04. On this computer, Firefox is happy as a clam, runs lightning fast. On the other hand, Chrome just sits there and spins, gives me lots of "page is unresponsive" messages, but eventually resolves the pages on some of the tabs that are open.

Clearly something went pear-shaped in the upgrade with respect to Chrome. In this sort of situation, is it best just to reinstall, or how does one go about a repair?

Also I have discovered a file in /home, named " my_500GB_MBR " that is 20.2GB in size. Under "Type", it says, "unknown".

I think this might have had something to do with a SimpleTech NAS that crashed many months ago, and having a Reiserf file format. Is MBR Master Boot Record? Any ideas?

---

### Post by Odyssey1942 on 2010-12-07
Any ideas on the Chrome issue?

Thanks.

---

