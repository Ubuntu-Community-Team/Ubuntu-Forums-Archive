---
title: "AE1000 USB Adapter help!!"
date: 2011-04-02
forum: General Help
---

### Post by Matt129 on 2011-04-02
Ok, so ive been trying and trying for the last 5 days to install my  Cisco AE1000 USB adapter but I can't figure it out for the life of me!! I  have read thread after thread but nothing I try works. I even went out  and bought a new adapter in light that linux would recognize and install  it. But to no avail. I have tried many steps over and over but would  not mind trying them again if someone more knowledgeable were to guide  me. I have installed Ubuntu 10.10 off of a live cd so I have run into a  few situations in which it would have worked had I ordered the cd.  Nonetheless im sure someone out there can assist me. You're welcome to  give ANY advice lol.

---

### Post by cbowman57 on 2011-04-02
It's simple but I have to jet, give me about an hour and I'll try to give you the important links & walk you through it.

You might want to search for Ralink 3572 in the mean time.

---

### Post by bkratz on 2011-04-02
> **Matt129 said:**
> Ok, so ive been trying and trying for the last 5 days to install my  Cisco AE1000 USB adapter but I can't figure it out for the life of me!! I  have read thread after thread but nothing I try works. I even went out  and bought a new adapter in light that linux would recognize and install  it. But to no avail. I have tried many steps over and over but would  not mind trying them again if someone more knowledgeable were to guide  me. I have installed Ubuntu 10.10 off of a live cd so I have run into a  few situations in which it would have worked had I ordered the cd.  Nonetheless im sure someone out there can assist me. You're welcome to  give ANY advice lol.


There are step by step instructions in post 4 of below:

[http://ubuntuforums.org/showthread.php?t=1621022](http://ubuntuforums.org/showthread.php?t=1621022)

---

### Post by Spyderkid on 2011-04-02
Here you go....


Step 1)run this to get the driver
```

wget -O ~/Download/RT3572_Linux_STA_v2.5.0.0.DPO.bz2 'http://www.ralinktech.com/download.php?t=U0wyRnpjMlYwY3k4eU1ERXdMekV5THpNeEwyUnZkMjVzYjJGa05qVTFOREF6TURNME55NWllakk5UFQweU1ERXdYekV5TVRWZlVsUXpOVGN5WDB4cGJuVjRYMU5VUVY5Mk1pNDFMakF1TUM1RVVFOD1D'

```
Unpackage the file, and cd into the directory.
```

tar -C ~/Download/ -xf ~/Download/RT3572_Linux_STA_v2.5.0.0.DPO.bz2
cd ~/Download/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/

```

Step 2) Follow the directions in the readme about changing HAS_WPA_SUPPLICANT and HAS_NATIVE_WPA_SUPPLICANT_SUPPORT to "y" in the config.mk file. 
```

sed -ir -e 's/^HAS_WPA_SUPPLICANT=n/HAS_WPA_SUPPLICANT=y/' -e 's/^HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n/HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y/' ./os/linux/config.mk

```

Step 3) Add your Vendor and Product ID to the RT2870 supported list. If your vendor/product ID is different, change it here before you run the command. I'm not sure if lowercase will work, so do all caps just in case. It's HEX, so there are not Letter O's, they are Zeros.
```

sed -ir -e 's!^#endif // RT2870 //!        {USB_DEVICE(0x13B1,0x002F)}, /* Linksys AE 1000 */\n#endif // RT2870 //!' ./common/rtusb_dev_id.c

```

Step 4) then do this....
```

sed -ir -e 's/\tusb_buffer_alloc/\tusb_alloc_coherent/' -e 's/\tusb_buffer_free/\tusb_free_coherent/' include/os/rt_linux.h

```

Step 5) Make and install
```

make && sudo make install

```
There are only two files that are of note:
rt3572sta.ko goes in /lib/modules/`uname -r`/kernel/drivers/net/wireless/
RT2870STA.dat goes in /etc/Wireless/RT2870STA/
The 'make install' should take care of that for you.

Step 6) Create a modprobe.d config file to make sure the modules load. Should also blacklist other conflicting modules:
```

sudo su -c "echo -e 'alias ra0 rt3572sta\nblacklist rt2800usb' > /etc/modprobe.d/rt3572sta.conf"

```
You can add other blacklist modules, here's the list from the Ubuntu page:
rt2870sta, rt2800usb, rt2860sta, rt2x00usb, rt2x00lib, rt2870sta. Now's a good time to check 'lsmod' and unload and blacklist any modules you find. Then run:
```

sudo modprobe ra0
```
You should now have an ra0 device:
```

ifconfig ra0
ra0       Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```
And NetworkManager should have picked it up. If not, try 'sudo ifconfig ra0 up' and 'iwlist ra0 scan'. Should good results.

---

### Post by cbowman57 on 2011-04-02
The cavalry arrived before I could get back on this, great.

Spyderkid, I think I'm going to adopt your method, it looks great.  It is for kernel 2.6.35 & above though so if anyone tries to use it with an older kernel they need to read the fine print in the post bkratz noted in his reply.

---

### Post by Matt129 on 2011-04-02
Whoa holy crap! Haha ive been busy all day and just checked back and BAM all this help. You guys rock! It will take me a while to post any further problems as I have to save all this info to a thumb drive and transfer machines because I do not have internet on my ubuntu desktop (as you can imagine) lol

---

### Post by Matt129 on 2011-04-02
I can just copy and paste these commands into my terminal correct?? Doing so create an error everytime

---

### Post by davidmohammed on 2011-04-02
obviously copy and paste one line at a time...

Which line are you running that gives an error?

Please copy and paste the line and the output including the error here in a reply.

---

### Post by Matt129 on 2011-04-02
When I run the code
sed -ir -e 's/\tusb_buffer_alloc/\tusb_alloc_coherent/' -e 's/\tusb_buffer_free/\tusb_free_coherent/' include/os/rt_linux.hI get 
sed: can't read include/os/rt_linux.h: No such file or directory.

I saved the file in my downloads and have been doing everything from there..Whats wrong here? I do apologize for sounding like such a noob :p

---

### Post by Matt129 on 2011-04-02
For the record..a while back I tried using ndiswrraper and I believe I got it to work. When I check my "Wireless Network Drivers" It says "netr28u" Hardware Present: Yes. So I assume the computer knows my NIC is present...but still no internet. Does that help anything?

---

### Post by davidmohammed on 2011-04-02
> **Matt129 said:**
> When I run the code
sed -ir -e 's/\tusb_buffer_alloc/\tusb_alloc_coherent/' -e 's/\tusb_buffer_free/\tusb_free_coherent/' include/os/rt_linux.hI get 
sed: can't read include/os/rt_linux.h: No such file or directory.

I saved the file in my downloads and have been doing everything from there..Whats wrong here? I do apologize for sounding like such a noob :p

hmmm - looks like the instruction you are using is missing a "./"

try

```
sed -ir -e 's/\tusb_buffer_alloc/\tusb_alloc_coherent/' -e 's/\tusb_buffer_free/\tusb_free_coherent/' ./include/os/rt_linux.h
```

---

### Post by Matt129 on 2011-04-02
After every line I copy and paste I get bash: No such file or directory. Im sick of it! There aren't any specific errors or anything. Just always tells me it can't read the extension

---

### Post by Matt129 on 2011-04-02
Maybe its because I'm having to copy and paste between machines...but still no success

---

### Post by davidmohammed on 2011-04-02
Ok, ignore the altered command I gave you - use the original poster's stuff - n.b. looks like it might have been cribbed from this [forum entry]("http://ubuntuforums.org/showthread.php?t=1507793&page=3").

I think what you may be missing is actually all the stuff to enable you to build correctly - the kernel headers in particular.

try

```
sudo apt-get install build-essential linux-headers-`uname -r`
```

---

### Post by davidmohammed on 2011-04-02
> **Matt129 said:**
> Maybe its because I'm having to copy and paste between machines...but still no success

... might be easier to copy the entire html page to a usb stick and open the html page on your other computer - it should be easier to copy and paste the command entries that way.

---

### Post by Matt129 on 2011-04-02
sudo apt-get install build-essential linux-headers-`uname -r`

matthew@matthew-System-Product-Name:~$ sudo apt-get install build-essential linux-headers-`uname -r`
[sudo] password for matthew: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by Matt129 on 2011-04-02
I did do that. Or try to at least. I still got errors like 'No such directory'. So I started doing it line by line

---

### Post by Matt129 on 2011-04-02
Ok. From the beginning, can anyone give me a more watered down version of what to do?? I understand copy and paste is about as easy as you get. But it's just not working for me and I have no idea why..I have done many of the steps already but will gladly do them over if someone can guide me and not throw it at me. Thank you again guys

---

### Post by Matt129 on 2011-04-06
[FONT=Times New Roman]For the record. I got it workin yesterday. Alls I had to do was take the driver file (which downloaded into my Downloads folder in my home directory) and just move it from inside the Downloads folder to inside the main directory (Where I can access my videos/music/downloads etc...It's your "Home") then once it was moved there (and all three files INSIDE the driver were altered), I just renamed it something that was easy to write, like Cisco. I then opened up my Terminal and did cd (change directory) Cisco. Now my Terminal will execute anything I tell it too from my CISCO folder were my driver is, nowhere else. once I wrote cd Cisco I could then execute "make clean", "sudo make install", then last but not least "sudo modprobe rt3572sta". My NIC was then populated with connections within a few seconds! And this internet is blazing fast! I hope this helps. I spent about three weeks trying to figure this thing out and once someone started helping me I had it running in less than an hour![/FONT]

---

### Post by Yoshis88 on 2011-05-19
So hopefully noone calls me out on digging up an old thread, but it is useful to point out this thread is currently #1 Google hit for "ubuntu natty ae1000" (which is weird considering the original poster specified 10.10)

Personally I found this youtube video to do it for me, even on 11.04 :)
[http://www.youtube.com/watch?v=cwMiHiaWtPI](http://www.youtube.com/watch?v=cwMiHiaWtPI)

I link it here to spread the goodness.

---

