---
title: "Firefox locked up-- trouble recovering windows and tabs"
date: 2012-01-12
forum: General Help
---

### Post by markMDW on 2012-01-12
Hi, Firefox 3.? is locked up completely, not responding, and reports in the browser that, "Firefox is having trouble recovering your windows and tabs.  This is usually caused by a recently opened web page."   It says I have two options to choose from by clicking on either  [Start New Session] or [Restore]  However, the browser is locked up completely. I can't click on either option.  

I can do a Force Quit by clicking the window [x], or Force Quit using the Gnome toolbar Force Quit Tool, but even after rebooting, when I run Firefox again I'm back to square one, with a session that is not responding and Firefox asking me again to select either  [Start New Session] or [Restore].  

I've also tried using the terminal to force Firefox to quit, using "Kill -9  ----" (followed by the process id rather than hyphens) which does force Firefox to quit, but after rebooting I'm once again at square one with Firefox not responding.

I'm using SeaMonkey Browser now.  All my beloved bookmarks are on Firefox.  Can anyone offer advice on how to resolve Firefox without losing my Bookmarks?  Thanks!

---

### Post by LinuxFan999 on 2012-01-12
Which version of Ubuntu are you using?

---

### Post by markMDW on 2012-01-13
I'm running 10.04

---

### Post by pretty_whistle on 2012-01-13
Maybe you could get an html file and open it with Firefox.  That might let something through the locked thing using a backdoor route, so to speak.

Edit:

I had a Firefox lock up like this and I did this and it worked.

---

### Post by markMDW on 2012-01-13
I tried opening a local html file, which it displayed, but Firefox remained locked up.  No buttons work.  No dropdown menus.  No bookmarks access.  

I looked in the Ubuntu Software Center under installed packages.  Firefox isn't even listed.  Also I checked for other web browsers and Firefox isn't listed, except for a package specifying kubuntu.  I'm not using that.  

I wonder why Firefox isn't listed in the Ubuntu Software Center like everything else that comes in by default for a Ubuntu install?

---

### Post by holycow131415 on 2012-01-13
Maybe upgrading it will help, from the ppa: [https://launchpad.net/~mozillateam/+archive/firefox-stable?field.series_filter=lucid](https://launchpad.net/~mozillateam/+archive/firefox-stable?field.series_filter=lucid)

---

### Post by markMDW on 2012-01-13
I tried adding one of the packages; that didn't work.

Then I tried the following :~$ sudo apt-get upgrade firefox

to which the bash terminal responded:

[INDENT]Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/INDENT]

But it still didn't work.

I'm thinking about uninstalling and re-installing from the terminal.   I'm thinking the package just called 'firefox' is the actual application itself.  

..or should I just hold off and wait till ubuntu sends something through the update manager for me to install, and use other browsers till then, in the hopes the update manager will eventually square it away?   

Thanks for everyone's advice!

---

### Post by markMDW on 2012-01-13
update, everything is still locked up on Firefox.  But, I was able to install Chromium Browser and it had a handy tool which did indeed import all my Bookmarks.  However, I had tons of beloved RSS Feed menus that Chromium didn't import.  Those were my bread and butter for web browsing.  This new browser is really nifty, I especially like the Chrome Application store, but I don't see it replacing Firefox.  My earlier post has my latest status.  Thanks for everyone's help!

---

### Post by markMDW on 2012-01-15
update - SUCCESS!   Firefox now works after being locked up for days.  Also, its now upgraded from 3.? to 9.0.1.   I looked at the link that Holycow131415 provided for Firefox's installable packages, then added the ppa site to my trusted repositories and installed the one just called 'Firefox' using the following terminal commands:
[INDENT]***sudo add-apt-repository ppa:mozillateam/firefox-stable***

***sudo apt-get install firefox***

[/INDENT] There were a lot of packages to potentially install using their ppa.  At first I had just tried adding the 'adblock' package, which hadn't revived Firefox[B]  

Thanks for the link from Holycow!
[/B]

---

