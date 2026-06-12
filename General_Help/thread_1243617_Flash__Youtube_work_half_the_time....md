---
title: "Flash / Youtube work half the time..."
date: 2009-08-18
forum: General Help
---

### Post by x C0MMAND0 x on 2009-08-18
I'm getting pretty tired of flash not working for one reason or another.  I have 64bit 9.04, Dell XPS m1330.  Everytime flash doesn't work, I do the following.

1. Close firefox
2. Open terminal
3. sudo apt-get purge flashplugin-nonfree
4. sudo apt-get install flashplugin-nonfree
5. start firefox again

Then it will work for a few days.  When I go to a video on youtube, it doesn't even give the "install flash player" option, it just is a big white box as if nothing was there. 

Also, when I go to [http://www.xbox.com/en-US/hardware/accessories](http://www.xbox.com/en-US/hardware/accessories) and click on the image it brings me to the adobe download site.

What should I do here?

---

### Post by razorboy5 on 2009-08-18
how did u install flash?
 
there was a few metods of installing when i did it
 
the newest "alpha version of 64bit flash" seems quite stable, for me at least

---

### Post by x C0MMAND0 x on 2009-08-18
I installed from the terminal...how do you install the "alpha" you were talking about?

---

### Post by x C0MMAND0 x on 2009-08-19
bump...

---

### Post by Cygnia on 2009-08-19
I'm also on 64 bit Jaunty and I have the same issue, only much more often, nearly a dozen times per day. I hope they figure out a fix for it.

---

### Post by razorboy5 on 2009-08-19
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)
 
download this file, it should be libflashplayer.so
 
go to home find .mozilla inside .mozilla create a folder called 'plugins' and add the libflashplayer.so file into the plugins folder and restart firefox
 
u may need to disable the 32bit of the flash player by removing ndiswrapper from Synaptic
 
sry again for being vague as i'm on XP again :S
 
also if ur using OSS4 u may need libflashsupport.so to hear sound

---

### Post by x C0MMAND0 x on 2009-08-31
That actually worked!  I will let you know if it works long term of if I continue to have issues...thank you!

---

### Post by x C0MMAND0 x on 2009-09-11
K.  Still having issues with Flash working all the time.  I use some websites that go along with some of my college textbooks that have videos that show how to do certain engineering problems.  I need to be able to view them to do my homework, and it is very frustrating when I'm trying to work and all of a sudden flash quits working. 

I have 64bit jaunty.  Any more suggestions or solutions?

---

### Post by NoaHall on 2009-09-11
First , make sure you don't have the bad ones in your package manager

Download the file from here -
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)
and extract it. You should get a file called "libflashplayer.so". 

Now, open a terminal (Applications -> Accessories -> Terminal )


Then run "sudo cp /home/$USERNAME/Desktop/libflashplayer.so /usr/lib/firefox-addons/plugins/libflashplayer.so"

It doesn't matter if you don't use firefox - most browsers now link to there anyway, and you change the place of which they point to (ah the beauty of open-sourceness).

Now, you have Flash 64 bit, which is better than performing than the 32 bit one on 32 bit OS's ! Enjoy.

---

### Post by x C0MMAND0 x on 2009-09-11
I put that file in the folder...should I now uninstall  versions of it from synaptic?  If so, what files am I supposed to uninstall?

---

### Post by NoaHall on 2009-09-11
Well, try and see if works first - then if it doesn't uninstall and try again.

---

### Post by x C0MMAND0 x on 2009-09-11
When I searched for "flash" in synaptic, I have the following installed (see screenshot)

---

### Post by x C0MMAND0 x on 2009-09-11
And I've had that file in the folder for a week or so now, and it has been working better, but not perfect yet...So I'm guessing I need to uninstall something...Thanks for your help also.

---

### Post by NoaHall on 2009-09-11
Maybe uninstalling all but the top one.

---

### Post by pelago on 2009-09-27
> **razorboy5 said:**
> [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)
 
download this file, it should be libflashplayer.so
 
go to home find .mozilla inside .mozilla create a folder called 'plugins' and add the libflashplayer.so file into the plugins folder and restart firefox


I've had trouble with Flash on 64-bit Jaunty for months (usually that Flash just stopped working in Firefox, and I had to quit and restart Firefox to fix it, at least once a day). After doing the above, I've been fine for a few weeks, so that's great.

---

### Post by x C0MMAND0 x on 2009-09-28
I have also had no issues since I applied this fix.  Thank you very much.

---

