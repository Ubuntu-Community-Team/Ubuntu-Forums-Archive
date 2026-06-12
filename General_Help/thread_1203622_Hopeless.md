---
title: "Hopeless?"
date: 2009-07-03
forum: General Help
---

### Post by mgtech on 2009-07-03
I had about 220 GB of movies and music on my ubuntu 9.04 64bit machine. I uninstalled a small utility that I had added, but apparently it was attached to other important files like gnome,firefox, mplayer, synaptic, packet manager etc. etc. etc. Now when I boot I have no picture and am in a command prompt-eque system and cannot login using my old password. Is there any way I could recover said entertainment files from the live boot, which I am currently in.

Help!!!

---

### Post by beastrace91 on 2009-07-03
Of course, when you are booted from the LiveCD just click into "places" at the top and then select your old hard drive, all the files should be right where you left them.

~Jeff

---

### Post by mgtech on 2009-07-03
how do i get permission to access the files? I previously had the files locked to the viewing of other users.

g's movs' - properties>contents unreadable

---

### Post by beastrace91 on 2009-07-03
You should be able to save your install though if all you did was uninstall a single application. Your login name/password should be the same for the terminal login as they are for the GUI, double check that you are entering them correctly. If you can log into terminal you can get Gnome back up and running again easy.

~Jeff

---

### Post by beastrace91 on 2009-07-03
Permission? Do you have the hard drive encrypted or some such thing? You should be able to just select the hard drive and see your files from the live disc.

~Jeff

---

### Post by mgtech on 2009-07-03
i had changed the file permissions
you said that i could get ut up and running easily if i could login; what do i do next?

---

### Post by mgtech on 2009-07-03
wait a sec pls i'm getting on another comp to continue the conversation, while i try to operate this comp

---

### Post by beastrace91 on 2009-07-03
Make sure you have an active internet connection and then try to run ```
sudo apt-get install ubuntu-desktop
``` and that should reinstall any default Ubuntu application/tools you may have removed by mistake.

~Jeff

---

### Post by mgtech on 2009-07-03
startin up - get you the results soon

---

### Post by mgtech on 2009-07-03
couldn't resolve archives from ubuntu website - oi presume b/c no firefox
it told me to try apt-get update and --fix missing? - both failed

---

### Post by beastrace91 on 2009-07-03
Do you have an active internet connection?... Try running ```
ping www.google.com
``` and see if it can connect.

~Jeff

---

### Post by mgtech on 2009-07-03
is there  a way to do that same thing off the live boot cd?

---

### Post by beastrace91 on 2009-07-03
I am sure there is but I am not certain how to go about doing it. Internet is your best friend when using Linux, try and get your connection hot.

~Jeff

---

### Post by mgtech on 2009-07-03
Internet :(

result to google ping attempt!!! failed - perhaps b/c no firefox web browser
it is physically connected to the net, but can't see it -- unknown host [www.google.com](www.google.com)

---

### Post by mgtech on 2009-07-03
do you know anyone who could tell me how to recover off a live boot cd?

---

### Post by beastrace91 on 2009-07-03
Is your ethernet/network cable hooked into the computer?

~Jeff

---

### Post by mgtech on 2009-07-03
yes, the net is hooked up- i was running running firefox and everything before my mistake on synaptic and i just checked

---

### Post by mgtech on 2009-07-03
The response to my command to install firefox gets me something that says "could not resolve us.archive.ubuntu.com"

i think its safe to say i won't be able to get help from the net

---

### Post by tvtech on 2009-07-03
if your in command line try installing lynx.   it's a text based web browser.

```
username@localhost:~$sudo apt-get install lynx
```

Network manager might be your problem.  Try restarting it.


I don't remember how tho

---

### Post by mgtech on 2009-07-03
result of lynx:

still cannot resolve :(

in all likelihood the network manager is damaged too

---

### Post by mgtech on 2009-07-03
i really need a way to use the live boot cd

---

### Post by Chronon on 2009-07-03
This discussion seems a bit useful for you:
[http://sidux.com/PNphpBB2-viewtopic-t-10488.html](http://sidux.com/PNphpBB2-viewtopic-t-10488.html)

---

### Post by beastrace91 on 2009-07-03
Alright, did some digging on google lets see if we can install the packages we need form the disc. Pop the livecd in your CD drive and then boot FROM THE HARD DRIVE to the terminal login. Once you are logged in run ```
sudo nano /etc/apt/sources.list
``` And un-comment the first line that says something along the lines of "deb cd <disc name>" then save and exit the file and run ```
sudo apt-get update
``` (it will odds are complain about not finding the internet sites but it *should* see the CD now) now try running ```
sudo apt-get install ubuntu-desktop
``` again and see if it installs off the disc.

~Jeff

---

### Post by mgtech on 2009-07-03
un-comment the first line - what? how do you do that?

---

### Post by beastrace91 on 2009-07-03
Yes, that will tell it to boot from the hardrive instead of the live CD

---

### Post by beastrace91 on 2009-07-03
> **mgtech said:**
> un-comment the first line - what? how do you do that?

Remove the # from in front of the line.

~Jeff

---

### Post by mgtech on 2009-07-03
i typed in the first line of code you told and i got a big page of text - what do i do next?

---

### Post by beastrace91 on 2009-07-03
You can scroll up and down in the file using the arrow keys, do you see any lines that say "deb cd" followed by a disc name (that should be the livecd you installed with)? Mine was at the top of the file, but your may be in a different order.

~Jeff

---

### Post by mgtech on 2009-07-03
i am looking @ the same file and i have no # sign in front of "deb cdrom"
how do i save and exit?
what does ^X mean? what do i press?

---

### Post by earthpigg on 2009-07-03
> Is there any way I could recover said entertainment files from the live boot, which I am currently in.

if that is your only goal (instead of fixing the system, which the rest of this thread seems devoted to), then your computers hard drive should be in places->computer when you are running the liveCD... it will be on the left, described by its partition size that you will probably recognize as a number you have seen before.

go to that hard drive, go to the 'home' folder, then to the folder with your username.... music is probably in the 'music' folder in there.

copy it off that hard drive onto an external hard drive or something else.

---

### Post by mgtech on 2009-07-03
that was my only goal until i new of a way to fix it - fixing the comp is by far preferable

---

### Post by mgtech on 2009-07-03
jeff i tried that but it still is trying to look off of the net & not the disk

---

### Post by mgtech on 2009-07-03
is ne1 here?

---

### Post by mgtech on 2009-07-03
if i was to put in the live cd and in that copy my filesto a portable drive, could i find a way to access them on another comp?

Basically, on the live cd is there a way to access file that have been closed to other users?

---

### Post by beastrace91 on 2009-07-03
Sorry got caught up at work, anyways if it cannot see the disc and you cannot get online then you cannot repair the broken install.

Are you sure the proper line is commented out? See below:

[IMG]http://i44.tinypic.com/24nfbqx.png[/IMG]

Also be sure when you ctrl+x to exit nano you say "y" to say changes.

~Jeff

---

### Post by mgtech on 2009-07-03
actually - is there a way to open my closed files on the live cd so i can copy them to a portable hd?

---

### Post by beastrace91 on 2009-07-03
What did you do to "close" the files?

~Jeff

---

### Post by mgtech on 2009-07-03
a couple of weeks ago i went under properties and made it so that only i ( my account) could read and write them.

---

### Post by mgtech on 2009-07-03
i was under file>properties>permissions

---

### Post by mgtech on 2009-07-03
i get a msg that says you aren't the owner you can't change these permissions

---

### Post by mgtech on 2009-07-03
is there a way to get admin privileges on a live cd?

---

### Post by beastrace91 on 2009-07-03
On the LiveCD you should be root by default.

~Jeff

---

### Post by nothingspecial on 2009-07-03
Same as normal - sudo cept you don`t need a password

---

### Post by blueridgedog on 2009-07-03
While on the live CD, if you bring up a root version of nautilus, you should be able to see them:

```
sudo nautilus
```

Also, on the live CD, you can change your root to your existing system and re-install the desktop (it seems that was the path you were going down).  I can walk you through it if you want to try, but see about those files first.

---

### Post by mgtech on 2009-07-03
is there a way to open them then?

---

### Post by blueridgedog on 2009-07-03
> **mgtech said:**
> is there a way to open them then?

Mgtech:  Perhaps you should quote the poster you are addressing, it is hard to tell at what point you are in the process.  If you mean the files after you have accessed with a root session of nautilus, you may not have the restricted codecs needed during your live CD session.  The issue at hand is really to save them at this point no?

---

### Post by mgtech on 2009-07-03
it ried what you said but that only gave me the virtual comp root and not the root priv on my hd

---

### Post by mgtech on 2009-07-03
lets try ur way

---

### Post by mgtech on 2009-07-03
yes the issue @ hand is to save the files, but it doesn't do me any good to have them saved if i can't access them.

---

### Post by blueridgedog on 2009-07-03
To install a package with a broken OS, you can boot off of the live CD, then chroot to your existing install and to maintenance.

For example, assuming your non-working system is mounted as /media/disk:

First: Change the root fs to your existing drive:


```
sudo mount --bind /dev /media/disk/dev
sudo chroot /media/disk
```

Now you have a booting system (via the liveCD) and are working on your dead or damaged system.  You can install anything you want with apt-get.  
```

sudo apt-get install gnome-desktop
```

(for example, as I am not certain that this is your problem)

---

### Post by mgtech on 2009-07-03
what would be a command line to change the properties of the files

---

### Post by blueridgedog on 2009-07-03
> **mgtech said:**
> it ried what you said but that only gave me the virtual comp root and not the root priv on my hd

Is the disk with the images and movies mounted?  Can you post the output of:

```
sudo fdisk -l 
```

and

```
mount
```

---

### Post by blueridgedog on 2009-07-03
> **mgtech said:**
> what would be a command line to change the properties of the files

I need to know more about the path to the files (see my post regarding fdisk and mount.  If you tell me where the drive/partition that contains them is mounted, then I can tell you have to change permissions).

---

### Post by mgtech on 2009-07-03
it is under /media/disk 
the files that need changing are on that disk under "home/grant/Desktop/Grant's Files/G's Mov's" & also "same..Desktop/Grant's Files/torrents"

---

### Post by mgtech on 2009-07-03
blueridge - what would be the side efffects of changing my root to that of the damaged hd. can you explain that process some more... it might be the way to go. I am not familiar with chroot. Would that allow me to repair my os and keep my files intact?

---

### Post by blueridgedog on 2009-07-03
> **mgtech said:**
> it is under /media/disk 
the files that need changing are on that disk under "home/grant/Desktop/Grant's Files/G's Mov's" & also "same..Desktop/Grant's Files/torrents"

And you can't browse to them with a root nautilus session?

You can reset file permissions with:

```
sudo chmod 666 /media/disk/home/grant/Desktop/* -R
```

This will make every file on the Desktop of user grant and all subdirectories and files readable and writable by all users.

---

### Post by blueridgedog on 2009-07-03
> **mgtech said:**
> blueridge - what would be the side efffects of changing my root to that of the damaged hd. can you explain that process some more... it might be the way to go. I am not familiar with chroot. Would that allow me to repair my os and keep my files intact?

I recommend recovering your files with the live CD and then doing a re-install at this point.  However, after you do recover your files you can attempt to repair the busted install using chroot as described.  The issue that needs to be addressed is why it is not working and I am not certain I can tell you how to fix it with the limited information I have seen.

---

### Post by mgtech on 2009-07-03
im sorry - i tried that chmod 666 and the operation isn't permitted

---

### Post by mgtech on 2009-07-03
blueridge- ask anything you want to know

---

### Post by blueridgedog on 2009-07-03
> **mgtech said:**
> im sorry - i tried that chmod 666 and the operation isn't permitted

Sorry, add sudo in front of it.
```

sudo chmod 666 /media/disk/home/grant/Desktop/* -R
```

---

### Post by mgtech on 2009-07-03
hey every1 good news - i found the files with sudo nautilus and was able to change the permisssion so everyone can read and write - lets see if they can be opened - back in 1 sec

---

### Post by mgtech on 2009-07-03
i canz haz file access!!!!!! i can't open them though b/c the live cd doesn't have codecs & stuffs

---

### Post by mgtech on 2009-07-03
so now should i copy the files to a portable hd. if i do this will a win xp xomp be able to see them?

---

### Post by blueridgedog on 2009-07-03
> **mgtech said:**
> so now should i copy the files to a portable hd. if i do this will a win xp xomp be able to see them?

Plug in the USB drive, if it shows as removable media, just drag and drop.

---

### Post by Arlanthir on 2009-07-03
> **mgtech said:**
> so now should i copy the files to a portable hd. if i do this will a win xp xomp be able to see them?

I don't see why not ;)
Why don't you try it out before deleting them anyway?

Remember to **unmount** the hard drive before unplugging it!

Also, you can edit your posts instead of making a new one everytime, saves a lot of forum space because it gets less cluttered and easier to see. Good luck :)

---

### Post by mgtech on 2009-07-03
Everyone, thanks for your help so far and i'll get back with you in a few once i move and attach my portable hd.

---

