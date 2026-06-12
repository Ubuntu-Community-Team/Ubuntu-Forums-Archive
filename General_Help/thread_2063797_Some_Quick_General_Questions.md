---
title: "Some Quick General Questions"
date: 2012-09-27
forum: General Help
---

### Post by rmbrown09 on 2012-09-27
Hello, I will make this post brief but I am really looking to jump to Ubuntu from Windows. I have used and installed Ubunutu before, probably 6 times over the last 4 years but I never stick with it and go back to Windows or OSX. 

I have a desktop I build with the following specs and was hoping that all of the hardware would work just fine, especially the video card.

Asus P8P67 Evo mainboard
2600k CPU
GTX 690 GPU
8GB 2133 MHz Ram
128GB M4 SSD
2560x1440 monitor

Questions:

1. Does Ubunutu support TRIM for my SSD? I see conflicting posts all over the internet about this.

2. Will my 690 work? I used to have two 6870's in crossfire and with Ubuntu could never get them to work. I couldn't turn on any of the visual candy and everything lagged. This was after the driver said it was successfully installed. 

3. Do any of you use the Crossover program or something like that for gaming? I like to play games like SC2 and BF3. I have read around and see that BF3 is basically impossible to get running correctly however Crossover seems to be able run things like SC2 and some other newer games without issue.

---

### Post by HiImTye on 2012-09-27
> **rmbrown09 said:**
> 1. Does Ubunutu support TRIM for my SSD? I see conflicting posts all over the internet about this.

2. Will my 690 work? I used to have two 6870's in crossfire and with Ubuntu could never get them to work. I couldn't turn on any of the visual candy and everything lagged. This was after the driver said it was successfully installed. 

3. Do any of you use the Crossover program or something like that for gaming? I like to play games like SC2 and BF3. I have read around and see that BF3 is basically impossible to get running correctly however Crossover seems to be able run things like SC2 and some other newer games without issue.

regarding TRIM on your SSD, here's some info on it:
[http://askubuntu.com/questions/18903/how-to-enable-trim](http://askubuntu.com/questions/18903/how-to-enable-trim)

on your GPU, I'm not sure about the GPU, but ATI has improved Linux support lately (in fact, they were the first to enable support for hybrid graphics in their default drivers, something I'm not sure if nVidia has actually gotten around to). the best way to find out is to try, or search the supported GPU list on the linux drivers README (nVidia's is available from their download page, I'm sure that ATI has something similar)

regarding gaming, it all depends on the WINE version you use. different WINE versions work with different games to differing degrees. I would recommend something like PlayOnLinux that lets you specify the WINE version to use for your games. I haven't been able to play them for a couple Ubuntu versions, but that is due to an nVidia issue.

---

