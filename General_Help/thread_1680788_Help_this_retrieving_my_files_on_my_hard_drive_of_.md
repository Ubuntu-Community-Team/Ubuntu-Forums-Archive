---
title: "Help this retrieving my files on my hard drive of my eMachines W3080 using Windows XP"
date: 2011-02-03
forum: General Help
---

### Post by kma711 on 2011-02-03
I just installed Ubuntu on a computer that was not booting. After hours of trying to boot I only have a half of screen. Did I download the wrong version for a Windows XP Home Edition OS? My first objective is to rescue my files off of my harddrive so I can figure out what's wrong and causing my boot failure. I see the word Install and an X sign near it. Afraid to push. The button does light up and my mouse is working. there are three symbols on the top plane I think one is an Internet symbol with an exclamation point an audio looking symbol and something that looks like it could be a power button symbol. Help.

---

### Post by sikander3786 on 2011-02-03
Welcome to the forums :-)

So basically you mean you've just booted an Ubuntu Live CD and you can only see half of the screen? If yes, reboot and keep on pressing ANY key as soon as the computer starts booting from the CD-ROM. You'll see a menu. Press F6, enable 'nomodeset' and again choose "Try without installing". Hopefully, your graphics problem should be sorted. See here for details.

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

[http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html](http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html)

Secondarily, you want to rescue your files. You'll see a Places menu at the top panel. If you are not seeing it now, it should be visible once you fix the graphics. From the drop down menu, either click your Partition or go to 'Computer' and open up your intended drive. Copy the files to a safe location say external drive.

Once you plug in your external drive, it should automatically be mounted and appear on your desktop from where you can access and read/write the data.

---

### Post by kma711 on 2011-02-03
Well I tried that and maybe I hit the F6 too fast. maybe I did not download the right download. My download only had 14 files were I saw 20 files in the correct view. I do see a button which I pushed that says suspend restart shut down. To the left is a red button with an X that light when you mouse over it. then I can not see anything.
I am going to push the shut down button on the page

---

### Post by kma711 on 2011-02-04
hey I got to the main page tried the nomode set but still getting a half screen when the desktop appears. I have a full page for the main page, but still getting a half of screen. What is the advantage of having ACPI I will try that ok here goes. We are getting further. I did check the disk and it had no errors. HELP!:lolflag:

---

### Post by kma711 on 2011-02-04
OH DOES ANYBODY KNOW WHAT the vga value should be?

---

### Post by kma711 on 2011-02-04
I got some of the steps and read the links but just need that full page. Ugh!

---

### Post by sikander3786 on 2011-02-05
Please post your hardware specs including RAM, graphics card and processor.

---

### Post by kma711 on 2011-02-08
Not sure about these things. I think my processor is AMD Athlon XP Prosessor 3000T, RAM I think is 512 MB DDR (PC2700). eMachines eView monitor somebody changed original video card. Original card was VIA S3  resolution is supposed to be1280 × 1024 @ 60Hz
30~72 KHz (horizontal)
50~160Hz (vertical)

---

### Post by sikander3786 on 2011-02-09
We need to know exactly which graphics card is there in order to find if it is supported under Ubuntu or not. And if not, where to find a workaround.

At the desktop, press Ctrl + Alt + F1. You should see a Terminal tty1. Login and post the output of this command.

```
lspci | grep VGA
```

---

### Post by kma711 on 2011-02-24
OK I am back online. I did the Ctrl + Alt + F1 All I get is a white square with the Ubuntu symbol. maybe I do not understand "at the desktop?"
Also I never had to "log in". I am trying Ubuntu without installing.

---

### Post by sikander3786 on 2011-02-24
As this is an old thread, I would want to ask once more about the actual problem. You are still getting half screen display?

At the desktop means, when you've booted the Live CD and can see the desktop (even half of it), press Ctrl + Alt + F1 and login to the Terminal. Username is 'ubuntu' and password is blank. Then post the output of above mentioned command.

---

