---
title: "so here's my situation"
date: 2009-06-25
forum: General Help
---

### Post by jake16424 on 2009-06-25
Second round with linux, last time used UBUNTU 7.14 or something like that. 

the H3ll with windows.

have my partitions ready. <--irrelevant for my current problem

Current issue

under 

Linux Mint 7

how do I creat a SU account?

Creat an account, Im running mint7 from a FLASH drive =D 
currently logged in as MINT

can i use WINE\Virtualbox to install windows programs on my clean partitions and can i install linux as a standalone OS with no other file systems on the disk?:confused:

account first please!:)

oh and its good to be back, had enough with windows, im here to stay linux!:popcorn:

---

### Post by doas777 on 2009-06-25
Welcome!

well, I don't know about mint per se, but i do know that I got yelled at last time I assisted a user in enabling a root account here on the forums, so the topic is not really something that can be discussed here. google is your friend. the answer you seek is out there. I don't really recommend that you have an enabled root or su account.

that said, i encourage you to reorganize your post, so we can easily determine what you are asking. I know, it's a pain, but it will prolly pay off. I've usually found that revising my post, is a good way to attract a response if one is not forthcoming.

good luck.

---

### Post by Sunset45 on 2009-06-25
I have just loaded Ubuntu 8.04 on a new hard drive and what comes up on the screen is DHCP??  What do I do now?  :(

---

### Post by Yellow Pasque on 2009-06-25
A better question: Why do you need a root account?

---

### Post by jimv on 2009-06-25
> **Temüjin said:**
> A better question: Why do you need a root account?

I think he means an account htat can use sudo.

---

### Post by jake16424 on 2009-06-25
> **Temüjin said:**
> A better question: Why do you need a root account?

If i can be assisted in how to mount an ISO image i will not need said account.

tutorial said to log in SU acount but i found the answer to that, however i am still ignorant as to how to mount an ISO file....

---

### Post by jake16424 on 2009-06-25
> **doas777 said:**
> Welcome!

well, I don't know about mint per se, but i do know that I got yelled at last time I assisted a user in enabling a root account here on the forums, so the topic is not really something that can be discussed here. google is your friend. the answer you seek is out there. I don't really recommend that you have an enabled root or su account.

that said, i encourage you to reorganize your post, so we can easily determine what you are asking. I know, it's a pain, but it will prolly pay off. I've usually found that revising my post, is a good way to attract a response if one is not forthcoming.

good luck.

ahhh haha, ok well i don't want to get you yelled at =D.

google i want to slap with a spiked hammer ATM heh.... but i get you. thanks

---

### Post by Ocxic on 2009-06-25
"sudo mount -o loop /path/to/.iso /path/to/mount/point"

"sudo -i" will provide a root prompt so that you don't need sudo in front of every command, but will keep the root account itself disabled.

---

### Post by Tyke91 on 2009-06-25
sudo mount -o loop /name/of/the/file/you/are/mounting/to /what/you/want/to/mount

for example, if i wanted to mount the file /mnt/iso to /home/joe/isos/awesomefilm.iso i would do

```
sudo mount -o loop /home/joe/isos/awesomefilm.iso /mnt/iso
```

---

### Post by jake16424 on 2009-06-25
> **Tyke91 said:**
> sudo mount -o loop /name/of/the/file/you/are/mounting/to /what/you/want/to/mount

for example, if i wanted to mount the file /mnt/iso to /home/joe/isos/awesomefilm.iso i would do

```
sudo mount -o loop /home/joe/isos/awesomefilm.iso /mnt/iso
```

so in my case 

sudo mount -o loop /media/movies/Games/cod4.uif / (this is where im confused, how do i make it mount? im lost at this part.. what is supposed to go here)

trying to mount an instillation disk from an image .uif

---

### Post by Tyke91 on 2009-06-25
> **jake16424 said:**
> so in my case 

sudo mount -o loop /media/movies/Games/cod4.uif / (this is where im confused, how do i make it mount? im lost at this part.. what is supposed to go here)

trying to mount an instillation disk from an image .uif


the last part is an empty directory. 

EASIEST way to do this
```
sudo mkdir /mnt/iso
sudo mount -o loop /media/movies/Games/cod4.uif /mnt/iso

```the first command makes an empty directory, /mnt/iso. the second command actually mounts it to that iso file in media.

later on, you will want to 
```
umount /mnt/iso
```

you can then use the same mountpoint later on.

---

### Post by doas777 on 2009-06-25
> **jake16424 said:**
> so in my case 

sudo mount -o loop /media/movies/Games/cod4.uif / (this is where im confused, how do i make it mount? im lost at this part.. what is supposed to go here)

trying to mount an instillation disk from an image .uif

from what i'm seeing [here]("http://ubuntuforums.org/showthread.php?t=513089") and [here]("http://onubuntu.blogspot.com/2007/11/dealing-with-uif-files.html"), uif files only work with magicISO, but they say it runs well in wine. 

you could install wine if you so choose, by entering at a terminal:
```
sudo apt-get install wine
```


after that, just download the windows version of magicISO, and install it with wine (right click file. and select open with wine application launcher) . I would then use magicISO to convert the uif to an iso, so you can easily use it in almost all programs that mount images.

have fun,

---

### Post by jake16424 on 2009-06-25
> **doas777 said:**
> from what i'm seeing [here]("http://ubuntuforums.org/showthread.php?t=513089") and [here]("http://onubuntu.blogspot.com/2007/11/dealing-with-uif-files.html"), uif files only work with magicISO, but they say it runs well in wine. 

you could install wine if you so choose, by entering at a terminal:
```
sudo apt-get install wine
```


after that, just download the windows version of magicISO, and install it with wine (right click file. and select open with wine application launcher) . I would then use magicISO to convert the uif to an iso, so you can easily use it in almost all programs that mount images.

have fun,

i have wine installed =)

so download the exe run it through wine to my partition and whambam thank you mam?

how do i install mint 7 to a hard drive from a flash drive? if its possible and easy as making a install disk? note~ there is no other OS on the hard drive

---

### Post by jake16424 on 2009-06-25
> **Tyke91 said:**
> the last part is an empty directory. 

EASIEST way to do this
```
sudo mkdir /mnt/iso
sudo mount -o loop /media/movies/Games/cod4.uif /mnt/iso

```the first command makes an empty directory, /mnt/iso. the second command actually mounts it to that iso file in media.

later on, you will want to 
```
umount /mnt/iso
```

you can then use the same mountpoint later on.

mkdir: cannot create directory `/mnt/iso': File exists

---

### Post by doas777 on 2009-06-25
> **jake16424 said:**
> mkdir: cannot create directory `/mnt/iso': File exists
just skip the first line of code. you need to do it the very first time, but not on subsequent mounts, since the directory already exists.

on the magicISO thing, yes, i have been lead to believe that it is just that easy. I havn't ever worked with that format (or magiciso in wine) so i cannot personally attest.

---

### Post by jake16424 on 2009-06-25
> **doas777 said:**
> from what i'm seeing [here]("http://ubuntuforums.org/showthread.php?t=513089") and [here]("http://onubuntu.blogspot.com/2007/11/dealing-with-uif-files.html"), uif files only work with magicISO, but they say it runs well in wine. 

you could install wine if you so choose, by entering at a terminal:
```
sudo apt-get install wine
```


after that, just download the windows version of magicISO, and install it with wine (right click file. and select open with wine application launcher) . I would then use magicISO to convert the uif to an iso, so you can easily use it in almost all programs that mount images.

have fun,

used wine to install magic iso,

instaled it, but no shortcut and no idea where it installed. 

said C drive but there is no drive labled C on my computer, i formatted that when i got familuar with mint 7, so i have no clue how to get to magic iso now haha... 

*cant wait to install windows an use virtual box to handle my gaming needs

---

### Post by doas777 on 2009-06-25
> **jake16424 said:**
> used wine to install magic iso,

instaled it, but no shortcut and no idea where it installed. 

said C drive but there is no drive labled C on my computer, i formatted that when i got familuar with mint 7, so i have no clue how to get to magic iso now haha... 

*cant wait to install windows an use virtual box to handle my gaming needs

look in your application menu. there should be a sub-menu for wine. you can use it to browse your virtual c drive (it's located at ~/.wine/drive_c/ ), or launch most programs installed into wine. 

if you can't find a menu, go to ~/.wine/drive_c/Program Files/ and look for your app directory. you can launch the app by rclicking and selecting open with wine, or you can create a launcher, and adding 'wine ' to the beginning of the command.

---

### Post by jake16424 on 2009-06-25
> **doas777 said:**
> look in your application menu. there should be a sub-menu for wine. you can use it to browse your virtual c drive (it's located at ~/.wine/drive_c/ ), or launch most programs installed into wine. 

if you can't find a menu, go to ~/.wine/drive_c/Program Files/ and look for your app directory. you can launch the app by rclicking and selecting open with wine, or you can create a launcher, and adding 'wine ' to the beginning of the command.

hmm,, and to think i didn't even think to look in there.. >.>

ok thank you.

quick ? is the virtual C drive on my flash drive ( my jump disk is where linux is and its only a 1gig... )


ok i found it =-), but it says i must "run as administrator" Right click on MAGICDISK.exe on windows explorer and click 'Run as administrator'

any ideas?

---

### Post by Tyke91 on 2009-06-25
[quote=jake16424]mkdir: cannot create directory `/mnt/iso': File exists[/quote]

heh... did not anticipate that :)

now that you have that file, you can re-use it.

also, it is my understanding now that uif is an evil format that can only be read by magiciso (so much for being universal :P )

If you are doing this all from a live USB environment, you might not have enough space to do so...

---

### Post by doas777 on 2009-06-25
> **jake16424 said:**
> hmm,, and to think i didn't even think to look in there.. >.>

ok thank you.

quick ? is the virtual C drive on my flash drive ( my jump disk is where linux is and its only a 1gig... )

'~' always refers to your logged in user's home directory. if i am logged in as steve, then ~ is the same as /home/steve 

your .wine directory is whereever your /home/<username> directory is, so it's probably on your flash.

ps: just hit alt+F2, and paste in 
```
~/.wine/drive_c
``` and it should take you right there. you could also paste it into the address bar in nautilus.

---

### Post by jake16424 on 2009-06-25
> **doas777 said:**
> '~' always refers to your logged in user's home directory. if i am logged in as steve, then ~ is the same as /home/steve 

your .wine directory is whereever your /home/<username> directory is, so it's probably on your flash.

ps: just hit alt+F2, and paste in 
```
~/.wine/drive_c
``` and it should take you right there. you could also paste it into the address bar in nautilus.

ok, well how do i run the program Magic iso as ADMIN, as it wants? i had group selected as ADMIN but it has no effect.

---

### Post by doas777 on 2009-06-25
> **jake16424 said:**
> ok, well how do i run the program Magic iso as ADMIN, as it wants? i had group selected as ADMIN but it has no effect.

hmmm. don't know that one. you could put 'gksu' in front of the wine command, to give it linux admin capacity, but that may not do the trick, as wine may or may not realize that you need admin. 

create a launcher to run the app with wine, and add 'gksu ' in front of wine. may work.

---

### Post by jake16424 on 2009-06-25
> **doas777 said:**
> hmmm. don't know that one. you could put 'gksu' in front of the wine command, to give it linux admin capacity, but that may not do the trick, as wine may or may not realize that you need admin. 

create a launcher to run the app with wine, and add 'gksu ' in front of wine. may work.

it put a launcher on the desktop

so it will look like this

[COLOR="Red"]gksu env[/COLOR] WINEPREFIX="/home/mint/.wine" wine "C:\PROG~FBU\MAGI~MZO\MagicDisc.exe" 

from this?

WINEPREFIX="/home/mint/.wine" wine "C:\PROG~FBU\MAGI~MZO\MagicDisc.exe"

---

### Post by doas777 on 2009-06-25
> **jake16424 said:**
> it put a launcher on the desktop

so it will look like this

[COLOR=Red]gksu env[/COLOR] WINEPREFIX="/home/mint/.wine" wine "C:\PROG~FBU\MAGI~MZO\MagicDisc.exe" 

from this?

WINEPREFIX="/home/mint/.wine" wine "C:\PROG~FBU\MAGI~MZO\MagicDisc.exe"

put the gksu right in front of the wine:
```

[COLOR=Black]env[/COLOR] WINEPREFIX="/home/mint/.wine" [COLOR=Red]gksu [/COLOR]wine "C:\PROG~FBU\MAGI~MZO\MagicDisc.exe" 

```

---

### Post by jake16424 on 2009-06-25
> **doas777 said:**
> put the gksu right in front of the wine:
```

[COLOR=Black]env[/COLOR] WINEPREFIX="/home/mint/.wine" [COLOR=Red]gksu [/COLOR]wine "C:\PROG~FBU\MAGI~MZO\MagicDisc.exe" 

```

now it doesn't even try to launch =(

hmm.. well i installed on my hdd , just found out how =-)

---

### Post by jake16424 on 2009-06-25
can someoen explain to a newbie how to mount a ISO image using terminal or some other very simple way?

im working on installing windows vista in virtualbox but it wont be ready until tomorrow..

---

### Post by doas777 on 2009-06-26
> **jake16424 said:**
> can someoen explain to a newbie how to mount a ISO image using terminal or some other very simple way?

im working on installing windows vista in virtualbox but it wont be ready until tomorrow..


the mount command on the previous page is how you do that. the problem is that you have an proprietary image file (.uif). if you have an .iso to mount, just follow the instructions posted by [Ocxic]("http://ubuntuforums.org/member.php?u=47233") on page 1 of this thread.

---

### Post by Greyfox_75 on 2009-06-26
I think I have a better way for you to mount this UIF file.  In terminal

sudo apt-get update
sudo apt-get install build-essential

Then go to [http://lapismanalis.freehosting.net/beos/](http://lapismanalis.freehosting.net/beos/) and download all2iso-0.2.zip to your home directory and then run

unzip all2iso-0.2.zip
cd all2iso/src
gcc uif2iso.c -o uif2iso
./uif2iso /path/to/your/uiffile.uif /where/youwantto/save/isofile.iso

As for the mounting procedure its pretty simple.  In the linux virtual filesystem you dont seperate your drives like you do in windows there is no C drive no D drive etc.  Your root drive (where you installed linux to) is mounted to / and if you want to mount any other drives they get mounted to folders in /  So when he told you to "mkdir /mnt/iso" you made an empty folder that you could mount your iso to.

sudo mount -o loop /home/joe/isos/awesomefilm.iso /mnt/iso

This is saying mount the file /home/joe/isos/awesomefilm.iso to the folder /mnt/iso with the special option loop (needed for mounting files instead of devices like normal)

So after you have run this command you can open your file browser and go to /mnt/iso and inside of that once empty folder you will now find all of the files that are in your iso image.

---

