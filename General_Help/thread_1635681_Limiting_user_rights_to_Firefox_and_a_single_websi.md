---
title: "Limiting user rights to Firefox and a single website"
date: 2010-12-02
forum: General Help
---

### Post by oynaz on 2010-12-02
Hi guys
At work, we use a lot of computers for demonstration purposes. These computers have only one task: Show the company website. As such, we would like the computers to show a browser full screen, and prevent the users from starting other applications or navigating away from the site. 

Right now, we use an application called Sitekiosk on Windows 7 machines, but there are a number of problems with this setup. Installation is a hassle, Sitekiosk is not very stable, and the software is expensive.

Thus, I am testing whether Ubuntu is the solution. Ultimately, I would like a solution where I simply pop in a DVD (or perhaps use network boot), which installs Ubuntu, drivers, locks Firefox to the company website, and prevents access to any other applications. 
Alternately a manual installation and a manually run script is OK.

I am an Ubuntu newbie, but I tried installing it on an old Dell Vostro. Installation works very nice. All drivers are automatically installed, a nice change from Windows. I tried playing around with it, using the applications. It seems very intuitive, and I have no problems installing and using Ubuntu. So far so good.

However, I am at a loss at how to lock Firefox at a single site, and preventing other applications from running.
I imagine setting up a user which would be able to run Firefox, but would be required to enter a password to run everything else. 

Security is not a huge issue. The computers are on separate networks, and the customers are generally well-behaved. If a customer managed to exit Firefox and run something else, it would not be a disaster. I am merely intending the restrictions to tell the customers that they are only supposed to use our site on the computers, and not use it to check Hotmail etc.

I am using Ubuntu 10.10 BTW.

I have read the documentation, and I feel the answer is in there somewhere. I am too inexperienced with Ubuntu to make it work, however. Any help is much appriciated.

---

### Post by Spyderkid on 2010-12-02
try having a search around on the sofware centre and on [source-forge]("sourceforge.net/search/") for something

---

### Post by aeiah on 2010-12-02
use IPTABLES to block all websites except those on the whitelist (ie, yours).

firefox probably has a kiosk mode or something. if not it doesn't really matter. just remove the panel and that'll stop the average joe from starting any other application up. like you said, you're not trying to thwart mischievous users so you shouldn't need to worry about them launching stuff with alt+F2


you could have a shell script that checks to see if firefox is running and if not, runs it. that way if they do close the browser it just pops up again.

---

### Post by oynaz on 2010-12-28
Thanks for the suggestion guys.

It turns out that both Opera and Chromium has built-in kiosk modes. This would solve my problem easily, however:

1. Opera's kiosk mode does not work properly in the Linux version. Users have access to the menu by pressing alt, even if the -nomenu switch is applied. It works fine in the Windows version, but that is not what I need :-(

2. Chromium has a simple kiosk mode which works as it should, but can be exited with Alt+F4. That is a bit too easy.

Aeiah mentioned a shell script. That would solve the problem with Chromium. How do I make such a script?

---

