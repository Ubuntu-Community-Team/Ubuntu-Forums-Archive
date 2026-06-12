---
title: "Trouble finding Nvidia drivers"
date: 2010-11-26
forum: General Help
---

### Post by igotsanevo4g on 2010-11-26
First off, this is my GPU. (if you need more info, maye i grabbed the wrong info let me know what i need to get, im a noob still haha)

 description: VGA compatible controller
                product: NVCrush11 [GeForce2 MX Integrated Graphics]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: b1
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-2.0 vga_controller bus_master cap_list

Well im having some trouble finding drivers for it, i understand its pretty old but i cannot find it on the nvidia website (maybe its there and im just dumb lol)

Is there another way to get them?

Thanks

Update -

I have the drivers downloaded its labeled this

 NVIDIA-Linux-x86-96.43.19-pkg1.run 

How do i install it?

and how do i install tar.gz files?

AND also ive found this link on nvidia forums for how to install in ubuntu, but dont understand it much... heres the link.

[http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)

---

### Post by emoguitarist06 on 2010-11-26
> **igotsanevo4g said:**
> 

I have the drivers downloaded its labeled this

 NVIDIA-Linux-x86-96.43.19-pkg1.run 

How do i install it?

and how do i install tar.gz files?

AND also ive found this link on nvidia forums for how to install in ubuntu, but dont understand it much... heres the link.

[http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)

**#1** That forum is outdated.
but run these codes
```
cd <directory of download>
sh ./NVIDIA-Linux-x86-96.43.19-pkg1.run 
```

**#2** tar.gz files is just a compressed folder like .7z or .zip
so you'll need to extract it (right click-extract here) and most will come with instructions on how to install :)

**[COLOR="Red"]#3[/COLOR]** In your Ubuntu machine have you tried System>Administration>Additional Drivers
??
That is the recommended way of installing the Nvidia driver
(granted it's typically not the absolute newest by maybe a couple of months but the version that Ubuntu includes will typically work without frustrations)

---

### Post by igotsanevo4g on 2010-11-26
> **emoguitarist06 said:**
> **#1** That forum is outdated.
but run these codes
```
cd <directory of download>
sh ./NVIDIA-Linux-x86-96.43.19-pkg1.run 
```

**#2** tar.gz files is just a compressed folder like .7z or .zip
so you'll need to extract it (right click-extract here) and most will come with instructions on how to install :)

**[COLOR="Red"]#3[/COLOR]** In your Ubuntu machine have you tried System>Administration>Additional Drivers
??
That is the recommended way of installing the Nvidia driver
(granted it's typically not the absolute newest by maybe a couple of months but the version that Ubuntu includes will typically work without frustrations)

Thanks for the heads up on the .tar stuff.

Went to check for additional drivers, and some might be installed but they are pretty **** poor compared to how it is when i boot Xp. Maybe installing these will help? I dont know, i hope i dont mess something up haha.

Also i ran those commands and it said i needed to be logged on as root. I dont know the commands to allow that, i know that a sudo should be in there somewhere tho.. lol

thanks for the help so far man :D

---

### Post by igotsanevo4g on 2010-11-26
Bump.

---

### Post by mikewhatever on 2010-11-26
You might be hitting the known bug.
[https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Graphics%20and%20Display](https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Graphics%20and%20Display)
> The new Xorg 1.9 available in Maverick is not compatible with nVidia based chipsets that use the (nvidia-96) and (nvidia-173) drivers. (626974) 

Nvidia didn't make the driver for your card that works with Xorg 1.9. You should be able to use Lucid and get the driver from the repositories.

---

### Post by igotsanevo4g on 2010-11-26
> **mikewhatever said:**
> You might be hitting the known bug.
[https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Graphics%20and%20Display](https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Graphics%20and%20Display)


Nvidia didn't make the driver for your card that works with Xorg 1.9. You should be able to use Lucid and get the driver from the repositories.

Meaning revert from 10.10 to lucid?

Besides i dont think that i have those nvidia cards, i think...

---

