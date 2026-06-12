---
title: "Grub rescue : no such device"
date: 2010-08-09
forum: General Help
---

### Post by nightrail on 2010-08-09
ok, i have used linux befor on my other pc. but switched back to windows.

now the otherday i wanted linux again. so i used the wubi installer for ubuntu 10.04
evrything went well. i rebooted and started up linux. i logged into my account and started exploring. 

after a hour or so a update poped up so i installed it and rebooted. however it didnt boot up. instead it displayed the 
error: no such device blablalba 
grub rescue>

i tried rebooting again.. and no luck.. i was stuck.. i serched the web on my other pc and people sait to get a windows recovery disk. or a livecd(ubuntu) so i did.. (i went for the ubuntu live)
and it worked thank god. (aparently some people didnt have success at this stage)
i am currently writing this from the live cd now. however .. i dont know what to do from here to fix my bootloader ..

can someone please help

OS's installed
Windows Vista
Ubuntu 10.04

anymore info just ask

thankyou

---

### Post by oldfred on 2010-08-09
Are you getting the grub error on initial boot? With wubi you have to have the windows boot loader in the MBR.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

From a liveCD you can install a windows type boot loader.

Restore basic windows boot loader - universe enabled from Ubuntu or liveCD
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

---

### Post by nightrail on 2010-08-09
yep im getting the error on the initial boot.
 
ok i ran the lilo stuff it gave me a nice little notice saying i need to run something after the first sudo command
the notice was this
 
"lilo configuration
it seems to be your first lilo installation. it is absolutely necessary to run liloconfig(8) when you compleate this process and execute /sbin/lilo after this 
 
LILO wont work if you dont do this"
 
any advice on what this is and what to do ?
 
edit: i have ran both of these
udo apt-get install lilo
sudo lilo -M /dev/sda mbr
 
 
 
SOLVED :D

---

### Post by phoenix6669 on 2010-08-23
ya i'm getting the error on the initial boot also but my wubi cd won't load up and i have no vista cd...also it won't recognize any commands...sudo = unknown command...i can't boot into either of my os's

---

### Post by wilee-nilee on 2010-08-23
> **phoenix6669 said:**
> ya i'm getting the error on the initial boot also but my wubi cd won't load up and i have no vista cd...also it won't recognize any commands...sudo = unknown command...i can't boot into either of my os's

Per your PM start your own thread and post the bootscript in my signature. Personally I'm not familiar with how to reload a wubi disc image after reloading the MS bootloader. You should also contact your computer maker and get the oem or full recovery DVD with the activation key confirmed. Personally I would never rely on a burned recovery from the setup itself I want a hard copy or ISO from the manufacturer or MS.

---

### Post by Alastairloh on 2010-11-17
I have a dell studio xps loaded with windows 7 home and also ubuntu netbook edition installed. recently, or rather yesterday, i experienced this problem called:  
 
"error :unknown filesystem
grub rescue> "
 
how do i solve this problem and allow me to run my win 7, cause my important documents are all in win 7.
 
 
 
Tks

---

### Post by bcbc on 2010-11-17
> **Alastairloh said:**
> I have a dell studio xps loaded with windows 7 home and also ubuntu netbook edition installed. recently, or rather yesterday, i experienced this problem called:  
 
"error :unknown filesystem
grub rescue> "
 
how do i solve this problem and allow me to run my win 7, cause my important documents are all in win 7.
 
 
 
Tks

reinstall the windows bootloader - boot from a windows 7 disc and run 'bootrec.exe /fixmbr'

---

### Post by MetalMikey666 on 2010-11-27
This worked for me too. I had a wubi-installed ubuntu and got the grub-rescue> prompt after an update. fix was as above;
 
boot from a live CD and start a terminal
* sudo apt-get install lilo
* sudo lilo -M /dev/sda mbr

Gives all sorts of warnings and things along the way but worked anyway!

---

### Post by pdemuth117 on 2011-01-14
Hey guys, I had that exact same problem.  This worked like a charm and now everything is up and running again.  Thank you so much for posting this.  I was in a similar situation where I was curious about trying Ubuntu, but did not have any Linux experience.  Now, to be honest, I'm afraid to try it again.  From people who have tried this duel boot with Windows, is this common at all, or can I expect to keep on using Ubuntu without any interference with Windows?  Even if this is rare, I really can't afford to not be able to boot for long periods of time again.  Thanks everyone.

---

### Post by unlucky on 2011-01-23
I am in the same situation as the user mentioned above. I have installed Ubuntu 10.10 on a 8GB flash drive and I have win xp sp3 on a separate hard drive that comes with the laptop - IBM THinkpad R52 model. What I have experienced so far is that when I install Ubuntu with the option of using the entire 8GB flash drive for complete installation of Ubuntu, it never comes up when I try to restart Ubuntu. 

I get the error "grub rescue - no such device". I followed the bunny trail for fixing this error and followed the advise given by the members here in this thread using the LiveCD and running lilo commands and it fixed the issue and windows xp was up and running again. However, I was never able to get the Ubuntu running, even when I tried to go thru the correct boot sequence in the BIOS and I chose the 8GB flash drive to boot first. Nothing helped and I was not going anywhere..Hence, I got frustrated and I tried to re-install again the Ubuntu on the 8GB flash drive again yesterday and lo & behold, I get the same exact message "grub rescue - no such device error..

What is up with this error? How can I fix it so that I can dual boot both Ubuntu 10.10 and Windows xp SP3..I tried various ways listed in these forums and other tools mentioned by other folks like EasyBCD (with xp, I guess EasyBCD doesn't work), but nothing has worked so far..

Experts I need your help here...Please.

Meanwhile, I use the same set of the commands that I used earlier to restart windows xp on my machine from the 'grub rescue' situation.

Thanks again.

---

### Post by bcbc on 2011-01-23
@unlucky, you should check out the [Grub Rescue Megathread]("http://ubuntuforums.org/showthread.php?t=1594052") and then post there (or create a new thread for specific help on your situation).

---

### Post by Andrew_nuts on 2012-02-05
This is the most asked question in Ubuntu forum.
The details solution for this problem is given on the following thread

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

And close the thread as it is solved

---

