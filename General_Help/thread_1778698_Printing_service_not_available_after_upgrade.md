---
title: "Printing service not available after upgrade"
date: 2011-06-09
forum: General Help
---

### Post by Solven on 2011-06-09
[COLOR=Black]Hi, I'm new to ubuntu and the forums so I hope I'm posting in the right place. I have Ubuntu 11.04 64 bit installed on a Dell Laptop, and my printer, a Samsung Laser ML - 1740[/COLOR] was working fine until yesterday when an upgrade for CUPS appeared in the Update Manager and I installed it. Now when I try to print, the printer is not listed and when I open up "Printing" a message appears stating "Printing service is not available. Start the service on this computer or connect to another server." The 'Start Service' option is grayed out and when I try 'Connect' another box appears   "Connect to CUPS server - CUPS server: localhost"  is the only option available. I try Connect but an error message appears stating "CUPS server error  There was an error during the CUPS operation: 'failed to connect to server' " . I also installed VirtualBox yesterday but I'm not sure if that has anything to do with it.

Forgot to add that the printer is connected directly to the laptop.

Thanks in advance for your help!

---

### Post by Solven on 2011-06-09
Never mind. Apparently there was an error during yesterday's update. I ran a new update just now, an option for a "Partial Update" appeared. After the update everything is working fine again. Thanks!

---

### Post by matthewetaft on 2011-07-14
I want to provide more detail here because it took me quite a few hours to figure this how.  Here's what I did:

I suddenly noticed I could no longer print.  When I tried to print a document, no printer was available in the dialogue.  When going into the Printing settings, there were no printers to select and it said the printing service was not running.  I didn't know how to start it, so I looked it up and found this:

sudo service cups start

I always saw one or two results: Either it would say Start / Waiting, or it would just hang.  I never got a process ID or anything.  When I went back to the printer settings, I still couldn't find a printer.  I uninstalled and reinstalled cups, I even went through:

sudo apt-get purge cups
sudo apt-get install cups --install-suggests

Still, nothing changed.

I looked in the Software Update Manager under "History," and found lots of updates to various cups packages, and realized that's probably where the problem happened, but I didn't know how to fix it.  I don't think there's any kind of "unroll" option on these updates.

Anway, at this point I found CUPS 's website (CUPS [dot] org).  In the news on the right, it said there was a new version (CUPS 1.4.7) that fixed a lot of bugs.  In my Software Update Manager, I had an older version.  So basically, CUPS got updated but the update was buggy and the fix hadn't become available in the repositories yet.  At least that's what I figured.  So I went ahead and installed this new package.  I clicked the link to the downloads section then downloaded cups-1.4.7-source.tar.bz2 to my Desktop.  Then I opened a terminal and navigated to my Desktop (cd /home/[username]/Desktop) and ran these commands:

tar xvfj cups-1.4.7-source.tar.bz2

cd cups-1.4.7/

./configure

make

sudo make install

sudo service cups start

At this point, I got a notification window saying the device was found, then a window opened asking me what drivers to install for my printer, and I went through those prompts.  Now I'm all set!  This was crazy, but I'm glad I figured it out finally.  Hope this helps someone.

---

### Post by neiljansons on 2012-01-31
had the same problem on one of my notebooks that I don't often use.
I got it out to install a new printer and found that the service was not running.
trying to manually restart it (sudo service cups start)
just resulted in an error
tried doing a reinstall (sudo apt-get install --reinstall cups)
but that did not work

but
[INDENT]sudo apt-get purge cups
sudo apt-get install cups --install-suggests[/INDENT]
worked

thanks

---

