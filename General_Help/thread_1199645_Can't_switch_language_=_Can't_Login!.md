---
title: "Can't switch language = Can't Login!"
date: 2009-06-29
forum: General Help
---

### Post by Geordino on 2009-06-29
I have Ubuntu 8.10 along with Windows XP installed on my PC.
On Ubuntu I have 2 languages(English and Arabic), English is the default language.

yesterday I was working on Ubuntu, but today out of the sudden, when I start Ubuntu, the default language in the login screen is Arabic.

The problem is that I can't change the language which means I can't enter my user name and password which are in English.

I tried Alt+Shift, I tried "Select language.." from the login screen menu.. but nothing changes, Ubuntu is stuck to Arabic.

the strange thing is that I didn't touch the language settings yesterday, I didn't install anything.. I was just on the internet and using some editors!

How can I fix this? 
If I can't get it to work, can I get my files which are stored in Ubuntu file system back?

thank you

---

### Post by kokkus on 2009-06-29
You can always get your files back. And to fix this problem, please check if you have an older kernel in grub.

---

### Post by Geordino on 2009-06-29
thanks for the fast reply..

"check if you have an older kernel in grub."
how can I check this? what should I look for?

---

### Post by kokkus on 2009-06-29
Oh I am sorry.
You have windows and ubuntu right?
The list you choose which OS you will start is called Grub.
I assume the newest kernel is the one you use when you login to Ubuntu.
And below that one there are other options like Microsoft Windows XP Professional, ubuntu recovery mode and etc.
If you don't have an older kernel version then the one you use now, go to recovery mode and in the menu that pops up, choose "repair broken packages".

---

### Post by Geordino on 2009-06-29
yes, I have two Linux kernels
actually I already have done what you suggested on both of them
I also tried to boot using both but nothing changes

---

### Post by kokkus on 2009-06-29
Ok. I really don't know then. SInce hacking info is illegal to post here.
So you can try 1 of 2 options.
1. Put in your live CD, find your files and move them over to your windows partition or windows disk.
2. Go to windows, install fs-driver from [www.fs-driver.org](www.fs-driver.org) to access your linux partition and then you can move your files to your windows folders.

---

### Post by t0p on 2009-06-29
Have you tried the other thing kokkus suggested?  Using recover mode?  I'm pretty sure the default language used in that mode is english... but I may be wrong.

If that won't work, to retrieve your files do the following:

Put your ubuntu cd in the drive and reboot;  

Select to try ubuntu without installing it;

Once it's started, you should be able to see a file system (possibly called "disk") which represents the computer's hard drive.  This will be either in Places or on the desktop.  Click to mount it.

Navigate to your home directory (called /media/disk/home/*your-user-name* or similar) and copy the files to a usb stick or some other removable media.

Success!  Files retrieved!  :)

---

### Post by kokkus on 2009-06-29
The last method I can mention legaly here is to change your root password from recovery mode (if none of the above works).
login as root shell and change the password
password is: passwd

---

### Post by Geordino on 2009-06-29
thank you for the help. I was able to copy the files after booting from the CD.. I formatted my disk and installed Ubuntu again

I really like linux, specially ubuntu, but it always keeps crashing with no obvious reason.

since a couple of weeks it started having problems with playing sounds. the problem was occuring occasionally and only if I open a web page that has any flash movies, in that case the sound will not work until I restart the system, but if I open a sound file with vlc media player before opening the flash page then no problem occurs later when I open youtube for example... so, I wrote a script to play my favourite song with vlc automatically when I log in to the system :) not very bad

one month before the desktop was freezing very often. the problem disappeared when I disabled the desktop "visual effects"

and many other problems, I can say every month or two I have a strange behaviour!

I don't know if all of you are experiencing such problems or may be it is just that I have a very bad luck :)

---

