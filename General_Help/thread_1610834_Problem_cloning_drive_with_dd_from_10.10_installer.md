---
title: "Problem cloning drive with dd from 10.10 installer CD"
date: 2010-11-01
forum: General Help
---

### Post by rmcellig on 2010-11-01
I am trying to clone my internal drive on my laptop using the dd command after starting up my computer using the 10.10 installer CD. Nothing happens when I follow the instructions from this site:

[http://tinyurl.com/2ed6wje](http://tinyurl.com/2ed6wje)

When I follow these instructions, it doesn't work. I know that I am not being specific here but all I can say is that nothing happens. What am I doing wrong. My internal drive is 250GB and the partition I created on my DOS formatted external drive is 250GB as well.

I am looking for a quick and easy one command way to clone my drive.

If there is a better way, let me know. Thanks!!

---

### Post by blueridgedog on 2010-11-01
Please post the command you used (exactly) and the output of 

```
sudo fdisk -l
```

You should not have partitions on the destination drive or use any partition references if you are trying to clone the drive.

---

### Post by rmcellig on 2010-11-01
I will post back. In the meantime, can I reformat my 500GB drive to a single partition instead of the two partitions I have on it now? Would that work with dd? Does it matter if it is DOS formatted or should I format ext 4?

---

### Post by HermanAB on 2010-11-01
Here are some tips:
[http://www.aeronetworks.ca/howtos/netcat-howto.html](http://www.aeronetworks.ca/howtos/netcat-howto.html)

dd doesn't necessarily care about the formatting of the drive.

---

### Post by rmcellig on 2010-11-01
This is what I got:

ubuntu@ubuntu:~$ sudo fdisk &#8211;l

Unable to open &#8211;l
ubuntu@ubuntu:~$

---

### Post by blueridgedog on 2010-11-01
the command is "sudo fdisk -l" with the option being the letter l (between k and m) in lower case...the font may make it look like a number one.

---

### Post by coffeecat on 2010-11-01
> **rmcellig said:**
> This is what I got:

ubuntu@ubuntu:~$ sudo fdisk &#8211;l

Unable to open &#8211;l
ubuntu@ubuntu:~$

You've got an em (long) dash instead of an en dash (hyphen). How did you do that? Are you using a Mac keyboard?

---

### Post by blueridgedog on 2010-11-01
> **coffeecat said:**
> You've got an em (long) dash instead of an en dash (hyphen). How did you do that? Are you using a Mac keyboard?

Doh!  Missed that one, I though it was the l vs 1 issue...good catch.

---

### Post by rmcellig on 2010-11-01
Does this look right?

sudo dd if=/dev/sda of=/dev/sdb

All I get is a flashing cursor.

---

### Post by rmcellig on 2010-11-01
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00073c51

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29255   234983424   83  Linux
/dev/sda2           29255       30402     9212929    5  Extended
/dev/sda5           29255       30402     9212928   82  Linux swap / Solaris
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: invalid flag 0x09ec of partition table 5 will be corrected by w(rite)

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00073c51

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       29255   234983424   83  Linux
/dev/sdb2           29255       30402     9212929    5  Extended
/dev/sdb5   ?      266260      266338      628744+  ea  Unknown
ubuntu@ubuntu:~$

---

### Post by coffeecat on 2010-11-01
> **rmcellig said:**
> All I get is a flashing cursor.

That means it's doing something - um, hopefully. I've looked at the dd manual and there doesn't seem to be a verbose switch, which is a pity. Most things I do from the terminal I use the -v option to be sure that I get feedback. One comment:

> **rmcellig said:**
> I am looking for a quick and easy one command way to clone my drive.

One thing dd is not is quick. Prepare for several hours for 250GB. Which is particularly disconcerting with no visual feedback.

---

### Post by rmcellig on 2010-11-01
Thanks Coffeecat!! You mention that dd is SLOW!! Better solution? I have the parted magic CD but I find everytime I clone my drive, I have to go through all of the steps over and over again. There must be a quicker way?

All I want is a quick easy and efficient way to clone my drive. Thanks for all the help so far!!!

I am going out with a friend of mine today to buy her a new laptop so that she can use Ubuntu. She is seriously considering ditching her Mac. I am in the same position. After over 20 years of using a Mac, I find I spend about 80% of my time in Ubuntu these days. I really like it!

---

### Post by coffeecat on 2010-11-01
> **rmcellig said:**
> Thanks Coffeecat!! You mention that dd is SLOW!! Better solution? I have the parted magic CD but I find everytime I clone my drive, I have to go through all of the steps over and over again. There must be a quicker way?

All I want is a quick easy and efficient way to clone my drive. Thanks for all the help so far!!!

If you want to clone the hard drive, dd is the best way, but the trouble is that it clones the probably 60-80% of the drive you are not actually using. All the spare bits and bytes in the as-yet unused sectors.

If you mean to clone your installed system, then yes there is a much quicker way, several in fact, but it's more challenging and needs more Linux knowledge. Let me give you an outline and then you'll see what I mean.

First, you simply need to partition and format your destination drive the same as your source drive. Then, looking at your fdisk output I would guess all you need to do is to get the contents of partition #1 on sda to sdb. Bootloader and swap we'll cover in a moment.

The cheapest, dirtiest, quickest, nastiest, but most effective way is simply to use 'sudo cp -av *' from sda1 to sdb1. There are people on this forum who might say, 'That won't work.' To which I reply:

<panto_mode>
**Oh, yes it does!**
</panto_mode>

However, that doesn't give you a bootable system. The UUIDs for both the root partition and the swap partition in /etc/fstab and in the grub files are wrong. Also, you do not have grub installed to the mbr yet. The best way of dealing with all this is to boot up a live CD - in fact the 'sudo cp' needs to be done from a live CD, 'outside' the system you are copying. Run 'sudo blkid' to determine all the UUIDs. Edit /etc/fstab on the destination drive to reference the correct swap UUID. Run tune2fs to write the sda1 UUID to sdb1. Finally, install grub2 stage 1 to the mbr [thusly]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")

A slightly more long-winded but more elegant way (from the live CD) would be to make a tar.gz or tar.bz2 tarball of the whole of sda1, and then untar this to sdb1. You'd need a separate storage drive for the (large) tarball, but this has the advantage of giving you an archive. And for those who will protest that you have to include a load of --excludes in your tar command, I reply:

<panto_mode>
**Oh, no you don't!**
</panto_mode>

If you detect the voice of bitter experience, you would be right. :wink:

But with the tar method you still have to deal with the UUIDs and grub.

If you want to try any of this, just post back.

---

### Post by blueridgedog on 2010-11-01
> **rmcellig said:**
> Does this look right?

sudo dd if=/dev/sda of=/dev/sdb

All I get is a flashing cursor.

It may take a few hours...a flashing cursor is an indicator of it working.  Open another terminal and enter the command "top" to watch what is happening...you should see the dd command using resources and doing its job.

---

### Post by BbUiDgZ on 2010-11-01
this may help with what your trying to do
[http://ping.windowsdream.com/](http://ping.windowsdream.com/)

---

### Post by rmcellig on 2010-11-01
Hi BbUiDgZ

So what you are saying is that I can use Ping to clone my drive? Looks like it is pretty straight forward.

---

### Post by blueridgedog on 2010-11-01
> **rmcellig said:**
> Hi BbUiDgZ

So what you are saying is that I can use Ping to clone my drive? Looks like it is pretty straight forward.

You are almost there with dd, no need to bail just yet.

---

### Post by rmcellig on 2010-11-01
Hi blueridgedog

Thanks for the vote of confidence. dd sounds like the best and easiest way but I am concerned about the length of time it takes.

---

### Post by blueridgedog on 2010-11-01
> **rmcellig said:**
> 
Thanks for the vote of confidence. dd sounds like the best and easiest way but I am concerned about the length of time it takes.

Hard drives are slow!  I used to start a dd on a server rebuild and go home for the night!

---

### Post by rmcellig on 2010-11-01
Can I split my 500GB drive in two so that I can backup my internal 250GB to the 250GB partition using dd? Options if I can't?

---

### Post by ezsit on 2010-11-01
I realize this is not exactly what the OP asked, but here is my routine that has worked very well for me using Ubuntu systems.

Go to [www.remastersys.com](www.remastersys.com) and follow the instructions to install the remastersys program. Install any updates and clean out the APT cache with the **sudo apt-get clean**.

Once you are ready to run remastersys, it will create a liveDVD installable copy of your Ubuntu installation. You can use the DIST mode to create a default setup without any of your personal data since the /home directory is ignored during DIST mode backup. The resulting liveDVD will contain all your software installations and changes but not your preferences changes, so the re-installed system will look like a fresh Ubuntu install, just with the updates and software changes already applied.

I use this and keep my data backed up separately on removable hard drives. If I re-install I use the same user name to avoid any problems with permissions and user numbers.

The BACKUP mode will copy your /home directory and retain all your data and passwords. This takes a lot more space and if you have more than 4.3GB of total used space, will prevent the remastersys from completing. So, even with the BACKUP mode, it is best to save your data separately.

---

### Post by rmcellig on 2010-11-01
Cool ezsit! Sounds interesting. So you are saying that I can just backup my home directory somewhere else and then use the app you recommended to make a live CD of my PC without the home directory?

On second thought. I wanted a solution where I could backup to an external drive.

---

### Post by ezsit on 2010-11-01
Here is what I do:

Right click on each folder in my /home directory and select "Compress" and choose .zip for compression method. In the case of my music folder which is 40+GB, I zip each band's folder. I then use the good old drag-n-drop into an external drive. It is a simple backup method, but I haven't lost a thing in years. As for bookmarks and email, I go into the .mozilla folder and copy the bookmarks.html file and a zip up the Mail folder in my profile directory and copy those thing as well. My method is certainly scriptable, but I haven't bothered to do that.

---

### Post by rmcellig on 2010-11-01
Thanks for the info!

---

### Post by rmcellig on 2010-11-02
Hi ezsit!


I just saw a video on how to use remastersys. This looks really easy. Am I right in assuming that I can also save the resulting /iso file to another hard drive or whatever? That it doesn't really have to be on a DVD?

---

### Post by alphaamanitin on 2010-11-02
> **rmcellig said:**
> Does this look right?

sudo dd if=/dev/sda of=/dev/sdb

All I get is a flashing cursor.


It is running.  You will not get anything until it finishes.  Also, don't use that command as is, you will spend weeks cloning a 250 gb drive (mine said 54 days at the rate it was going).  Here is what I used when I did it.

```
sudo dd if=/dev/sda of=/dev/sdb bs=16M  
```That code says read 16 MB at a time and then write it.  Much faster and I have not had any issues (did the same 250 gb drive in about 1.5 hours).  You may also want to add the conv=notrunc, noerror to copy all the free space as well.  I don't bother with it and have had great success.  

Now to check the progress of your dd:

Open a new terminal

```
pgrep -l '^dd$'
```Should give an output like: 
8789 dd  the number will change though

Then:
```
kill -USR1  8789
```That may or may not need to be sudo.  Then go back to the original terminal and it should have spit out some info.

> **rmcellig said:**
> 
I just saw a video on how to use remastersys. This looks really easy. Am I right in assuming that I can also save the resulting /iso file to another hard drive or whatever? That it doesn't really have to be on a DVD?

Yes, just change the of=/.. to be whatever directory and name you want to save it in/as. 
AlphaA

---

### Post by rmcellig on 2010-11-02
Thanks alphaamanitin!!

So adding bs=16M will speed up the process considerably?

---

### Post by rmcellig on 2010-11-02
Just tried remastersys and after the backup it said that the file as too large based on iso standards so I guess this is not the tool for me in my case :(

I will try dd and see how that goes. Still looking for other solutions. Had problems with Ping as well.

---

### Post by alphaamanitin on 2010-11-02
Much much faster.  I am not kidding, when I used the method of getting the info about how dd is working I used it to calculate how long it would take me (it reports how many bytes per second you are copying).  It was going to be 54.n days.  I have done this a few times now and when I used a computer for 4 gb of ram I tried bs=32M and had a transfer rate of 55.1 mb/s.  It only took a ~hour to copy the drive.  The whole operation depends on your ram and the speed of your ram though.  If you don't have enough ram to support bs=32M it might only run as fast as say bs=22M.  I just used this method to clone a drive for data recovery.  I had accidentally deleted a windows XP hard drive and reformatted it to FAT32.  I was able to clone the hard drive completely with dd and recover the old NTFS partition, rebuild the partition table, rebuild windows master boot record, and Windows XP booted up like nothing happened with no loss of data at all.

AlphaA

---

### Post by alphaamanitin on 2010-11-02
> **rmcellig said:**
> Just tried remastersys and after the backup it said that the file as too large based on iso standards so I guess this is not the tool for me in my case :(

I will try dd and see how that goes. Still looking for other solutions. Had problems with Ping as well.

You should still be able to do what you describe in your first post-clone the laptops internal HD to another HD.  By the way dd doesn't give a crap about the size of the drive it is cloning to; if it is not large enough it just stops when it fills the drive up, if it is too large it stops when it clones the entire hard drive.  In the latter case you can use gparted to extend the partion to fill the left over space on the larger drive.

AlphaA

---

### Post by alphaamanitin on 2010-11-02
> **rmcellig said:**
> Can I split my 500GB drive in two so that I can backup my internal 250GB to the 250GB partition using dd? Options if I can't?


Not sure if you can split it in two before you use dd.  But dd will only fill up the 250 gb you clone over to the 500 gb drive, so you may be able to use gparted to create a new partition with the left over space.  However, dd [COLOR=Red]*may*[/COLOR] [COLOR=Black]allow you to clone to a partition.  I would guess the code would be this for you:

[/COLOR]```
sudo dd if=/dev/sda of=/dev/sdb0
```  
Where /dev/sdb0 is the first partition on your 500 gb hard drive.  Hell, try it out, at worst you are out an hour or so and will just have to clone the drive not using partitions.  Assuming you don't mess up the if/of statements and wipe your drive out.

AlphaA

---

### Post by coffeecat on 2010-11-02
> **alphaamanitin said:**
> [COLOR=Black]I would guess the code would be this for you:

[/COLOR]```
sudo dd if=/dev/sda of=/dev/sdb0
```Where /dev/sdb0 is the first partition on your 500 gb hard drive.

I'm prepared to be corrected, but I don't think that will work. With if=/dev/sda you'll copy the sda mbr with  partition table and all available partitions into the first partition on sdb. Goodness knows what effect that will have.

---

### Post by alphaamanitin on 2010-11-02
Well that is true.  If you didn't plan to put a different OS on the other partition it should not be a problem.  Well maybe it would, not sure.  If you are planning to do so, I think you would have to use GRUB, possibly editing the boot partition the first time you booted it and update it after that.  I know I have read something about doing this stuff with dd and I can't remember if it was possible, or it was described why it was not possible (or perhaps simply not feasible).  

AlphaA

---

### Post by rmcellig on 2010-11-03
Hi ezsit!

I am going to try the option you suggested. As long as I can save it as an iso file.

---

### Post by alphaamanitin on 2010-11-03
> **rmcellig said:**
> Hi ezsit!

I am going to try the option you suggested. As long as I can save it as an iso file.


If it says it can't do and .iso you could try  a .img

AlphaA

---

### Post by rmcellig on 2010-11-04
I have a couple of questions:

1. Is there a way to tell how long it took to clone the drive.

2. Is there a way to do incremental clones so that subsequent clones won't take as long? I realize that the initial clone would take a while but subsequent ones shouldn't take that long?

---

### Post by blueridgedog on 2010-11-04
> **rmcellig said:**
> 
2. Is there a way to do incremental clones so that subsequent clones won't take as long? I realize that the initial clone would take a while but subsequent ones shouldn't take that long?

Once cloned, you may try to use rsync to keep them together.  It would take some experimentation, but worth a try.

---

### Post by rmcellig on 2010-11-04
Good idea! I use an rsync GUI that works very well so I can try that out. Neve thought of that.....but that's why we have these forums :)

---

### Post by alphaamanitin on 2010-11-04
A clone will take the same amount of time every time basically.  I think what you are wanting is a back up system to back up only updated files.  I don't know if you can do this with DD or not.

AlphaA

---

### Post by rmcellig on 2010-11-04
I use Lucky Backup for syncing folders and it works greeat. I'm just looking for something that would allow me to take a snapshot (clone) of my drive and update it on a regular basis. On the Mac side, this is what I was using:

[http://tinyurl.com/6krpz](http://tinyurl.com/6krpz)

What I like about Superduper is that I can schedule the clones so that for example, every morning at 1am, my main drive is cloned to an external drive. The first time it does a full clone and then after that only updates changed files. The clone is fully bootable as well so that I am up and running in no time.

I am looking for the same kind of functionality (hopefully a GUI solution), on the Linux side.

---

### Post by rmcellig on 2010-11-05
I just tried Remastersys on my machine but am now unsure what to do with the resulting files.

---

### Post by VraiChevalier on 2010-11-05
> **rmcellig said:**
> I just tried Remastersys on my machine but am now unsure what to do with the resulting files.

I just tried remastersys for the first time. I wanted a live version of my Ubuntu install with the Broadcom wireless drivers included. After running remastersys I ran the Ubuntu startup disk creator and just pointed it to the "customdist.iso" made by remastersys. Everything worked from there.

For a cloning solution have you considered or tried CloneZilla?
[http://clonezilla.org/](http://clonezilla.org/)

---

