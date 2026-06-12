---
title: "After logging in, screen is blank or distorted"
date: 2012-06-12
forum: General Help
---

### Post by carltower on 2012-06-12
Hi. I am new to Ubuntu and I wanted to try 12.04. I installed Ubuntu in a new system by USB. The installation worked and I got into the login screen. But when I logged in, the screen is blank with purple rectangular artifacts. When I click on the screen, I get random things appearing like distorted text or orange boxes. The cursor changes to different pointers like a text input or window resize. Could anyone help me what the problem is and fix for this?

---

### Post by carltower on 2012-06-12
I managed to make it work. When I'm in the log in screen, I clicked on the Ubuntu icon (circular icon) beside the user account name. I chose Ubuntu 2d. Then when I logged in, the display screen is now showing properly. I hope someone can explain this to me because I am still new to this. All are working but it says in the system that the graphics driver is unknown. My setup is Biostar N68S3B, AMD Athlon II X2 260 and 500GB Seagate SATA disk.

---

### Post by wilee-nilee on 2012-06-12
Try this command for the graphic card.
                                  ```
lspci | grep VGA
```This will name the hardware in general, post only what is needed.
```
lspci
```Run a update and upgrade check the additional drivers app to see if any drivers are offered as well.

This might be the card you have.
[http://ph.answers.yahoo.com/question/index?qid=20120109020701AAQKKoT](http://ph.answers.yahoo.com/question/index?qid=20120109020701AAQKKoT)

If it is a nvidia the drivers may be in the repos here are the standard commands
```
sudo apt-get install nvidia-curre[FONT=Verdana, sans-serif][SIZE=1]nt[/SIZE][/FONT]
```
 ```
sudo apt-get install --reinstall nvidia-current
```

---

### Post by aim2help on 2012-06-12
I'm having a similar problem with a twist!

I added a new drive to my system because the old one was full and stopped. I installed 12.04 at the same time, onto the new drive using a flash disk while off line.

The system performs fine on 12.04 from the flash disk and it booted from the new drive OK and I was able to recover all my old data.

The updater suggested that I update, so I went ahead and did so. At the end of which it wanted to reboot. I went ahead but on reboot I get to the log in prompt and then the whole system crashes. It tries to recover and then performs a bug report during which it tells me that a whole bunch of files are out of date (these would be the new ones I just updated!) and the screen goes black. Game over.

I've tried to reboot several times ... same result.

I can boot off the flash drive OK.

How do I restore the system I had before the update, without over writing all my hard earned recovered data? Or how do I identify the "new updates" that are causing me grief?

---

### Post by wilee-nilee on 2012-06-12
> **aim2help said:**
> I'm having a similar problem with a twist!

I added a new drive to my system because the old one was full and stopped. I installed 12.04 at the same time, onto the new drive using a flash disk while off line.

The system performs fine on 12.04 from the flash disk and it booted from the new drive OK and I was able to recover all my old data.

The updater suggested that I update, so I went ahead and did so. At the end of which it wanted to reboot. I went ahead but on reboot I get to the log in prompt and then the whole system crashes. It tries to recover and then performs a bug report during which it tells me that a whole bunch of files are out of date (these would be the new ones I just updated!) and the screen goes black. Game over.

I've tried to reboot several times ... same result.

I can boot off the flash drive OK.

How do I restore the system I had before the update, without over writing all my hard earned recovered data? Or how do I identify the "new updates" that are causing me grief?

Start your own thread.

---

### Post by carltower on 2012-06-13
Thanks wilee-nilee.

I've done the command in the terminal. The on-board graphics card are the same with card in the link that you provided.
```
00:0d.0 VGA compatible controller: NVIDIA Corporation C61 [GeForce 7025 / nForce 630a] (rev a2) 
```

I've updated the system (260+ files) and then when I restarted, I logged in using Ubuntu 2d again. A prompt window appeared about something about requiring additional drivers. I chose and activated NVIDIA accelerated graphics driver (version current) because it said that it's the one recommended. There is another NVIDIA version - (post-release updates)(version current-updates)

I restarted, as suggested, then I tried the Ubuntu instead of Ubuntu 2d. I'm able to log in but this time, the desktop wallpaper is present. Just the wallpaper. However, I'm still unable to click anything and a bit of flickering happens whenever I click. Nothing else is showing up. I logged in via Ubuntu 2d. In the System>Details>Graphics, the driver is still unknown. But in Hardware>Additional Drivers, the NVIDIA driver is activated. Also, the width of the screen has shifted to the left, maybe, by 80 pixels. I'm not sure if the screen has shrunk. I didn't notice it before I updated the driver.

Do I still need to do the last 2 commands? I can't tell if what you're saying is to still do the commands after or do the commands if there are no drivers.

---

### Post by wilee-nilee on 2012-06-13
> **carltower said:**
> Thanks wilee-nilee.

I've done the command in the terminal. The on-board graphics card are the same with card in the link that you provided.
```
00:0d.0 VGA compatible controller: NVIDIA Corporation C61 [GeForce 7025 / nForce 630a] (rev a2) 
```I've updated the system (260+ files) and then when I restarted, I logged in using Ubuntu 2d again. A prompt window appeared about something about requiring additional drivers. I chose and activated NVIDIA accelerated graphics driver (version current) because it said that it's the one recommended. There is another NVIDIA version - (post-release updates)(version current-updates)

I restarted, as suggested, then I tried the Ubuntu instead of Ubuntu 2d. I'm able to log in but this time, the desktop wallpaper is present. Just the wallpaper. However, I'm still unable to click anything and a bit of flickering happens whenever I click. Nothing else is showing up. I logged in via Ubuntu 2d. In the System>Details>Graphics, the driver is still unknown. But in Hardware>Additional Drivers, the NVIDIA driver is activated. Also, the width of the screen has shifted to the left, maybe, by 80 pixels. I'm not sure if the screen has shrunk. I didn't notice it before I updated the driver.

Do I still need to do the last 2 commands? I can't tell if what you're saying is to still do the commands after or do the commands if there are no drivers.

So graphic cards are not a real strong area for me I suggest we see what others say from here.

I was mainly trying to get the card identified, and provide some info as I have seen it provided in other cases.

---

### Post by carltower on 2012-06-13
Alright! You've been helpful. I'll try to research and explore some more about Linux. For the mean time, this will do. Thank you, wilee-nilee.

---

### Post by madtom1999 on 2012-06-14
Just to add I've just upgraded to 11.10 and am getting similar problems
The machine boots - grub is OK and then as linux boots the screen complains of being being sent too fast data. The machine eventually comes into X11 and all is well but ctrl-alt-f1... etc reveals a too fast driven monitor on the text screens but works on the X11 screens.

Freinds on my local LUG have reported similar problems with Nvidia stuff too on 12.04 after similar problems on 11.10 and are considering moving to other distibutions

---

