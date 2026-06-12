---
title: "ISZ File support?"
date: 2009-06-26
forum: General Help
---

### Post by Markei on 2009-06-26
Hi guys, 

I've been searching for the past hour or so for info on ISZ file support in Ubuntu, but really can't find anything other than 'you should be able to run it although it says it's not supported' - which doesn't help me all that much. I'm a newbie so still pretty confused by alot of things Linux.

If anyone could point me in the right direction as to how I can open an ISZ file I would be very grateful! 

Thanks in advance! 

Mark

---

### Post by Markei on 2009-06-26
Anyone??

---

### Post by Greyfox_75 on 2009-06-26
Try this... Install wine if you don't have it already.
sudo apt-get install wine

The company that makes the program that makes these isz files has a free converter (for windows) that converts from an isz to an iso

wget [http://www.ezbsystems.com/isz/unisz.zip](http://www.ezbsystems.com/isz/unisz.zip)
unzip unisz.zip

Run with wine and cross your fingers.
wine unisz.exe youriszfile.isz

Good luck.

---

### Post by Andruk Tatum on 2010-03-02
I can confirm that this works in Wine.  It's really too bad that there isn't an open source program that can decompress these files.  ](*,)

---

### Post by EduardoMartins on 2010-10-24
Running unisz through Wine on Ubuntu 10.04 64-bit didn't work for me. I had to install a trial version of WimMount on Windows to work with an .ISZ file. I hope I'll never meet such a silly format again.

Eduardo

---

### Post by mastermindg on 2010-11-08
You need to run unisz under dos.

```
wine cmd
unisz file.isz file.iso
```

I'm running Wine under 10.04 64-bit as well and it worked for me.

---

### Post by oserres on 2012-07-14
Alternatively, you can use a small tool I wrote, isz-tool which is a small Python utility that convert isz files to iso. It just requires Python 3.2.

It can be download at :
[https://github.com/oserres/isz-tool/zipball/master](https://github.com/oserres/isz-tool/zipball/master)

And used as :
./isz-tool.py isz2iso file.isz file.iso

---

### Post by oldos2er on 2012-07-15
Please don't bump old threads.

---

