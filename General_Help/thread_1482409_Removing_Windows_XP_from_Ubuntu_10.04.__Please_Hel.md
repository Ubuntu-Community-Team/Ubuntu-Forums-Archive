---
title: "Removing Windows XP from Ubuntu 10.04.  Please Help!"
date: 2010-05-13
forum: General Help
---

### Post by lulabelf on 2010-05-13
[IMG]http://ubuntuforums.org/images/icons/icon6.gif[/IMG]                 **Removing Windows XP from Ubuntu 10.04.  Please Help!**             
                                                                How do I remove  Windows XP for good?    If I do it through GParted  (which I have  downloaded, but  am not clear on what the ***Step-by-Step***   actions are)  will I screw up Ubuntu 10.04???      I need someone in the   community who has the patience of **JOB** who can give me  clear   directions -without any assumptions that I know what I'm doing.    Pretend you're instructing a Martian from another planet.  Please!  I'm  so tired  of trying to recover my XP.   

Last month I installed Ubuntu 9.10 Karmic Koala within my Windows XP  Pro.  My mistake:  not researching Ubuntu first!   The installation disc  **did not** offer me a choice as to which OS to boot.  Therefore,*  it was not a Wubi* installation and it's been hell ever sense! 

Each time I've asked for help, a few wonderful community members have  responded.  However, each bit of information and direction was  inadvertently missing key steps to complete the process.  I think it's  just too hard for seasoned folks to remember  back when they first  started  from 'scratch' and needed **step by step **guidance.  Like  for instance, it took days before I realized   that when you plug in  your password in terminal, it stays invisible!  No joke!  I thought  something was really wrong.  It's such a small, yet vital piece of  information to not be aware of!

Next, I  tried codes suggested and downloaded files that have been  recommended to fix my missing MBR for XP.  Now the terminal says that  the XP file can't be found.     I've got software sitting in  my  download file waiting - because I don't have the proper next step to get  Ubuntu to recognize and activate files such as  ms-sys 2.1.5 and so  forth.  My MBR is missing or corrupt! * Booting from an XP cd or  download is not an option!*   I've marked earlier threads as resolved  - because I  gave up.       It still  burns me that I can see my XP  files and everything else associated with them - but I  just can't talk  to Ubuntu.   I've even gone on line to YouTube and found a wonderful  tutorial, with details; but it will take me a while to get through it.   Still, it's not going to answer my issue because everything assumes Wubi  was the installation process.

In all of this, I happen to love Ubuntu.  Still!!!    I only wanted to  access XP to be able to view Netflix!!!    I'm beat down and am giving  up on that.   Now I just want to clear out XP unless someone can truly  offer a miracle diagnosis!    Thanks

---

### Post by mike555 on 2010-05-13
if XP is still bootable , you might try booting it with a live cd bootmanager like ;    [http://www.plop.at/en/bootmanager.html](http://www.plop.at/en/bootmanager.html)

 or Grub live cd ;     [http://en.kioskea.net/faq/2677-super-grub-disk-live-cd](http://en.kioskea.net/faq/2677-super-grub-disk-live-cd)

---

### Post by lulabelf on 2010-05-13
> **mike555 said:**
> if XP is still bootable , you might try booting it with a live cd bootmanager like ;    [http://www.plop.at/en/bootmanager.html](http://www.plop.at/en/bootmanager.html)

 or Grub live cd ;     [http://en.kioskea.net/faq/2677-super-grub-disk-live-cd](http://en.kioskea.net/faq/2677-super-grub-disk-live-cd)

Hi!  Thanks for input.  Unfortunately, I'm not sure XP is still bootable.  I wouldn't know how to tell.   I went to the sites you suggested.  The problem is, and always has been -* I don't know the steps to take after downloading the file *- particularly the last one.  When I open up the site's download page, it asks me to choose the latest download.  I have no way of knowing that info!     Also, I can always download, but how would I open it?   If it's done through Terminal, I would need step by step (or detailed command by command) to act on it.

This is the circle I've been turning in for a month.  I'm appreciative of the suggestions...just need the info to act on it.

Thanks

---

### Post by sir_nasty on 2010-05-13
Here - give this a shot....

open a terminal, press enter after typing each line.


Edit the Grub File
```

sudo gedit /etc/default/grub

```
put a # in front of the line that reads:
GRUB_HIDDEN_TIMEOUT=0
so that it looks like
#GRUB_HIDDEN_TIMEOUT=0

Now change (xx just stands for whatever is there):
GRUB_TIMEOUT=xx
to
GRUB_TIMEOUT=10

save that file and close it
then run
```

sudo update-grub

```

reboot the computer, it should display the boot loader, it may have a windows xp boot option now, press the arrow key down to highlight it, then press enter

report back.

---

### Post by mike555 on 2010-05-13
You say you installed Ubuntu within Xp , but not wubi ???

 You must have used wubi .... that is how you install Ubuntu within XP ... 
  unless you downloaded the Ubuntu .iso file, burned it as an image to a cd, restarted the computer to the cd , then installed Ubuntu ... if you did it this way it's not within XP ...
    we need to know exactly what you did in order to help you ... 
  when you startup do you see the grub bootloader or the windows loader?

 also in gparted do you see two partitions , one of which is ntfs file format ??

 also what do you mean you can't talk to Ubuntu??   what operating system are you using now??

---

### Post by oldfred on 2010-05-13
In at least two other threads I or wilee-nilee have asked you to post this so we can see your entire configuration and make suggestions.


Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by sandyd on 2010-05-13
> **lulabelf said:**
> [IMG]http://ubuntuforums.org/images/icons/icon6.gif[/IMG]                 **Removing Windows XP from Ubuntu 10.04.  Please Help!**             
                                                                How do I remove  Windows XP for good?    If I do it through GParted  (which I have  downloaded, but  am not clear on what the ***Step-by-Step***   actions are)  will I screw up Ubuntu 10.04???      I need someone in the   community who has the patience of **JOB** who can give me  clear   directions -without any assumptions that I know what I'm doing.    Pretend you're instructing a Martian from another planet.  Please!  I'm  so tired  of trying to recover my XP.   

Last month I installed Ubuntu 9.10 Karmic Koala within my Windows XP  Pro.  My mistake:  not researching Ubuntu first!   The installation disc  **did not** offer me a choice as to which OS to boot.  Therefore,*  it was not a Wubi* installation and it's been hell ever sense! 

Each time I've asked for help, a few wonderful community members have  responded.  However, each bit of information and direction was  inadvertently missing key steps to complete the process.  I think it's  just too hard for seasoned folks to remember  back when they first  started  from 'scratch' and needed **step by step **guidance.  Like  for instance, it took days before I realized   that when you plug in  your password in terminal, it stays invisible!  No joke!  I thought  something was really wrong.  It's such a small, yet vital piece of  information to not be aware of!

Next, I  tried codes suggested and downloaded files that have been  recommended to fix my missing MBR for XP.  Now the terminal says that  the XP file can't be found.     I've got software sitting in  my  download file waiting - because I don't have the proper next step to get  Ubuntu to recognize and activate files such as  ms-sys 2.1.5 and so  forth.  My MBR is missing or corrupt! * Booting from an XP cd or  download is not an option!*   I've marked earlier threads as resolved  - because I  gave up.       It still  burns me that I can see my XP  files and everything else associated with them - but I  just can't talk  to Ubuntu.   I've even gone on line to YouTube and found a wonderful  tutorial, with details; but it will take me a while to get through it.   Still, it's not going to answer my issue because everything assumes Wubi  was the installation process.

In all of this, I happen to love Ubuntu.  Still!!!    I only wanted to  access XP to be able to view Netflix!!!    I'm beat down and am giving  up on that.   Now I just want to clear out XP unless someone can truly  offer a miracle diagnosis!    Thanksi guess in this case, the best thing to do is to reinstall grub2.

Please post the output of the boot info script (see above post), and we will take it from there.

---

### Post by almufadado on 2010-05-13
[SIZE=2][B]1 backup your files
[/B][/SIZE]
Open nautilus or go to PLACES and see the partitions you have :
by what you have told us you must have 2 partitions :
one with ubuntu (ext2 or ext3)
one with windows (ntfs)

if you want to copy your files in the win partition and you have space in  the ubuntu partition to store them :
this are the standard data folders 
\documents and settings\<your user name>\my documents
  \documents and settings\<your user name>\desktop
 
if you have some special programs there can also be data in
\documents and settings\<your user name>\applications data
 
search the drive for other files you might want to keep (search for doc txt jpg avi mpg files)

so move all your personnal files to the /home/<user>  directory in the ubuntu partition

[SIZE=2]2 delete or slide the partition  [/SIZE]

First you must download the live cd from here [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Burn it into a cdrom.
Keep the cd in the drive and restart your computer.
When the bios screen appears press F8 (for amibios ) to choose the boot options.

if a screen appears with the hard drives and cd drives select the one with the cd you just burned.
if not reset again and enter the Bios . so the the boot option and put the cdrom  drive  first.

After a successful boot now Inside the live ubuntu

Analise the space you have with
system -> administration -> gparted

in this graphical tool you can graphically test your configuration and then apply the changes ONLY WHEN ABSOLUTELY SURE !

you can either :
slide the windows partition to one side to the minimum space +4096 mb 
delete the partition 

Then create a new ext3 or ext4 (this keeps tracks of file usage) and  use the new partion to set a /home directory were you files will be  store separated from the system

---

### Post by lulabelf on 2010-05-14
> **oldfred said:**
> In at least two other threads I or wilee-nilee have asked you to post this so we can see your entire configuration and make suggestions.


Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.


Sorry that I couldn't follow through.  I went to boot info script and downloaded it.  The first thing it asks for is what I want to open the file with.   ????  I have no idea what to choose!   I've been trying to follow everybody's suggestions and keep running into situations like this.  Even directions assume I know what I'm doing.    I cannot make it any clearer that I don't.

---

### Post by oldfred on 2010-05-14
If you go back to the link I provided it has better instructions than I can give here. You just have to know whether you downloaded to the desktop or to download directory and follow the steps listed. 

It will create a file resutls.txt. Be sure to post results.txt back in code tags which you automatically add as paste (while still highlighted) by clicking on the # sign on the right side of the edit panel above where you are pasting.

---

### Post by lulabelf on 2010-05-14
> **oldfred said:**
> If you go back to the link I provided it has better instructions than I can give here. You just have to know whether you downloaded to the desktop or to download directory and follow the steps listed. 

It will create a file resutls.txt. Be sure to post results.txt back in code tags which you automatically add as paste (while still highlighted) by clicking on the # sign on the right side of the edit panel above where you are pasting.



Hello.  Thanks for hanging in there with me.       	 	 	 	 	 	  I downloaded boot info script.  Put in on my desktop and right-clicked to open the file.  I chose gedit and  it displayed the file information.  Next I went to terminal and put in the suggested code:  
  sudo bash boot_info_script055.sh    
 

 

 This is what I got:
 

 lydia@Puter:~$ sudo bash boot_info_script055.sh 
 [sudo] password for lydia:  
 bash: boot_info_script055.sh: No such file or directory
 

 

 I'm still missing some step.    Not sure what to do next.

---

### Post by lulabelf on 2010-05-14
> **sir_nasty said:**
> Here - give this a shot....

open a terminal, press enter after typing each line.


Edit the Grub File
```

sudo gedit /etc/default/grub

```put a # in front of the line that reads:
GRUB_HIDDEN_TIMEOUT=0
so that it looks like
#GRUB_HIDDEN_TIMEOUT=0

Now change (xx just stands for whatever is there):
GRUB_TIMEOUT=xx
to
GRUB_TIMEOUT=10

save that file and close it
then run
```

sudo update-grub

```reboot the computer, it should display the boot loader, it may have a windows xp boot option now, press the arrow key down to highlight it, then press enter

report back.

Hi.  Thanks for your input.
  	 	 	 	 	 	  **Here is my screen before I followed your instructions:**
 

  # If you change this file, run 'update-grub' afterwards to update  
 # /boot/grub/grub.cfg.  
 

 GRUB_DEFAULT= "Microsoft Windows XP Professional"  
 GRUB_HIDDEN_TIMEOUT=5  
 GRUB_HIDDEN_TIMEOUT_QUIET=true  
 GRUB_TIMEOUT=10  
 GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`  
 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"  
 GRUB_CMDLINE_LINUX=""  
 

 # Uncomment to disable graphical terminal (grub-pc only)  
 #GRUB_TERMINAL=console  
 

 # The resolution used on graphical terminal  
 # note that you can use only modes which your graphic card supports via VBE  
 # you can see them in real GRUB with the command `vbeinfo'  
 #GRUB_GFXMODE=640x480  
 

 # Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux  
 #GRUB_DISABLE_LINUX_UUID=true  
 

 # Uncomment to disable generation of recovery mode menu entrys  
 #GRUB_DISABLE_LINUX_RECOVERY="true"
 

 

 **Here's the screen with my adding the changes you suggested:**  
 

 # If you change this file, run 'update-grub' afterwards to update  
 # /boot/grub/grub.cfg.  
 

 GRUB_DEFAULT= "Microsoft Windows XP Professional"  
 # GRUB_HIDDEN_TIMEOUT=0  
 GRUB_HIDDEN_TIMEOUT_QUIET=true  
 GRUB_TIMEOUT=10  
 GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`  
 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"  
 GRUB_CMDLINE_LINUX=""  
 

 # Uncomment to disable graphical terminal (grub-pc only)  
 #GRUB_TERMINAL=console  
 

 # The resolution used on graphical terminal  
 # note that you can use only modes which your graphic card supports via VBE  
 # you can see them in real GRUB with the command `vbeinfo'  
 #GRUB_GFXMODE=640x480  
   
 # Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux  
 #GRUB_DISABLE_LINUX_UUID=true  
 

 # Uncomment to disable generation of recovery mode menu entrys  
 #GRUB_DISABLE_LINUX_RECOVERY="true"
 

 

 **Here's the end result screen after doing sudo update grub:**
 

 

 me@Puter:~$ sudo gedit /etc/default/grub  
 me@Puter:~$ sudo update-grub  
 /etc/default/grub: 4: Microsoft Windows XP Professional: not found  
 me@Puter:~$  
 

 

 Not sure what's up nor where to go.

---

### Post by lulabelf on 2010-05-14
> **almufadado said:**
> [SIZE=2][B]1 backup your files
[/B][/SIZE]
Open nautilus or go to PLACES and see the partitions you have :
by what you have told us you must have 2 partitions :
one with ubuntu (ext2 or ext3)
one with windows (ntfs)

if you want to copy your files in the win partition and you have space in  the ubuntu partition to store them :
this are the standard data folders 
\documents and settings\<your user name>\my documents
  \documents and settings\<your user name>\desktop
 
if you have some special programs there can also be data in
\documents and settings\<your user name>\applications data
 
search the drive for other files you might want to keep (search for doc txt jpg avi mpg files)

so move all your personnal files to the /home/<user>  directory in the ubuntu partition

[SIZE=2]2 delete or slide the partition  [/SIZE]

First you must download the live cd from here [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Burn it into a cdrom.
Keep the cd in the drive and restart your computer.
When the bios screen appears press F8 (for amibios ) to choose the boot options.

if a screen appears with the hard drives and cd drives select the one with the cd you just burned.
if not reset again and enter the Bios . so the the boot option and put the cdrom  drive  first.

After a successful boot now Inside the live ubuntu

Analise the space you have with
system -> administration -> gparted

in this graphical tool you can graphically test your configuration and then apply the changes ONLY WHEN ABSOLUTELY SURE !

you can either :
slide the windows partition to one side to the minimum space +4096 mb 
delete the partition 

Then create a new ext3 or ext4 (this keeps tracks of file usage) and  use the new partion to set a /home directory were you files will be  store separated from the system


Thanks for input.  I will try this approach and report back.

---

### Post by lulabelf on 2010-05-14
> **mike555 said:**
> You say you installed Ubuntu within Xp , but not wubi ???

 You must have used wubi .... that is how you install Ubuntu within XP ... 
  unless you downloaded the Ubuntu .iso file, burned it as an image to a cd, restarted the computer to the cd , then installed Ubuntu ... if you did it this way it's not within XP ...
    we need to know exactly what you did in order to help you ... 


  when you startup do you see the grub bootloader or the windows loader?

 also in gparted do you see two partitions , one of which is ntfs file format ??

 also what do you mean you can't talk to Ubuntu??   what operating system are you using now??

I'm using Ubuntu lingo incorrectly.  Yes I must have install with  Wubi.   Let me start over:  I bought a Linus Starter Kit for 9.10 Karmic Koala w/cd & installed  it on my Windows XP.  

In the process, I must have inadvertently  instructed Ubuntu 9.10 (Karmic K) to be the main OS.   I do remember a  screen asking if I wanted Ubuntu in a different partition so that I  could keep windows.  I do not remember what I chose after that.  However, when I re-booted my computer after the installation, _it went  right to Ubuntu_.   No boot-up screen ever appeared offering me the  choice of booting to Ubuntu or Windows.  (Updated to Ubuntu 10.04)

  Yes, gparted shows that I have both XP (ntfs) and Ubuntu partitions.   
    
 When I wrote I can't 'talk to Ubuntu', I was jokingly referring to the fact that I can't find the right code or process within Ubuntu to find my way back to XP.

---

### Post by j0eb0b on 2010-05-14
I have been down this path before with dual boot  Ubuntu (8.10) and XP.  The work around for me was to burn a copy of Super Grub to CD, Set the bios in my machine to boot from CD and then use Super Grub to select either the XP or Ubuntu bootloader to execute.  This was a workaround because I was never able to get either Unbuntu or XP to recognize the existence of the other OS and had to boot from CD each time. Looking at my hard drive with Partition Magic, my disk had corruption that could not be resolved.  My final fix was to rebuild the machine from scratch.  

If XP is still viable, this should give you the capability of getting it to boot.

Do you ultimately want to dual boot XP and Unbuntu or are you looking to have an Ubuntu only desktop?

---

### Post by oldfred on 2010-05-14
If it is in your desktop you can either change to that directory  with a cd /desktop and run the command as you did or as the instructions say include the path in the command:

 sudo bash [path/to/the/download_folder]/boot_info_script*.sh 
 For example if you downloaded the file to the desktop, use          
sudo bash ~/Desktop/boot_info_script*.sh 

the tilde (~) just means /home/lydia as a shortcut to typing the full path.
You also can use tab after typing a few letters and it will fill in the rest as far as it is unique. with tab it may be
sudo bash ~/desktop/boo - tab then may find ..tinfo.script55.sh and it will work.

---

### Post by sandyd on 2010-05-14
1. Boot Info script
```

wget -c http://cdnetworks-us-2.dl.sourceforge.net/project/bootinfoscript/bootinfoscript/0.55/boot_info_script055.sh
chmod 667 boot_info_script055.sh
sudo bash ./boot_info_script055.sh

```

2. 
```

sudo update-grub
cat /boot/grub/device.map

```

3. 
Try holding down the shift key while booting.

---

### Post by mike555 on 2010-05-14
You should be able to see XP partition in Nautilus , if you click on it it should mount so you can read and write it ...... 

 have you tried typing in terminal "  sudo update-grub " without the quote marks ?

---

### Post by lulabelf on 2010-05-18
> **carlee said:**
> 1. Boot Info script
```

wget -c http://cdnetworks-us-2.dl.sourceforge.net/project/bootinfoscript/bootinfoscript/0.55/boot_info_script055.sh
chmod 667 boot_info_script055.sh
sudo bash ./boot_info_script055.sh

```2. 
```

sudo update-grub
cat /boot/grub/device.map

```3. 
Try holding down the shift key while booting.


Hi, tried your suggestion.  Here's what I got:

  	 	 	 	 	 	  me@Puter:~$ wget -c [http://cdnetworks-us-2.dl.sourceforge.net/project/bootinfoscript/bootinfoscript/0.55/boot_info_script055.sh](http://cdnetworks-us-2.dl.sourceforge.net/project/bootinfoscript/bootinfoscript/0.55/boot_info_script055.sh) 
 --2010-05-18 10:12:50--  [http://cdnetworks-us-2.dl.sourceforge.net/project/bootinfoscript/bootinfoscript/0.55/boot_info_script055.sh](http://cdnetworks-us-2.dl.sourceforge.net/project/bootinfoscript/bootinfoscript/0.55/boot_info_script055.sh) 
 Resolving cdnetworks-us-2.dl.sourceforge.net... 174.35.19.12 
 Connecting to cdnetworks-us-2.dl.sourceforge.net|174.35.19.12|:80... connected. 
 HTTP request sent, awaiting response... 200 OK 
 Length: 70588 (69K) [application/x-sh] 
 Saving to: `boot_info_script055.sh' 
  
 100%[======================================>] 70,588      85.9K/s   in 0.8s     
  
 2010-05-18 10:12:51 (85.9 KB/s) - `boot_info_script055.sh' saved [70588/70588] 
  
 me@Puter:~$ chmod 667 boot_info_script055.sh 
 me@Puter:~$  
 


 me@Puter:~$ chmod 667 boot_info_script055.sh 
 me@Puter:~$ sudo update-grub 
 [sudo] password for me:  
 Sorry, try again. 
 [sudo] password for me:  
 /etc/default/grub: 4: Microsoft Windows XP Professional: not found 





I tried accessing my xp files by mounting them (via another forum).  I'm still locked out of files.  This seems to explain that some error occurred during my original installation - I think:


   	 	 	 	 	 	  
me@Puter:~$ sudo fdisk -l 
  
 Disk /dev/sda: 160.0 GB, 160041885696 bytes 
 255 heads, 63 sectors/track, 19457 cylinders 
 Units = cylinders of 16065 * 512 = 8225280 bytes 
 Sector size (logical/physical): 512 bytes / 512 bytes 
 I/O size (minimum/optimal): 512 bytes / 512 bytes 
 Disk identifier: 0x28ee28ed 
  
    Device Boot      Start         End      Blocks   Id  System 
 /dev/sda1   *           1       11040    88678768+   7  HPFS/NTFS 
 /dev/sda2           11041       19457    67609552+   5  Extended 
 /dev/sda5           11041       19272    66123508+  83  Linux 
 /dev/sda6           19273       19457     1485981   82  Linux swap / Solaris 
 me@Puter:~$ sudo cp /etc/fstab /etc/fstab.bak 
 me@Puter:~$ sudo cp /etc/fstab /etc/fstab.bak 
 me@Puter:~$ cat /etc/fstab 
 # /etc/fstab: static file system information. 
 # 
 # Use 'blkid -o value -s UUID' to print the universally unique identifier 
 # for a device; this may be used with UUID= as a more robust way to name 
 # devices that works even if disks are added and removed. See fstab(5). 
 # 
 # <file system> <mount point>   <type>  <options>       <dump>  <pass> 
 proc            /proc           proc    defaults        0       0 
 # / was on /dev/sda5 during installation 
 UUID=20529aa6-93fe-4b95-8ce6-04821524e745 /               ext4    errors=remount-ro 0       1 
 # swap was on /dev/sda6 during installation 
 UUID=ec12b266-72cf-469b-b8e7-727615c6a640 none            swap    sw              0       0 
 /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0 
 /dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0 
 me@Puter:~$ sudo mkdir /media/windows 
 me@Puter:~$ /dev/sda1 /media/sda1 ntfs-3g defaults,nls=utf8,umask=007,gid=46 0 1 
 bash: /dev/sda1: Permission denied 
 
 
I'm at a loss.  This is leading me back to my original question:  How do I delete windows completely using Gparted?   I prefer Ubuntu; I just hate not being able to switch back and forth since the files do exist.

---

### Post by lulabelf on 2010-05-18
> **mike555 said:**
> You should be able to see XP partition in Nautilus , if you click on it it should mount so you can read and write it ...... 

 have you tried typing in terminal "  sudo update-grub " without the quote marks ?



 Hi.  Yes, I have.  I followed advice on accessing the boot script.  Here's what I got:

  	 	 	 	 	 	  me@Puter:~$ wget -c [http://cdnetworks-us-2.dl.sourceforge.net/project/bootinfoscript/bootinfoscript/0.55/boot_info_script055.sh](http://cdnetworks-us-2.dl.sourceforge.net/project/bootinfoscript/bootinfoscript/0.55/boot_info_script055.sh) 
 --2010-05-18 10:12:50--  [http://cdnetworks-us-2.dl.sourceforge.net/project/bootinfoscript/bootinfoscript/0.55/boot_info_script055.sh](http://cdnetworks-us-2.dl.sourceforge.net/project/bootinfoscript/bootinfoscript/0.55/boot_info_script055.sh) 
 Resolving cdnetworks-us-2.dl.sourceforge.net... 174.35.19.12 
 Connecting to cdnetworks-us-2.dl.sourceforge.net|174.35.19.12|:80... connected. 
 HTTP request sent, awaiting response... 200 OK 
 Length: 70588 (69K) [application/x-sh] 
 Saving to: `boot_info_script055.sh' 
  
 100%[======================================>] 70,588      85.9K/s   in 0.8s     
  
 2010-05-18 10:12:51 (85.9 KB/s) - `boot_info_script055.sh' saved [70588/70588] 
  
 me@Puter:~$ chmod 667 boot_info_script055.sh 
 me@Puter:~$  
 

 me@Puter:~$ chmod 667 boot_info_script055.sh 
 me@Puter:~$ sudo update-grub 
 [sudo] password for me:  
 Sorry, try again. 
 [sudo] password for me:  
 /etc/default/grub: 4: Microsoft Windows XP Professional: not found 



I also tried mounting xp files (from notes on another forum.  It seems to be pointing out that there was an error during initial installation (not sure on this).  Here are results:


   	 	 	 	 	 	  me@Puter:~$ sudo fdisk -l 
  
 Disk /dev/sda: 160.0 GB, 160041885696 bytes 
 255 heads, 63 sectors/track, 19457 cylinders 
 Units = cylinders of 16065 * 512 = 8225280 bytes 
 Sector size (logical/physical): 512 bytes / 512 bytes 
 I/O size (minimum/optimal): 512 bytes / 512 bytes 
 Disk identifier: 0x28ee28ed 
  
    Device Boot      Start         End      Blocks   Id  System 
 /dev/sda1   *           1       11040    88678768+   7  HPFS/NTFS 
 /dev/sda2           11041       19457    67609552+   5  Extended 
 /dev/sda5           11041       19272    66123508+  83  Linux 
 /dev/sda6           19273       19457     1485981   82  Linux swap / Solaris 
 me@Puter:~$ sudo cp /etc/fstab /etc/fstab.bak 
 me@Puter:~$ sudo cp /etc/fstab /etc/fstab.bak 
 me@Puter:~$ cat /etc/fstab 
 # /etc/fstab: static file system information. 
 # 
 # Use 'blkid -o value -s UUID' to print the universally unique identifier 
 # for a device; this may be used with UUID= as a more robust way to name 
 # devices that works even if disks are added and removed. See fstab(5). 
 # 
 # <file system> <mount point>   <type>  <options>       <dump>  <pass> 
 proc            /proc           proc    defaults        0       0 
 # / was on /dev/sda5 during installation 
 UUID=20529aa6-93fe-4b95-8ce6-04821524e745 /               ext4    errors=remount-ro 0       1 
 # swap was on /dev/sda6 during installation 
 UUID=ec12b266-72cf-469b-b8e7-727615c6a640 none            swap    sw              0       0 
 /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0 
 /dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0 
 me@Puter:~$ sudo mkdir /media/windows 
 me@Puter:~$ /dev/sda1 /media/sda1 ntfs-3g defaults,nls=utf8,umask=007,gid=46 0 1 
 bash: /dev/sda1: Permission denied.




This brings me back to original question - how do I eliminate xp files all together?  The plot thickens; it is a mystery since the files are clearly present.  I prefer Ubuntu and would like to move on.   Thanks for any advice at this point.

---

### Post by lulabelf on 2010-05-18
> **j0eb0b said:**
> I have been down this path before with dual boot  Ubuntu (8.10) and XP.  The work around for me was to burn a copy of Super Grub to CD, Set the bios in my machine to boot from CD and then use Super Grub to select either the XP or Ubuntu bootloader to execute.  This was a workaround because I was never able to get either Unbuntu or XP to recognize the existence of the other OS and had to boot from CD each time. Looking at my hard drive with Partition Magic, my disk had corruption that could not be resolved.  My final fix was to rebuild the machine from scratch.  

If XP is still viable, this should give you the capability of getting it to boot.

Do you ultimately want to dual boot XP and Unbuntu or are you looking to have an Ubuntu only desktop?


Hi & thanks.  I think an error occurred during initial installation.  I tried a procedure of mounting XP.   (Instructions were on another forum).   It didn't work.  Here's what I got:

  	 	 	 	 	 	  me@Puter:~$ sudo fdisk -l 
  
 Disk /dev/sda: 160.0 GB, 160041885696 bytes 
 255 heads, 63 sectors/track, 19457 cylinders 
 Units = cylinders of 16065 * 512 = 8225280 bytes 
 Sector size (logical/physical): 512 bytes / 512 bytes 
 I/O size (minimum/optimal): 512 bytes / 512 bytes 
 Disk identifier: 0x28ee28ed 
  
    Device Boot      Start         End      Blocks   Id  System 
 /dev/sda1   *           1       11040    88678768+   7  HPFS/NTFS 
 /dev/sda2           11041       19457    67609552+   5  Extended 
 /dev/sda5           11041       19272    66123508+  83  Linux 
 /dev/sda6           19273       19457     1485981   82  Linux swap / Solaris 
 me@Puter:~$ sudo cp /etc/fstab /etc/fstab.bak 
 me@Puter:~$ sudo cp /etc/fstab /etc/fstab.bak 
 me@Puter:~$ cat /etc/fstab 
 # /etc/fstab: static file system information. 
 # 
 # Use 'blkid -o value -s UUID' to print the universally unique identifier 
 # for a device; this may be used with UUID= as a more robust way to name 
 # devices that works even if disks are added and removed. See fstab(5). 
 # 
 # <file system> <mount point>   <type>  <options>       <dump>  <pass> 
 proc            /proc           proc    defaults        0       0 
 # / was on /dev/sda5 during installation 
 UUID=20529aa6-93fe-4b95-8ce6-04821524e745 /               ext4    errors=remount-ro 0       1 
 # swap was on /dev/sda6 during installation 
 UUID=ec12b266-72cf-469b-b8e7-727615c6a640 none            swap    sw              0       0 
 /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0 
 /dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0 
 me@Puter:~$ sudo mkdir /media/windows 
 me@Puter:~$ /dev/sda1 /media/sda1 ntfs-3g defaults,nls=utf8,umask=007,gid=46 0 1 
 bash: /dev/sda1: Permission denied




At this point, I want to get rid of XP and keep Ubuntu.  The mysterious xp and present but not accessible have driven me nuts - but ultimately, I want to keep Ubuntu.   Just wanted the safest way to dump xp without affecting Ubuntu.    Any advice at this point would be welcomed.

---

### Post by lulabelf on 2010-05-18
> **j0eb0b said:**
> I have been down this path before with dual boot  Ubuntu (8.10) and XP.  The work around for me was to burn a copy of Super Grub to CD, Set the bios in my machine to boot from CD and then use Super Grub to select either the XP or Ubuntu bootloader to execute.  This was a workaround because I was never able to get either Unbuntu or XP to recognize the existence of the other OS and had to boot from CD each time. Looking at my hard drive with Partition Magic, my disk had corruption that could not be resolved.  My final fix was to rebuild the machine from scratch.  

If XP is still viable, this should give you the capability of getting it to boot.

Do you ultimately want to dual boot XP and Unbuntu or are you looking to have an Ubuntu only desktop?


Hi & thanks.  I think an error occurred during initial installation.  I tried a procedure of mounting XP.   (Instructions were on another forum).   It didn't work.  Here's what I got:

  	 	 	 	 	 	  me@Puter:~$ sudo fdisk -l 
  
 Disk /dev/sda: 160.0 GB, 160041885696 bytes 
 255 heads, 63 sectors/track, 19457 cylinders 
 Units = cylinders of 16065 * 512 = 8225280 bytes 
 Sector size (logical/physical): 512 bytes / 512 bytes 
 I/O size (minimum/optimal): 512 bytes / 512 bytes 
 Disk identifier: 0x28ee28ed 
  
    Device Boot      Start         End      Blocks   Id  System 
 /dev/sda1   *           1       11040    88678768+   7  HPFS/NTFS 
 /dev/sda2           11041       19457    67609552+   5  Extended 
 /dev/sda5           11041       19272    66123508+  83  Linux 
 /dev/sda6           19273       19457     1485981   82  Linux swap / Solaris 
 me@Puter:~$ sudo cp /etc/fstab /etc/fstab.bak 
 me@Puter:~$ sudo cp /etc/fstab /etc/fstab.bak 
 me@Puter:~$ cat /etc/fstab 
 # /etc/fstab: static file system information. 
 # 
 # Use 'blkid -o value -s UUID' to print the universally unique identifier 
 # for a device; this may be used with UUID= as a more robust way to name 
 # devices that works even if disks are added and removed. See fstab(5). 
 # 
 # <file system> <mount point>   <type>  <options>       <dump>  <pass> 
 proc            /proc           proc    defaults        0       0 
 # / was on /dev/sda5 during installation 
 UUID=20529aa6-93fe-4b95-8ce6-04821524e745 /               ext4    errors=remount-ro 0       1 
 # swap was on /dev/sda6 during installation 
 UUID=ec12b266-72cf-469b-b8e7-727615c6a640 none            swap    sw              0       0 
 /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0 
 /dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0 
 me@Puter:~$ sudo mkdir /media/windows 
 me@Puter:~$ /dev/sda1 /media/sda1 ntfs-3g defaults,nls=utf8,umask=007,gid=46 0 1 
 bash: /dev/sda1: Permission denied




At this point, I want to get rid of XP and keep Ubuntu.  The mysterious present but not accessible XP files have driven me nuts!   Just want the safest way to dump xp without affecting Ubuntu.    Any advice at this point would be welcomed.

---

### Post by oldfred on 2010-05-18
This line is intended to be copied and pasted into fstab. But the directory you make has to be the same as the one your mount.
 sudo mkdir [COLOR=DarkRed]/media/windows[/COLOR] 
then the /media/sda1 should be /media/windows

dev/sda1 /media/sda1 ntfs-3g defaults,nls=utf8,umask=007,gid=46 0 1 


dev/sda1[COLOR=DarkRed] /media/windows[/COLOR] ntfs-3g defaults,nls=utf8,umask=007,gid=46 0 1 



So if you 
You then run

```
mount -a
```to reload fstab and if it has errors it will list them, it it just come back then it is ok and will have mounted your new entry.

To edit fstab:
```

gksudo gedit /etc/fstab
```It is often better for new users to copy and paste into the terminal to avoid typos.

I am not sure how this helps you, if the goal is to delete windows? You can use gparted to reformat the entire partition and use it in linux.

---

