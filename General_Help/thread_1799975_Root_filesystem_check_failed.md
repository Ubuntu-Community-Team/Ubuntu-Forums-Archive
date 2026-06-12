---
title: "Root filesystem check failed"
date: 2011-07-08
forum: General Help
---

### Post by Pingui on 2011-07-08
Hi everybody,

I installed a Ubuntu on a HDD, I made a Image of the HDD to put it on a Compact Flash Card.

The transfert works properly good, but when I restart the computer with the Compact Flash Card Ubuntu display this error message (in command line) :

Root filesystem check failed
Ctrl D to retart
#

I have run this 2 commands :
sudo fdisk -l                              => to retrieve the good sda
sudo fidsk -f -y /dev/sda1          => to fix the problem on the sda1

And when I restart the computer the interface gui is not launch, the prompt ask me the user and password.
I try to lunch the startx but It can not start.

Do you I have an idea to fix the problem ?

Thanks you for your help

---

### Post by Blasphemist on 2011-07-08
I'm not sure I understand what you are trying to do. So I'm not sure how to help. What is your goal? Are you trying to be able to boot to ubuntu from either the hdd or the flash card? What preparation of the flash card did you do prior to what sounds like a copy of the disk image to it? What does GParted show on each drive? Please download the bootinfoscript, run it and post the results for us to review. [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

Again, knowing what your desired result is will help. There is a difference in what you describe that you did and what is necessary to make the flash card bootable.

---

### Post by Pingui on 2011-07-08
Thanks Blasphemist for your quick answer.

I have an Acronis Image of an Ubuntu (the source is from a HDD).
I would like to put this image on a Compact Flash Card.

When I put the Image on the Compact Flash Card, I restart the computer and I have the error message.

I will try monday, the GParted, and bootinfoscript, I will put on the forum the result.

---

### Post by Blasphemist on 2011-07-08
When you reboot and get the error, are you using the pc's boot manager in bios to try and boot from the flash card? I started looking at the documentation ([http://www.acronis.com/support/documentation/](http://www.acronis.com/support/documentation/) ) but it will help if you can refer me to the documentation on what process you are using.

---

### Post by Pingui on 2011-07-13
Here we are the results about :

* _the GParted _:

/dev/sda => 7.44 GiB

/dev/sda1 => 3.72 GiB
/dev/sda5 => 3.72 GiB

Partition            ............... FileSystem            ...............           Size            ...............         Used            ..........            Unused            ......       Flags
Unallocated            ..........        Unallocated            ..............          1.00 Mib            .........      --                            ............... -- 
/dev/sda1            ............              ext4            ........................                 3.72 GiB            .........     2.25 GiB            .....      1.47 GiB            ......    boot
/dev/sda2            ............            extended            .................            3.72 GiB            .........      --                            ............... -- 
Unallocated            ..........         Unallocated            ..............         1.00 MiB            .........      --            ...............                 --
/dev/sda5            ............            linux-swap            ...............          3.72 GiB            .........      --            ...............                --

* _the bootinfoscript _:
The result is in the attach file 


Thanks.

---

### Post by Blasphemist on 2011-07-14
I'm not sure that I see the whole results.txt from the bootscript but here goes. I see only 1 "drive". Is this 8GB drive the card or the hdd? The only Ubuntu that I know of that installs that small is Lubuntu. Are you using that or did you somehow get normal Ubuntu to install that small? Are you booting with both "drives" in or just one of them? I just want to be sure if I understand that you are just booting with the card only. 

Please do post the screen from GParted that I asked about. I'd like to see the whole results.txt as from what I see in this one I don't see any errors. In GParted both devices will show if they are both in. I do believe that if you want to boot from the card you will have to use your pc's boot menu and choose usb as the boot device.

---

### Post by Pingui on 2011-07-15
Hi,

All the result is in the file.

There is only 1 drive (the CF) connected to the computer, the 8GB drive is the Compact Flash Card. There is no HDD connecte to the computer.

The Compact Flash is connected to the IDE solt on the MotherBoard, and I just booting with the Compact Flash Card.
I used the Ubuntu 10.0 not the Lubuntu.

You can find in attach the GParted screen.

---

### Post by Pingui on 2011-07-15
Hi,

I worked on it and now I have the prompt user@usr:~$ without the error message Root filesystem check failed. But the interface cannot launch.

When I would like to launch the X-server I have this error message :

Warning GdmLocalDisplayFacotry:maximum number of x display failures reached Checked X server log for errors.

And in the Errors log :

Setting IM through in-switch for local=en_Us
start IM through /etc/X11/xinit/xinput.d/ all_ALL linked to /etc/X11/xinput.d/default

x/o : fatal IO error11(Ressource temporarily unavailable) on x server":5.0" after 20 requests (19 known processed) with 0 event remaining.


Did you see this error message before ?

---

### Post by Blasphemist on 2011-07-15
No, I haven't seen that error. I did google it and there are results but without knowing what you had to do to get to this I didn't have much of idea if anything of help showed up. From this prompt have you tried to start gdm?

---

