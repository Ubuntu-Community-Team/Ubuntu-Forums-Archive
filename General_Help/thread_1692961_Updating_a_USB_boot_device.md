---
title: "Updating a USB boot device"
date: 2011-02-22
forum: General Help
---

### Post by ArthurDent123 on 2011-02-22
Hello,

I recently created a USB boot stick so that I could have Linux in my pocket wherever I went. This was a great success.

I put Ubuntu 10.10 on to a 2Gb USB stick and it works just fine. I always like to keep my software up to date and so I thought I would run the update manager. I forget the exact numbers, but it told me that I had about 320 updates pending which required about 280Mb. Whatever the numbers, it was far less than the 1.1gb reported free space on the USB device. So I went ahead. Not long into the install process I got "low on disc space" warnings and finally the update crashed. The update was incomplete - neither apt-get clean or apt-get --fix-broken would work and the device would n longer boot.

So I recreated the USB boot drive and started again. This time I tried to do the updates in batches of 10 or so with apt-get clean in between each. Eventually I ran into the same problem.

Now - I thought that as I was just *updating* software already on the USB (not installing new stuff) that on completion, the disc space usage would be roughly the same. Is this not the case?

I can understand that as each package is downloaded, unpacked and installed there will be a temporary surge in disc space usage, but surely once installed and "cleaned" the net usage should be about the same. Or are the files stored in compressed format on a USB boot drive and when I update the S/W they are uncompressed?

My question boils down to this:
a) Is it possible to update a USB Boot system on a 2gb USB stick?
b) If not would a 4gb device work (I have one but don't want to waste it if I will run into the same problem).
c) Is there any other way of doing this? I wonder for example if it is possible to create a USB Boot device from an up-to-date Ubuntu system already installed on a PC?

Thanks in advance for any help or suggestions.

Mark

---

### Post by Hippytaff on 2011-02-22
You can do c) by using [remastersys]("http://en.wikipedia.org/wiki/Remastersys") to create an ISO of an updated system.
 
To upgrade a usb install I'm not sure if the install has to be [persistent]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent")?

---

### Post by HermanAB on 2011-02-22
Howdy,

Don't fix it if it ain't broke...

The USB system works right?  So an update can only leave it the same or worse - it can't make it better. 

Also, you typically don't have any room to waste on a stick. So the best policy is hands off.

---

### Post by Hippytaff on 2011-02-22
> **HermanAB said:**
> Howdy,
 
Don't fix it if it ain't broke...
 

 
If you don't break it you can't fix it ;-)

---

### Post by TechnikAlsace on 2011-02-22
The downloaded and compressed updates are kept in an application cache which is the most probable cause for your disk space problem. There are GUI tools like *Ubuntu Tweak* which allow cleaning up all this. So you may install a part of the updates, clean up the packet cache, install the next part and so on.

---

### Post by oldfred on 2011-02-22
A USB install flash drive has the ISO file, but downloaded data goes into the persistence location.

You can do a full install into a 4GB but you have limited room to work as it ends up over 3GB. You have to constantly houseclean and maybe downgrade to smaller packages. 

If you want a full Ubuntu install 8GB or large works well. Flash drive have become relatively cheap at about US$1.50 per GB. I have seen unbranded 16GB for just over $20 on sale.

---

### Post by ArthurDent123 on 2011-02-22
> **oldfred said:**
> A USB install flash drive has the ISO file, but downloaded data goes into the persistence location.
.

Ahhh - That makes sense. Thank you for the explanation.

> **HermanAB said:**
> 
The USB system works right?  So an update can only leave it the same or worse - it can't make it better. 

Also, you typically don't have any room to waste on a stick. So the best policy is hands off.


When I opened this thread I was determined to find a way to make this work, but the more I think about it the more I am coming around to HermanAB's way of thinking. I have a working system in my pocket. So what if a few of the packages aren't bleeding edge?

Thanks to everyone for their input...

Cheers

Mark

---

### Post by C.S.Cameron on 2011-02-22
Do not try to update a persistent install, it will quickly fill the device, even if it is 16GB and the kernel is frozen inside a squash file.

If you want to update and upgrade do a full install. For this a 4GB drive is minimum.

---

