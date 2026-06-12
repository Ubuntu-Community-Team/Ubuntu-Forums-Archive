---
title: "Some update erased graphics card stuff, now I see all black"
date: 2011-07-02
forum: General Help
---

### Post by linux_dream on 2011-07-02
Yesterday night my ubuntu started an automatic update.  Telling me that some stuff were about being erased, other updated, etc.  I clicked on continue, the installation of new packages went without any problem.
Now that I rebooted, I can't enter in Ubuntu.  Well I guess I can, but I can't see anything but a black screen.
If I remember well, the Ubuntu updates erased something with "Nvidia 173", though I'm not 100% sure about the 173.
By the way, I'm (wasn't?) not using the latest nvidia drivers because Unity cannot work (all freezes and took me tons of time to fix that as you can see if you look into my posts here) with my graphic card+latest Nvidia drivers.

So my question is: How do I do to enter in Ubuntu as I used to?  I mean, being able to see something!

A chance I dual boot with Windows XP (that I terribly hate).  It saved me lots of time and still does, apparently.
Thanks in advance.

---

### Post by wildmanne39 on 2011-07-02
> **linux_dream said:**
> Yesterday night my ubuntu started an automatic update.  Telling me that some stuff were about being erased, other updated, etc.  I clicked on continue, the installation of new packages went without any problem.
Now that I rebooted, I can't enter in Ubuntu.  Well I guess I can, but I can't see anything but a black screen.
If I remember well, the Ubuntu updates erased something with "Nvidia 173", though I'm not 100% sure about the 173.
By the way, I'm (wasn't?) not using the latest nvidia drivers because Unity cannot work (all freezes and took me tons of time to fix that as you can see if you look into my posts here) with my graphic card+latest Nvidia drivers.

So my question is: How do I do to enter in Ubuntu as I used to?  I mean, being able to see something!

A chance I dual boot with Windows XP (that I terribly hate).  It saved me lots of time and still does, apparently.
Thanks in advance.
Hi, here is a link that should get you back into ubuntu then you can check your nvidia driver.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by linux_dream on 2011-07-02
Thanks for the link and help.  If I understood well, I must type "
acpi_osi=" in a terminal?

---

### Post by wildmanne39 on 2011-07-02
you add it to the boot parameter on startup, go back and read it again and make sure you understand it, I am leaving for a little while, I will check on you when I get back.

---

### Post by linux_dream on 2011-07-02
> **wildmanne39 said:**
> you add it to the boot parameter on startup, go back and read it again and make sure you understand it, I am leaving for a little while, I will check on you when I get back.
I appreciate very much your help!
What I did was: reboot (since I'm using Windows XP and dual boot with Ubuntu).  When the choice of operative systems appeared, I pressed "E" when selecting Ubuntu.  I edited the text after "squash".  By this I mean I erased the text that was there and wrote "nomodset" instead.
Then I typed "ctrl+x" in order to boot Ubuntu.  I could see the "Ubuntu" logo and just before entering into it, I'm not sure what happened.  Not sure if the screen froze or if never finished to load.  I waited like 15 minutes (went to cook then came back) and the screen was still with the Ubuntu logo.  No mouse cursor, nothing.  I tried to type on my keyboard but nothing hapened.  I had to reboot and use Win XP to post here.
I'm totally lost on what to do now.

---

### Post by wildmanne39 on 2011-07-02
> **linux_dream said:**
> I appreciate very much your help!
What I did was: reboot (since I'm using Windows XP and dual boot with Ubuntu).  When the choice of operative systems appeared, I pressed "E" when selecting Ubuntu.  I edited the text after "squash".  By this I mean I erased the text that was there and wrote "nomodset" instead.
Then I typed "ctrl+x" in order to boot Ubuntu.  I could see the "Ubuntu" logo and just before entering into it, I'm not sure what happened.  Not sure if the screen froze or if never finished to load.  I waited like 15 minutes (went to cook then came back) and the screen was still with the Ubuntu logo.  No mouse cursor, nothing.  I tried to type on my keyboard but nothing hapened.  I had to reboot and use Win XP to post here.
I'm totally lost on what to do now.
Hi, you do not erase the text, you just add nomodset to the end of that line, also you might can use one of the other options on the page instead you just have to try one at a time until it works.;)

---

### Post by linux_dream on 2011-07-02
> **wildmanne39 said:**
> Hi, you do not erase the text, you just add nomodset to the end of that line, also you might can use one of the other options on the page instead you just have to try one at a time until it works.;)
Ah I see.  Well I added the "nomodset" to the line without erasing anything.  I couldn't even see the "Ubuntu" logo.  Black screen.
I've reread the website you gave me in post #2 but I really don't see what to do now.
I don't have a laptop, no fan problem, etc.  No error in display of temperature or something of the like.
Also I can't do all things at a time.  If my screen turns black, I have to reboot and try something else.  But since I can't use internet, I must boot Windows and reread what to do.  (I have no ink in my printer to print the page of the website).
What should I do now?  I can't even enter in Ubuntu.

---

### Post by wildmanne39 on 2011-07-02
> **linux_dream said:**
> Ah I see.  Well I added the "nomodset" to the line without erasing anything.  I couldn't even see the "Ubuntu" logo.  Black screen.
I've reread the website you gave me in post #2 but I really don't see what to do now.
I don't have a laptop, no fan problem, etc.  No error in display of temperature or something of the like.
Also I can't do all things at a time.  If my screen turns black, I have to reboot and try something else.  But since I can't use internet, I must boot Windows and reread what to do.  (I have no ink in my printer to print the page of the website).
What should I do now?  I can't even enter in Ubuntu.Hi, yes you have to try each one, one at a time, I have been in your place and there are only a few options to try and you do them the same way you did the first option, so what I would do is go to the page and right down the few options, then try them one at a time, that is how I have done it in the past.

---

### Post by linux_dream on 2011-07-02
> **wildmanne39 said:**
> Hi, yes you have to try each one, one at a time, I have been in your place and there are only a few options to try and you do them the same way you did the first option, so what I would do is go to the page and right down the few options, then try them one at a time, that is how I have done it in the past.
Ok.
So now I want to try "acpi_osi="
How to add it in the boot options?  I must use Grub?  But it seems it will permanently change the boot options.  I ask to you if it's ok, since I don't want to "break" my Ubuntu even more.

---

### Post by wildmanne39 on 2011-07-03
> **linux_dream said:**
> Ok.
So now I want to try "acpi_osi="
How to add it in the boot options?  I must use Grub?  But it seems it will permanently change the boot options.  I ask to you if it's ok, since I don't want to "break" my Ubuntu even more.Hi, it will only change it for one boot, what it does is allow you to boot so you can go in and fix your driver problem, or if needed, once you are booted you can go back to that page and read how to make it permanent.

---

### Post by linux_dream on 2011-07-03
> **wildmanne39 said:**
> Hi, it will only change it for one boot, what it does is allow you to boot so you can go in and fix your driver problem, or if needed, once you are booted you can go back to that page and read how to make it permanent.
Ok thanks.  
How do I do this?  It's not explained in the link.  I tried to add it after the word "nomodset".  I also tried it after the word I have if I don't erase the boot option I have instead of nomodset but nothing works.
It made no difference if the "acpi_osi=" was there or not.  I guess I didn't put it in the right place.

---

### Post by wildmanne39 on 2011-07-03
> **linux_dream said:**
> Ok thanks.  
How do I do this?  It's not explained in the link.  I tried to add it after the word "nomodset".  I also tried it after the word I have if I don't erase the boot option I have instead of nomodset but nothing works.
It made no difference if the "acpi_osi=" was there or not.  I guess I didn't put it in the right place.Hi, you remove 
nomodset and replace it with the other option because nomodset did not work.

---

### Post by linux_dream on 2011-07-03
> **wildmanne39 said:**
> Hi, you remove 
nomodset and replace it with the other option because nomodset did not work.
What other option?  The one I have if I don't modify anything?  I already tried and there was no difference between putting acpi_osi= and no putting anything.  :/

---

### Post by wildmanne39 on 2011-07-03
> **linux_dream said:**
> What other option?  The one I have if I don't modify anything?  I already tried and there was no difference between putting acpi_osi= and no putting anything.  :/Hi, I want to make sure you are putting the option in the right place, are you putting it in the the line that starts with linux /boot? Now remove the last option you used and replace it with noapic nolapic at the end of the line. Put both of those options in at the same time.

---

### Post by linux_dream on 2011-07-03
> **wildmanne39 said:**
> Hi, I want to make sure you are putting the option in the right place, are you putting it in the the line that starts with linux /boot? Now remove the last option you used and replace it with noapic nolapic at the end of the line. Put both of those options in at the same time.
Sincerely, thanks for your concern about my Ubuntu.  Unfortunately nothing works.  Here is all what I've tried so far, with details:
1)```
linux /boot/vmlinuz-2.6.38-8-generic root=UUID=e115914c-a889-45a6-a8\43-1b81d2d31ec4 ro vga=771  quiet splash vt.handoff=7
```This gives a black screen (can't see anything after I press ctrl+x, not even the Ubuntu logo).  This is the default option.
2)```
linux /boot/vmlinuz-2.6.38-8-generic  root=UUID=e115914c-a889-45a6-a8\43-1b81d2d31ec4 ro vga=771  quiet splash  vt.handoff=7 nomodset
```Gives exactly the same as 1).
3)```
linux /boot/vmlinuz-2.6.38-8-generic  root=UUID=e115914c-a889-45a6-a8\43-1b81d2d31ec4 ro vga=771  quiet splash nomodset
``` This way I see the Ubuntu logo (with 5 red dots under it) and nothing else.  I waited 15 minutes and still no change.
4)```
linux /boot/vmlinuz-2.6.38-8-generic  root=UUID=e115914c-a889-45a6-a8\43-1b81d2d31ec4 ro vga=771  quiet splash noapic nolapic
```Gives me exactly the same as 3).


Edit: I forgot to say I tried the acpi_osi= but got no change either.

---

### Post by Swagman on 2011-07-03
[COLOR="White"]As you have a black screen I'm surprised no-ones written in white so you can see it !!

Poor Joke I know (I'll get me coat)[/COLOR]

---

### Post by wildmanne39 on 2011-07-03
Hi, ok lets look at this from a different perspective, please put run this script and post the information from this script so we can see where everything is located:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans

Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

### Post by linux_dream on 2011-07-03
> **wildmanne39 said:**
> Hi, ok lets look at this from a different perspective, please put run this script and post the information from this script so we can see where everything is located:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans

Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Thanks once again for your help.
What do I do if I have only Windows XP?  I mean, I can't enter in Ubuntu.  I downloaded the .zip file.  What do I do now?  I could maybe run Ubuntu in safe mod, but not sure how to enter in my Windows XP desktop (this is where my .zip file is).

---

### Post by wildmanne39 on 2011-07-03
> **linux_dream said:**
> Thanks once again for your help.
What do I do if I have only Windows XP?  I mean, I can't enter in Ubuntu.  I downloaded the .zip file.  What do I do now?  I could maybe run Ubuntu in safe mod, but not sure how to enter in my Windows XP desktop (this is where my .zip file is).Hi, I am sorry I got distracted and forgot to tell you to boot from your livecd or usb stick whichever you use to install ubuntu, and click try, then you can run that script and post it using the livecd.

---

### Post by linux_dream on 2011-07-03
> **wildmanne39 said:**
> Hi, I am sorry I got distracted and forgot to tell you to boot from your livecd or usb stick whichever you use to install ubuntu, and click try, then you can run that script and post it using the livecd.
I installed Ubuntu more than 1 year ago, I think it was Ubuntu 8. something.  I don't think I still have the CD.  Now my CD/DVD reader is broken (I went to the store where I bought it to repair it but they said it can't be repaired so I must buy a new one).  I don't have a pendrive either.
:/

---

### Post by wildmanne39 on 2011-07-03
Hi, I am out of ideas, without being able to use a livecd or pendrive. Maybe someone else will have an idea.

---

### Post by linux_dream on 2011-07-03
> **wildmanne39 said:**
> Hi, I am out of ideas, without being able to use a livecd or pendrive. Maybe someone else will have an idea.
Thanks.  I hope so too.
My idea is: enter in safe mod.  Download old Nvidia drivers with a command (that I don't know).  Then modify a file to tell my cpu to use the old Nvidia drivers; with a text editor.
Could this work?

---

### Post by wildmanne39 on 2011-07-03
> **linux_dream said:**
> Thanks.  I hope so too.
My idea is: enter in safe mod.  Download old Nvidia drivers with a command (that I don't know).  Then modify a file to tell my cpu to use the old Nvidia drivers; with a text editor.
Could this work?Hi, one last idea boot recovery and run these to commands, even if the first one fails run the second one.
```
sudo rm /etc/X11/xorg.conf

```
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by linux_dream on 2011-07-03
> **wildmanne39 said:**
> Hi, one last idea boot recovery and run these to commands, even if the first one fails run the second one.
```
sudo rm /etc/X11/xorg.conf

``````
sudo dpkg-reconfigure xserver-xorg
```
WOWWWWWWW  Hey this worked! I mean removing the xorg.conf worked!  Hi from Ubuntu :D  
Thank you so much!  :D

---

### Post by wildmanne39 on 2011-07-04
> **linux_dream said:**
> WOWWWWWWW  Hey this worked! I mean removing the xorg.conf worked!  Hi from Ubuntu :D  
Thank you so much!  :D
Hi, your welcome, I am glad it did it was my last idea.

---

### Post by linux_dream on 2011-07-04
> **wildmanne39 said:**
> Hi, your welcome, I am glad it did it was my last idea.
Nice one.  It makes me use some new Nvidia drivers (experimentals) instead of the non working 195.  Now I can go back to the 173's ones but for now I'll stick with the experimental drivers. 
I'm very glad to be back on Ubuntu, thanks once again.

---

