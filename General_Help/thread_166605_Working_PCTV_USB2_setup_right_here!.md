---
title: "Working PCTV USB2 setup right here!"
date: 2006-04-26
forum: General Help
---

### Post by kraz on 2006-04-26
I googled for a few days for some solutions for my PCTV USB2 to work in Ubuntu 5.10, and none of the solutions I got seemed to work.

Today I found another page, which was in french, in this adress:

[http://www.sylvek.net/dotclear/index.php?2006/02/14/191-pinnacle-pctv-usb2-100e-et-ubuntu](http://www.sylvek.net/dotclear/index.php?2006/02/14/191-pinnacle-pctv-usb2-100e-et-ubuntu)

You dont ned to understand much of what the guy is saying except for the commands he is issuing - in brackets.

I followed it from start to end


```

cd /home/yourdir

Get the Linux headers:       
sudo apt-get install linux-headers-2.6.12-10-686 
*(make sure these are indeed the headers you need..dont ask me how to find out!)*

Install gcc 3.4:      
sudo apt-get install gcc-3.4

Install tvtime:       
sudo apt-get install tvtime

install cvs:            
sudo apt-get install cvs

get latest video4linux drivers:
cvs -d :pserver:anonymous@cvs.linuxtv.org:/cvs/video4linux co -P v4l-dvb

Change dir:           
cd v4l-dvb

Compile:               
make

Install:                   
sudo make install

put info about specific sound settings to avoid stuttering images when sound is on:

                            
sudo gedit /etc/modprobe.d/pctv
insert line: options snd-usb-audio enable=1 index=1 nrpacks=10

save, exit, reboot


Run in console:

sox -r 44100 -t ossdsp /dev/dsp1 -t ossdsp /dev/dsp&tvtime --mixer=/dev/mixer:vol&

Enjoy!


```


This was the last program I needed to get working in linux for a full change, so...windows doesnt live here anymore!

---

### Post by wvelez on 2006-04-27
Hi,

Great instructions!  I´m now able to get some channels but only noise for sound...this is an improvement over the last dozen times I´ve tried to get this device to work.

Best regards.

Thanks,
-will

---

### Post by WebbyBabe on 2006-06-11
UGH! I've been looking for this for AGES!!! Now to install ubuntu and try it out! Thanks a million! :)

---

### Post by WebbyBabe on 2006-06-13
Hmmm, when I type "make" it says bash: command not recognized (something like that)

---

### Post by WebbyBabe on 2006-06-14
Okay, I got it working but I get no sound. :( How do you record with tvtime?

---

### Post by wvelez on 2006-06-14
Hi,

I don´t think you can record with TvTime but it is possible with xawtv.  I also can´t get sound and the image quality is poor, same deal as with Badger.

Please post back if you do get the sound working, I´ll keep trying to get it working.

Best regards,
-will

---

### Post by WebbyBabe on 2006-06-14
Hi, my sound isn't working at all. I have a red x over the volume icon and no sound cards are detected. :( I don't know how to fix this.

---

### Post by SanDiego on 2006-06-25
Hi,
I have sound and I can find and chose channels. Problem is, I have no picture. Just a few colored stripes on top, and the rest of the screen is green. Can someone help me? Do I have to change the configuration?

---

### Post by hwert on 2006-07-06
You are not plugged into a usb2 port but a usb1
I had the same problem.

Harry

---

