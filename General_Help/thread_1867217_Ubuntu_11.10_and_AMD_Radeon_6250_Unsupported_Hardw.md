---
title: "Ubuntu 11.10 and AMD Radeon 6250 Unsupported Hardware"
date: 2011-10-22
forum: General Help
---

### Post by sweaterman on 2011-10-22
I know there are a few related threads, but none that I have found that address my specific problem and I am quite a newb when it comes to ubuntu.  Still learning the ropes.  

My new netbook is having trouble on startup up Ubuntu and gives a watermark in the lower right hand corner "AMD Unsupported Hardware." It freezes on the login page most of the time (just lucky this time, I think).  Specs below:

Acer - Aspire One AO522-BZ465
AMD Dual Core Processor C-50 (1.00GHz)
AMD Radeon HD 6250
DDR3 1GB
SATA 5400 - 250GB

Need anything else from me?  Thanks in advance for the help!

---

### Post by azomega on 2011-10-25
i have same problem to


my notebook is
Asus A43SA
intel core i5 2430M
VGA AMD radeon graphics HD 6730M (2GB)
ram 4 GB


any one can help us?? please

---

### Post by oldtimer7777 on 2011-10-25
Here is what I would do if I was you.

I would create a USB Live Bootable Stick of Ubuntu 10.10 and see if it still hangs after a while. Boot from that USB stick and see if you still have that error message and try updating the driver on a persistent USB stick.  It looks like there is a bug issue with both of the above laptops and the latest kernel. I'm not sure, but that is how you test it. You can create a Ubuntu 10.10 live USB persistence stick of Ubuntu with Ubuntu Startup Disc Creator. 

> **azomega said:**
> i have same problem to


my notebook is
Asus A43SA
intel core i5 2430M
VGA AMD radeon graphics HD 6730M (2GB)
ram 4 GB


any one can help us?? please

---

### Post by uwabaki on 2011-11-02
i found that setting booting from network to be the first in bios boot settings seems to fix freezing on startup

but the watermark in the lower left corner is annoying
does anybody know how to fix it?

i have 11.8 version of catalyst instaled

edit:  found something that worked here [http://superuser.com/questions/54157/amd-unsupported-hardware-watermark-in-linux-mint]("http://superuser.com/questions/54157/amd-unsupported-hardware-watermark-in-linux-mint")


edit2: it fixed the watermark, but disabled direct rendering, so it rebooted to unity2d

---

### Post by pqwoerituytrueiwoq on 2011-11-02
> **uwabaki said:**
> i found that setting booting from network to be the first in bios boot settings seems to fix freezing on startup

but the watermark in the lower left corner is annoying
does anybody know how to fix it?

i have 11.8 version of catalyst instaled
i saw a script dor this for this it mods the .so file
i gust google a lot of key words i rememberer and fund this script
save it as a .sh file and[FONT=Courier New] chmod+x[/FONT] it and run it with sudo
```
#!/bin/sh 
DRIVER=/usr/lib/xorg/modules/drivers/fglrx_drv.so
for x in $(objdump -d $DRIVER|awk '/call/&&/EnableLogo/{
print "\\x"$2"\\x"$3"\\x"$4"\\x"$5"\\x"$6}'); do  
sed -i "s/$x/\x90\x90\x90\x90\x90/g" $DRIVER
done
```

---

### Post by uwabaki on 2011-11-05
building package from ati driver manualy solves the problem with watermark
you need to install these packages:

debhelper dh-modaliases execstack dpkg-dev

then run 
 
sudo ./ati-driver-installer-11-10-x86.x86_64.run --buildpkg Ubuntu/oneiric

for Ubuntu 11.10

for other distros run 

./ati-driver-installer-11-10-x86.x86_64.run --listpkg

after building you should get 3 packages, install them using

sudo dpkg -i fglrx_8.902-0ubuntu1_amd64.deb fglrx-amdcccle_8.902-0ubuntu1_amd64.deb

I installed these two, reboot and the watermark should disappear

---

### Post by Monemvasier on 2011-11-10
Using Ubuntu 11.10 and having the drivers installed from the Ubuntu distribution, you may want to follow these steps
1. Open a text editor
2. Copy these lines into the editor

#!/bin/sh
#DRIVER=/usr/lib/xorg/modules/drivers/fglrx_drv.so
DRIVER=/usr/lib/fglrx/xorg/modules/drivers/fglrx_drv.so
for x in $(objdump -d $DRIVER|awk '/call/&&/EnableLogo/{print "\\x"$2"\\x"$3"\\x"$4"\\x"$5"\\x"$6}'); do
sed -i "s/$x/\x90\x90\x90\x90\x90/g" $DRIVER
done

3. Save the file  using a name of your choice. Exampe: rmwatermark.sh

4. Open a terminal, get into the folder where you saved the file

5. Make the file executabe:  chmod +x rmwatermark.sh

6: Execute the file:  sudo sh ./rmwatermark.sh

7. Wait until the execution is finished, then reboot.

The watermark is gone. 
It is a good idea to keep this file. If the AMD driver is updated, the watermark will reappear. But now you know how to remove it.

Note: This script is basically the one indicated in several other threads with a modified DRIVER=...  line.

---

### Post by willo24 on 2011-12-19
Many thanks to [Monemvasier]("http://ubuntuforums.org/member.php?u=1491438") who's solution worked perfectly for my new install of 11.10 on an old Asus p5 gdc mx with a Raedon 3650 agp graphics card!

Willo.

---

