---
title: "Wirieless driver and other problems..."
date: 2010-12-10
forum: General Help
---

### Post by user1001 on 2010-12-10
I am having problems with wireless adapter driver which is my biggest problem, but while I'm here I thought I'd write my other problems rather than starting a hundred threads.

Because of the numerous problems I face, I am planning to leave the Linux World for good..

The problems I encounter are the following..
**Inconsistencies**
[LIST=1][*]Cursor changing on some apps, such as Clementine and Opera[*]**Weak Wireless adapter support, such that sometimes it doesn't allow me to boot into Ubuntu, it asks me to log in to a command line shell on boot time and sometimes the wireless adapter works straight when I log-in. Sometimes it requires me to pull the adapter out and plug it in again. It often leads me to re-installing the driver for it again through windows wireless drivers**
[/LIST]

**[COLOR="Red"]Note:[/COLOR]** My wireless device is **WPN111** *from* **Netgear**

**And other problems such as ..**
[LIST=1][*]Boot logo is plain text rather than what it's meant to be[*]Memory leak from indicator applet.. 100% memory usage shown on 'top' command
[/LIST]
*and more..*

As I have mentioned in the beginning, my main concern is the wireless driver and the lack of support for wireless (maybe all linux users are wired to their routers.. who knows?)

I may not leave if someone helps me to solve these problems, it seams like linux(Ubuntu) is always going to give me such problems.

Thanks.

---

### Post by ender4 on 2010-12-10
A couple of suggestions.  My first suggestion would be to use Wicd instead of Network Manager.  (Do this by installing Wicd from software manager, removing NetworkManager from the list of startup applications, and ad wicd).  In my experience network manager has been rather finicky on Ubuntu, sometimes it works, sometimes it doesn't.  And no not all linux users are wired to routers.  However, the amount of support Linux has for wireless depends on what adapter you are using.  Most adapters should work out of the box with Ubuntu, but some require separately downloading and installing the drivers yourself.  This isn't terribly hard once you have found the driver, the tricky part is finding the right driver for your adapter.  

You may want to have a look at 
[http://ubuntuforums.org/showthread.php?t=414023](http://ubuntuforums.org/showthread.php?t=414023)
and 
[http://www.techtalkz.com/linux-opensource/380328-ndiswrapper-1-9-wnp111-atheros-ar5523.html](http://www.techtalkz.com/linux-opensource/380328-ndiswrapper-1-9-wnp111-atheros-ar5523.html)

As far as the cursor is concerned, my guess is that those programs override the Desktop's settings for the cursor.  I don't use those programs so I don't know for sure. For Clementine you can probably change the cursor to something that matches what you normally use using the Qt4 Settings (which may or may not be installed).

The logo issue seems pretty minor to me, and the logo is displayed by a program called Plymouth, if that helps.  As for the memory, I would kill the indicator applet. From a cursory google search it doesn't look like you are the only one with that problem, and there is a Bug report filed on it.  Hopefully it will be fixed soon.

As a final note, Ubuntu is just one of many Linux distributions, and it isn't perfect for everyone.  If you like the idea of Linux, are having trouble with Ubuntu, and are willing to try out other alternative, some places to start would be Mint (based on Ubuntu), OpenSUSE, and Sabayon.  A listing of Linux distrubitions can be found at distrowatch.com.  

I hope that that was helpful to you.  And I sincerely hope that you can easily resolve your problems.

---

### Post by Spyderkid on 2010-12-10
1. make sure ndiswrapper is installed (use synaptic if its missing)

2. put the driver disk in and cd to /media/cdrom0/ndis5

3. run: sudo ndiswrapper -i netwpn11.inf

4. run: sudo ndiswrapper -m

5. run: sudo modprobe ndiswrapper (this will happen automatically when you reboot)

6. put the device in the USB slot (if it wasn't there already).



That should work ;)

---

### Post by user1001 on 2010-12-11
> **Spyderkid said:**
> 1. make sure ndiswrapper is installed (use synaptic if its missing)

2. put the driver disk in and cd to /media/cdrom0/ndis5

3. run: sudo ndiswrapper -i netwpn11.inf

4. run: sudo ndiswrapper -m

5. run: sudo modprobe ndiswrapper (this will happen automatically when you reboot)

6. put the device in the USB slot (if it wasn't there already).



That should work ;)

I've done all of these already.. it's still giving me problems, no matter i type my wep key right, it doesn't connect until i type it ten times... :(:(:(:(

---

