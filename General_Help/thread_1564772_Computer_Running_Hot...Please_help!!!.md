---
title: "Computer Running Hot...Please help!!!"
date: 2010-08-31
forum: General Help
---

### Post by borth92 on 2010-08-31
The problem does occur with both Windows 7 and Ubuntu 10.04. Whenever I watch a movie on Megavideo that uses flash, my computer runs so hot I can barely hold it and the video gets really choppy. It makes movies unbearable to watch. Either the fan isn't running at a high enough speed or maybe it needs to be replaced? please give me something...

---

### Post by Rasa1111 on 2010-08-31
the fan probably does need to be replaced. 
but I dont know for sure. 

my dads wife has had 3 laptops do this over the years,
all from the fans. 

She got to the point where she bought 3 "dock" type things, (after fixing the fans)
but the dock things had fans in them also, and the laptop sits on it, while it draws the heat away from the bottom. 
Guess it helps to prolong the life of the machine. 

Get it looked at (or fix it yourself) before too much longer or youll likely fry the CPU.

 It may also just need a good cleaning.

---

### Post by wojox on 2010-08-31
Try installing [Video DownloadHelper  4.8]("https://addons.mozilla.org/en-US/firefox/addon/3006/") and saving the .flv to your drive and watch it with VLC, Totem, MPlayer, etc...

Also are your fan ports clean?

---

### Post by JBAlaska on 2010-08-31
I assume this is a laptop, Take the bottom off and check and blow the dust out of the Fan/Heatsink and GPU heatsink if it has one.

Watch your CPU usage while playing a flash video & see if it goes to 100%

---

### Post by borth92 on 2010-08-31
After a few minutes of a flash video my cpu maxes out...

---

### Post by borth92 on 2010-08-31
well new progress...turns out that I was using Firefox as the web browser for both OS's...Chromium for linux is not running nearly as hot. So how can I get FF to handle flash better

---

### Post by TheNessus on 2010-08-31
> **borth92 said:**
> well new progress...turns out that I was using Firefox as the web browser for both OS's...Chromium for linux is not running nearly as hot. So how can I get FF to handle flash better
that is only combating a symptom, but not the illness. Is your graphics card Nvidia 8xxx?

---

### Post by JBAlaska on 2010-08-31
You can try disabling hardware acceleration in flash, Sounds backwards I know but sometimes it helps.

Open system monitor and play the same flash video with and without hardware acceleration & see which uses less CPU.

To disable hardware acceleration right click on the video window and uncheck the box.

---

### Post by borth92 on 2010-08-31
> **TheNessus said:**
> that is only combating a symptom, but not the illness. Is your graphics card Nvidia 8xxx?

Nvidia GeForce 8400M is my graphics chip...you don't think it is perhaps an issue with firefox 64-bit? i am running an alpha 64-bit flash player because there are no stable 64-bit flash players on linux...but i did not mess with Windows 7's flash player

---

### Post by TheNessus on 2010-08-31
> **borth92 said:**
> Nvidia GeForce 8400M is my graphics chip...you don't think it is perhaps an issue with firefox 64-bit? i am running an alpha 64-bit flash player because there are no stable 64-bit flash players on linux...but i did not mess with Windows 7's flash player

No, it's your Nvidia 8400. End of story. Onboard, irreplaceable. That is the cause. But yeah, you can fight the symptoms, to prolong your computer's life. The Nvidia 8xxx series is infamous for its heat problems.

The latest Nvidia driver, 250 or 260 or something, helps lower the temperature a bit more.
It's not in the repo. In the repo (Lucid) it is 196. Try installing the newer from Nvidia's website.

---

### Post by borth92 on 2010-08-31
well thats not exactly good news...good news is i got this computer free with 4gb ram and a 2.2ghz processor...so i guess ill ride it into the ground, salvage the ram and move on. thanx for the help

---

### Post by TheNessus on 2010-08-31
> **borth92 said:**
> well thats not exactly good news...good news is i got this computer free with 4gb ram and a 2.2ghz processor...so i guess ill ride it into the ground, salvage the ram and move on. thanx for the help

Nope, not exactly good news. And I know how you feel because I'm in the same situation as you :)

If (when) your graphics card dies it has the potential to take the motherboard with it, killing the RAM and CPU as well... so :-\

---

### Post by borth92 on 2010-08-31
> **TheNessus said:**
> Nope, not exactly good news. And I know how you feel because I'm in the same situation as you :)

If (when) your graphics card dies it has the potential to take the motherboard with it, killing the RAM and CPU as well... so :-\

I downloaded  the new driver but its a .run file extension. any idea on how it works to install?

---

### Post by TheNessus on 2010-08-31
> **borth92 said:**
> I downloaded  the new driver but its a .run file extension. any idea on how it works to install?

do the following:
either (a) login to root shell, at GRUB (in recovery option), or (b) do alt-ctrl-f1 to drop to root shell. But before you do that write this down:

if (b), you need to close X, so do "sudo /etc/init.d/gdm stop"
(replace kdm with gdm if you use KDE instead of gnome)
now, for both options:
"cd Desktop" (assuming your downloaded driver is at Desktop)
and to run the script simply do "sudo sh ./N(press TAB to autocomplete driver name) run".
accept, accept, accept, done.
reboot, and then run "sudo nvidia-xconfig", then logout or reboot. should work.

---

### Post by JedMeister on 2010-08-31
My sister had the same problem with her laptop. Good news (well sort of) was that after the GPU died, I managed to somewhat revive it by removing the nVidia driver and just using the default one. You loose all the graphical niceness but it still works!

---

### Post by luceerose on 2010-08-31
If your motherboard has anything like amd's 'cool & quiet' technology, disable it in the bios.
That will make sure all fans run at full speed. That would be a good starting point.

---

### Post by borth92 on 2010-08-31
> **TheNessus said:**
> do the following:
either (a) login to root shell, at GRUB (in recovery option), or (b) do alt-ctrl-f1 to drop to root shell. But before you do that write this down:

if (b), you need to close X, so do "sudo /etc/init.d/gdm stop"
(replace kdm with gdm if you use KDE instead of gnome)
now, for both options:
"cd Desktop" (assuming your downloaded driver is at Desktop)
and to run the script simply do "sudo sh ./N(press TAB to autocomplete driver name) run".
accept, accept, accept, done.
reboot, and then run "sudo nvidia-xconfig", then logout or reboot. should work.

Everything was just like you said, but as I rebooted it said there was an error. I had to boot into low graphics and reinstalling the recommended driver...

---

### Post by nerdy_kid on 2010-08-31
I have a Nvidia geforce 8600M and i have no over heating issues at all.

DO NOT install the driver from nvidia's site; instead use the one in the repos.  If this is not up to date enough for you; then add this ppa:
```

sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade

```
this will upgrade your nvidia drivers.
How old is the laptop?  If it is over 2 years there is a good chance that dust is your problem.  If not; are you letting the laptop "breathe"?  You don't want to lay it on a bed/couch, it should be on a hard flat surface to allow air to reach the fan on the bottom.

---

### Post by nerdy_kid on 2010-08-31
> **borth92 said:**
> Everything was just like you said, but as I rebooted it said there was an error. I had to boot into low graphics and reinstalling the recommended driver...

you need to uninstall that driver; i am not sure but I think that if you run the .run file with --uninstall it will remove it.
I am downloading the file right now
[edit]
ok i was right; so cd to the folder you downloaded the .run:
```

sudo ./DRIVERNAME.run --uninstall

```
then reboot and install the ppa as I said in my previous post and reboot again.

---

### Post by Rasa1111 on 2010-08-31
> "Microsoft Windows: A collection of 32bit extensions and a graphical shell for a 16bit patch to an 8bit O.S. originally coded for a 4bit microprocessor written by a 2bit company who cant stand 1 bit of competition." Jargon File 4.4.7

 :lol:, Great sig, nerdy kid! :D
and good advice.  <3

---

### Post by borth92 on 2010-08-31
> **nerdy_kid said:**
> you need to uninstall that driver; i am not sure but I think that if you run the .run file with --uninstall it will remove it.
I am downloading the file right now
[edit]
ok i was right; so cd to the folder you downloaded the .run:
```

sudo ./DRIVERNAME.run --uninstall

```then reboot and install the ppa as I said in my previous post and reboot again.

great advice, added the repo and it updated the driver...will check in a few minutes if it helped the heating issues. I think maybe going into the bios to unrestrict the fan or maybe a more powerful fan is needed.

---

### Post by borth92 on 2010-08-31
computer has been cooling ever since i rebooted when the new driver installed. brilliant advice everyone, thank you so much.

Cheers

---

### Post by Rasa1111 on 2010-09-01
hell yeah.
that's why this community is so awesome. :D
congrats!

---

### Post by TheNessus on 2010-09-01
Well it should indeed have brought you to a low graphics session, and then you do "sudo nvidia-xconfig",reboot, and then it would work with the new driver. Anyway,  glad you got to install it anyway.

---

### Post by nerdy_kid on 2010-09-01
> **Rasa1111 said:**
> :lol:, Great sig, nerdy kid! :D
and good advice.  <3

thanks; glad it solved the problem :)

---

