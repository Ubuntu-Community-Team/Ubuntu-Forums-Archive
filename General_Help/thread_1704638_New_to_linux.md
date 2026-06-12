---
title: "New to linux"
date: 2011-03-10
forum: General Help
---

### Post by yamaharider848 on 2011-03-10
Hi, im Austin and as you might have already read that i am new to Linux.  So far everything seems ok i have noticed that flash does take up 90+  cpu.  i have read that its mostly normal and i have read up on and have  installed cpulimit but when i try to limit say Firefox the program seems  to craw. I would like to say  that everything does seem to work. 

this is what i think i have based on Google (my laptop is a emachines e627 blackfriday edition ) 


[LIST]
[*] **Processor**  AMD Athlon 64 TF-20 / 1.6 GHz
[*] **64-bit Computing**  Yes
[*]**RAM 2gb**
[*]**Graphics Processor / Vendor**  ATI Radeon HD 3200
[/LIST]

i could have the advance appearance settings on (with the cube and  compiz doing its thing) but i just have wobbly windows and min and max  effects

my Internet seems slow, but not the speed of the Internet that seems to  be slow.  just im pretty sure that loading up facebook was a bit faster  on windows 7 ..

i don't know how i would know if all my drivers are set up and running the way they should 
and also what else could i do to make things faster seems like every  time i open up or create a new tab or just about anything my cpu hits  100 but drops fast maybe its my cheep computer. 

maybe this is a waste of time for ubuntu fourms but i thought i might  post this to see what you all might have to say  but thanks for reading  and  thanks for answering !
if i got a new computer what computer should i get next for ubuntu

---

### Post by nickleboyblue on 2011-03-10
As for the internet issue, it's Firefox.  The versions that ship with ubuntu 10.10 and before are slow compared to what is going on now.  If you want to speed things up, either get Google Chrome or Chromium, or you could go through all the extra work to get the latest and greatest firefox version running on your box.

And by the way, it's not a waste of time to post such issues on the forums unless you haven't yet searched through them on your own for threads that carry similar information.  You will most likely find someone else out there who has the same issues you do.

As for cpu frequency, my own laptop jumps rather high when working with flash and similar systems.  This has never been an issue for me.  If your computer starts overheating, well, that's when I would start to worry.

One last thing:  I would install the 32-bit version of ubuntu if I were you, even though your computer has a 64-bit capable processor, because the 32 bit version has a lot more support even now.  The 64 bit version is catching up, but new features usually come to 32-bit in a stable state a lot sooner, and you will not notice any performance lag vs 64 bit.

---

### Post by Krytarik on 2011-03-10
Hi and welcome to the forums and to Linux in general!

About your driver, I guess you mean the video driver, check with the following command which driver is running:
```
lshw -c video
```
"fglrx" is the proprietary driver, "ati", "radeon" and "radeonhd" are all default open source drivers.

I recommend installing the proprietary driver via "System -> Administration -> Additional Drivers (10.10) / Hardware Drivers (10.04)", if you haven't done so already.

To get the most recent packaged version of the proprietary driver you can use Ubuntu-X-Swat's PPA (after you installed it the mentioned way):
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade
```

Maybe that will also help your internet browsing speed. If it doesn't, you may try Chromium, and Firefox 4 should also be released in the near future, hopefully ;-).

About the 100%-CPU-usage jump-ups: That's normal, it's the same at my system, the OS simply utilizes all the available power, even if it's just for a second, to deliver the fastest possible result.

And about Flash: Flash simply *is* that way, I believe you could have the fastest ever machine and it still fires it up to 100%-CPU-usage anyway, regardless if it is Windows or Linux.

---

### Post by Timmer1240 on 2011-03-10
Install Chromium its faster than firefox.

---

### Post by WinterMadness on 2011-03-11
As they have said, Chromium, Chrome, Opera and Epiphany are the best browsers for linux

Epiphany is based on Firefox, but its EXTREMELY light weight and doesnt have any features

I recommend chrome or chromium, as I use that on a regular basis. Firefox on linux is a disaster imo.

---

### Post by kidsodateless on 2011-03-11
> **Timmer1240 said:**
> Install Chromium its faster than firefox.


I use Firefox 4 beta and on my calculation it is now faster than Chromium.

---

### Post by Krytarik on 2011-03-11
Hey, Firefox is not *that* bad on Linux, I use it almost solely, but Chromium's/Chrome's script handling is somewhat faster and more stable, like it's also the case for Firefox 4. Firefox 3 tends to grow-and-grow in your RAM if you run much scripts, the others don't. But when I compare Firefox 3 and Chromium at the same website with not overly much scripts, I really can't judge which one is faster, because that of course also depends on the response time of the web server.

---

### Post by bwang on 2011-03-11
AFAIK Chrome's V8 engine is still the fastest Javascript interpreter out there.
Flash using 90% of your CPU is not unusual considering you have a single-core ultra-low power chip inside your machine.

---

### Post by yamaharider848 on 2011-03-13
Hey thanks guys, im glad theres people  to help. 
i have downloaded my additional drivers
and ill figure out how to go from 64bit to 32bit

---

### Post by Krytarik on 2011-03-13
> **yamaharider848 said:**
> ill figure out how to go from 64bit to 32bit
Therefore you would have to re-install!

---

