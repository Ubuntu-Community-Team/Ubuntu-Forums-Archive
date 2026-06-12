---
title: "Wired networking on 1005ha"
date: 2009-09-11
forum: General Help
---

### Post by note32 on 2009-09-11
how to i do this:
 
terminal, navigate (’cd’) to the ’src’ directory so i can run this

           make
           sudo make install
           sudo insmod atl1e.ko

ive already extracted the the src file to my desktop im kinda stuck

---

### Post by Sin@Sin-Sacrifice on 2009-09-11
Open the terminal in Accessories>Terminal and type ```
cd ~/thenameoftheextractedfilehere/src
``` and hit enter (change "thenameoftheextractedfilehere" to the actual name of the folder). Then type ```
make
```  and hit enter. If no errors then ```
sudo make install
``` and hit enter, enter your password and hit enter. If there's still no errors then ```
sudo insmod atl1e.ko
``` and then your stuff SHOULD work. Sound to me that you only extracted the src file. Delete that and extract the whole thing to your home dir because when compiling source the things in the src folder may need things in the other folders. I've never installed that specific software so I don't know exactly what you need to do but this [http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html) may help.

---

### Post by hal10000 on 2009-09-11
Dont' do this!!!!!!!
You are a beginner and want to install a driver that presumably already exists in your system.
It's a much better idea to describe what your really problem is, i.e why do you want to install this driver for your network card, is it not working, or what else.

I'm pretty sure, if you run the commands you posted, you will get a lot of problems.
These commands are going to install source code programs, which is in many cases even for linux professionals a bloody game.

Usually more than 95% of the Software you like to install is available through your package manager (File--->Add/Remove Software or a program called synaptic).

But in your case, if you want to install the driver for your atheros network card it's not necessary, because it's already installed. If you have problems with your network card, then post a brief description.

---

### Post by Sin@Sin-Sacrifice on 2009-09-12
And then again.... how does one learn without making a few mistakes? My system would be base model crap if I was to follow the advice of people like you. I spent most of my time fixing my mistakes and I know a LOT more about PCs because of it. But that's just me. No one has to listen or like it. Yeah... don't do what I described... if you want to live in the shadow of these forums for the rest of your Linuxing.

---

