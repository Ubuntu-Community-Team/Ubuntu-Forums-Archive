---
title: "Problem with compilation"
date: 2010-05-04
forum: General Help
---

### Post by birkopf on 2010-05-04
Hi,

I run 64bit ubuntu 9.10
I have strange problem. I am trying to install driver for my network card Ralink. I am following this tutorial:

[http://www.apfelkraut.org/2009/02/howto-wlan-ralink-rt2870-usb-stick-kubuntu-810/](http://www.apfelkraut.org/2009/02/howto-wlan-ralink-rt2870-usb-stick-kubuntu-810/)

all is fine when I am making file (sudo make) but when i try to install it (sudo make install) it comes out with this error:

```

rich@rich:~/Desktop/ralink/DPO_RT3070_LinuxSTA_V2.3.0.2_20100412$ ls
chips	 iwpriv_usage.txt	      os		 RT2870STA.dat		   tools
common	 LICENSE ralink-firmware.txt  README_STA_usb	 sta
include  Makefile		      RT2870STACard.dat  sta_ate_iwpriv_usage.txt

rich@rich:~/Desktop/ralink/DPO_RT3070_LinuxSTA_V2.3.0.2_20100412$ sudo make install
make -C /home/rich/Desktop/ralink/DPO_RT3070_LinuxSTA_V2.3.0.2_20100412/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/rich/Desktop/ralink/DPO_RT3070_LinuxSTA_V2.3.0.2_20100412/os/linux'
rm -rf /etc/Wireless/RT3070STA
mkdir /etc/Wireless/RT3070STA
cp /home/rich/Desktop/ralink/DPO_RT3070_LinuxSTA_V2.3.0.2_20100412/RT3070STA.dat /etc/Wireless/RT3070STA/.
cp: cannot stat `/home/rich/Desktop/ralink/DPO_RT3070_LinuxSTA_V2.3.0.2_20100412/RT3070STA.dat': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/rich/Desktop/ralink/DPO_RT3070_LinuxSTA_V2.3.0.2_20100412/os/linux'
make: *** [install] Error 2

```


File is on my desktop but I dont think it's a problem. Could you please help ? I have checked file permissions and all are

---

### Post by gmargo on 2010-05-04
> **birkopf said:**
> File is on my desktop but I dont think it's a problem. 

Where? Your directory listing does not show a file named "RT3070STA.dat".

---

### Post by birkopf on 2010-05-07
> **gmargo said:**
> Where? Your directory listing does not show a file named "RT3070STA.dat".

I was so focused on making this driver work that I didn't noticed that. 
That was silly. Sorry about that. 

One good thing came out of that - I contacted developers and helped correct mistake as there is file RT28*.dat from previous driver-pack included in this RT307 version. 

Thanks for replying ):P

---

### Post by odius on 2010-05-28
so what was the solution? did you just rename it or did the developers give you a new file???

---

### Post by birkopf on 2010-05-28
> **odius said:**
> so what was the solution? did you just rename it or did the developers give you a new file???

I have used previous version as mentioned above. Than I followed how-to send to my be company from which I bought antena based on ralink chipset.

---

