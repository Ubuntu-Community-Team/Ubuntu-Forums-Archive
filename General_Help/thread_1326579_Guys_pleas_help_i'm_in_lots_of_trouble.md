---
title: "Guys pleas help i'm in lots of trouble"
date: 2009-11-14
forum: General Help
---

### Post by spikeyross on 2009-11-14
Basically i got a new netbook yesterday and put the new Ubuntu on it along side windows 7

Basically it really didnt work
and deleted windows 7 

now the sound doesnt work on Ubuntu
and the download centre doesnt work so i can't download anything 

If i could fix these then i could keep Ubuntu

but my grampa bought me this netbook yesterday and i feel like an idiot

Please help guys

Thanks Ross

---

### Post by coldReactive on 2009-11-14
What netbook is it? (You won't be able to get windows back regardless, unless you made a back up with the company's back up creator.)

---

### Post by jeb800e on 2009-11-14
You don't have a "rescue disk" type disk or thumb drive or something that came with your netbook?

---

### Post by coldReactive on 2009-11-14
> **jeb800e said:**
> You don't have a "rescue disk" type disk or thumb drive or something that came with your netbook?

They don't make these anymore, companies are cutting back on this so that people can mess up and they can laugh at you since you didn't know about the recovery disk creators they install in windows (IE: Like Gateway does now.)

---

### Post by jeb800e on 2009-11-14
Also, did you set Ubuntu to remove your Windows partition when you installed it? Some of the files may have just been jumbled around and Windows may very likely still be in your system if that is the case.

---

### Post by spikeyross on 2009-11-14
Its a Acer aspire one
when i turn it on it goes straight onto Ubuntu
before i reinstalled ubuntu it gave me the option of ubuntu or windows 7 now it doesn't

and i didn't make a backup

any suggestions

---

### Post by spikeyross on 2009-11-14
anyway
if you guys can get my sound to work and it to download programs off the centre then 5 stars from me 
I feel really crap right now

---

### Post by mike555 on 2009-11-14
If you don't have internet maybe you can plug into a friends ethernet cable from their modem and download the needed drivers or whatever .........

---

### Post by spikeyross on 2009-11-14
No i have Internet and the Wifi works

---

### Post by mike555 on 2009-11-14
once you get internet you can download "GParted" and use it to see if you still have the Windows partition .....

---

### Post by spikeyross on 2009-11-14
when i go into the Ubuntu software centre
everything is 
"not available in the current data"

---

### Post by spikeyross on 2009-11-14
Ok
Update Manager worked and is currently installing  57 updates

---

### Post by Monotoko on 2009-11-14
go to terminal and run

```
sudo fdisk -l
```

then post the output here
this will tell me if your windows partition is there or not

no need for any of this gparted rubbish ^.^ (sorry GUI fans...huge fan of CLI here :P)

---

### Post by mike555 on 2009-11-14
try the Synaptic package manager , enter your password and click on "reload" ....... then type gparted in the search box , put a check in the little box next to gparted ,then click apply .........

---

### Post by spikeyross on 2009-11-14
I'll try both of those things in a minute once these Updates install

---

### Post by Monotoko on 2009-11-14
you dont need to wait for the updates to run fdisk

fidsk also has the advantage that there can be no going wrong, its a simple copy and paste here, then i read it ^.^

---

### Post by mike555 on 2009-11-14
of course you might check that the speakers are not muted and are turned up ,

---

### Post by Onesimus on 2009-11-14
Sometimes it doesn't see the operating system even though it may be there still intact.

Have you tried typing:  

```
sudo update-grub
```

at the terminal.  This will update grub and you maybe able to see Windows 7.

---

### Post by spikeyross on 2009-11-14
when it asks for my password
the password is Q
it doesnt accept any letters

---

### Post by Monotoko on 2009-11-14
just type it in and press enter, its a security feature, it doesnt look like its accepting letters but it is

---

### Post by coldReactive on 2009-11-14
> **spikeyross said:**
> when it asks for my password
the password is Q
it doesnt accept any letters

That's normal, the cursor will not produce any characters when running sudo in terminal.

---

### Post by Onesimus on 2009-11-14
> **spikeyross said:**
> when it asks for my password
the password is Q
it doesnt accept any letters

You shouldn't tell anyone your password, and it should be at least 8 characters long.

If you have typed that in at the terminal, then it won't show you any letters at all. You just type away and press return.

---

### Post by spikeyross on 2009-11-14
sudo update- grub was fine
when i done fdisk it came up with the error
fdisk : invaild option -- "1"

---

### Post by coldReactive on 2009-11-14
> **spikeyross said:**
> sudo update- grub was fine
when i done fdisk it came up with the error
fdisk : invaild option -- "1"

That's because you ran a 1 instead of a lowercase L.

---

### Post by spikeyross on 2009-11-14
Ok no windows 7 then
Linux
Extended 
and Linux swap / solaris

Basically any opinions on 
how to get the sound to work
and how to get youtube videos to work

Can i donate to this forum?

---

### Post by coldReactive on 2009-11-14
For youtube:

sudo apt-get install flashplugin-nonfree

---

### Post by Monotoko on 2009-11-14
for sound troubleshooting, this will be able to help you more than i ever could:

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

and it is possible to make donations to ubuntu, here: [http://www.ubuntu.com/community/donations](http://www.ubuntu.com/community/donations)

---

### Post by Perturbed Penguin on 2009-11-14
I have heard that some people are having an issue w/ Karmic where when they upgrade to Karmic the kernal is an old kernal version and it is related to Grub somehow... symptoms include not being able to download through software center and odd Grub(boot) issues if I remember correctly. I don't have time to look for the post I was reading on this at the moment but later today perhaps I'll be able to give you some links. I don't know if this is related at all but it sounds familiar. In the meantime you may want to search this forum for something to the effect of Grub/Grub2 kernal issues, can't install apps through software center, etc. Sorry I'm not being particularly helpful... g2g. Hope this helps a bit and good luck!! ;)

---

### Post by spikeyross on 2009-11-14
Is there anyway to specifically donate to this forum

Thanks SO MUCH guys
You have pretty much saved this laptop

---

### Post by deusdiabolus on 2009-11-14
As far as getting flash videos to work, you'll probably need to install the[ restricted extras package]("http://hacktolive.org/wiki/Ubuntu-restricted-extras").  As far as your sound...[check this thread]("http://ubuntuforums.org/showthread.php?t=205449").

---

### Post by Monotoko on 2009-11-14
Well, the forum is run by the ubuntu staff, so it goes to the same people

---

### Post by spikeyross on 2009-11-14
any im chat recommendation for Ubuntu ?
ones that work with webcam and msn ?

---

### Post by coldReactive on 2009-11-14
> **Monotoko said:**
> Well, the forum is run by the ubuntu staff, so it goes to the same people

I think the user wants one of those fancy shmancy forum donator things below the username

> **spikeyross said:**
> any im chat recommendation for Ubuntu ?
ones that work with webcam and msn ?

Empathy, installed by default in 9.10, should have voice and video chat. But you BOTH need to be able to do voice/video, you can't do it one way like MSN.

---

### Post by 23dornot23d on 2009-11-14
Sorry ... posted after reading first page .... my bad

---

### Post by spikeyross on 2009-11-14
Thanks guys for all your help
I reeeealy appreciate it
I really don't know what i would have done without you
Thanks again 
Ross

---

### Post by Monotoko on 2009-11-14
No worries, its what were here for :)

If your problem is solved, click "Thread Options" (at the top) and them click "Mark as solved" so everyone knows its solved if they have the same problem ;)

---

### Post by 23dornot23d on 2009-11-14
> **spikeyross said:**
> Ok no windows 7 then
Linux
Extended 
and Linux swap / solaris

Basically any opinions on 
how to get the sound to work
and how to get youtube videos to work

Can i donate to this forum?




Just a quick question here ,,,,, is that a typo ..........

Ok no windows 7 then
Linux

__________________________________________________________

Did you mean to type NOW ,,,,, instead of NO ......... just seems odd to me the way you wrote it ......

---

### Post by coldReactive on 2009-11-14
> **23dornot23d said:**
> Just a quick question here ,,,,, is that a typo ..........

Ok no windows 7 then
Linux

__________________________________________________________

Did you mean to type NOW ,,,,, instead of NO ......... just seems odd to me the way you wrote it ......

It's not a typo, the user really meant there was no windows 7.

---

### Post by Monotoko on 2009-11-14
Those are the partitions he found on the drive using fdisk...

Linux
Extended
Linux Swap

---

### Post by 23dornot23d on 2009-11-14
Cheers guys .... it was just using the word he used 


   THEN       ...... that threw me .......

I would have wrote the same as you have just wrote above MONOTOKO ,,,,,, just checking .....

my Acer Aspire had a restore ISO in it thats all ......

---

### Post by spikeyross on 2009-11-14
> **Monotoko said:**
> No worries, its what were here for :)

If your problem is solved, click "Thread Options" (at the top) and them click "Mark as solved" so everyone knows its solved if they have the same problem ;)
Can't see Thread Options ?

---

### Post by coldReactive on 2009-11-14
> **spikeyross said:**
> Can't see Thread Options ?

See the "View First Unread" or the page numbers at the top of the post listing?

There's a "Thread Tools" link. Click it, then click Mark thread as solved.

---

### Post by Perturbed Penguin on 2009-11-15
Glad to hear you got it all figured out!

---

