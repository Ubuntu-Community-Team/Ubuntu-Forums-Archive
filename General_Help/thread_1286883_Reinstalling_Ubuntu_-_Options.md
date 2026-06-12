---
title: "Reinstalling Ubuntu - Options?"
date: 2009-10-09
forum: General Help
---

### Post by Gosport on 2009-10-09
I need to reinstall Ubuntu.  (Blank screen after splash)  I would like to save all the work that Picasa has been doing (facial recognition in 3.5 running in Wine that has been running for the last week, and also my user accounts and Firefox settings, etc if possible)  

Should I:

1)  Just copy my home folder (using the live CD), wipe out the hard drive, install Ubuntu, then finally replace the new home folder with my backed up home folder?

2)  Boot into recovery mode, chose "Drop into Shell Prompt" (I think that was the name) and enter some code like this: "sudo apt-get update" then "  [FONT=&quot]sudo apt-get dist-upgrade"  (obviously I don't know what I'm doing but I saw this code for upgrading and thought it may work for a reinstall too)

3)  Something else??
[/FONT][FONT=&quot][/FONT]

---

### Post by QIII on 2009-10-09
Which version of Ubuntu are you using and when did you last update?

If you use dist-upgrade from Jaunty you'll get the Karmic Beta, which you probably don't want right now.

---

### Post by Gosport on 2009-10-09
I'm running Jaunty.  Just installed the thing on a new computer the other week.  I just messed up my system and need to reinstall.  (I had tried to add a printer but things locked up and now I only get a blank screen after the splash screen)

---

### Post by QIII on 2009-10-09
I would try your option 2 first.  It may or may not work (I don't know what happened when it crashed, so I can't say for certain.)

But instead of dist-upgrade, use:

```
sudo apt-get update && sudo apt-get upgrade
```

Then next thing will be to try to repair your X, but let's try this first.

---

### Post by louieb on 2009-10-09
Installing a printer should not cause X to die. There is something else going on. Have you tried booting in recovery mode and select the fix X server option?  

If you have to reinstall. Note: When you copy your home folder off and put it back use the -a option. That will preserve ownership and permissions of the copied files and folders.

---

### Post by Gosport on 2009-10-09
> **louieb said:**
> Installing a printer should not cause X to die. There is something else going on. Have you tried booting in recovery mode and select the fix X server option?  

If you have to reinstall. Note: When you copy your home folder off and put it back use the -a option. That will preserve ownership and permissions of the copied files and folders.


What is the "-a" option?

What happened is that I was logged in as a regular user (not the primary user) and, forgetting this, I started to add a printer.  I was prompted for a password but the primary user password was unsuccessful (I think it actually wanted a root password, which I don't have anyway.)   Anyway I moved my mouse to the upper right corner and selected my primary user account and the screen went blank and froze up.   

I am using a proprietary video driver, don't know if that had anything to do with it.

I did boot into the recovery mode and did select the "Fix X Server" option (along with just about everything else :))

If you have any suggestions I would love to try them.  I have had a very hard time finding anything helpful on the web.  Thank you.

---

### Post by louieb on 2009-10-09
The -a option preserves ownership and permission information. - Very important in Linux. 
> regular user ... I was prompted for a password but the primary user password was unsuccessfulPassword needed was the users password,  but would not have worked unless user is a member of the admin group. (There is not root password in Ubuntu - root can't login).

> Anyway I moved my mouse to the upper right corner and selected my primary user account and the screen went blank and froze up.Thats the fast user switcher - it starts another X server or switches X server if that user is logged on. hummm...
> I am using a proprietary video driver, don't know if that had anything to do with it.Can't remember if the "fix X server" gives you the option to select the **VESA**  driver if so try it . The  VESA video driver works with about everything. At least you'll have a GUI to work on.

Do you get the Graphical Desktop  when you boot with the Live CD?

---

### Post by Gosport on 2009-10-09
How do I copy with the -a option?  Could you give me an example of a comand?  I'm new to linux and am just now reading the Ubuntu Pocket Guide and haven't seen anything like that yet.  (I tried Googleing it and don't come up with much)

I don't remember any options in the "fix X Server" option.  I'm pretty sure I would have remembered that, but I'll try that and also the live CD when I get home tonight.  My suspicion is that the live CD will work.  Will you be online later tonight?  I really appreciate the fact that you are taking an interest in my problem.

---

### Post by Vaphell on 2009-10-09
**cp --help** shows you options

in this case probably **cp -ra /source/path/ /destination/path/**

you just combine options after -
r = recursive (with subdirectories)

---

### Post by Gosport on 2009-10-09
OK, so "-a" is like "list all" and "r" (recursive) is to do this to all sub directories.

First I'll mount my external hard drive:
sudo mkdir /mnt/harddrive
sudo mount /dev/sda1 /mnt/harddrive

Then I copy all files and all subdirectories to the external hard drive:
sudo cp -ra /home/ /sda1/copy

Then I can reinstall unbuntu and copy all the files back:

First I'll mount my external hard drive again:
sudo mkdir /mnt/harddrive
 sudo mount /dev/sda1 /mnt/harddrive

Then I copy all files and all subdirectories to the hard drive:
sudo cp -ra  /sda1/copy/  /home/

Does this look right?

---

### Post by Gosport on 2009-10-09
On the repair end, does anybody think that this code would help my situation:


sudo apt-get --reinstall install xserver-xorg

---

### Post by louieb on 2009-10-09
The -a option of the copy command means archive - can be written as --archive

To reconfigure the X server.
Try this:
```
sudo dpkg-reconfigure xserver-xorg
```or 
```
sudo dpkg-reconfigure --phigh xserver-xorg

```Do you have a Desktop with the Live CD?

> sudo apt-get --reinstall install xserver-xorg

never tried it or seen it recommended - but that does not mean it would not work - won't hurt to try?

---

### Post by Gosport on 2009-10-09
No??  The live CD isn't booting??

---

### Post by louieb on 2009-10-09
Exactly what does CD Not booting mean?  Does it seem to be doing anything? 

Or does it just ignore it and boot straight to the hard drive? 

Please be descriptive as possible. 

I'm trying to help you decide if there is hardware problem or if the problem is software.  Are you still getting the Ubuntu splash screen?

---

### Post by Gosport on 2009-10-09
sudo apt-get update and sudo apt-get upgrade  ---> didn't help (tried to reboot but no luck)

sudo dpkg-reconfigure xserver-xorg  ----> "xserver-org is not installed"

sudo dpkg-reconfigure --phigh xserver-org  --> gave me a list of options:
-a, --all                                   Reconfigure all packages.
-u, --unseen-only                     Show only not yet seen qusetions.
     --default-proprietary           Use default priority instead of low.
     --force                               Force reconfiguratuin of broken packages

This list goes on, but I don't know how to make any of the selections!
Do you know what option I should chose and how I can make that selection?

---

### Post by Gosport on 2009-10-09
It just ignores it and goes to the hard drive boot.  The BIOS are set to boot to the CD drive first too.

---

### Post by louieb on 2009-10-09
Selecting recovery from GRUB menu and running  xfix did not work - are you sure you selected it?  Said you were using a proprietary video driver what card do you have? 

Won't boot to CD - and you checked BIOS for the boot order. Is the CD scratched up? Can you check it on another computer? Can you burn another one?

---

### Post by Gosport on 2009-10-09
I have an integrated ATI Radeon HD 4200.  I had the watermark in the bottom right corner that said AMD unsuported hardware

The CD should be fine.  I can't boot my Puppy Linux either.  I'll go double check on the computer next door.

---

### Post by Gosport on 2009-10-09
Ok, I figured out why the computer wasn't booting to the CD.  I checked the BIOS again and saw that indeed the CD was the first boot priority but not the HP DVD Writer that I have.  (It did work for my initial installation though)

So live CD is working!  The normal graphical environment of Ubunto on the hard drive is still not though.

Hopefully the Live CD not working issue didn't scare every one off :)

---

### Post by louieb on 2009-10-10
Good At least now it seems to be the X server thats the problem 

Wish you can avoid a reinstall - but I'm out of ideas of what to do to fix the X server.  Or at least restore it to its defaults. Still wonder what broke it.  

One last shot - boot to the Live CD and compare the file **/etc/X11/xorg.conf **with the one on the hard drive.  

lol - on one PC I copied the xorg.conf file from a Puppy install to the Ubuntu install - and that fixed a low resolution problem I was having - just a shot in the dark that worked. 

Thought of another way to copy and preserve ownership. 

The way you put in post #10 should work. But IF you have trouble - you can use the file manager to copy the files off.

Then after the reinstall have each user copy his own files back to his home directory. The way it works when a file is copied - the user that copied the file owns the copy.

---

### Post by Gosport on 2009-10-10
What I have done is to copy the home directory to my external hard drive using Puppy (turned on the view all files to copy everything) .  I just couldn't get into my external through the shell.  I think filesystem messed me up.  I was thinking of using Puppy to put everything back, but maybe I should log in as each user and copy them the way you suggested.

I'll check out the /etc/X11/xorg.conf files.Anything in particular I should look for?  Could I just copy the flie frome the live CD to the hard drive?  I could boot puppy into ram then remove the CD and add the Ubuntu CD and copy from there.  Think it would work?

---

### Post by Gosport on 2009-10-10
Of course I wont be able to find the file on the live CD without booting it up.  I guess all I can do is look and compare.   Oh well.

---

### Post by Gosport on 2009-10-10
The two files look identical!  Who knows.  I'm going to do a re-install of Ubuntu now.  I'll let you know how it goes.

---

### Post by Gosport on 2009-10-10
I used the copy of of my home folder to replace my files, the way you said, by loging in to each user account to replace their files.  My attempt at using Puppy to replace everyone's home folder at once failed, and necessitated another reinstall. 

One thing I would like to note.  I was running Picasa 3.5 with facial recognition under Wine.  My computer had been processing the photos for days.  I thought I had lost all that work, but I simply deleted all files in the .wine folder (need to check view all files) and replaced them with the .wine folder from my home directory backup.  (just replacing the Picasa folder under .wine did not work)  Picassa picked right up where it had been!

Thank you so much for all your help.  To bad we couldn't figure out what had origionally gon wrong.

---

### Post by louieb on 2009-10-10
> To bad we couldn't figure out what had originally gone wrong.

Great that you back up. Thanks for letting us know.  Good Luck. lou

---

