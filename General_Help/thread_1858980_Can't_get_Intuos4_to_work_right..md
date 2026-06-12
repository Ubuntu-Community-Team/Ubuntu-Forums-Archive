---
title: "Can't get Intuos4 to work right."
date: 2011-10-13
forum: General Help
---

### Post by KozaG on 2011-10-13
Hello,

I have now searched for two day a way to get my LEDs working in my intuos4 L pad. I have found guides but I guess I don't understand them. My pad just don't work. 

Here is some guides I've tried to follow:
[http://www.davidrevoy.com/index.php?article70/set-the-led-display-of-the-wacom-intuos4-tablet-on-ubuntu-linuxmint](http://www.davidrevoy.com/index.php?article70/set-the-led-display-of-the-wacom-intuos4-tablet-on-ubuntu-linuxmint)
[http://braindump.kargulus.de/](http://braindump.kargulus.de/)

I'm completely new to Ubuntu (using 10.10). If you are willing to help me please threat me as a total novice. I know how to start Terminal and how to copy paste lines. But that is about it. Please point me to some clear guide or tell it yourself how in heck I'm going to get my pad LED's working and adjusting buttons to regular commands like zoom, ctrl + z, pan etc. Why Ubundu don't have such clear programs what Windows had when editing your pad?

I'm an artist and don't have brains to learn how to hack things. I've just switched from Windows XP and don't want to go back! 

Please.

---

### Post by Favux on 2011-10-14
Hi KozaG,

Welcome to Ubuntu forums!

Support for the Intuos LED's was just added to the 3.2 kernel by Eduard Hasenleithner and his xsetwacom support is currently being added to the xf86-input-wacom driver:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Wacom_Tablet_Set_Up#Intuos4_LED_and_OLED](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Wacom_Tablet_Set_Up#Intuos4_LED_and_OLED)

The Intuos4 OLED thread has an earlier way to get them working from Christoph Karg (the author of the blog in your second link) along with some modifications of it by sanette.  These were then adapted to handle one of Eduard's earlied kernel patches:  [http://ubuntuforums.org/showthread.php?t=1380744&page=25](http://ubuntuforums.org/showthread.php?t=1380744&page=25)  Notice support has been backported to input-wacom so you don't necessarily need to wait for the 3.2 kernel.  No one's tried that yet that I know about.  Anyway your best shot currently is to post on that thread and hope someone who has done it will help you.

Configuring the buttons is not difficult.  See:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration)

By the way both HOW TO's are on the Linux Wacom Project's mediawiki HOW TO page:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO)  A sample xsetwacom script is on the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") as well as instructions on cloning input-wacom in appendix II.

On the HOW TO page in External Programs are some links to configuration gui's.  Because of all the changes to the driver in the last year whether they work or not is sort of hit or miss.  Oneiric has GNOME 3.2 and that has the first version of a Wacom tablet control panel applet in System Settings.  It only handles the stylus in this first version.  But it is a start.

---

### Post by KozaG on 2011-11-07
Thank you for your help.

If there is an application in the newest Ubuntu to setup your Wacom keys. Do you suggest that it would be wise to update my Maverick Meerkat 10.10 to Oneiric 11.10?

---

### Post by Favux on 2011-11-07
I wouldn't update to Oneiric just yet until they fix this bug:  [https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/863154](https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/863154)  That's assuming you want to use Gimp.

Besides the first version of things in Oneiric/GNOME 3.2 aren't as flexible as xsetwacom commands anyway at this point.

---

### Post by KozaG on 2011-11-08
After setting xsetwacom command they reset after computer restart. How do I prevent this? Do I need to make a script or to write xsetwacom commands to some start-up file?

Also it seems that I have old parameter names ([http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xsetwacom#Table_of_New_Parameter_Names](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xsetwacom#Table_of_New_Parameter_Names)):
eg. Command xsetwacom set "Wacom Intuos4 8x13 pad" Button 3 "key alt" will not work for me. I need to write button3 [with out the space].

Is it because my xf86-input-wacom is not up-to-date? Is there a easy way to update it?

---

### Post by Favux on 2011-11-08
The BambooPT HOW TO linked above shows you how to do both.  Part II updates xf86-input-wacom and part IV. shows how to autostart a script file.

---

### Post by KozaG on 2011-11-09
Great! Thanks! :)

---

### Post by KozaG on 2011-11-09
I followed both parts, II and IV. Copied every line and made sure that I copied the whole line, also the hidden part.

Now I think my xsetwacom or something else is even more crazy. I do have now new parameter names thou.

In terminal typing this: 
"xsetwacom get "Wacom Intuos4 8x13 pad" button 9"
gives me this:
"key +Control_L +z -z"
It is undo command BUT pressing the lowest button in my Intuos4 pad, which is the button 9, nothing happends. And guess what? Button 9 is not moved to replace button 5 (next button above the touch ring). So pressing that button does the undo. It should be TAB.
"xsetwacom get "Wacom Intuos4 8x13 pad" button 5" gives
"key +Tab -Tab"

I have installed Wacom Control Panel. Maybe that disturbes somehow. I just don't know how to uninstall it. I can't find it neither in Ubuntu Software Center nor in Synaptic Package Manager.

---

### Post by Favux on 2011-11-09
The Wacom Control Panel is called wacom-utility in Synaptic.  The configuration gui's have had a tough time keeping up with all the changes made to xf86-input-wacom over the last year or so.  So maybe uninstall that first.

Then check and see if your button map takes into account Xinput reserving 4 to 7 for vertical and horizontal scroll, i.e. you see the jump of 4 after button 3 so it goes 1, 2, 3, 8, 9, etc.

---

### Post by KozaG on 2011-11-11
Ok, I managed to uninstall Wacom Control Panel but it doesn't make anything diffirent.

> **Favux said:**
> Then check and see if your button map takes into account Xinput reserving 4 to 7 for vertical and horizontal scroll, i.e. you see the jump of 4 after button 3 so it goes 1, 2, 3, 8, 9, etc.

This is something I didn't understand. How do I check it?

---

### Post by Favux on 2011-11-11
Use the *xsetwacom get* command to see what the button is set at.  Then use the *set* command to reassign it.  Then check again with the *get* command to see if the assignment worked.  For example to get your physical button 4 assigned the way you wanted did you have tell X it was button 8?  If so you end up have a physical button number mapping to a X button number.

---

### Post by KozaG on 2011-11-17
I have mapped all my pad's keys from a to k to make this simple.

This is what I've set:
[SIZE="1"]konstantin@konstantin:~$ xsetwacom set "Wacom Intuos4 8x13 pad" Button 1 "key a"
konstantin@konstantin:~$ xsetwacom set "Wacom Intuos4 8x13 pad" Button 2 "key b"
konstantin@konstantin:~$ xsetwacom set "Wacom Intuos4 8x13 pad" Button 3 "key c"
konstantin@konstantin:~$ xsetwacom set "Wacom Intuos4 8x13 pad" Button 4 "key d"
konstantin@konstantin:~$ xsetwacom set "Wacom Intuos4 8x13 pad" Button 5 "key e"
konstantin@konstantin:~$ xsetwacom set "Wacom Intuos4 8x13 pad" Button 6 "key f"
konstantin@konstantin:~$ xsetwacom set "Wacom Intuos4 8x13 pad" Button 7 "key g"
konstantin@konstantin:~$ xsetwacom set "Wacom Intuos4 8x13 pad" Button 8 "key h"
konstantin@konstantin:~$ xsetwacom set "Wacom Intuos4 8x13 pad" Button 9 "key i"
konstantin@konstantin:~$ xsetwacom set "Wacom Intuos4 8x13 pad" AbsWheelUp "key j"
konstantin@konstantin:~$ xsetwacom set "Wacom Intuos4 8x13 pad" AbsWheelDown "key k"
[/SIZE]

GET command shows me this:
[SIZE="1"]konstantin@konstantin:~$ xsetwacom get "Wacom Intuos4 8x13 pad" Button 1
key +a -a 
konstantin@konstantin:~$ xsetwacom get "Wacom Intuos4 8x13 pad" Button 2
key +b -b 
konstantin@konstantin:~$ xsetwacom get "Wacom Intuos4 8x13 pad" Button 3
key +c -c 
konstantin@konstantin:~$ xsetwacom get "Wacom Intuos4 8x13 pad" Button 4
key +d -d 
konstantin@konstantin:~$ xsetwacom get "Wacom Intuos4 8x13 pad" Button 5
key +e -e 
konstantin@konstantin:~$ xsetwacom get "Wacom Intuos4 8x13 pad" Button 6
key +f -f 
konstantin@konstantin:~$ xsetwacom get "Wacom Intuos4 8x13 pad" Button 7
key +g -g 
konstantin@konstantin:~$ xsetwacom get "Wacom Intuos4 8x13 pad" Button 8
key +h -h 
konstantin@konstantin:~$ xsetwacom get "Wacom Intuos4 8x13 pad" Button 9
key +i -i 
konstantin@konstantin:~$ xsetwacom get "Wacom Intuos4 8x13 pad" AbsWheelUp
0
konstantin@konstantin:~$ xsetwacom get "Wacom Intuos4 8x13 pad" AbsWheelDown
0
[/SIZE]

Here "is" my pad:

[Button 2] Pressing this gives me "b"
[Button 3] Pressing this gives me "c"
[Button 4] Pressing this gives me "h"
[Button 5] Pressing this gives me "i"

[AbsWheelUp] Revolving the touchwheel clockwise gives me "jjjjjjj..."
[Button 1] Pressing this gives me "a"
[AbsWheelDown] Revolving the touchwheel counterclockwise, nothing happens

[Button 6] Pressing this gives, nothing happens
[Button 7] Pressing this gives, nothing happens
[Button 8] Pressing this gives, nothing happens
[Button 9] Pressing this gives, nothing happens

Hopefully this is clear enough to understand how my keys are mixed. I don't know what is wrong here.

ps. I updated my Ubuntu to 11.04.

---

### Post by Favux on 2011-11-17
Hi KozaG,

So now using Natty.

Alright.  So define physical button as the actual pad button order.  Then the X button number is what X thinks the button number is.  Because buttons 4 through 7 are reserved for scroll there is a jump of 4 between the physical button number and the X button number after Button 3.  This gives you:

Physical v.s. X         Button number
[Button 2] > [Button 2]
[Button 3] > [Button 3]
[Button 4] > [Button 8]
[Button 5] > [Button 9]

[AbsWheelUp]
[Button 1] > [Button 1]
[AbsWheelDown]

[Button 6] > [Button 10]
[Button 7] > [Button 11]
[Button 8] > [Button 12]
[Button 9] > [Button 13]

Not sure what's going on with AbsWheel.  Because we are having problems assigning the Airbrush scrollwheel also I'm starting to wonder if a bug was introduced to AbsWheel, and that's the problem.

---

