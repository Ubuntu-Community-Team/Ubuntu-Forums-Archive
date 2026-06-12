---
title: "Recover Windows Partition &amp; Files?"
date: 2010-12-21
forum: General Help
---

### Post by gopwop on 2010-12-21
I have searched for a similar problem and found [this]("http://ubuntuforums.org/showthread.php?t=1602137") which is closest, but does not have as much explanation for me to be comfortable before proceeding, as I am an absolute beginner when it comes to ubuntu.

When I bought my laptop over a year ago, it had Windows Vista installed on a 486.1 GB partition, with some kind of recovery drive set up on a 14.0 GB partition (500.1 GB total). I later upgraded to Windows 7.

Recently, something went wrong with my windows installation, as it would start up and present me with a blank black log-on screen, with nothing more than the Shut Down/Restart/etc. button and accessibilities button. I'm usually pretty good with Windows, but I was stumped as to how to get past this point and actually log on to try to fix my error. I'd been meaning to install ubuntu along side windows anyway, so I figured this was a good time, and I'd already made a disc as well as a flash drive loaded with 10.10, although I've only tinkered with ubuntu previously and know nothing of linux.

I ran off my cd to install ubuntu. At first I was going to simply install along side windows, but then saw and remembered there was that 14 GB partition (sda2) that I never use and didn't need as it was still a recovery drive for the old Vista OS I no longer had. I decided to install ubuntu over that partition and keep windows untouched on the larger partition (sda1). I set sda2 to be formatted, root "/" and boot sda2. It then had a pop-up that recommended setting up swap space. This is where I was an idiot and assumed I understood what it meant without doing further research first. From what I thought I understood, I set sda1 as the swap drive and proceeded with the installation. I guess I thought it would just use the free space on sda1 since it wasn't in use while running from sda2.

When finished, when I tried to boot from my hard drive I just got "Missing operating system" for some reason. After trying various times to boot to something without success, I had to run off the disc again. I went to the installation screen to see my partitions and became sick to my stomach to see sda1 was wiped clean. I almost cried over thinking of the first year of home videos of our son being lost.

I have since had to run in trial mode from the cd off my RAM, which is lucky since from what I understand, I should have a better chance of recovering everything. I just don't know how to do that using ubuntu. All the software I find online is for windows. I just ordered a 1TB external, which I'd been planning on buying for backup anyway, in case I need to make a drive image. It will be here in a couple of days.

I know this has been addressed in sorts in various threads, but I since I'm going to be waiting for the external drive to arrive before I proceed, I figured I'd ask for any guidance specific to my case, which would be greatly appreciated. Thanks for your time and help. Sorry if I was long-winded.

---

### Post by dandnsmith on 2010-12-21
Two points, which might be trivial, or might influence someones reply:
1. I assume sda1 is where Vista/Win7 was installed.
2. Do you know whether you would have had the option to format the swap partition set?

I think it possible that, if formatted as swap, most of the information will have been lost, but am not sufficiently experienced with NTFS structures to comment properly.

Have you tried running Gparted from the liveCD to see what it says about the partitions and partition table?

---

### Post by Phanes on 2010-12-21
It is wise to wait for the new hard drive first, and then I would disconnect the old drive so that you dont make a mistake and cause issues with whatever remains of the original operating system. Install Ubuntu first and then reconnect the old drive and that will give the ability to browse the partitions as with windows quite often moving or resizing partitions will stop the operating system from running even though its still there. So browse before looking at recovery options. In the past I have used the Convar pc inspector to recover files as its freeware but as you say it is windows software. I dont know if there are better options for Ubuntu and would be grateful if anyone else can recommend.....

---

### Post by Mark Phelps on 2010-12-21
> **gopwop said:**
> I know this has been addressed in sorts in various threads, but I since I'm going to be waiting for the external drive to arrive before I proceed, I figured I'd ask for any guidance specific to my case, which would be greatly appreciated. Thanks for your time and help. Sorry if I was long-winded.

First thing -- remove the overwritten drive and do NOT use it anymore, period.  Every write you do to it worsens your chances of recoverying ANYTHING.

Second, you will need to decide which approach you want to take:
1) Use MS Windows utilities to recover Windows-formatted partitions and Windows filesystem contents.
2) Use Linux utilities to do that work, instead.

My OWN experience, has been that 1) is by far the better choice when trying to recovery MS Windows partitions and filesystems.  But it comes at a price -- while there are trial versions of MS Windows utilities you can run to scan the drive, you are most likely going to have to PURCHASE a product to do the actual recovery.

I have found Recovery My Files to be the BEST MS Windows filesystem recovery product -- but it costs $70.

However ... you could mess around with Testdisk and Photorec, both Linux utilities, and who knows, maybe you'll get "lucky" and be able to recovery your partitions and files.

Your machine ... your data ... your money ... your choice.

---

### Post by gopwop on 2010-12-21
> **dandnsmith said:**
> Two points, which might be trivial, or might influence someones reply:

1. I assume sda1 is where Vista/Win7 was installed.
2. Do you know whether you would have had the option to format the swap partition set?

I think it possible that, if formatted as swap, most of the information will have been lost, but am not sufficiently experienced with NTFS structures to comment properly.

Have you tried running Gparted from the liveCD to see what it says about the partitions and partition table?

1. Yes, you are correct. Windows was on sda1.
2. It did give me the option to format the swap partition (sda1), but I made sure to leave it UNCHECKED since I thought that would leave the files alone and just use any free space, whereas I did have the format option checked for sda2. That is why it later surprised me to see the sda1 partition listed as having 0MB used, i.e., blank.

I have not tried running Gparted or anything other than what I mentioned in my post, and am unfamiliar with it. When I tried to browse the computer and file systems with the liveCD, it did not even list sda1 at all, under any name. It only listed the 14GB partition which had the ubuntu system files on it. 

> **Mark Phelps said:**
> First thing -- remove the overwritten drive and do NOT use it anymore, period.  Every write you do to it worsens your chances of recoverying ANYTHING.

Second, you will need to decide which approach you want to take:
1) Use MS Windows utilities to recover Windows-formatted partitions and Windows filesystem contents.
2) Use Linux utilities to do that work, instead.

My OWN experience, has been that 1) is by far the better choice when trying to recovery MS Windows partitions and filesystems.  But it comes at a price -- while there are trial versions of MS Windows utilities you can run to scan the drive, you are most likely going to have to PURCHASE a product to do the actual recovery.

I have found Recovery My Files to be the BEST MS Windows filesystem recovery product -- but it costs $70.

However ... you could mess around with Testdisk and Photorec, both Linux utilities, and who knows, maybe you'll get "lucky" and be able to recovery your partitions and files.

Your machine ... your data ... your money ... your choice.

I am currently on my computer at work and will be sure to not run my drive anymore. I am thinking I will wait for the external drive, install windows on it, and go ahead and purchase a recovery good program. There's quite a few out there, but I've read many good things about "Recover My Files." I'm usually a cheapskate, but by this point I'm willing to pay anything for the chance of recovering those home videos. Thanks Mark!

---

### Post by dandnsmith on 2010-12-22
I'd be tempted, especially after re-reading the thread you linked to initially, to use fdisk to mark that swap partition as NTFS, and then see whether anything is visible.

By making the partition type change (fdisk has help) as the only change you can see if if becomes visible, and then consider your options (one of which could be to reverse that change). If it does, you might try a file recovery operation. I've heard good things about testdisk and you can make a CD with it on, but, if you want a Windows oriented tool **recuva** is well thought of.

My reading of its web site is that it's primarily for recovering deleted files, so I don't know how it would do if it presented with an empty-seeming filesystem - but you might be able to just have a look at things without committing to doing the recovery.

Good luck

---

### Post by argedion on 2010-12-22
I do hope others will read an learn from the mistake you have made and I'm sure have now learned from. Here is a small tutorial on setting up a dual boot that I have written. I have no place on the web to post it so I'll place it here for you. 

```
Steps to doing a dual boot configuration

Doing a dual boot configuration is something that Linux users will do. This allows them the opportunity to be able to get the best out of both systems. Most people keep their MS Windows for Gaming and other Programs that they have paid to use. There are several steps that one should take before delving off into the world of 2 or more OS‘s. This tutorial is assuming you are wanting to dual boot Windows and Linux. 

IMPORTANT: You need to understand how to Partition hard drives. You should never just Partition a drive with out understanding all the consequences involved. Partitioning a drive can completely destroy all data. Please take the time to read the Manufactures installation instructions before attempting this procedure.

1. Burn a Live image of the OS you think you want to dual boot with and makes sure that you have all your hardware hooked up to your computer and everything is on. Boot the live image and check your hardware and make sure there are no issues. If there is then check out the forums and make sure that the solution is something that 1. You can do and 2. Actually works for you. 

IMPORTANT: When going into a forum with a problem/question about your hardware or anything else be as specific as possible (Example: Instead of saying hey Linux doesn’t pick up my printer! Try: Linux is not picking up my HP Officejet 5610v.) The later will get you more specific help that will actually be help.

2. After you have checked out your complete system on the Linux distribution you wish to install then you want to run check disk. 

If you run from the command line do this:
 
chkdsk (drive) /f /r 



this will check the drive and automatically fix errors and it will check for bad spots on the disk. Do this for all drives involved in the procedure.

If you run the GUI then check both boxes and click Start. If Windows throws up a dialog box asking you if you would like to schedule then check yes and immediately reboot the machine and allow check disk to run

No need to try to install on a bad disk.

3. Run a disk cleanup program of some kind even if it’s the one that comes with Windows. Do this for all the disk involved in the dual boot scenario. No need to have a bunch of worthless files using up valuable disk space. 

4. Defrag your hard drive /drives. This will help speed up the process a bit and will ensure that all your files are together. 

5. Clone or at least Backup the Drive in which you wish to use as the dual boot drive / boot loader drive.

If you are using 2 different drives one for windows and one for your other OS then Clone both. If there is a problem its always easier to go back with an image and start over. 

6. Figure out the layout of your partitions before starting.

If your installing Linux as a dual boot with Windows you need to set up at a minimal 3 different mount points. These are {/swap} {/} and {/home} Some even recommend {/boot} so lets look at these (Note: Some Distro’s may do this without user intervention that’s why its important to read the installation of the distro)

{/swap} this is the area of the disk that Linux will use as virtual memory this area should be as big as the memory you have installed on your computer. I do recommend nothing less than a 2gig swap area.

{/} this is the root point. All the system files will go here

{/home} this is your personal files and folders

{/boot} this is recommended if you are using an encrypted file system. 

7. After the layout is configured then its time to put it into action and start installing your system. Remember your check list. Make sure you have read the installation procedure developed by the Manufacturer and Make sure you have an understanding of the boot loader and how it works. Having a dual boot configuration can be extremely useful when you wish to use more than on OS. There are other things you need to consider before make the plunge into a dual boot system or a multiboot system. Some of these include but are not limited to, How much space to give the files system and will the home folder need to be accessible in both Windows and Linux or just Linux? The big thing about Linux is that it is a community willing to help. NEVER BE AFRAID TO ASK


```

---

### Post by Phanes on 2010-12-22
The alternative is to remove the hard disk from your machine and connect it as a secondary drive to another working machine either ubuntu or windows. If the ntfs partitions and data exist they will be browsable from this location. if not then recovery is the only option. i would also say that i have used pc inspector freeware to recover files avi and jpegs from an overwritten sd card and that was successful, but i understand your dilemma with the thought of losing valuable stuff.

---

### Post by amsterdamharu on 2010-12-22
If you haven't formatted or written anything to the swap partition yet there is a good chance of recovery.

If you boot from the live CD and open a terminal (press alt + F2 and type gnome-terminal) then copy and paste the following command in the terminal:
```
sudo apt-get testdisk
```Now testdisk does not run in a gui so we have to shutdown gnome, to do that you can:
log out -> press control + alt + F1 -> log into the terminal (text only) -> type the following commands (you need to write these down as you can't copy and paste it).
Remember; the commands are case sensitive.

```
sudo service gdm stop
sudo testdisk
```Testdisk can check sda and recover a previous partition table, although I never used it I hear great things about it.

---

