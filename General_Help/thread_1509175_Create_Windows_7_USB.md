---
title: "Create Windows 7 USB"
date: 2010-06-13
forum: General Help
---

### Post by lvalen18 on 2010-06-13
You think why would i want to do that.. I fix PC for people sometimes and I aways suggest Ubuntu but their stupid and want Windows.. I lose my W7 DVD a couple of times and im tired of making DVDs when i can just create a Bootable USB but the only thing wrong is that i know of ...you can only create Ubuntu USB in Ubuntu.... In Windows you can create a Windows USB with progrmas and UBuntu as well... SO since windows can make multiple USB bootable...

 Does Ubuntu have a Program that will allow me to Create a Bootable Windows 7 USB?

---

### Post by Ozymandias_117 on 2010-06-13
You can try running Microsoft's program through Wine.

[http://store.microsoft.com/Help/ISO-Tool]("http://store.microsoft.com/Help/ISO-Tool")

The download link, and instructions, are about a quarter of the way down the page.

---

### Post by lvalen18 on 2010-06-14
> **Ozymandias_117 said:**
> You can try running Microsoft's program through Wine.

[http://store.microsoft.com/Help/ISO-Tool]("http://store.microsoft.com/Help/ISO-Tool")

The download link, and instructions, are about a quarter of the way down the page.

I downloaded it but it loads for a few seconds and stops loading and nothing pops up... SO i guess that won't work

---

### Post by wilee-nilee on 2010-06-14
Lets make this simple eh go to a windows computer that you can have admin access to and load the thumb with the MS W7 thumbloader.

---

### Post by LMP900 on 2010-06-14
I've never been able to do it from Ubuntu alone. First you must format it as ntfs and then make it bootable using the bootsect file. After that, you can plug it into Ubuntu and drag the files from the DVD into the flash drive.

Here's the source I roughly followed: [http://kmwoley.com/blog/?p=345](http://kmwoley.com/blog/?p=345)

---

### Post by amedac on 2010-06-14
This is easy. I have done it. 

1. sudo apt-get install gparted
2. open gparted -> format stick to ntfs
                -> put bootable flag (right click in gparted -    manage flags)

3. extract win7.iso to usb stick or if you have live dvd just copy contents to usb stick

---

### Post by LMP900 on 2010-06-15
Thanks amedac. I'm gonna give your suggestion a try. It was always a hassle having to use two computers to perform the task.

---

### Post by demarshall on 2010-06-25
> **amedac said:**
> This is easy. I have done it. 

1. sudo apt-get install gparted
2. open gparted -> format stick to ntfs
                -> put bootable flag (right click in gparted -    manage flags)

3. extract win7.iso to usb stick or if you have live dvd just copy contents to usb stick

Awesome amedac!  That worked for me and it was so easy.  :-)

---

### Post by arpeggi on 2010-07-25
hello,

i've followed these instructions up to trying to extract the windows 7 iso to the usb however when viewing the iso with the archive manager and try to extract to the usb drive all i can see is a readme.txt file containing the message "This disc contains a "UDF" file system and requires an operating system
that supports the ISO-13346 "UDF" file system specification."

any ideas?

---

### Post by CharlesA on 2010-07-25
7zip doesn't support UDF as far as I know.

You'd have the mount the ISO and copy the files from it that way.

---

### Post by Nick_Jinn on 2010-07-25
If I have a version of Windows7 that was intended for my (now dead) Acer laptop, can I copy my windows7 OS to my desktop harddrive and make it bootable and working on my custom build Asus motherboard? I would like to salvage the disk and use it for something....I could also run it as a second OS. 


I dont really use Windows for anything but my web design class and the occasional game, but 7 is a step up from the old XP disk I am currently using for my desktop.

---

### Post by arpeggi on 2010-07-25
will it be sufficient just to copy and paste the files from the mounted iso to the usb in order to make it bootable?

---

### Post by CharlesA on 2010-07-25
> **Nick_Jinn said:**
> If I have a version of Windows7 that was intended for my (now dead) Acer laptop, can I copy my windows7 OS to my desktop harddrive and make it bootable and working on my custom build Asus motherboard? I would like to salvage the disk and use it for something....I could also run it as a second OS. 

If it's an OEM copy (which it is if it came with the machine) you cannot transfer it to a new machine.

I guess you could try it, but it would more then likely not work.

> **arpeggi said:**
> will it be sufficient just to copy and paste the files from the mounted iso to the usb in order to make it bootable?

As long as you set it as bootable when you created the partition, it should be fine. I've always created bootable USB installs of Windows from within Windows, but it should work that way.

---

### Post by Nick_Jinn on 2010-07-25
Swapping works with Windows XP. It wont allow me to download it to another PC but it will still work if you swap the hard drive....neat little secret.

But I dont know if Windows 7 has additional security for that.

---

### Post by arpeggi on 2010-07-25
this is a copy of windows 7 professional iso i downloaded through my university from MSNDAA. it's all above board.

even when i try to mount the iso with archive mounter i'm only seeing the text file. is there another (probably more geeky ;)) way to mount the UDF image and see all the files?

---

### Post by arpeggi on 2010-07-25
ah i'm sorry guys but i admitted defeat and ran away to a windows computer :( thanks for the help nonetheless

---

### Post by Nick_Jinn on 2010-07-25
It could be worse.....Ubuntu is where its at.


But if people think Ubuntu is too hard, give them Mint....it quicker to install....and dont just give people the default install. Set up all of their hardware and download programs you think they will like, download docky or another dock bar for them, install the most eye candy their hardware will support at a good speed, and really rock it.....Dont expect noobs to do everything themselves their first time out.

---

### Post by arpeggi on 2010-07-25
i've been on ubuntu for a year and it's been a great experience. but now i'm going into my final year of uni and i need to write a huge project. openoffice just doesn't cut it i'm afraid and i've not found a good enough alternative to ms word. you've got 30 minutes to find one for me...

---

### Post by princerameses on 2010-07-25
How are you getting the windows 7 iso? Aren't there all kinds of blocks put in place to keep one from illegally making copies? Or am I missing something? :/ 

I would love windows 7.  o_o;

---

### Post by Nick_Jinn on 2010-07-25
I think you can use MS word in Ubuntu with WINE. Am I mistaken?

---

### Post by C.S.Cameron on 2010-07-25
I used the Ngine.de method to make a bootable XP flash drive.
It only boots on the motherboard it was created on.

---

### Post by vega191 on 2010-08-06
```

sudo apt-get install gparted

```
open gparted and format usb drive as nfts
when finished, right click>manage flags and select boot
your flash drive is now bootable

to copy files from your iso just use the mount -o loop method
```
mkdir filesgohere 
mount -o loop someimage.iso filesgohere
```

hope i helped somebody. it would have saved me hours of searching!

---

### Post by Mark Phelps on 2010-08-06
This is all very interesting ... but ... unless I misread the original post, the OP wants a USB from which to RUN Win7, not from which to INSTALL Win7.

As has been discussed on the REAL Win7 forums numerous times, this simply is NOT possible.

MS does not want folks carrying around a portable version of their flagship OS.

---

### Post by SoulSmasher on 2011-02-18
> **amedac said:**
> This is easy. I have done it. 

1. sudo apt-get install gparted
2. open gparted -> format stick to ntfs
                -> put bootable flag (right click in gparted -    manage flags)

3. extract win7.iso to usb stick or if you have live dvd just copy contents to usb stick

I can confirm this method still works. Thanks!

---

### Post by williamts99 on 2011-02-18
Also, once you make your USB stick, if you want to use it for something else, you can use dd to make an image of the memory stick to make it easy to copy back later.  I used this method for a WindowsXP USB installer.

---

### Post by hookitup on 2011-08-31
> **amedac said:**
> This is easy. I have done it. 

1. sudo apt-get install gparted
2. open gparted -> format stick to ntfs
                -> put bootable flag (right click in gparted -    manage flags)

3. extract win7.iso to usb stick or if you have live dvd just copy contents to usb stick


hello when i attempt to extract the file, it works then it gets stuck when trying to extract file "AUDITETW.DLL"  , i look up the archive manage process in system monitoring and it appears to be sleeping .... why is it getting stuck on this file ???



Nevermind it worked, i guess it looked like it was stuck but it wasnt. it just needs time

---

