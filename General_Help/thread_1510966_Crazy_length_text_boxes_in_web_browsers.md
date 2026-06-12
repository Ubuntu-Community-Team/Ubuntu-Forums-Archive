---
title: "Crazy length text boxes in web browsers"
date: 2010-06-16
forum: General Help
---

### Post by portach king on 2010-06-16
Hi Guys,

I did a search and I can't believe I seem to be only person reporting this. It's been a bug since I did a fresh install of 10.04 UNR, but it's only gotten to the tipping point where I actually HAVE to do something about it today. I finally cracked.

As you can see in the screen shot attached the one line text box (ie, search bars mostly, but the thread title in this case) stretches way beyond length it is supposed to. For the first screen shot I have "zoomed out" to give a better idea of the full effect, the second screen is what I see during normal browsing.

If anyone could help me fix this error it would be greatly appreciated. I've tried both Firefox and Chrome (and Chromium) and the same issue occours. The screen shot is taken from Chrome 5.0.375.70.

Thanks in advance.

---

### Post by warfacegod on 2010-06-16
Almost seems like it thinks it's in fullscreen mode. Try F11.

---

### Post by dino99 on 2010-06-16
remove xorg.conf if any

sudo rm -f /etc/X11/xorg.conf
sudo dpkg --configure -a

---

### Post by portach king on 2010-06-16
Hi Dino99, I followed those commands, and restarted my computer, but still no change in the situation.

Warfacegod, for the record those screen shots were taken in fullscreen mode but it renders that way when it isn't either.

I am on a netbook, the screen res is 1024x600, as in the screens I attached.

Really appreciate both of your advise, hopefully this issue can be resolved. :)

---

### Post by warfacegod on 2010-06-16
Removing the xorg.conf file probably wouldn't work anyway. They've been shipping blank since 9.10 so if there's nothing in them to read, removing nothing gives you nothing.

I assume you have your drivers all in order?

---

### Post by portach king on 2010-06-16
I presume they're all in order. I'm running into no other issues other than this minor one and a blankscreen instead of a splashscreen during the first 20 seconds of the boot up.

Is there a quick way I can find out if they are?

---

### Post by warfacegod on 2010-06-16
System> Admin.> Hardware Drivers> activate the "Recommended" driver.

---

### Post by portach king on 2010-06-16
After it searches for drivers, the window reads "No proprietary drivers are in use in this system," and there is nothing there for me to enable.

---

### Post by Ryan Dwyer on 2010-06-16
In Chromium, right click the textbox and choose Inspect Element. Expand the computed style section and read what width Chromium is assigning it. If the width is big you know your problem isn't with Xorg or drivers.

---

### Post by warfacegod on 2010-06-16
That probably means that you have Intel graphics. If your on a Netbook, it's practically certain to be Intel. While the Intel drivers are essentially worthless, this *probably* isn't the issue.

Check the Troubleshooting section: [http://ubuntuforums.org/showthread.php?t=1193567]("http://ubuntuforums.org/showthread.php?t=1193567")

---

### Post by portach king on 2010-06-16
"width: 891px"

Just want to repeat my appreciation again guys, you're what makes Ubuntu so fantastic.

---

### Post by Ryan Dwyer on 2010-06-16
> **portach king said:**
> "width: 891px"

OK, so it's not a hardware problem. In Chromium's developer tool thing, look at the right hand panel and see what declaration is assigning it that width (eg. user stylesheet, style attribute or an actual CSS file). Custom CSS or extensions could cause this behaviour.

---

### Post by portach king on 2010-06-16
From what I can see no style are attributed to the width.
Bear in mind also, that this same exact problem is occouring in Chromium, Chrome & Firefox also.

---

### Post by warfacegod on 2010-06-16
Have you tried creating a new user account to see if the problem exists there as well?

---

### Post by portach king on 2010-06-16
Hey,

I created a new account and the problem does not exist there. It seems to only be present when I'm logged in to my default account.

---

### Post by warfacegod on 2010-06-16
Then either you can migrate your stuff to the new account or use the guide I posted earlier to delete your browser profiles.

---

