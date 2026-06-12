---
title: "Help with Genius Easypen i405X"
date: 2012-01-03
forum: General Help
---

### Post by Kaladze on 2012-01-03
hello everyone, 
I have genius easypen i405X, so i think is almost the same, but i cannot make it work. (O.S. ubuntu 11.10) 
I've tried to follow the steps in several tutorials which I've found on google or on this forum and still nothing.
Can someone please help me?

---

### Post by oldos2er on 2012-01-03
Post moved to its own thread.

---

### Post by Kaladze on 2012-01-05
but why you moved it? this thread wasn't good? [http://ubuntuforums.org/showthread.php?t=1886167&page=2](http://ubuntuforums.org/showthread.php?t=1886167&page=2)
PS: any solutions? :D

---

### Post by oldos2er on 2012-01-05
Nothing personal, but it's generally considered rude to hijack someone else's thread.

It might help if you can give links to tutorials you've tried, or explain what exactly you tried.

---

### Post by Kaladze on 2012-01-06
> **oldos2er said:**
> Nothing personal, but it's generally considered rude to hijack someone else's thread.

It might help if you can give links to tutorials you've tried, or explain what exactly you tried.
Ok, sorry I didn't know that it's better to start a new thread, i'm new on this forum. On other forums is not a good thing to start new threads if they have the same topic.
About my g.tablet i've tried to install wizardpen and followed some steps from 
[http://ubuntuforums.org/showpost.php?p=11572948&postcount=17](http://ubuntuforums.org/showpost.php?p=11572948&postcount=17)
[http://ubuntuforums.org/showthread.php?t=1886167&page=2](http://ubuntuforums.org/showthread.php?t=1886167&page=2)
[http://ubuntuforums.org/showthread.php?t=1886167](http://ubuntuforums.org/showthread.php?t=1886167)
[http://ubuntuforums.org/showthread.php?p=8851715](http://ubuntuforums.org/showthread.php?p=8851715)

and now i'm afriad that i've created a mix :D btw I started with: [https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen) 
When this didn't worked I had tried the others.

About what i've done, I don't remember all the steps, but I think the mainly steps are from the TabletSetupWizardpen

---

### Post by Favux on 2012-01-06
Hi Kaladze,

Sorry it took me so long to find you.  Not quite sure why it took this long.

Anyway the last post (#12) on the thread you apparently were originally on explains the problem.  The new KYE Systems tablets like your i405X and the i608X are not yet supported in the kernel.

The way to get them working is to send the information Nick requests to Nick so he can build kernel patches to the usb hid driver to include your tablet.  However there is an extra twist with the new KYE Systems tablets.  They apparently require sending a specific packet to turn on their tablet mode, instead of the mouse mode they default to.  Nick doesn't know how to do that yet.  He doesn't have one of the KYE tablets to play with, apparently they don't sell them in Finland.  So he needs someone who also has Windows installed and is willing to use a usb packet sniffer in Windows so he can figure out what the magic "tablet on" code is.

For what it is worth to me all of your links seem relevant.  We just don't have a solution yet.

---

### Post by Kaladze on 2012-01-06
Hi Favux,

Thanks for you answer, then I'll have to wait for a solution.
Have a nice day!

---

### Post by Favux on 2012-01-27
[SIZE="3"]**FYI Update**[/SIZE]:

Nikolai Kondrashov with the help of viktoria.s has "discovered the way to make the KYE tablets report all the data, including pressure. This was tested with EasyPen i405X, EasyPen M610X and MousePen i608X in userspace with modified usbhid-dump."

Nick is now working on the kernel driver for the KYE tablets.  He's gone to the extent of ordering an EasyPen i405X from Amazon UK to be delivered to him in Finland!  So with a little luck support should be available shortly.  :)

---

### Post by Favux on 2012-02-15
**[SIZE="3"]FYI Update:[/SIZE]**

Viktoria.s has posted Nick's new kernel support (with instructions) for the Kye Systems new tablets, the EasyPen i405X, EasyPen M610X, MousePen i608 on post #28 here:  [http://ubuntuforums.org/showthread.php?t=1899225&page=3](http://ubuntuforums.org/showthread.php?t=1899225&page=3)  Once the patched kernel driver is in place the evdev X driver should pick up the tablets automatically and you will not have to configure them in a xorg.conf.d .conf file.

The instructions are for Oneiric as is the pre-compiled patched 64-bit kernel.  I am not sure if the Natty evdev driver will work for these tablets like the Oneiric evdev driver does.


**[SIZE="3"]FYI everyone[/SIZE]**:  I've created a new [**HOW TO Add Support for KYE, UC-logic, and Waltop Tablets in Ubuntu**]("http://ubuntuforums.org/showthread.php?t=1946486") which includes the KYE tablet support instructions linked above for Oneiric and Precise.

---

