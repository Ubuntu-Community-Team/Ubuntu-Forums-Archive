---
title: "Multi Function Printer Problem"
date: 2010-09-24
forum: General Help
---

### Post by Skyline911 on 2010-09-24
Hello Everyone. I'm new to Ubuntu and I'm having real problems getting my Epson DX7450 to scan.  It prints okay.  I've googled and searched lots of forums and I'm not really having a great deal of success. I keep getting sent to the Avansys page and then I just get lost :(   If someone could please help me, I will be eternally grateful. Thank you very much.  Please be gentle with me as I'm a newbie!!

---

### Post by coffeecat on 2010-09-24
> **Skyline911 said:**
> I keep getting sent to the Avansys page and then I just get lost :( 

So did I!

Anyway, I found this bug report:

[https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/385505](https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/385505)

Which is marked as a duplicate of this:

[https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/377977](https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/377977)

If I read that correctly, simply adding "usb 0x4b8 0x838" to the file /etc/sane.d/epson2.conf solves the problem. Before I tell you how to do that - it's very easy - let's just check what's in that file. Open a terminal (Applications > Accessories) and run this command:

```
cat /etc/sane.d/epson2.conf
```Copy and paste the output from the terminal into the message field to post it. I want to make sure your epson2.conf hasn't changed from the default before we go any further.

---

### Post by Skyline911 on 2010-09-25
Hi Coffeecat. Thank you so much for responding so quickly. I have done as you say and this is the result:

# epson2.conf
#
# here are some examples for how to configure the EPSON2 backend

# SCSI
scsi EPSON
# for the GT-6500:
#scsi "EPSON SC"

# Parallel port
#pio 0x278
#pio 0x378
#pio 0x3BC

# USB
usb

# For libusb support for unknown scanners use the following command
# usb <product ID> <device ID>
# e.g.:
# usb 0x4b8 0x110

# Network
# 
# net 192.168.1.123
net autodiscovery


I hope I've done that right....

John.

---

### Post by coffeecat on 2010-09-25
That's fine. In order to get that extra line into that configuration file, I'm going to give you a lengthy terminal command. In order to get it right - one mistake and it won't work or the wrong thing will happen - I suggest you copy and paste from this post. Highlight the code in the code box, copy it to the clipboard with ctrl-C and then paste it to a terminal prompt with ctrl-shift-V. Note that keyboard shortcuts in the terminal need the shift key as well.

Once you've pasted the command in, press enter and you will be prompted for your password. This is your login password. You won't see anything as you type it in - that's normal in the terminal. Don't worry, it's going in so long as you press enter after the password. This is the command to copy and paste:

```
echo "usb 0x4b8 0x838" | sudo tee -a /etc/sane.d/epson2.conf
```Once you've done that, type the command 'cat /etc/sane.d/epson2.conf' in the terminal again to get the contents of the epson2.conf file. You should see the "usb 0x4b8 0x838" line, but without the quotes, at the end.

If that has worked OK, reboot and see if your Epson scanner works now. If it doesn't, we need to check something. The 0x4b8 0x838 number is a unique identifier for that Epson machine. I'm taking it on trust that the person who posted that number in the Launchpad thread got it right. If your Epson scanner is still not working, make sure it is switched on, open a terminal again, and post the output of:

```
lsusb
```The output will include the identifier for your Epson and we can compare it with the above.

---

### Post by Skyline911 on 2010-09-25
Thank you so much, Coffeecat. That has worked a treat.  I just wish I had come here first for help rather than trawling the internet for hours and attempting to follow so many complicated instructions and "solutions". I shall know next time!  Having only been on Ubuntu for about two months, I can honestly say it's getting better and better - especially when I have moments like this!!  Thanks again - I wish there was some way I could repay you... :)

---

### Post by coffeecat on 2010-09-25
You have! I enjoy a problem solved.

Good luck with Ubuntu! :)

---

### Post by Skyline911 on 2010-09-26
I'm back!!

Do you (or anyone!?) know of a way of reliably monitoring the ink levels on the DX7450, please? I have tried using mtink but that does not seem to be working.  

Thank you.

---

### Post by coffeecat on 2010-09-26
> **Skyline911 said:**
> I'm back!!

So am I. :wink:

I don't use an Epson (I use HP and the HPLIP-GUI does this for me) but looking in Synaptic I can see inkblot. Unfortunately named, but it uses the libinklevel library, website here:

[http://libinklevel.sourceforge.net/#supported](http://libinklevel.sourceforge.net/#supported)

... and I can see that the DX7450 is listed as supported.

Let us know how you get on with inkblot.

---

### Post by Skyline911 on 2010-09-26
Thanks. I've installed it from the software centre (I assume that was right?).

It is now an option under System menu.  I clicked it and a little icon has appeared on my taskbar with a red cross on it.  I right clicked on the icon and selected rescan devices and got the message

Inkblot Error

No supported printers found.

Please check your printer and cables and scan for printers again.

The printer is quite clearly connected and switched on!!

When I have sent this message I am going to do a reboot to see if that has any effect.... must be worth a try, mustn't it?

---

### Post by Skyline911 on 2010-09-26
No joy, I'm afraid :(

---

### Post by Skyline911 on 2010-09-26
Oo-er?  

I just opened a terminal (hark at me being all technical!!) and typed

sudo inkblot

The same icon has appeared but when I right click on it, it recognises the printer.........

[I][B]Printer Detection Complete

Found EPSON Stylus DX7400 USB printer on lp0

Inkblot will report the ink level on this device.[/B][/I]

In the terminal. it just reeled of a long list:
[B][I]
Result was -6
Result was -6
Result was -6
Result was -6
Result was -6
Result was -6
Result was -6
Result was -6
Result was -6
Result was -6
Result was -6
Result was -6
Result was -6
Result was -6
Result was -6
Result was -6
Result was -6
Result was -4
Result was -2
Result was -2
Result was -2
Result was -2
Result was -2
Result was -2
Result was -2
Result was -2
Result was -2
Result was -2
Result was -2
Result was -2
Result was -2
Result was -2
Result was -2
Result was -2
Result was -5
Result was -5
Result was -5
Result was -5
Result was -5
Result was -5
Result was -5
Result was -5
Result was -5
Result was -5
Result was -5
Result was -5
Result was -5
Result was -5
Result was -5
Result was -5
Result was -6
Result was -6
Result was -6
Result was -6
Result was -6
Result was -6
Result was -6
Result was -6
Result was -6
Result was -6
Result was -6
Result was -6
Result was -6
Result was -6
Result was -6
Result was -6
Result was -6
Result was -4
Result was -2
Result was -2
Result was -2
Result was -2
Result was -2
Result was -2
Result was -2
Result was -2
Result was -2
Result was -2
Result was -2
Result was -2
Result was -2
Result was -2
Result was -2
Result was -2
Result was -5
Result was -5
Result was -5
Result was -5
Result was -5
Result was -5
Result was -5
Result was -5
Result was -5
Result was -5
Result was -5
Result was -5
Result was -5
Result was -5
Result was -5
Result was -5
Result was -6
Result was -6
Result was -6
Result was -6
Result was -6
Result was -6
Result was -6
Result was -6
Result was -6
Result was -6
Result was -6
Result was -6
Result was -6
Result was -6
Result was -6
Result was -6
Result was -6
Result was -4
Result was -2
Result was -2
Result was -2
Result was -2
Result was -2
Result was -2
Result was -2
Result was -2
Result was -2
Result was -2
Result was -2
Result was -2
Result was -2
Result was -2
Result was -2
Result was -2
Result was -5
Result was -5
Result was -5
Result was -5
Result was -5
Result was -5
Result was -5
Result was -5
Result was -5
Result was -5
Result was -5
Result was -5
Result was -5
Result was -5
Result was -5
Result was -5[/I][/B]

So does this relate to the ink levels?????

---

### Post by Skyline911 on 2010-09-26
Sorry - if I hover over the new icon it says

***Error: problem with printer***

---

### Post by coffeecat on 2010-09-26
> **Skyline911 said:**
> 
So does this relate to the ink levels?????

The list reports the same four values, but different numbers of times, three times over. Are there four ink catridges in your Epson? If so, perhaps the four values relate to the four catrridges. But why -6 should appear 17 times (x3) and -4 only once, is beyond me.

I have two HP printers, a desket and Officejet. The exact models are not in that list but nearly related ones are. I'll try inkblot with my HPs and see what I get. I'll be a couple of hours. In the meantime a google with inkblot and DX7450 as search items might bring up something useful. Or it might just find complaints from people complaining about blotty prints from their Epsons. :|

---

### Post by coffeecat on 2010-09-26
> **coffeecat said:**
> I'll be a couple of hours.

Didn't take that long. :)

First - it's a rough and ready little app. It's in the Universe repo which means it doesn't get the QA that Ubuntu-supported packages get - and it shows!

This is how I got it to work with my HP Deskjet 9800 even though that particular model isn't in the supported list. You're right about having to use sudo - you don't get anything unless you invoke administrator privileges.

So - first thing. Right-click on the main menu in the panel, top-left. Select Edit Menus. Highlight System Tools in the left pane and you should see Inkblot in the middle pane. Highlight the Inkblot line and click on the Properties button. In the command field, add 'gksu' to the beginning so that it reads, "gksu inkblot" (no quotes). Close that and close Edit menu.

Now run inkblot from the menu. You'll be prompted for your password if you haven't invoked gksu(do) in the last few minutes and a red inkblot icon should appear in the panel. Left click on that and it should show you the ink levels graphically. It finds my deskjet but not the Officejet.

At least, that's how it worked with the HP. See if it works with your Epson with gksu or gksudo rather than sudo.

---

### Post by Skyline911 on 2010-09-26
Thanks Coffeecat, it works (no surprises there then!)

So, is the method of adding gksu to the properties bit a way of avoiding having to run things in a terminal with sudo?

Also, is there a way to make things autostart with Ubuntu? Like putting them in the startup folder on W*n*ows (didn't want to use bad language on the forum!)

Sorry for endless questions and thanks so much for your help this weekend.

John.

---

### Post by coffeecat on 2010-09-26
> **Skyline911 said:**
> Thanks Coffeecat, it works (no surprises there then!)

Glad to hear it. :)

> **Skyline911 said:**
>  So, is the method of adding gksu to the properties bit a way of avoiding having to run things in a terminal with sudo?

No. Apples and oranges. Administrative apples and oranges, but horses and courses nevertheless. Sorry! :lol: You use gksu and gksudo (they do the same thing the way Ubuntu is set up) for graphical apps; sudo is just for the terminal. Sudo will work for some graphical apps but may break others, so it's best to use gksu(do) when invoking GUI apps. See here for more:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

> **Skyline911 said:**
> Also, is there a way to make things autostart with Ubuntu? Like putting them in the startup folder on W*n*ows (didn't want to use bad language on the forum!)

System > Preferences > Startup Applications I should think. If you need to know the startup command, access the main menu the way I described earlier and copy the command from the menu entry.

> **Skyline911 said:**
> Sorry for endless questions and thanks so much for your help this weekend.

No problem - just glad the scanner issue is sorted. By the way, I came across another thread this afternoon from someone with a different Epson scanner which wouldn't work. They had managed to download something from Avasys but had then got stuck. I posted a suggestion to use the command that worked for you (linking to this thread) but modifying it to include the USB identifier they had already posted. They haven't reposted yet so I don't know what the outcome is.

---

