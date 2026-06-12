---
title: "Unable to do software update or install programs"
date: 2010-08-14
forum: General Help
---

### Post by akawhitey on 2010-08-14
I am brand new to ubuntu. I loaded, by usb, Ubuntu Netbook Remix. Internet and firefox work perfectly. I tried to load Skype and the install hung with the "gdebi-gtk is not responding." 

I gave up and tried to update current software the message received was, "unable to get exclusive lock" which led me to this page: [http://ubuntuforums.org/showthread.php?t=145432](http://ubuntuforums.org/showthread.php?t=145432)

Which suggests this in teerminal: sudo dpkg --configure -a
 resulted in this error in terminal: "status database area is locked by another process"

which led me here [http://ubuntuforums.org/showthread.php?t=1015279](http://ubuntuforums.org/showthread.php?t=1015279) ... no help

or, pkill apt
which said: Operation not permitted

So then I tried to load a game and got this message: "Waiting for other  software managers to quit" and tried this thread [http://ubuntuforums.org/showthread.php?t=1434531](http://ubuntuforums.org/showthread.php?t=1434531) and tried their suggestions of  **sudo apt-get clean **and then [B]sudo dpkg --configure -a 

which left me with this message [/B]E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource  temporarily unavailable)
E: Unable to lock the download directory and this thread

I searched and tried a bunch of other stuff based on my error messages,
sudo apt-get update and sudo killall dpkg) but this is getting out of hand. Following directions but with no idea why.

I have never used the prompt before today. I am sure this problem is due to my complete inexperience. 

thanks

---

### Post by wojox on 2010-08-14
Sounds like you have to many package managers open. Are you trying to run commands through the terminal while Synaptic Package Manager or Software Center is open.

---

### Post by akawhitey on 2010-08-14
I  believe they are both closed. Is there a simple way to find out?

I did this:
laptop:~$ sudo killall dpkg 
dpkg: no process found

---

### Post by akawhitey on 2010-08-14
Also the update manager is hung and won't close the others are closed

---

### Post by akawhitey on 2010-08-14
Also, when I try to restart I get At SPI Registry Not Responding

---

### Post by rollin on 2010-08-14
> **akawhitey said:**
> Also, when I try to restart I get At SPI Registry Not Responding

There are bugs I believe that relate to the problem but as far as I understand you can boot back into the Ubuntu system though?

If so can you get a screenshot of: Go to System>Administration>System Monitor and click the tab titled "Processes".

You could also do this by typing "top" into a Terminal. 

This should help provide a bit more info with what is running on the system. Welcome to the forum BTW!

---

### Post by akawhitey on 2010-08-14
> **rollin said:**
> There are bugs I believe that relate to the problem but as far as I understand you can boot back into the Ubuntu system though?

If so can you get a screenshot of: Go to System>Administration>System Monitor and click the tab titled "Processes".

You could also do this by typing "top" into a Terminal. 

This should help provide a bit more info with what is running on the system. Welcome to the forum BTW!

Thanks for the welcome. I have no idea how to do a screen shot, but saw the AT SPI Registry in the system monitor, I killed it and was then able to install the updates. After the restart, I was able to install the Skype program (what I was originally trying to do).

Thanks for your help. Now I will go try and find how to do a screen shot for next time! Thanks again!

---

### Post by akawhitey on 2010-08-14
I can't believe I wasted so much time before asking, thanks again!

---

### Post by rollin on 2010-08-15
> **akawhitey said:**
> Thanks for the welcome. I have no idea how to  do a screen shot, but saw the AT SPI Registry in the system monitor, I  killed it and was then able to install the updates. After the restart, I  was able to install the Skype program (what I was originally trying to  do).

Thanks for your help. Now I will go try and find how to do a screen shot for next time! Thanks again!
 
Your most welcome. You seemed to have found the solution though and thanks for posting it, which will help other people! 
For the screenshot have a look under menus: Applications>Accessories>Screenshot. There should be quite a lot of info around on the subject but something like this may help  [http://www.addictivetips.com/ubuntu-linux-tips/three-ways-to-capture-screenshot-in-ubuntu-linux/](http://www.addictivetips.com/ubuntu-linux-tips/three-ways-to-capture-screenshot-in-ubuntu-linux/)

> **akawhitey said:**
> I can't believe I wasted so much time before asking, thanks again!

Absolutely not! Your research means your learning for yourself which is much better than just getting answers. You'll be the one with the knowledge helping people in no time. Good luck and have fun with it :)

---

### Post by akawhitey on 2010-08-15
For the screenshot have a look under menus: Applications>Accessories>Screenshot. There should be quite a lot of info around on the subject but something like this may help  [http://www.addictivetips.com/ubuntu-linux-tips/three-ways-to-capture-screenshot-in-ubuntu-linux/](http://www.addictivetips.com/ubuntu-linux-tips/three-ways-to-capture-screenshot-in-ubuntu-linux/)

If it is better for me to start a new question, I will. But I am using the Ubuntu Netbook Edition, which rather than having the layout form your link like on this page: [https://wiki.ubuntu.com/UNR](https://wiki.ubuntu.com/UNR)

When I click accessories on the sidebar only a few program show up, even though Gnome Utilities is loaded there is no icon or words that say screen shot (which is surprising given your example above). I was able to access the screen shot tool through the terminal using "gnome-screenshot"

My question is in UNE is there a way to search through, and activate, installed applications without using the terminal?

---

### Post by akawhitey on 2010-08-15
Got it! Had to go into system>main menu then highlight the category (ie accessories) then check box screenshot then it showed up in the appropriate spot in the GUI. 

Thanks again. I might just get the hang of this.

---

### Post by rollin on 2010-08-15
> **akawhitey said:**
> Got it! Had to go into system>main menu then highlight the category (ie accessories) then check box screenshot then it showed up in the appropriate spot in the GUI. 

Thanks again. I might just get the hang of this.

Outstanding! I think you are already getting the hang of it. Again finding your answers and trying to solve things I think is a great idea. If you're stuck or need advice then absolutely open a thread and get typing. It's a friendly place with loads of expertise so don't be shy create some threads ;) Also as a last tip, check out "man" command in front of the program name if you need more info. Eg 
 
```
man gnome-screenshot
```

You might be suprised how much info you can get trying this out on different programs. To exit hit "q" or to print to a text file saved in your home directory just add >"chosenname" Eg:

```

man gnome-screenshot>screenshotsmanpage
```

Have fun! :)

---

