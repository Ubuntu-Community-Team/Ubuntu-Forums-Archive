---
title: "Widows files onto Ubuntu desktop"
date: 2010-03-09
forum: General Help
---

### Post by yomnym on 2010-03-09
Can i mount the partition on which windows is currently installed in (dual boot, win and ubuntu) and navigate through its folders and take files, eg. pics, songs... to place on my ubuntu desktop.  Just wondering, im trying to get others used to linux enviroment and want to start transfering things wihtout making it too drastic for them.  The process that i described above doesn't have to be exactly like that, but basically anything that gets me similar results.  thanks

---

### Post by Method X on 2010-03-09
> **yomnym said:**
> Can i mount the partition on which windows is currently installed in (dual boot, win and ubuntu) and navigate through its folders and take files, eg. pics, songs... to place on my ubuntu desktop.  Just wondering, im trying to get others used to linux enviroment and want to start transfering things wihtout making it too drastic for them.  The process that i described above doesn't have to be exactly like that, but basically anything that gets me similar results.  thanks

Hi there.
Yes, of course you can.

sudo fdisk -l

You'll see all your partitions.

you must remember one of your windows sda (sdb etc) with number

sudo /etc/fstab

add line:
/dev/sdXX       /mnt/Windows   ntfs,user,noauto,exec           0       0

(sdXX is your sda or sdb)
And don't remember to:
sudo mkdir /mnt/Windows

than try
sudo mount -a
If you can see windows files in /mnt/Windows everything is ok. it will mount windows on every boot

---

### Post by coffeecat on 2010-03-09
> **Method X said:**
> 
add line:
/dev/sdXX       /mnt/Windows   ntfs,user,noauto,exec           0       0


Point of information: you've got a typo in there. There should be a space, not a comma, between ntfs and user, thus:

```
/dev/sdXX     /mnt/Windows     ntfs     user,noauto,exec      0  0
```Personally, I prefer a simple 'defaults' in the options field. It works just fine. Thus:

```
/dev/sdXX     /mnt/Windows      ntfs    defaults       0  0
```

---

### Post by Method X on 2010-03-09
> **coffeecat said:**
> Point of information: you've got a typo in there. There should be a space, not a comma, between ntfs and user, thus:

```
/dev/sdXX     /mnt/Windows     ntfs     user,noauto,exec      0  0
```Personally, I prefer a simple 'defaults' in the options field. It works just fine. Thus:

```
/dev/sdXX     /mnt/Windows      ntfs    defaults       0  0
```

oh, thx, it was my fstab output, but it works.

Anyway, will bookmark your method.
Thanks again.

---

### Post by Elfy on 2010-03-09
First - if your dual boot is actually a wubi install (ubuntu installed inside windows) then the windows drives should be there already under /host(s)

If not, then fstab is the way to go - some more information can be found here - [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131) . You can also use a GUI method with pysdm - search for it in synaptic and mark it for installation or run this in a terminal to install it. 


```
sudo apt-get install pysdm
```

[http://ubuntuforums.org/showpost.php?p=5470813&postcount=1](http://ubuntuforums.org/showpost.php?p=5470813&postcount=1)

Second - if you actually want to see the drive on your desktop in Ubuntu then instead of using /mnt use /media as drives mounted on /media will show on the desktop.

---

### Post by yomnym on 2010-03-09
sorry for the lack of intellect but im very new to linux Os's and i need to follow instructions very well in order to get thigns to work..
 
first:
sudo fdisk -l  (L or i)?
 
then:
see which partition is carrying my windows Os?
 
then: 
sudo /etc/fstab (what does this do, just bring up a certain file? so i could add the following line?
 
/dev/sdXX     /mnt/Windows     ntfs     user,noauto,exec      0  0
 or 
/dev/sdXX     /mnt/Windows      ntfs    defaults       0  0
 
then:
sudo mkdir /mnt/Windows  (what is this for)
 
Again i apologize but im just trying to learn the language so i wont have to be bugging people on the forums any more :lolflag:

---

### Post by Dayofswords on 2010-03-09
for a non CLI

open the file manager and click on the left "XXGB media"

it will ask for your password, type it in

you can now fiddle with windows's files

---

### Post by Elfy on 2010-03-09
No need for apologies - you might be best using the pysdm tool, have a look at your fstab now 

```
cat /etc/fstab
```

run the tool and have another look at the file again.

But to answer it is a lower case L :)

mkdir - creates a folder for the drive to be mounted into
fstab is the file which controls whatt drives are mounted at boot and to where they mount

If you are confused by the output of fdisk then paste it here for us to look at - please though use code tags - that is [noparse]```
 [/noparse] at the start of the paste and [noparse]
``` [/noparse] at the end of the paste.

---

### Post by yomnym on 2010-03-09
so you guys recommend using pysdm tool? do i get this in synaptic?
I'll run cat /etc/fstab and just see what files are currently set to mount? '
 
"Daysofwords" the file manager is synaptic right? so i go to the navagation area or area on the left and select XXGB media"?
 
Also i dont want to always have the Win files mounted, i just want to be able to access it just so i could transfer things back and forth.  
 
Thanks for all your support.

---

### Post by yomnym on 2010-03-09
Guys before i go ahead, cant i just go to Places>Computer>xxx (win7 drive) Just select the partition where i have my windows and go through the docs?  I just did and i was able to see all the files in the Win7 OS.  Does that work?  I really appreciate all your help. Thanks a million.

Daysofwords whats a non CLI, i went to synaptic and couldn't find XXGB media.

---

### Post by Miljet on 2010-03-09
> Guys before i go ahead, cant i just go to Places>Computer>xxx (win7 drive) Just select the partition where i have my windows and go through the docs?
Absolutely, as I read through this post, I couldn't understand why someone didn't suggest it before.

Your file manager is not Synaptic. Synaptic is a download manager similiar to Software Center. The file manager is the "Places" menu as you have discovered. It is confusing that it isn't marked as File Manager since everyone refers to it as such.

CLI stands for Command Line Interface, which is where you are when using the terminal.

---

### Post by yomnym on 2010-03-09
Thanks alit miljet, so then file manager is places, that's where you obviously manage your files.  Thanks alot for the explanation of CLI. I really appreciate everyones help, it has been most informative and helpful.

---

