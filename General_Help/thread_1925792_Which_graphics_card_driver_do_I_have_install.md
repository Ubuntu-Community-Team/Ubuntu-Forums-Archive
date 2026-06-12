---
title: "Which graphics card driver do I have install?"
date: 2012-02-15
forum: General Help
---

### Post by CProgramming on 2012-02-15
Hey friends :)

I'm using Ubuntu 11.10 on my desktop and I have some problems with my graphical interface 

the reason probably is I have wrong \ incompatible graphics card driver installed.

My computer:
Processor: Intel Core2 duo E8800
Memory: 4GB RAM
Graphics card: nVidia GeForce 430

Can someone help me decide which driver should I install to get the best graphical interface on my ubuntu?

thanks , and sorry about the wrong English :\

---

### Post by haqking on 2012-02-15
> **CProgramming said:**
> Hey friends :)

I'm using Ubuntu 11.10 on my desktop and I have some problems with my graphical interface 

the reason probably is I have wrong \ incompatible graphics card driver installed.

My computer:
Processor: Intel Core2 duo E8800
Memory: 4GB RAM
Graphics card: nVidia GeForce 430

Can someone help me decide which driver should I install to get the best graphical interface on my ubuntu?

thanks , and sorry about the wrong English :\

it depends some people like proprietary and some like Open source drivers.

I prefer proprietary

[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

choose your device and download.

Cheers

---

### Post by CProgramming on 2012-02-15
> **haqking said:**
> it depends some people like proprietary and some like Open source drivers.

I prefer proprietary

[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

choose your device and download.

Cheers

Thanks , I thought they are not developing drivers for linux.

anyway , I downloaded this: [http://www.nvidia.com/content/DriverDownload-March2009/confirmation.php?url=/XFree86/Linux-x86/295.20/NVIDIA-Linux-x86-295.20.run&lang=us&type=GeForce](http://www.nvidia.com/content/DriverDownload-March2009/confirmation.php?url=/XFree86/Linux-x86/295.20/NVIDIA-Linux-x86-295.20.run&lang=us&type=GeForce)

NVIDIA-Linux-x86-295.20.run

I got that error: 
You appear to be running an X server; please exit X before            
         installing.  For further details, please see the section INSTALLING   
         THE NVIDIA DRIVER in the README available on the Linux driver         
         download page at [www.nvidia.com](www.nvidia.com).


What sould I do?..

---

### Post by mastablasta on 2012-02-15
isn't it possible to enable drivers form system->hardware devices menu?
 
you should run the file (make it as executable and run it). 
 
also check out the readmefile. usualyl it has detailed isntructions with command lines that you can copy&paste to terminal.

---

### Post by CProgramming on 2012-02-15
The boot is freezing!
First of all I got error message something like:
"Error mount. enter S to skip to M to recover"
Then I press S and the boot freeze on "Checking for running unattende-upgrades"

Do someone know what sould I do??? I can't use my computer!!

currently Im writing on my laptop, the problem on the desktop.

---

### Post by haqking on 2012-02-15
> **CProgramming said:**
> Thanks , I thought they are not developing drivers for linux.

anyway , I downloaded this: [http://www.nvidia.com/content/DriverDownload-March2009/confirmation.php?url=/XFree86/Linux-x86/295.20/NVIDIA-Linux-x86-295.20.run&lang=us&type=GeForce](http://www.nvidia.com/content/DriverDownload-March2009/confirmation.php?url=/XFree86/Linux-x86/295.20/NVIDIA-Linux-x86-295.20.run&lang=us&type=GeForce)

NVIDIA-Linux-x86-295.20.run

I got that error: 
You appear to be running an X server; please exit X before            
         installing.  For further details, please see the section INSTALLING   
         THE NVIDIA DRIVER in the README available on the Linux driver         
         download page at [www.nvidia.com](www.nvidia.com).


What sould I do?..

yes exit from X.

Drop to a tty or somit.

you may need to chmod the exe or you can do it from gui if needed.

Then from terminal

sh <filename>

during install it may detect nouveau or similar, modprobe it to blacklist it.

Then should be good.

I am running latest 295 driver though im in slackware currently but works fine and if it works in slack then it should work easily in ubuntu (im guessing) ;-)

---

