---
title: "Seeking Linux Equivalent of Windows Program"
date: 2012-04-30
forum: General Help
---

### Post by U8UNTU on 2012-04-30
I use the program called ccleaner to wipe (not just simply delete) operating system logs, cache, browser history, internet cookies, etc. all in one click. Is there a program for Ubuntu that does this? I am using Unity on Ubuntu 12.04 LTS.

---

### Post by qamelian on 2012-04-30
Try Bleachbit. It's in the Software Center.

---

### Post by 3rdalbum on 2012-04-30
> **U8UNTU said:**
> I use the program called ccleaner to wipe (not just simply delete) operating system logs, cache, browser history, internet cookies, etc. all in one click. Is there a program for Ubuntu that does this? I am using Unity on Ubuntu 12.04 LTS.

A lot of people seem to think that these things (logs, cache, temp files etc) make your computer slower, and that removing the files will speed up the computer. Not true. If you have a particular reason why you want to remove this stuff (privacy?) then go ahead - Bleachbit will help. If you're looking to speed up your computer, look elsewhere. You won't even save much disk space by removing cache and history and cookies.

---

### Post by U8UNTU on 2012-04-30
It is for privacy, not speed. 

I installed Bleachbit from the Ubuntu Software Center and installed it. The icon is a square with zeros and ones. It showed up in the Unity bar after I installed it. When I click it, nothing (visible or noticeable) happens. I tried opening it through the Dash too. Nothing (visible or noticeable) happens when I double-click the icon there either. I tried opening it as root and it prompted me for a password. After I entered my password, nothing happened. I opened Firefox to see if it ran in the background and my history was not cleared. 

Is this a Terminal-only program?

---

### Post by U8UNTU on 2012-04-30
The sourceforge [download page]("http://bleachbit.sourceforge.net/download/linux") does not list a 12.04 LTS version. That could be the problem. There is no bleachbit for this new version of Linux.

---

### Post by Enigmapond on 2012-04-30
Yes there is..open your terminal and do:
```
sudo apt-get install bleachbit
```
It's in the universal repo...

---

### Post by U8UNTU on 2012-04-30
I did that and installed it from the Terminal. It never works. The program always says it installs successfully no matter what I do. Then when I double-click, it does absolutely nothing. I have a fresh install of Ubuntu 12.04 LTS (64-bit) with no errors. It detected my wireless perfectly and everything. I do not get why bleachbit is not working.

---

### Post by Cheesemill on 2012-04-30
Try running bleachbit from the terminal and see if it gives you any errors:
```
bleachbit
```

---

### Post by U8UNTU on 2012-04-30
I started a thread at the Bleachbit forum and the developer said it is not working because I need to have GTK+ and PyGTK installed. If you are interested in more details, you can [read the thread here]("http://bleachbit.sourceforge.net/forum/not-working-ubuntu-1204-lts"). I am not sure how to mark this as SOLVED. Thank you for the responses.

---

### Post by Cheesemill on 2012-04-30
> **U8UNTU said:**
> I started a thread at the Bleachbit forum and the developer said it is not working because I need to have GTK+ and PyGTK installed. If you are interested in more details, you can [read the thread here]("http://bleachbit.sourceforge.net/forum/not-working-ubuntu-1204-lts"). I am not sure how to mark this as SOLVED. Thank you for the responses.
To mark as solved use the 'Thread Tools' link at the top of the page.

Have you raised a bug on launchpad as suggested by the bleachbit devs?

---

### Post by Stray Wolf on 2012-04-30
I think what you're looking for may be a Firefox add-on called "BetterPrivacy". Plus, if you set FF to clear history, not store cookies, and delete LSO's (using BetterPrivacy for clearing LSO's).

Install BetterPrivacy. Restart FF. Go to Tools>BetterPrivacy>Options and Help (tab). Select "Add LSO items to Firefox 'Clear History' dialogue and settings". Then, in FF, go to Edit>Preferences>Privacy (tab). Turn of tracking (can't hurt). Then, under History select the options that best suit you. I have mine set as "Use custom settings for history". Then, I have 
"Aways use private browsing mode" unchecked. 
"Remember my browsing history" unchecked. 
"Remember download history" unchecked. 
"Remember search and form history" unchecked. "Accept cookies from sites" checked. "Accept third-party cookies" unchecked. 
"Keep until: I close Firefox". 
"Clear history when Firefox closes" checked. 
Next to that is "Settings". Under it: Everything is checked.

This should take care of what you're trying to take care of.

---

### Post by U8UNTU on 2012-04-30
While that extension is great and I am glad you brought it to my attention, it is not what I am looking for. I want to actually wipe the cookies, history, etc. with a very secure delete like CCleaner does. 

Cheesemill:  I did not report the bug. I tried to but had no luck. I created a Launchpad account and logged in. Then I searched for Ubuntu. I clicked "Report a Bug" and it sent me back to the [Ubuntu instructions]("https://help.ubuntu.com/community/ReportingBugs#A5._Complete_the_bug_report_filing_process"). Then I tried to follow Step #4 and nothing showed up in my Dash for "ubuntu-bug" as I was typing it. Nothing showed up in my Dash for "Apport" either. Grrr. Nothing just works. I encourage anyone reading to report the bug if they know how. I want to help Ubuntu.

---

### Post by Humanity for Others on 2012-05-01
> A lot of people seem to think that these things (logs, cache, temp files  etc) make your computer slower, and that removing the files will speed  up the computer. Not true.

On Windows, it definitely is true.  Linux seems to run faster, so you probably don't recognize the difference or possibly there is a different way to handle accessing files.

---

### Post by OpenSourceRules on 2012-05-01
Things often run faster after Bleachbit; it is more because of the apt-get files rather than log files and caches, though.

---

