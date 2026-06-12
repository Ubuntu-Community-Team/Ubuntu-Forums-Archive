---
title: "Karmic kernel panicking(?) and crashing."
date: 2009-12-28
forum: General Help
---

### Post by andybusse on 2009-12-28
Hello,

I have recently installed 64-bit Ubuntu Karmic Koala on to my laptop, and it seems to randomly enter kernel panic (I get the all-too familiar Black Screen of Death, and the Caps Lock LED flashes, which the internet tells me is a sign of kernel panic. I know that I shouldn't press the power button to shut it down, but Alt+SysRq+R, E, I, S, U, B - what I am told should shut it down safely - does nothing)

I have had to coax the wireless card into working by downloading [http://launchpadlibrarian.net/34090326/rtl8192se_linux_2.6.0010.1012.2009_64bit.tar.gz](http://launchpadlibrarian.net/34090326/rtl8192se_linux_2.6.0010.1012.2009_64bit.tar.gz) from the following page, and trying to follow some of the instructions on there: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126?comments=all#](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126?comments=all#) and then doing the following in a terminal: 
```
 sudo tar -xvzf rtl8192se_linux_2.6.0010.1012.2009_64bit.tar.gz
cd rtl8192se_linux_2.6.0010.1020.2009_64bit/
sudo make
sudo su
make install
sudo modprobe r8192se_pci

```After which, my wireless card (Realtek 8172 rev. 10) (the last line of lspci) worked.

Apart from this, I don't see what else is going wrong. I have pasted the output from /var/logs/kern.log here [http://pastebin.com/m2ee64531](http://pastebin.com/m2ee64531) Also, this sort of line is appearing quite frequently in between the 'DMA: Out of.... ' lines. ```
Dec 28 18:03:59 blueberry kernel: [ 1167.851923] ===>u4bAcParam:731c, ===>u4bAcParam:731c, ===>u4bAcParam:731c, ===>u4bAcParam:731c,
```Any help would be appreciated.

Regards,
Andy

---

