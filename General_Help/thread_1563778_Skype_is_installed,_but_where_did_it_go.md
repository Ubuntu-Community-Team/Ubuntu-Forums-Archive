---
title: "Skype is installed, but where did it go?"
date: 2010-08-29
forum: General Help
---

### Post by flopwich on 2010-08-29
I went to the Skype web site and downloaded a copy of it for Ubuntu.  When I went to install it, though, the installer told me there was a version available that was supported better for Ubuntu, so I used Synaptic Package Manager to install it, which it said it did.  I can't find it anywhere, though.  I looked through all the menus and it's not there.  So I tried Ubuntu Software Center, and it tells me that Skype is installed.  I tried searching for any file with the word "skype" in it with the file manager and came up empty.

Where did it go?  Why can't I find it?  How can I find it?

Thanks.

---

### Post by davidmohammed on 2010-08-29
normally its under "Internet".

If you right click "applications" and choose edit menus - navigate to internet and see if skype is there - maybe you have to "enable" it.

---

### Post by flopwich on 2010-08-29
> **davidmohammed said:**
> normally its under "Internet".

If you right click "applications" and choose edit menus - navigate to internet and see if skype is there - maybe you have to "enable" it.

I assume you mean "applications" under "Main Menu" under "System"?  I looked there, too.  As I said, I looked through all the menus and it doesn't show up anywhere.

Thanks.

---

### Post by davidmohammed on 2010-08-29
... when you choose edit menus - is it there but not ticked?

---

### Post by howefield on 2010-08-29
Go to System > Preferences > Main Menu.

Click on Internet in the left hand pane, and then on the New Item button. 

Name : Skype
Description : Whatever you want.
Command : skype-wrapper 
Comment : Skype Internet Telephony

This will place a entry in you Applications > Internet menu.

---

### Post by flopwich on 2010-08-29
> **howefield said:**
> Go to System > Preferences > Main Menu.

Click on Internet in the left hand pane, and then on the New Item button. 

Name : Skype
Description : Whatever you want.
Command : skype-wrapper 
Comment : Skype Internet Telephony

This will place a entry in you Applications > Internet menu.

Yup, that did it, all right.  Thank you very much.

What did that do?  How did you know to do it, and how would I know another time what to type in the command line?

Thanks again.

---

### Post by gvernold on 2010-08-29
> **flopwich said:**
> I assume you mean "applications" under "Main Menu" under "System"?  I looked there, too.  As I said, I looked through all the menus and it doesn't show up anywhere.

Thanks.
Actually I think that the first solution provided was to right click on "Applications" on the left of the panel at the top of your desktop assuming you are using the default 10.04 theme. Once you click on "Edit Menu" it offers you a 'tree' style directory editor where you can enter the Internet section and see if Skype appeared as an option to add to the menu.

It doesn't really matter anyway... I had the same problem on two machines. On the first I had to restart the machine and Skype appeared in the application menu under internet. On the second I removed Skype using Synaptic and downloaded the 8.10 version from Skype's website and installed that. It worked for me on all versions since 8.10.

The version of Skype I have installed under synaptic has occasional sound problems and lock ups too. I'll reinstall from the Skype website version in the morning now I've got a day off for bank holiday :D.

Update after solution provided: Ahhh, I've never used the menu editor under System before.... didn't even know it was there, thank you.

---

### Post by flopwich on 2010-08-29
> **gvernold said:**
> Actually I think that the first solution provided was to right click on "Applications" on the left of the panel at the top of your desktop assuming you are using the default 10.04 theme. Once you click on "Edit Menu" it offers you a 'tree' style directory editor where you can enter the Internet section and see if Skype appeared as an option to add to the menu.

That's interesting.  As far as I know, I have the default 10.04 configuration, mostly because I'm not competent enough to have anything else. ;-)  Yet I have no "application" entry in the desktop.

---

### Post by davidmohammed on 2010-08-29
if you dont have the "Applications Places System" menu - maybe you have deleted from the panel.  Right click the panel and add "menu bar - a custom panel"

---

### Post by flopwich on 2010-08-29
> **davidmohammed said:**
> if you dont have the "Applications Places System" menu - maybe you have deleted from the panel.  Right click the panel and add "menu bar - a custom panel"

When I right click on the left panel of the desktop, nothing happens at all.  If I right click on the bar at the top of the screen, the only option is a "Preferences", which when I click on it offers me the chance to uncheck a box that says "Show windows from all workspaces".  I must be missing something here.

Thanks.

---

### Post by howefield on 2010-08-29
> **flopwich said:**
> Yup, that did it, all right.  Thank you very much.

You're welcome, I forgot to tell you where the icon is, if you wanted the skype icon click on the icon symbol when creating the menu entry and navigate to /usr/share/icons

If you have created the menu item and have the "screw" icon, you can go back in and highlight the entry and select properties. Then find the icon as above.

---

### Post by flopwich on 2010-08-29
> **howefield said:**
> You're welcome, I forgot to tell you where the icon is, if you wanted the skype icon click on the icon symbol when creating the menu entry and navigate to /usr/share/icons

If you have created the menu item and have the "screw" icon, you can go back in and highlight the entry and select properties. Then find the icon as above.

No, the icon popped up by itself with the skype-wrapper command.

---

### Post by davidmohammed on 2010-08-29
> **flopwich said:**
> When I right click on the left panel of the desktop, nothing happens at all.  If I right click on the bar at the top of the screen, the only option is a "Preferences", which when I click on it offers me the chance to uncheck a box that says "Show windows from all workspaces".  I must be missing something here.

Thanks.

are you using ubuntu or kubuntu?  The edit menus stuff I mentioned is for ubuntu (gnome interface).

---

### Post by howefield on 2010-08-29
> **flopwich said:**
> No, the icon popped up by itself with the skype-wrapper command.

Oh, ok, that's good. Sometimes you have to track the icon down.

---

### Post by flopwich on 2010-08-29
> **davidmohammed said:**
> are you using ubuntu or kubuntu?  The edit menus stuff I mentioned is for ubuntu (gnome interface).

It's Ubuntu 10.04 with the Gnome interface.  I don't understand why I don't see what you do.

---

### Post by gvernold on 2010-08-29
Take a look at the screenshot at the top of the page here:

[http://www.ubuntu.com/desktop](http://www.ubuntu.com/desktop)
(might have to wait for the slide to scroll over)

You should have a menu like that with  -  Applications    Places    System

---

### Post by howefield on 2010-08-29
Could be Ubuntu netbook remix.

[https://wiki.ubuntu.com/UNR](https://wiki.ubuntu.com/UNR)

---

### Post by flopwich on 2010-08-29
> **gvernold said:**
> Take a look at the screenshot at the top of the page here:

[http://www.ubuntu.com/desktop](http://www.ubuntu.com/desktop)
(might have to wait for the slide to scroll over)

You should have a menu like that with  -  Applications    Places    System

That's odd.  My screen looks like this. (Please see the attachment.)

[IMG]file:///tmp/moz-screenshot.png[/IMG]

---

### Post by howefield on 2010-08-29
> **flopwich said:**
> That's odd. 

Not odd at all, Ubuntu Netbook Remix, which is Ubuntu with a desktop specifically optimised for the typically  smaller netbook screen size.

---

### Post by flopwich on 2010-08-29
> **howefield said:**
> Not odd at all, Ubuntu Netbook Remix, which is Ubuntu with a desktop specifically optimised for the typically  smaller netbook screen size.

Yes, you're right.  I didn't realize it was that different from the regular version.

---

### Post by howefield on 2010-08-29
> **flopwich said:**
> Yes, you're right.  I didn't realize it was that different from the regular version.

Only the desktop is different, it is the same "underneath".

After your second post in this thread, it seemed likely that you were running UNR and confirmed after your 5th ;-)

Anyway, glad you are sorted.

---

### Post by flopwich on 2010-08-29
> **howefield said:**
> Only the desktop is different, it is the same "underneath".

After your second post in this thread, it seemed likely that you were running UNR and confirmed after your 5th ;-)

Anyway, glad you are sorted.

Yes, I am, and Skype is working fine, except that for some reason all its drop-down menus show up black letters on a black background and I have to hold the cursor over each item, one at a time, to see what it is.  Very strange, but that I can live with.

Thank you again for your help.

---

