---
title: "sudo problems, please help."
date: 2011-08-07
forum: General Help
---

### Post by thatguy93 on 2011-08-07
Hey guys,
I recently installed Ubuntu 11.04 on my laptop, and gave it t my sister.
On there were some important files, and I copied them to a USB drive and transfered them to my computer, of course, I clicked "cut" instead of "copy", and pulled the drive out a second too early, and lost all the data. Every file is blank. 
So I was going to try and install scalpel, and see if I could recover the files, and thats when I ran into this issue.

My account is the only one on the computer, and I am the system admin. However, when I try to use the 'sudo' command, it asks for my password, I enter it, and it says "user is not in the sudoers file. this incident will be reported".
I tried to go to user accounts, and change my settings, but it asks for the root password. 

What do I do? 

thanks!

---

### Post by jerrrys on 2011-08-07
if you have not restarted your computer

gksudo nautilus 

and paste

---

### Post by Serpher on 2011-08-07
You're going to have to activate your root account and edit your sudoers file.

```
su -
passwd
visudo
```

From there look for the line with your username and post it. If it's not there add this line: '%admin ALL=(ALL) ALL'

[http://ubuntuforums.org/showthread.php?t=1132821](http://ubuntuforums.org/showthread.php?t=1132821)


Also to get your files off, find out what your device identifier is for your USB. It's probably something like /dev/sdb or /dev/sdc. After you know which one it is run the following commands where ? is the last letter of your device identifier:

```
sudo dd if=/dev/sd? of=~/usb
cat ~/usb.fs ~/usb
rm ~/usb.fs
less ~/usb

```

You will now be manually reading your USB's filesystem. Using commands like 'cat -n | grep "<keyword>"' to make things easier. Recovering plain text files should be a breeze but other things should be more difficult and there are probably better ways to do this.

---

### Post by bodhi.zazen on 2011-08-07
> **Serpher said:**
> You're going to have to activate your root account and edit your sudoers file.

Sorry, but that is just wrong. You can either boot to recovery mode or boot a live CD, no need to activate the root account.

With potential data loss the fist thing is to STOP using the hard drive , if you keep editing files as you suggest you may well over write the data you are trying to recover.

Best boot a live CD and start your data recovery process. If possible it is usually best to work on an image or copy of the hard drive.

---

### Post by thatguy93 on 2011-08-07
> **jerrrys said:**
> if you have not restarted your computer

gksudo nautilus 

and paste

Does not work.
I get an error: "Failed to run nautilus as root".

---

### Post by thatguy93 on 2011-08-07
> **bodhi.zazen said:**
> Sorry, but that is just wrong. You can either boot to recovery mode or boot a live CD, no need to activate the root account.

With potential data loss the fist thing is to STOP using the hard drive , if you keep editing files as you suggest you may well over write the data you are trying to recover.

Best boot a live CD and start your data recovery process. If possible it is usually best to work on an image or copy of the hard drive.

Can I use a LiveUSB?

---

### Post by Spyderkid on 2011-08-07
yes you can use USB there the same they just use different slots. and i think USB might be a bit slower but appart from that there the same

---

### Post by thatguy93 on 2011-08-07
How do I recover data?

---

### Post by thatguy93 on 2011-08-07
Okay well I changed the root password now. I downloaded Ubuntu rescue remix, and changed my root password in there.
Now to recover the data.

EDIT:
Okay nevermind, looks like I did not get anywhere.
When I use terminal, and type in SU and enter the password, it gives me and "authentication failure", and if I type sudo passwd and enter my password, or the root password, it doesnt work, and then gives me "user is not in the sudoers file".

What the heck am I doing wrong?

---

### Post by bodhi.zazen on 2011-08-07
Boot a live CD (or USB)

Become root with ```
sudo -i
```

Stop using your hard drive or flash drive where you are trying to recover data.

Other then that I can not really tell what you are doing. booting from flash drive ? Changing your password and root password where ? how ?

And what have you done for data recovery ?

---

### Post by thatguy93 on 2011-08-08
> **bodhi.zazen said:**
> Boot a live CD (or USB)

Become root with ```
sudo -i
```

Stop using your hard drive or flash drive where you are trying to recover data.

Other then that I can not really tell what you are doing. booting from flash drive ? Changing your password and root password where ? how ?

And what have you done for data recovery ?

I installed Ubuntu recovery remix on a flash drive. Then booted up the laptop. Its a text program, so you can type commands and whatnot.
I typed ```
sudo passwd
``` and changed the password. I also tried ```
su passwd
``` and ```
sudo -i
```.
They all worked. 
However, once I reboot, and remove the drive, and try to install things, it wont allow me. It still says I am not in the sudoers file.

I have not done anything for data recovery yet, because I dont know what to do. I was trying to install scalpel to see if I could get the files back. But they were "cut" not copy pasted, and deleted. So I am not even sure if I can find them.

I removed the drive to early, the notification that saus "writing files to drive" was in the background, so I thought it had finished.

---

### Post by thatguy93 on 2011-08-08
Alright I started Ubuntu in recovery mode. Then added my user to the admin group, and changed the root password.
So now I do have access to everything once again.
Thanks for the help guys. I will mark the thread as solved.

---

