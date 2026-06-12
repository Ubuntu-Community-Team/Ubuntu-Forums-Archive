---
title: "Firefox and Java Plugin Problem"
date: 2009-12-20
forum: General Help
---

### Post by ahamilton55 on 2009-12-20
Hi,

I'm having trouble with keyboard input in Firefox 3.5.6 in a Java applet at [www.aleks.com](www.aleks.com).  When the applet loads I am unable to input any text into the text box but if I click outside of the text box and then back in then inside I can then enter text.  The Google Chrome Beta however works fine with this same website and Java plugin.

I've been trying to get this to work myself for about a month now but have had no luck.  I'm currently using XUbuntu 9.10 but have also tried Ubuntu 8.04.1/9.04/9.10/10.05alpha1, KUbuntu 8.04/9.10, and Debian Testing. I have tried OpenJDK, IcedTea, Sun Java 5, Sun Java 1.6.0_15, Sun Java 1.6.0_17 in Wine (which worked) and Sun Java 1.6.0_17.  Browser wide I've tried Firefox 2.0.0.*, 3.5.3, 3.5.5, 3.5.6, Firefox 3.5.5 in Wine(which worked), Konquer, abrowser, and Google Chrome Beta.  I've also played with scim, im-switch, i-bus, hal, xorg, update-alternatives, about:config, changing locales, purging locales, and anything else that I could think of before but not now while typing this.

This problem is bothering me because I don't see why it would work in Chrome but not in Firefox.  It's just annoying to have to click outside and then back inside of a text box each time you wish to input any text.

Thanks in advance...

---

### Post by lovinglinux on 2009-12-20
Which java plugin are you using?

Have you tried to use a clean Firefox profile to check if the problem persists?

---

### Post by ahamilton55 on 2009-12-20
I have tried both the older java plugin for i386 as well as the "next generation" sun java 6 plugin for both i386 and x86_64.

Yes I've done that as well as every other command line argument I could find for firefox.  Tried removing ~/.mozilla, ~/.java,  ~/.scim, and ~/.xinput.

I have put a lot of time in on this problem before asking and have done a lot of different things that were not listed above because I don't remember them all.  Thank you for the prompt reply as well.

---

### Post by lovinglinux on 2009-12-20
> **ahamilton55 said:**
> I have tried both the older java plugin for i386 as well as the "next generation" sun java 6 plugin for both i386 and x86_64.

Yes I've done that as well as every other command line argument I could find for firefox.  Tried removing ~/.mozilla, ~/.java,  ~/.scim, and ~/.xinput.

I have put a lot of time in on this problem before asking and have done a lot of different things that were not listed above because I don't remember them all.  Thank you for the prompt reply as well.

Have you tried to remove sun java plugin and install [icedtea6-plugin](apt:icedtea6-plugin)?

---

### Post by ahamilton55 on 2009-12-20
Yes I have and the applet wouldn't even finish loading with that plugin.

---

