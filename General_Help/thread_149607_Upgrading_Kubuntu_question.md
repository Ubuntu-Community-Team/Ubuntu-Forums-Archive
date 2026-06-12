---
title: "Upgrading Kubuntu question"
date: 2006-03-24
forum: General Help
---

### Post by adie273 on 2006-03-24
Hey, this has probably been asked before, i'm not sure.

But i've been dual booting between Kubuntu and Windows for a few months now, because there is software in Windows that I needed and Kubuntu just couldn't supply me with anything I personally found as good to use. I tried Virtual machines such as Qemu but those were too slow when trying to run Windows XP in them (Even with Kqemu module), even tho I don't use Windows that much in all honesty.

However, now thanks to messing about with VMware player and what not, I can use windows with a much more reasonable speed inside Kubuntu when I need to use these specific programs. So I'm gonna Install Kubuntu as the sole OS on my system.

However I was gonna wait till Dapper was released before I did this, Now that Dapper is said to be now released in June rather than April, and me being the impatient person I am, i'm planning on just installing Kubuntu 5.10 now. Which leads me to my question....

If I install Kubuntu 5.10, how easy is it to upgrade to the latest release? Meaning, does it upgrade fine, or is it likely to result in a lot of things stopping working which i'd have to resolve manually?

I read somewhere that once something works in Linux, it will always work. However my own experience (granted it was when I used to use Fedora) I found that this was not the case.

Thanks in advance for any feedback,

Adie

---

### Post by aysiu on 2006-03-24
Let me get this straight.

You currently have a dual boot with Kubuntu 5.10 and Windows, and you want to make it a single-boot with just Kubuntu 5.10?

You're then wondering about what's going on with 6.06?

If I understand you correctly, and if Kubuntu's in charge of the MBR, your best bet is to use a live CD to delete your Windows partition and create a new Ext3 (Linux) partition. Then copy over your /home folder to that partition and edit your /etc/fstab file to include an entry mounting the former Windows partition as your /home folder.

That way, you won't have to reinstall Kubuntu 5.10, and you can be prepared for any possible screw-up with upgrading to Dapper.

With a separate /home partition, you can reinstall Dapper fresh and keep your files and settings intact. So that way, if you do a dist-upgrade to Dapper and things don't work, you can just do a clean install.

If this sounds like something you want to do, I can give you more details about the step-by-step of how to do it.

---

### Post by adie273 on 2006-03-24
Sounds like a good idea.

Never done that before, I've only ever installed from a Kubuntu Install CD. The partition Kubuntu is currently on is only about 8Gb in size though. The rest is allocated to Windows, since at the time I just wanted to mess about with Kubuntu to see how it was. So there's not really anything I desperately need to keep that I can't easy sort out again.

If you don't mind I'd love to know the best way to setup Kubuntu with a fresh install, but with the /home folder seperate incase any problems do arise.

Would all I need to do is just create a partition dedicated for my /home folder or what?

Have a feeling I created a partition with another Linux distro specifically for my /home folder and it failed to work for reasons unknown to me.:-?

---

### Post by aysiu on 2006-03-24
That situation is ideal, actually. The size of the installation (all the programs and system-wide configuration files) rarely goes above 8 GB. The bigger partition should almost always be the /home partition.

I'm going to make some assumptions about your partitioning scheme just for the sake of these instructions, but pay attention to your exact numbers.

First of all, back up whatever important data you have. We'll be moving some stuff around, deleting partitions. It may go smoothly. But you may also accidentally do something you regret. Get blank CDs, floppy disks, blank DVDs, an iPod--whatever you got. Back up *everything*.

Then, boot into a live CD.

First we need to delete your Windows partition.
Go to KMenu > System > Konsole and type ```
sudo apt-get update
sudo apt-get install gparted ntfsprogs
sudo gparted
``` A graphical partitioner will pop up. Delete the Windows partition and then from the free space, recreate a new Ext3 partition. Once you've applied the changes, exit GParted. Before you leave, though, make note of the locations of each partition. For the sake of this example, I'm going to assume that your Kubuntu partition is /dev/hda2 and that your former Windows partition is /dev/hda1.

To copy over your /home partition, we'll need to mount both partitions, so we're going to create mount points (folders) and mount them: ```
sudo mkdir /former_windows
sudo mkdir /kubuntu
sudo mount -t ext3 /dev/hda1 /former_windows
sudo mount -t ext3 /dev/hda2 /kubuntu
``` Next, we'll copy your /home folder to your new /home partition and edit your /etc/fstab accordingly: ```
sudo cp -R /kubuntu/home /former_windows
sudo cp /kubuntu/etc/fstab /kubuntu/etc/fstab_backup
sudo kwrite /kubuntu/etc/fstab
``` Add a new line that says: ```
/dev/hda1 /home ext3 defaults 0 0
``` Save /etc/fstab. Now when you exit and reboot, you should have a separate /home partition where your Windows used to be.

---

### Post by adie273 on 2006-03-24
Sounds good, I'll give it a shot,

Cheers mate! :p 

Adie

---

