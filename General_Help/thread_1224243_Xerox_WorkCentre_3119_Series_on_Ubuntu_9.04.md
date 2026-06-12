---
title: "Xerox WorkCentre 3119 Series on Ubuntu 9.04"
date: 2009-07-27
forum: General Help
---

### Post by klondike21 on 2009-07-27
hello. I'm having problems in making my scanner work (Xerox WorkCentre 3119). I have no problems using the printer function but when I try to run XSane, it says invalid argument. the device being found is my webcam. when i type lsusb in  terminal my device appears there, in bus 001 and dev 004: Xerox. 

From the start, I just plugged in the usb and my ubuntu 9.04 was able to detect it and I was able to use the printer function right away. Anyone can help about this?:D

---

### Post by jerrrys on 2009-07-27
do not own one, but found this (post # 8 )

[http://ubuntuforums.org/showthread.php?t=392225](http://ubuntuforums.org/showthread.php?t=392225)

---

### Post by klondike21 on 2009-07-29
tnx for the reply. i was also able to find that thread but it didn't help me. i don't know if im doing something wrong. i can't even install the driver that could be downloaded here  [http://www.support.xerox.com/go/resu..._GB&Xcntry=GBR]("http://www.support.xerox.com/go/results.asp?Xtype=download&prodID=WC3119&Xlang=en_GB&Xcntry=GBR")

---

### Post by krozzie on 2009-10-04
(Linux baz-desktop 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:48:52 UTC 2009 x86_64 GNU/Linux)

Ubuntu 9.04 worked "Out of the box" with this printer (which was great! much better than previous versions) 

My problem I am having is configuring this particular scanner device. (I have never had it working since Ubuntu 8.04)

Ref: [http://ubuntuforums.org/showthread.php?t=392225&highlight=Xerox+WorkCentre+3119+Series]("http://ubuntuforums.org/showthread.php?t=392225&highlight=Xerox+WorkCentre+3119+Series") 

Post #8 states "/etc/init.d/mountdevsubfs" as the file to edit, but I've only found "/etc/init.d/mountdevsubfs.sh" which has no uncommented lines (at the EOF). 


How should I go about trying to resolve this issue? I would love a little knowledge how scanners work with linux, in particular the multifunctional printers.

Cheers

---

### Post by krozzie on 2009-10-05
I've been doing some more research

```
sane-find-scanner
```

which brings up

```
found USB scanner (vendor=0x0924 [Xerox], product=0x4265 [WorkCentre 3119 Series]) at libusb:001:004
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

```

FYI scanimage -L doesn't do much :(
also checked out lsusb, same result as the libusb bus no#

```
baz@baz-desktop:~$ lsusb
Bus 001 Device 004: ID 0924:4265 Xerox 
```

Okay then, gave the the 2006 xerox manufactures drivers a go. I've extracted them, change permissions & executed ```
sudo ./install.sh
```  with the response ```
./install.sh: 11: source: not found
[: 670: unexpected operator

``` this is to be expected as previous threads state. [URL="http://ubuntuforums.org/showthread.php?t=392225&highlight=Xerox+WorkCentre+3119"][This one, post #4]
[/URL]
```
cd /bin
sudo rm -f sh
sudo ln -s bash sh
``` 
Went back to my install directory and tried ```
baz@baz-desktop:~/xerox$ sudo ./install.sh
cat: ../autorun.inf: No such file or directory

Please, select your device model...
	 [1] Cancel installation
Please make your choice [1,2, ...]: 2
Please make your choice [1,2, ...]: 1
baz@baz-desktop:~/xerox$ 

```

damn! back to square one ](*,)](*,) to revert the bash commands I used 
```
cd /bin
sudo rm -f sh
sudo ln -s dash sh
```

must admit those commands worked for the printer in 8.04 but no such luck in 9.04 :confused:

what's causing my grief? Would love any input!

---

### Post by montres on 2009-10-06
Same problem here. My 3119 printer was recognized automatically through the "printer configuration" page under "System<Administration". However, I can't print anything. Photocopying (which is done by pressing a button on the printer itself) works normally.I downloaded the drivers but encountered the same problem as krozzie and couldn't install them.

---

### Post by krozzie on 2009-10-08
> **montres said:**
> Same problem here. My 3119 printer was recognized automatically through the "printer configuration" page under "System<Administration". However, I can't print anything. .... .I downloaded the drivers but encountered the same problem as krozzie and couldn't install them.

Are you using ubuntu 9.04? Check if your printer is set to default. I've right clicked on my printer and it's given me the address _usb://Xerox/WorkCentre%203119%20Series _ 

I've been trying to get the scanner to communicate with xsane, but only found my printer worked "out of the box" under 9.04. Earlier versions <8 of ubuntu I would have to install the drivers through the xerox 2006 driver. 

[ This thread]("http://ubuntuforums.org/showthread.php?t=341621") *may be* our answer (from a google search [here]("http://www.google.com.au/search?q=modprobe+xerox+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a")), but it's quite dated :( I've read the samsung is a very close to the xerox printer, but would love some feedback before I stuff up a working printer. [The last few posts seem promising]("http://ubuntuforums.org/showpost.php?p=8039433&postcount=323")

---

### Post by montres on 2009-10-08
The system in question uses ubuntu 8.04. I really don't care very much about the scanner, if I can just get it to print properly, I'll be happy.

---

### Post by krozzie on 2009-10-08
[here is the post where I was reading the samsung is similar to the xerox]("http://ubuntuforums.org/showthread.php?t=874492&highlight=Xerox+WorkCentre+3119")

---

### Post by krozzie on 2009-10-08
> **montres said:**
> The system in question uses ubuntu 8.04. I really don't care very much about the scanner, if I can just get it to print properly, I'll be happy.

the ubuntu 8.04 version worked fine for me (using the 2006 xerox drivers), are you having similar problems that i've posted about 9.04? I'll admit i'm no expert, but I don't mind giving ago trying to solve problems. 

Can you test print? seems quite odd if your printer is installed and is detected why it can't print!??! If it's shooting out blank pages perhaps give the toner a shake? If the test page works but webpages, documents don't... etc check that the printer it's sending it out to that printer....and have to ask... was it working before or have you never used this printer on ubuntu?

---

### Post by sunnydrake on 2010-01-27
printer drivers work ok but scanner is big problem it's not recognized by ubuntu 9.10 properly and xerox drivers drivers don't have proper kernel image

---

