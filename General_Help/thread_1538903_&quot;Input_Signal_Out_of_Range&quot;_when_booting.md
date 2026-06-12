---
title: "&quot;Input Signal Out of Range&quot; when booting"
date: 2010-07-25
forum: General Help
---

### Post by 8jwong14 on 2010-07-25
Hello.  I have a HP w1907 monitor and when I boot my PC and get to BURG, the monitor shows the the "input signal is out of range" and to change settings to 1440 x 900 and 60 ghz.  This message won't go away until I select an OS to boot.  The message blocks the the center of BURG where I select the OS but I can still select the Os although the image is partly blocked by the "Input Signal Out of Range" message.  Using BURG-Manager I set the Resolution to 1440 x 900 but I still get the message.

---

### Post by robsoles on 2010-07-26
Can you confirm that when you set 1440x900 you are also setting 60Hz refresh rate?

---

### Post by 8jwong14 on 2010-07-26
> **robsoles said:**
> Can you confirm that when you set 1440x900 you are also setting 60Hz refresh rate?
Thanks for the quick reply.  For BURG I know I can set the resolution but In don't know how to set the refresh rate.

---

### Post by robsoles on 2010-07-26
Can you ditch BURG and just use the 'monitors' out of 'System'->'Preferences' instead?

---

### Post by 8jwong14 on 2010-07-26
> **robsoles said:**
> Can you ditch BURG and just use the 'monitors' out of 'System'->'Preferences' instead?
What do you mean ditch BURG? When I go to System>Preferences>Monitors, I can set the resolution but not the refresh rate.  I set it to 1440x900 and 60 ghz(The only option)

---

### Post by robsoles on 2010-07-26
When I tried to checkout BURG on the internet a quick impression I took is that it is an alternative monitor/video manager - please link to a page on the internet that has info about the BURG you are using.

---

### Post by 8jwong14 on 2010-07-26
> **robsoles said:**
> When I tried to checkout BURG on the internet a quick impression I took is that it is an alternative monitor/video manager - please link to a page on the internet that has info about the BURG you are using.
BURG is an graphical boot-loader based on GRUB.  
[http://www.omgubuntu.co.uk/2010/01/make-grub-themes-beautiful-look-nicer.html](http://www.omgubuntu.co.uk/2010/01/make-grub-themes-beautiful-look-nicer.html)
I installed BURG using BURG-Manager since it is easier as I don't need to use much command lines.  
[http://www.omgubuntu.co.uk/2010/07/burg-boot-loader-installation-themeing.html](http://www.omgubuntu.co.uk/2010/07/burg-boot-loader-installation-themeing.html)

---

### Post by robsoles on 2010-07-26
OK, now I've had a very brief read around;

source: [http://code.google.com/p/burg/](http://code.google.com/p/burg/) which links to

here-ish: [https://help.ubuntu.com/community/Burg](https://help.ubuntu.com/community/Burg) & forum: [http://www.burgloader.com/](http://www.burgloader.com/)


I didn't spot a way to set the refresh rate that BURG will use to display your boot menu with, mentions of 'refresh rate' in their forum seemed to be more a matter of how long the program took to redraw it's GUI rather than the monitor's refresh rate - maybe my search terms weren't good enough, I only tried one search in their forum.


I hate these 'clever' monitors that keep that blasted message on display while a non-optimal display setting is being used, dumbest stuff I've come across in years.

I spent a while on the phone with Samsung clowns over it - they don't seem to understand that having the message flashed up for 3 seconds every 20 or more seconds in a corner would make their equipment much more usable in more circumstances - Samsung reps told me I'd be better off in Windows and I told them I could find other manufacturers for future purchases!


I wonder if BURG is meant to refer to your /etc/X11/xorg.conf (and related files) to get a correct refresh rate - the developer(s) are probably paying attention in it's own forum and pursuing it there is bound to get you better results than my responses IMHO.

---

### Post by 8jwong14 on 2010-07-27
> **robsoles said:**
> OK, now I've had a very brief read around;

source: [http://code.google.com/p/burg/](http://code.google.com/p/burg/) which links to

here-ish: [https://help.ubuntu.com/community/Burg](https://help.ubuntu.com/community/Burg) & forum: [http://www.burgloader.com/](http://www.burgloader.com/)


I didn't spot a way to set the refresh rate that BURG will use to display your boot menu with, mentions of 'refresh rate' in their forum seemed to be more a matter of how long the program took to redraw it's GUI rather than the monitor's refresh rate - maybe my search terms weren't good enough, I only tried one search in their forum.


I hate these 'clever' monitors that keep that blasted message on display while a non-optimal display setting is being used, dumbest stuff I've come across in years.

I spent a while on the phone with Samsung clowns over it - they don't seem to understand that having the message flashed up for 3 seconds every 20 or more seconds in a corner would make their equipment much more usable in more circumstances - Samsung reps told me I'd be better off in Windows and I told them I could find other manufacturers for future purchases!


I wonder if BURG is meant to refer to your /etc/X11/xorg.conf (and related files) to get a correct refresh rate - the developer(s) are probably paying attention in it's own forum and pursuing it there is bound to get you better results than my responses IMHO.
Thanks.  I've also searched around the web and couldn't find anything about setting the refresh rate.  A reason I'm so annoyed with my HP monitor is because BURG displays properly and nicely but the "input signal out of range" has to pop up right in the middle of the screen.  HP should at least have the message appear in a corner and make the message smaller and less attention grabbing.  This is  why I don't want to get another HP monitor next time.  I might go with ACER, ASUS, etc.  Perhaps you could provide some recommendations?  Thanks again.

---

### Post by robsoles on 2010-07-27
My Acer monitors don't seem to have this nonsense but unfortunately to be sure you are not buying another of these lemons I would recommend taking your PC (hopefully a Laptop!!!) to the shop and making them show your prospective new monitor's behavior under your preferred circumstances.

Any manufacturer could make anything make themselves look like dimwits anytime they like!

That Samsung monitor allows the user to 'hide the message' but it comes back after about a minute each time and smack bang in the darn middle of the display again - most annoying when you are trying to find why x has bombed your user's previous settings before just giving in and re-writing their config!

---

### Post by 8jwong14 on 2010-07-27
> **robsoles said:**
> My Acer monitors don't seem to have this nonsense but unfortunately to be sure you are not buying another of these lemons I would recommend taking your PC (hopefully a Laptop!!!) to the shop and making them show your prospective new monitor's behavior under your preferred circumstances.

Any manufacturer could make anything make themselves look like dimwits anytime they like!

That Samsung monitor allows the user to 'hide the message' but it comes back after about a minute each time and smack bang in the darn middle of the display again - most annoying when you are trying to find why x has bombed your user's previous settings before just giving in and re-writing their config!
Thanks for the advice.  Personally, i dislike Samsung products because for me they've had products.  For example, I have a Samsung laser AIO and laser Printer that both use the same toner.  Yet, when I take the toner from one that has been partially used, and put it into another, it refuses to work.  I did research and found that the toners have chips to prevent refilling and switching between printers!  Also, Samsung still tends to use proprietary ports which I don't like at all.  I think I'll try Acer.

---

