---
title: "Thinking of switching to ubuntu"
date: 2011-03-24
forum: General Help
---

### Post by dlemos on 2011-03-24
Hi all

I tried ubuntu 10.0 yesterday (running from my usb pen) and I liked it. A lot. 

However, there are a few issues that i need to know if there's any way to solve them, before making the transition:

-  Keyboard keys are swapped; I mean, if I press alt+(anyNumber) I get another character. Why does this happen?

-I develop a lot of code in VBA; I tried to record a macro using Open Office Calc, but I got the impression that the code used in the recorded macro is slightly different... Can anyone confirm this?

- Can I run Photoshop Cs5 in Ubuntu?

Thank you =)

---

### Post by Zirts on 2011-03-24
Photoshop Cs5 will work on Ubuntu, but you have to use Wine for it.
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=20158](http://appdb.winehq.org/objectManager.php?sClass=version&iId=20158)
As you see from the link it's given a gold, so it works very well.

About the keyboard problem,  you can change everything to the way it was before when you used Windows, in System > Preferences > Keyboard.

---

### Post by mendhak on 2011-03-24
About the keyboard keys - I think you may be referring to "Alt Gr".  On many keyboards now, the right Alt key is "Alt Gr" and when you press it you get an alternate character.  For example, when I press AltGr+4, I get the Euro symbol.  I believe you can get rid of this if you change your keyboard layout to a default one, but you'll need to experiment or just learn to use it.

About macros - the macros you develop in Open Office are a port of VBA; they have tried to get it as close to VBA as possible so that MS Office users can easily transition over.  There are, however, slight differences such as your object declarations which will not be COM objects but packages such as "com.sun.star.frame.DispatchHelper".  

Photoshop doesn't run natively on Ubuntu.  You can either try Gimp or you can try to run it on Wine.  Since you're starting out, I suggest you get an app called "PlayOnLinux" which will get the correct Wine prefix for you in order to run CS5.  If there are other Windows apps that you want to run, you can check their compatibility and "how well they do" on the WineHQ website.  Here's the page for Photoshop:

[http://appdb.winehq.org/appview.php?appId=17](http://appdb.winehq.org/appview.php?appId=17)

You can see that CS5 is level Gold which means it isn't perfect but most of it should work. You can see that CS runs almost perfectly.  When I transitioned over, I didn't like OpenOffice so I was running MS Office (Word, PPT and Excel only) on Wine which I installed using PlayOnLinux. 

You said you're currently running off a USB stick.  Might I suggest you get a dual boot set up (using wubi) and then try these things out?  The great thing with wubi is you can then uninstall it from within Windows when you want to start afresh.

One more thing to add - you can also make Ubuntu a main OS and use VirtualBox to run Windows in it which hosts your "I can't live without it" apps.  For example, on Ubuntu 10.10, I am running VirtualBox in which I run Adobe Lightroom and Visual Studio.

---

### Post by mastablasta on 2011-03-24
> **dlemos said:**
> Hi all
 
I tried ubuntu 10.0 yesterday (running from my usb pen) and I liked it. A lot. 
 
However, there are a few issues that i need to know if there's any way to solve them, before making the transition:
 
- Keyboard keys are swapped; I mean, if I press alt+(anyNumber) I get another character. Why does this happen?

During install you would select your keyboard layout and that will fix the "issue". 
 
> 
-I develop a lot of code in VBA; I tried to record a macro using Open Office Calc, but I got the impression that the code used in the recorded macro is slightly different... Can anyone confirm this?

 
Macros are not covered so good and can often be incomaptible with MS Excel. 
 
> 
- Can I run Photoshop Cs5 in Ubuntu?
 
Thank you =)
 
No, not fully: 
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=20158](http://appdb.winehq.org/objectManager.php?sClass=version&iId=20158)
 
Can be run through WINE but considerign Wine is simualtion of sorts you might need a much stronger maschine to process something than you would in its native OS (Windows) environment.
 
If you use applications that are based exclusively on MS Windows then there is not much point into switching to Linux. Linux has it's own applications (e.g. GIMP for photo editing, Inkscape for vector graphics design...).
 
then again you can always dual boot and learn.

---

### Post by grahammechanical on 2011-03-24
Your question:

> Can I run Photoshop Cs5 in Ubuntu?

Is it a Linux program? Ubuntu uses the Linux operating system. We cannot run Microsoft programs as they are coded for the Microsoft operating system. You need to examine a Linux program called wine.

[http://www.winehq.org/](http://www.winehq.org/)

Its purpose is to fool Windows coded programs that they are running under Windows when they are in fact running under Linux. May be it will allow you to run Photoshop. I do not know. I use wine for a specific program that is not available for Linux. You can download and install wine from the Ubuntu Software Centre.

Your question:

 > Keyboard keys are swapped; I mean, if I press alt+(anyNumber) I get another character. Why does this happen?

Do you really mean alt+(any number)? Or shift+(any number)? Are you referring to the way you can in Windows press alt then four numbers and get an accented character that is not available on the keyboard?

When we install Ubuntu we can choose not only the language but also the keyboard layout. We can set up different keyboard layouts to type in different languages. I use this feature in my work. And in my word processor (OpenOffice) I select the Insert menu and click on Special Character, then I get a grid of all the characters available in the font that I am using and I can paste any character into my document. The fonts are unicode fonts so I have available a large number of characters from many languages. It may be possible to do this through an alt key + some numbers combination or some other key combination but I have not worked out how to do it. And the method that I use is good enough for me.

Regards.

---

### Post by Dieselville on 2011-03-24
I recently made the switch, and am so in love with it :) I only use Windows for a few select games now. It takes a while to customise ubuntu to your likings, but once you're done, its absolutely amazing.  :P

---

### Post by DipreSantana on 2011-03-24
About that CS5 on Ubuntu, how could I get a tablet to work with wine?

---

### Post by dlemos on 2011-03-25
Thank you all for your answers.

Well I'm particulary worried about the VBA part...

ABout wine, just to make sure:
Do I get to run directly the programs I want, after I start Wine, or do I need to run Windows on Wine, then start MS Office, like some kind of remote destkop access? (sorry if this question sounds silly but i never used nothing like this before)

---

### Post by 4plaay on 2011-03-25
> **DipreSantana said:**
> About that CS5 on Ubuntu, how could I get a tablet to work with wine?

What tablet are you thinking? Android or OSX tablets don't have the power to run photoshop native, definitely won't happen through an emulator. Possibly some of the windows netbook/tablets could do it but you'd be pushing it.

---

### Post by DipreSantana on 2011-03-26
> **4plaay said:**
> What tablet are you thinking? Android or OSX tablets don't have the power to run photoshop native, definitely won't happen through an emulator. Possibly some of the windows netbook/tablets could do it but you'd be pushing it.

It's an HP business class convertible tablet, I need to get the Wacom crap to work under linux.

---

