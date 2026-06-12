---
title: "New to Ubuntu(I have some questions)"
date: 2011-03-26
forum: General Help
---

### Post by TheJuggernaut on 2011-03-26
Hi guys first let me tell you that this rockz:guitar: is an awesome OS.

i did the switch yesterday and im pretty newb if not NOOB to it so lets get it by parts 

How do i create an iso. backup of my sistem?

I mean to be later stored on a usb using liveusb creator or comanding some stuff (Googling how to)

I know some will tell me to use Remastersys, but it wont install, i get a inssatifaction error
:dialog, or something like that


Thx :KS

---

### Post by linuxuser12345 on 2011-03-26
You don't have to create an iso backup of your system. Go to the Ubuntu Software Center, and type in "Deja Dup Backup" and install it. With Deja Dup, you can decide which folders you want to back up (like your home folder), and if anything goes wrong with your system, reinstall ubuntu and Deja Dup, and click the "Restore" button with the medium you backed it up plugged in.

---

### Post by TheJuggernaut on 2011-03-26
Thanks for the quick response
im using ubuntu 8.0.4 TSL Where can u found software center? it seems not to be there excuse my ignorance if it is

---

### Post by DeMus on 2011-03-26
> **linuxuser12345 said:**
> You don't have to create an iso backup of your system. Go to the Ubuntu Software Center, and type in "Deja Dup Backup" and install it. With Deja Dup, you can decide which folders you want to back up (like your home folder), and if anything goes wrong with your system, reinstall ubuntu and Deja Dup, and click the "Restore" button with the medium you backed it up plugged in.

Can it also backup the running system folders, or just /home?

---

### Post by TheJuggernaut on 2011-03-26
Wait its not the same as synaptic?

---

### Post by TheJuggernaut on 2011-03-26
No its not there but i found it by Googling and i downloaded it

Wich bring me to my other question......

How do I install a tar.bz2 or tar.gz

i can take out the content but i dont see any intaller?

---

### Post by newbuntuxx on 2011-03-26
Here are some useful commands for untaring an archive:

- If the extension is .tar only, then you can untar it like this:

```
tar -xvf filename.tar
```

x for extract, v for verbose, f for file name follows

- If the extension is .tar.gz (an archive compressed with gzip), then use:

```
tar -xvzf filename.tar.gz
```

x for extract, v for verbose, z for gzip, f for file name follows

- If the extension is tar.bz2 (an archive compressed with bzip2) then use:

```
tar -xvjf filename.tar.bz2
```

Can you cd into the directory that you extracted and post the output of:
```
ls -lah
```

Or post the link to where you downloaded the archive from.

Usually with tar balls, you will need to give permission to the installer/config script first. Then execute it like this:

```
./install_config_script
```

There should be a readme.txt file in the archive which will detail how to go about installing it.

---

### Post by newbuntuxx on 2011-03-26
> **TheJuggernaut said:**
> Wait its not the same as synaptic?

The Ubuntu Software center was released in 9.10 I believe. So, if you have 8.04 installed then you won't see it. 

Synaptic and the ubuntu software center pretty do the same thing. However, the Ubuntu Software Center hides a lot of the details that may confuse beginners. 

I recommend that you upgrade to the latest build of Ubuntu (10.10).

---

### Post by linuxuser12345 on 2011-03-26
> **TheJuggernaut said:**
> Thanks for the quick response
im using ubuntu 8.0.4 TSL Where can u found software center? it seems not to be there excuse my ignorance if it is
I would suggest upgrading to a newer version of Ubuntu, like 10.04.2 LTS, or 10.10

---

### Post by TheJuggernaut on 2011-03-26
> **linuxuser12345 said:**
> I would suggest upgrading to a newer version of Ubuntu, like 10.04.2 LTS, or 10.10

Sorry i couldnt my pc would die if I

trust me it did 

it got stucked on exiting bus  stuff and nothing happened if i will i need ti backup my system if something goes wrong again

---

### Post by TheJuggernaut on 2011-03-26
so how to install Remastersys its the way i see

---

### Post by searchfgold6789 on 2011-03-26
Well, apparently you currently have downloaded a Source Archive of Deja Dup - The raw code straight from the developers - and going about installing things from source can sometimes be a lengthy and difficult process, not for Ubuntu beginners.
Since Ubuntu 8.04 is no longer supported by Canonical, I would not be surprised if you had some trouble installing software from Synaptic - This is because Synaptic tries to connect to the Ubuntu 8.04 Server which is no longer supported, as mentioned. You could try it anyway, though - just look in the applications menu for Synaptic Package Manager.
So, I would instead try to install a newer version of Ubuntu like 10.04 or 10.10, or if you can't maybe you could try a different variant like Xubuntu or even a whole other distro like Fedora or Lubuntu.
Good luck,
 - search

---

### Post by TheJuggernaut on 2011-03-26
And what about Puppy?
i had it but idk how to do some stuff so i switched

---

### Post by newbuntuxx on 2011-03-26
> **TheJuggernaut said:**
> Sorry i couldnt my pc would die if I

trust me it did 

it got stucked on exiting bus  stuff and nothing happened if i will i need ti backup my system if something goes wrong again

Have you tried upgrading to 8.10? 9.04? 9.10?

Download the afore-mentioned ISOs, burn them to a cd or a usb stick (instructions are at Ubuntu.com) and boot from them. If you are able to boot the live CD of those versions, then installation will be fine.

You can also post any errors that you get and people here will help.

In addition, if you find that you can boot the live CD of one of the latter versions, then you can simply use gpart 

```
sudo apt-get install gpart
```

to create a new partition or re-size your existing partition to make room for a new one. And then you can try installing another version of Ubuntu on that newly created partition. That way, if the installation fails, you would still have a working Ubuntu system and at the same, you can troubleshoot the failing inst allation. Note that different Linux installations can use the same swap partition (not concurrently of course). So, you don't need to create a swap partition for the other Ubuntu installation.

If you have any questions, post away.

---

### Post by TheJuggernaut on 2011-03-26
I mean lucyd Puppy is based on 10.10 or 10.04 
RIGHT?
so idk It was easy to use but idk if .db packages would work

---

### Post by newbuntuxx on 2011-03-26
> **TheJuggernaut said:**
> And what about Puppy?
i had it but idk how to do some stuff so i switched

If this is your first time moving to a Linux system, then you should definitely stick with Ubuntu for now. Get your feet wet first, then you can move on to other distributions, which have a smaller community and are a bit more technical than Ubuntu. 

Since this is a new experience for you, there is a bit of a learning curve that you need to put up with. This learning curve is not as steep (well, the tangents of the curve!) when using Ubuntu.

Puppy is good for old hardware, or hardware with really low resources.

---

### Post by newbuntuxx on 2011-03-26
> **TheJuggernaut said:**
> I mean lucyd Puppy is based on 10.10 or 10.04 
RIGHT?
so idk It was easy to use but idk if .db packages would work

I think you mean: Ubuntu 10.04 LTS (Lucid Lynx)

Here is a list of some of the Ubuntu releases:

 Ubuntu 8.04 LTS (Hardy Heron)
 Ubuntu 8.10 (Intrepid Ibex)
 Ubuntu 9.04 (Jaunty Jackalope)
 Ubuntu 9.10 (Karmic Koala)
 Ubuntu 10.04 LTS (Lucid Lynx)
 Ubuntu 10.10 (Maverick Meerkat)

Which ones have you tried? Which ones worked? Which ones failed?

---

### Post by TheJuggernaut on 2011-03-26
Gutsy
Hardy

above havent im afraid of having to unstall gutsy and then update again
so can i stick to
HARDY?

---

### Post by TheJuggernaut on 2011-03-26
thx guys but i would like to create an iso of it

id how

---

### Post by newbuntuxx on 2011-03-27
To burn an Ubuntu CD:

    Insert a blank CD into your burner. A 'CD/DVD Creator' or 'Choose Disc Type' window might pop up. Close this, as we will not be using it.

    Look for the downloaded ISO image in the file browser.
    Right click on the ISO image file and choose 'Write to Disc'.
    Where it says 'Write disc to', you may have options such as 'File image' as well as your CD drive. Choose your CD drive. Your CD drive may show as something like 'BD-MLT UJ-210S'

    Select the write speed. If you are burning an Ubuntu Live CD (one that you may want to boot from), it is recommended that you write at the lowest possible speed.
    Start the burning process.
    After burning is completed, verify that your CD contains multiple files and folders and not just the ISO file. This way you will know the process was completed correctly.

---

