---
title: "64 bit vs 32 bit Ubuntu"
date: 2011-08-12
forum: General Help
---

### Post by Wheel on 2011-08-12
Hi,

I'm a fairly lightweight home desktop user; I don't do anything which requires huge system resources.
I currently dual boot Win Vista with Ubuntu Natty.  32 bit.
Next week my new machine arrives with Win 7 pre-installed.  It's a Dell XPS 8300--64 bit.
Can I continue to use Natty 32 bit version?  Will it work on a 64 bit system?
Or should I just download & burn the 64 bit version of Natty and install that alongside Win 7?

And--if I _HAVE TO_ use the 64 bit version of Natty, is it even worth my while backing up my 32 bit home folder before the move to 64?  
Will a 32 bit backup (Deja Dup) restore into a 64 bit version?
Or will I have to spend some time customizing the new 64 bit Natty install from "scratch"?

---

### Post by NightwishFan on 2011-08-12
> **Wheel said:**
> Hi
Hello.

> I'm a fairly lightweight home desktop user; I don't do anything which requires huge system resources.
Either 32-bit or 64-bit would be fine for this.


> Can I continue to use Natty 32 bit version?  Will it work on a 64 bit system?
Certainly. :)

> And--if I _HAVE TO_ use the 64 bit version of Natty, is it even worth my while backing up my 32 bit home folder before the move to 64?
The home folder should be compatible between bits.

> Will a 32 bit backup (Deja Dup) restore into a 64 bit version?
Or will I have to spend some time customizing the new 64 bit Natty install from "scratch"?

Any 'software' will need to be re-downloaded. Configuration and files will work fine. So system backups wont work but data backups will. As for deja-dup specifically no clue, I manually back up with .tar files.

As for 64-bit it is no worse off than 32-bit. Either is fine for someone who doesn't care but I should say the world is moving away from 32-bit.

---

### Post by Kira_Belka on 2011-08-12
mmmmm.. I think you can use your i386 (32bit system) as well on new pc .. so you can clone your disk and use on new pc.. then you won't need to reinstall software and configure.
about x64 system.. I 'll prefer x64 to i386 just in one case if I have more than 4Gb RAM and I need to use VMs under VirtualBox that have to be x64 too :)

---

### Post by jeffreyldavidson on 2011-08-12
I have a Intel I3 but have never been able to get Ununtu 64 to install. I have downloaded the ISO several times and tried to burn a new cd but no luck. So you may want to stay with 32bit. I have install Arch 64 before so I cannot figure out what is up with Ubuntu 64. However, 32bit runs fine.

---

### Post by b2zeldafreak on 2011-08-12
> **Kira_Belka said:**
> mmmmm.. I think you can use your i386 (32bit system) as well on new pc .. so you can clone your disk and use on new pc.. then you won't need to reinstall software and configure.
about x64 system.. I 'll prefer x64 to i386 just in one case if I have more than 4Gb RAM and I need to use VMs under VirtualBox that have to be x64 too :)

As a warning, if you clone your disk it will erase the preinstalled Windows 7.

64 bit gives you 2(+1) primary benefits.

1. It allows your computer to recognize more RAM. Without a modified kernel, 32 bit can only recognize 3gb (iirc) of RAM, while 64 bit can recognize a very very much larger number (in the terabyte range iirc).

2. 64 bit means that your proeccesor can calculate twice as much on each pass/calculation. This is somewhat limited by the software you are using, and I'm no expert on the specific details, but overall it will allow your computer to run faster.

3. This is a result of #2, but it will allow you to run 64 bit applications, which are becoming more common (slowly).

As far as I know theres no major bugs with 64-bit Ubuntu, so I would recommend going ahead and upgrading to that. You might not need the extra RAM recognized as a lightweight user, but you might as well use the full power of your system, or at least have it available.

~b2zeldafreak

---

### Post by magic8ball on 2011-08-12
Hi,

I recently did some updates on my dual-boot (Ubuntu/Windows XP) laptop.  My main reason was to update from 32-bit to 64-bit Ubuntu 10.04 and also resize my partitions and format my / as ext4.  My system has a separate / and /home.

I used the commands in the following post to backup/restore installed packages:

[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

After making the requisite disk image for safety, I installed 64-bit without doing anything to /home.  Upon first boot, all my settings were there and everything looked just like it did before (i.e. 32-bit).  I ran the restore command from the link above and reinstalled a couple things manually.  The whole process was surprisingly easy and everything has been running great.

Not sure if it was reformatting / as ext4 or changing to 64-bit, but my "new" system is noticeably faster.

---

### Post by Wheel on 2011-08-13
Thanks, everyone.  Lots of good info in each of your posts.

My (tentative) game plan:
-Initial set up of Win 7.
-Burn recovery disk.
-Install 32 bit Natty. 
-Customize/configure both O.S.
-Image the hard drive.  (This will be my first time doing an image.  I'm leaning towards Clonezilla.)

After that, it's just routine maintenance and backing up.  And--oh yeah--having some fun.

When Oneiric comes down the road in a couple of months, I'll move up to 64 bit then (and possibly add more RAM--my new system has 6Gb installed with a 16Gb capacity).

@magic8ball
Great link!  I will definitely give that a shot. 
If I understand that correctly, once I've run the first code & created "my-packages" in /home, I can then back up /home, install Natty on the new machine, restore /home, then run the 2nd code to recover at least some of my installed packages.
Do I have that about right?

I don't suppose there's a way to easily save/recover enabled 3rd party Repos?  
Or am I asking for the Moon on this one?
The question about Repos is not a huge deal.  I only have 5 or 6 enabled and so would not be be too time consuming to re-enable them.

I also have a couple of questions regarding partitions, but I will open a new thread about that when I'm done with this one.

---

### Post by magic8ball on 2011-08-13
Hi Wheel,

That sounds right.  I'll give you a heads up to the only issue that I had with the restore process -- I had an MS fonts pack installed that, when restored, presented a terms and conditions confirmation screen in the terminal window and I couldn't figure out how to select OK for it to continue and install.  It ends up that you need to hit the TAB key to highlight OK and then press ENTER to select it and continue.

As far as imaging, I used Clonezilla.  I just burned the latest Clonezilla CD, booted from it, selected the first option (Live, I think) and followed the instructions.  I did a couple images during my process and everything appeared to work fine.  Fortunately everything went OK for me and I didn't have to use the image, so I can't attest to how well the restore part works, but I'm guessing that it won't be a problem.

My process was basically:
1) Created installed package list with the link I gave
2)  Imaged entire drive with Clonezilla
3)  Shrink Windows XP partition (I used GParted, but you have to do something different for Win7)
4)  Start Windows a couple times to make sure that it is working OK
5)  Resize/expand my Ubuntu partitions with GParted
6)  Start Windows and Ubuntu to make sure that they still work
7)  Imaged entire drive again with Clonezilla to capture working system with new partition structure
8- Install Ubuntu 10.04 64-bit without modifying the contents of /home
9)  Restore installed packages with the link I gave and reinstall some stuff manually

I hope everything works smooth for you.

- Chuck

---

### Post by Megaptera on 2011-08-13
You could use Remastersys to make an installable copy of your current 32 bit set-up to put on your new machine.

Quote "Remastersys is a tool that can be used to do 2 things with an existing Debian,  Ubuntu or derivative installation.

   1. It can make a full system backup including personal data to a live cd or dvd that you can use anywhere and install.
   2. It can make a distributable copy you can share with friends.  This will not have any of your personal user data in it."

[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

---

### Post by Wheel on 2011-08-14
@magic8ball--
Thanks for the Clonezilla basics and for sharing the process you followed.  Both helpful.

I have GParted installed but have only used it to look at my partitions, not to actually manipulate them.

I'm expecting to use Windows Disk Management Tool to shrink 7 after the initial set up since I have used it before with good results.  I'll only have to figure out the differences as to how this tool functions in 7 compared to Vista.

And for now, I think I'll simply do a "vanilla" Ubuntu install into the newly freed-up space without pre-setting any specific partitions.
As to my earlier comment about beginning a new thread concerning partitions--I'm going to postpone that until I'm completely set up with the new machine.  There'll be plenty of time for that later.

@Megaptera--
I followed your link and read up on Remastersys.  Looks very promising and I'll investigate this further.

This is one of the things I love about the Ubuntu community.  Someone sees a need and builds a tool to fill it.  Very cool.

---

### Post by Wheel on 2011-08-23
Just a final note on this.
I spent most of the weekend setting up my new machine.  All went well.
Restoring my Home folder via Deja Dup was also successful.  
Thanks for everyone's help.

@magic8ball--Thanks again for the link to the "my-packages" trick.  It worked like a charm.  I was amazed, watching the terminal scroll through item after item as it recovered them for me!  This was a terrific time/labor saver.

And an extra thanks for your little "heads-up".  It was MS Corefonts which required my input.  I **may** have hit the Tab key eventually--trying everything I could think of--but that tip saved me some frustration and a few aspirin.  

After a few adjustments to my Unity Launcher and adding a couple of appindicators to the top panel, I was all set to go.  Very nice.

I actually spent most of my time tweaking--and exploring--Win 7.  And killing lots of bloatware...I love using Revo to remove the myriad hooks into the registry that all this crap had laid down.

Did my Clonezilla image.  That came off without a hitch as well.

I'm marking this as solved and moving on.

---

