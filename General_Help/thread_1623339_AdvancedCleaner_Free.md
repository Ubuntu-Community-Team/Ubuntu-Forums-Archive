---
title: "AdvancedCleaner Free"
date: 2010-11-16
forum: General Help
---

### Post by joey00 on 2010-11-16
Hardy.

I have a box which is used by other people, although I have the only admin privileges.

In the users part of the system, an installation has appeared.

I didn't install it, and it seems to be some sort of windoze malware.

How do I get rid of this totally?

A simple 1,2,3...  would be appreciated.

The name of the App is AdvancedCleaner Free. It is running in WINE.

Since I certainly didn't install either of these....  :confused:

I checked synaptic for wine, but it doesn't show as installed.

---

### Post by a-user on 2010-11-16
so you see the wine process?
then maybe one of your  users installed in locally in his home directory. locate the wine binary. if installed "locate" try:
locate wine

if "wine" is the name of the executable (not sure about that).
then you know where it got installed. but remember, a program running as a normal user can only dmg the users home.

---

### Post by coffeecat on 2010-11-16
> **joey00 said:**
> I didn't install it, and it seems to be some sort of windoze malware.

How do I get rid of this totally?

If you google "advanced cleaner free", you get plenty of how to remove hits. Here are three representative ones:

[http://www.spywareremove.com/removeAdvancedCleanerFree.html](http://www.spywareremove.com/removeAdvancedCleanerFree.html)

[http://www.2-spyware.com/remove-advancedcleaner.html](http://www.2-spyware.com/remove-advancedcleaner.html)

[http://www.spywarevoid.com/remove-advancedcleaner-free-advanced-cleaner-free-removal-help.html](http://www.spywarevoid.com/remove-advancedcleaner-free-advanced-cleaner-free-removal-help.html)

I have no idea whether those links are any good or reputable. They are simply what a google search threw up, but they all have removal instructions.

---

### Post by joey00 on 2010-11-17
> **coffeecat said:**
> If you google "advanced cleaner free", you get plenty of how to remove hits. Here are three representative ones:

[http://www.spywareremove.com/removeAdvancedCleanerFree.html](http://www.spywareremove.com/removeAdvancedCleanerFree.html)

[http://www.2-spyware.com/remove-advancedcleaner.html](http://www.2-spyware.com/remove-advancedcleaner.html)

[http://www.spywarevoid.com/remove-advancedcleaner-free-advanced-cleaner-free-removal-help.html](http://www.spywarevoid.com/remove-advancedcleaner-free-advanced-cleaner-free-removal-help.html)

I have no idea whether those links are any good or reputable. They are simply what a google search threw up, but they all have removal instructions.
I also googled and found a myriad of links.

So many that I did not know which to go for. The "solutions" were useless in the few I actually tried out.

Most links offered an ubuntu solution and gave windoze information.

I can think of a few suitable hints for myself, including hosing the HDD. But, as I mentioned, I need something definitive and straightforward. 

I posted here cos I thought someone would really know how to do it.

---

### Post by joey00 on 2010-11-17
> **a-user said:**
> so you see the wine process?
then maybe one of your  users installed in locally in his home directory. locate the wine binary. if installed "locate" try:
locate wine

if "wine" is the name of the executable (not sure about that).
then you know where it got installed. but remember, a program running as a normal user can only dmg the users home.
The menu listing gives a listing under "WINE". I had the idea that the program name was "Wine", but I could be mistaken.

AFA installations, the ordinary users have very limited privileges. I thought Wine was outside that range (again could be wrong).

This one had to be installed by someone clicking on a web link. I doubt whether anything more complicated would have happened.

I can rip out the programs, assuming they are easily found, but I am concerned about off-shoots lurking in unexpected places.

Bleachbit refuses to properly scan certain areas, so this alarms me further. (no access even as sudo).

---

### Post by gandaran on 2010-11-17
> **joey00 said:**
> The menu listing gives a listing under "WINE". I had the idea that the program name was "Wine", but I could be mistaken.

AFA installations, the ordinary users have very limited privileges. I thought Wine was outside that range (again could be wrong).

This one had to be installed by someone clicking on a web link. I doubt whether anything more complicated would have happened.

I can rip out the programs, assuming they are easily found, but I am concerned about off-shoots lurking in unexpected places.

Bleachbit refuses to properly scan certain areas, so this alarms me further. (no access even as sudo).
why not just delete the /home/user/.wine folder? deleting the .wine folder gets rid of every windows programs installed in the wine drive C, (they don't install anywhere else) it may not eliminate the applications menu shortcuts but that you can do it with the system » preferences » main menu.
then click the applications » wine » configure wine, a new wine drive is created again, very easy to clean your system of windows applications.

---

### Post by joey00 on 2010-11-18
> **gandaran said:**
> why not just delete the /home/user/.wine folder? deleting the .wine folder gets rid of every windows programs installed in the wine drive C, (they don't install anywhere else) it may not eliminate the applications menu shortcuts but that you can do it with the system » preferences » main menu.
then click the applications » wine » configure wine, a new wine drive is created again, very easy to clean your system of windows applications.
I guess I can do this, but I want to undo any mischief that may have been done too.

Or am I imagining things lurking?

Anyhow, I will give it a try since early action seems a good idea.

---

