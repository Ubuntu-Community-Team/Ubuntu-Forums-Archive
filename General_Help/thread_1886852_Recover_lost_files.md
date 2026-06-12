---
title: "Recover lost files"
date: 2011-11-25
forum: General Help
---

### Post by riddem on 2011-11-25
erm- I sorely need some simple assitance.. My Ubuntu 11 crashed bigtime after switching on a some driver, and I have no way of figuring it all out on my own, so I am going to do a clean reinstall..

However. I in a moment of silliness forgot to make backup of the most essential files on my laptop.. So I want to try to recover them using the windows 7 (gulp!) partition, as that is the only way currently that I can make any meaningful communication with my machine.

So I wonder if anyone can tell me how I go about to enter the main ubuntu partition and retrieving my files onto Windows, before I start from scratch again?

Ok?

---

### Post by Basher101 on 2011-11-25
what i got from your text is, that you want to log into windows, get the data from your ubuntu and then reinstall..

---

### Post by surfer on 2011-11-25
why don't you boot your machine with your ubuntu installation CD (or usb drive), log in to the live session, mount the partitions you need to get data from and copy the data to an external drive?

---

### Post by riddem on 2011-11-25
Thanks, yes, Well I have tried that. And I have also tried getting updates and upgrades, but the buck stops at the loading screen... So yeah, just getting the important bits out of the comp using windows, then reinstalling the whole shebang.

---

### Post by Basher101 on 2011-11-25
you cannot access the linux partition from windows as windows cannot read ext4. You must log in using the Live CD and copy then with the live CD session all your files

---

### Post by riddem on 2011-11-25
That didnt work. Not with USB either... I think it has to do with a graphicdriver I switched on as I was trying to re-establish internet connection... I was at afriends place that is pretty good dabbling with Ubuntu, but in the end I did not have the conscience to ask him for all the ins and outs.. He was also somewhat dumbfounded by it all.

---

### Post by riddem on 2011-11-26
> **Basher101 said:**
> you cannot access the linux partition from windows as windows cannot read ext4. You must log in using the Live CD and copy then with the live CD session all your files

I use USB - the Ubuntu load screen fades to white, and nothing more happens..
:(

---

### Post by HalfEmptyHero on 2011-11-26
What type of graphics card do you have? With my NVIDIA I have to add nomodeset to the boot options whenever I use live cds. If you want to try that, when you get to the load screen that says Try Ubuntu, Test Disk and all that stuff, hit escape and press F4. Then you should see an option where it says nomodeset. Unfortunately, selecting that does nothing. You have to hit escape and type in nomodeset.

---

### Post by mörgæs on 2011-11-26
Next time please use a more descriptive title.

---

### Post by riddem on 2011-11-28
> **HalfEmptyHero said:**
> What type of graphics card do you have? With my NVIDIA I have to add nomodeset to the boot options whenever I use live cds. If you want to try that, when you get to the load screen that says Try Ubuntu, Test Disk and all that stuff, hit escape and press F4. Then you should see an option where it says nomodeset. Unfortunately, selecting that does nothing. You have to hit escape and type in nomodeset.


--- slow going, im off and on the net so... Thanks for the tip, my gfx is [Radeon HD]("http://www.pcworld.com/search?qt=radeon") 6490M graphics chip.. I did as you suggested and that got me to a lower res boot screen that eventually gave way to this message:

     4.271646 Console: switchingto color frame buffer device 80x30
      4.328768 usb 5-3: configuration #1 chosen from 1 choice
ALERT! does not excist. Dropping to shell!

BusyBox v1.13.3 (Ubuntu 1:1 13.3-1ubuntu11) built in shell (ash)
Enter "help" for a list of built in commands

That is the end of the message, then I can type commands thrugh (initframs) - But I dont know what to do?

Yes, wil l try to be more specific in the header next time :)

---

