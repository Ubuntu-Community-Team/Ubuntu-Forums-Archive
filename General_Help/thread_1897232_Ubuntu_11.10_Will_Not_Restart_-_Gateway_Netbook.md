---
title: "Ubuntu 11.10 Will Not Restart - Gateway Netbook"
date: 2011-12-18
forum: General Help
---

### Post by preumbra on 2011-12-18
All,

I have read through the other threads I could find, but none of the proposed solutions worked for me.

I bought a Gateway Netbook for my nephew for Christmas, and I am trying to get Ubuntu working on it.  Here is what I have:

1) Restart (from Ubuntu) hangs indefinatley at black screen during shutdown - I have to use the power button.

2) Shutdown (from Ubuntu) works nominally.

3) All functions work nominally in windows 7.

This is a fresh install of 11.10.

Any help would be appreciated.

---

### Post by jerrrys on 2011-12-20
here's a natty fix

[http://ubuntuforums.org/showthread.php?t=1741668&page=7](http://ubuntuforums.org/showthread.php?t=1741668&page=7)

that I found here

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Restart+reboot+hangs+indefinatley&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Restart+reboot+hangs+indefinatley&sa=Search&cof=FORID:9)

---

### Post by preumbra on 2011-12-20
Thanks for the reply jerrys.

I tried all the solutions in that thread (prior to posting, and then again today) and none of them worked.  The only one I was unable to do was the editing of /etc/init.d/umountnfs.sh as I am unable to edit that file.  I also had no network drives mounted.

Maybe my poor nephew will have to learn windows 7 light.

---

### Post by LinuxFan999 on 2011-12-20
The obvious solution would be to never reboot.

---

### Post by wildmanne39 on 2011-12-20
Hi, look at your log files and see if you can find any errors right after you reboot from the black screen.
```
sudo tail -n100 /var/log/syslog
```
```
sudo tail -n100 /var/log/kern.log
```
```
dmesg | less
```
Thanks

---

### Post by preumbra on 2011-12-21
> **wildmanne39 said:**
> Hi, look at your log files and see if you can find any errors right after you reboot from the black screen.
```
sudo tail -n100 /var/log/syslog
```
```
sudo tail -n100 /var/log/kern.log
```
```
dmesg | less
```
Thanks

Thanks for the reply wildman.

For the first command:
[ATTACH]209468[/ATTACH]

For the second command:
[ATTACH]209469[/ATTACH]

The third is too big,so hereate the first 200 or so lines:
[ATTACH]209470[/ATTACH]

Thanks again.

---

### Post by wildmanne39 on 2011-12-21
Hi, the only thing I see is > scsi: killing requests for dead queue and it has to do with a drive not being seen or activated properly I believe it is a sd drive but I did not find any information that said it causes lockups on shutdown.
You can have a look at the link but I am not sure it will help.
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)
Thanks

---

### Post by nardis_Miles1 on 2012-03-25
Have you resolved your issues with the gateway netbook yet? Does the wifi work?

---

