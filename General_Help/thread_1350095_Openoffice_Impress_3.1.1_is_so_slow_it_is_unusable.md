---
title: "Openoffice Impress 3.1.1 is so slow it is unusable."
date: 2009-12-09
forum: General Help
---

### Post by lethalfang on 2009-12-09
I've looked up the web, and some said it's the anti-aliasing problem. I've turned off anti-aliasing and Impress is still unusable. 
Anyone knows where can I get the version 3.0 instead?

---

### Post by wilee-nilee on 2009-12-09
Here is some information on speeding up OO in general.
[http://www.ghacks.net/2007/08/18/speed-up-open-office/](http://www.ghacks.net/2007/08/18/speed-up-open-office/)
How much ram do you have?

---

### Post by lethalfang on 2009-12-09
> **wilee-nilee said:**
> Here is some information on speeding up OO in general.
[http://www.ghacks.net/2007/08/18/speed-up-open-office/](http://www.ghacks.net/2007/08/18/speed-up-open-office/)
How much ram do you have?

Thanks. I have 4 GB of RAM (although only 3.4 GB are accessible). 
I used those modifications, and it's still slow as hell. This is frustrating. I made the slides on Jaunty with Impress 3.0, and now I can barely open it in 3.1.1 and it's experiencing unreasonable slowdown. 
How can a simple revision make things this much worse?

---

### Post by lethalfang on 2009-12-09
My process when I'm using Impress shows lots of CPU power is consumed by gs and convert. 
I have a bunch of .eps files in the .odp. Does that have something to do with it, even though it didn't seem to be a problem in the previous 3.0 version.

---

### Post by Hagar Delest on 2009-12-09
Try perhaps to [reset your OOo user profile](http://user.services.openoffice.org/en/forum/viewtopic.php?p=58403#p58403) but don't transfer your personal data during the welcome process (if you had 2.x before), configuration files from the former version might corrupt the new profile.

And if no change, try the Sun version: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by andrew_a72 on 2010-02-20
I had the same issue, followed instructions on [http://www.ghacks.net/2007/08/18/speed-up-open-office/](http://www.ghacks.net/2007/08/18/speed-up-open-office/) and then disabled anti-aliasing in tools -> options -> view -> uncheck "Use Anti-Aliasing" and now it works great.

---

### Post by hsaariko on 2010-03-17
I have the same problem after upgrading to Ubuntu Karmic Koala. Impress presentations done with the Impress 2.4 run extremely slow in the version 3.1. I increased the memory size, as suggested here, and Impress does run apparently faster for some time but then it stucks very often for maybe 15 seconds and the process 'gs' uses 100% of the CPU-time. This happens so often that the program is unusable. I tried to turn off anti-aliasing and turn on hardware acceleration etc. but this did not help either.

---

### Post by m4lte on 2010-04-22
> **andrew_a72 said:**
> I had the same issue, followed instructions on [http://www.ghacks.net/2007/08/18/speed-up-open-office/](http://www.ghacks.net/2007/08/18/speed-up-open-office/) and then disabled anti-aliasing in tools -> options -> view -> uncheck "Use Anti-Aliasing" and now it works great.

Thanks a lot. Without anti aliasing OO runs much faster on my machine. Actually, there seems to be a bug with anti aliasing making OO extremely slow. It's filed here: [https://bugs.launchpad.net/openoffice/+bug/411542](https://bugs.launchpad.net/openoffice/+bug/411542)

---

### Post by anjames on 2010-06-04
I unchecked both anti-aliasing options in tools->options->view and restarted OOo but am still having problems with very slow operation. Turning off anti-aliasing sped up certain page rendering operations, but the remaining problem is attached to OOo using gs and convert to display embedded eps files. 

When I make a presentation using only png graphics, OOo runs fine, but when I insert the same graphics as eps OOo runs gs and convert at opening of the document and when switching between pages. I would guess that this has to do with OOo using gs and convert to actually display eps, where it can (more?) natively display png figures.

My solution has been to just insert png graphics for each of my figures and edit them externally in inkscape, though this is a cumbersome workaround.

It seems to work better when I have the slide pane closed as well, so maybe it makes the small thumbnail images in the slide pane with gs and convert, which was somehow done differently before?

---

### Post by scouser73 on 2010-06-04
OpenOffice 3.2.1 is now out.

Firstly, go to the OpenOffice website: [http://download.openoffice.org/](http://download.openoffice.org/) and download the Linux .deb file to your desktop

Once you have done that, extract the .deb file, 

OOo_3.2.1_LinuxIntel_install_en-US_deb.tar.gz

Then you'll see a file called OOO320_m18_native_packed-1_en-US.9502

You can remove the existing version of OpenOffice if you wish with this command: 

**> sudo apt-get remove openoffice*.* **

Then paste this command:

**> sudo dpkg -i ~/Desktop/OOO320_m18_native_packed-1_en-US.9502/DEBS/*.deb**

Then paste this command: 

**> sudo dpkg -i ~/Desktop/OOO320_m18_native_packed-1_en-US.9502/DEBS/desktop-integration/openoffice.org3.2-debian-menus_3.2-9502_all.deb**

Once you've done that you'll find OpenOffice 3.2.1 in Office.

---

### Post by anjames on 2010-06-08
Tried 3.2.1 and still have the same problem. gs and convert are spawned periodically presumably to make thumbnails for the slide pane, and suck cycles way longer than it seems like it should take to make a thumbnail. Maybe this is a problem with ghostscript or imagemagick?

---

### Post by yellow.hat on 2010-06-09
Thanks for tips wilee-nilee.

---

### Post by fcastillo on 2010-06-14
Is there a way to just upgrade the existing ones? I don't want to install oppenoffice database and other packages that I don't need. I just want to update the ones I already have, is there a way?

---

### Post by Subito Piano on 2010-06-14
Scouser73: THANK YOU!  There was a bug with no navigation buttons when exporting a presentation as a series of html slides; this is resolved and i NEED that feature in my teaching.  Your instructions prevented me from having to wait for the repos to get up-to-date.  Blessings!!!  [IMG]http://mepislovers.org/forums/images/smilies/snoozer_likelinux_man.gif[/IMG]

---

### Post by Hagar Delest on 2010-06-14
> **fcastillo said:**
> Is there a way to just upgrade the existing ones? I don't want to install oppenoffice database and other packages that I don't need. I just want to update the ones I already have, is there a way?
No. OOo is an integrated suite. Most of the code is made of shared libraries. So not installing all the components won't spare much room (less than 10MB per module).

---

### Post by robertcoulson on 2010-08-04
Tried it... OpenOffice loaded with incredible speed...Thanks
Robert

---

### Post by juliobahar on 2010-08-16
Disabling anti-aliasing really made my Impress rock. Thanks guys

Btw, what does anti-aliasing mean? and what am I missing by disbling it?

---

### Post by Subito Piano on 2010-08-16
see [http://www.pantherproducts.co.uk/Articles/Graphics/anti_aliasing.shtml](http://www.pantherproducts.co.uk/Articles/Graphics/anti_aliasing.shtml)

---

### Post by Subito Piano on 2010-08-16
see [http://www.pantherproducts.co.uk/Articles/Graphics/anti_aliasing.shtml](http://www.pantherproducts.co.uk/Articles/Graphics/anti_aliasing.shtml)

---

### Post by Ferralll on 2010-11-23
I know this is a bit of an old message, but it was the first one to come up when I did a search looking for a solution to the problem. 

I have been having this problem, and one of the solutions that I have found is to break the links to images. 
From what I can understand, when you import images by just dragging and dropping the system sets up a link to the image rather than importing the data.  So it spends a lot of time accessing the image from another source.  

To break links do the following:
Edit> Links...
Then hilight all of your images and hit the "Break links" button.  This should speed up and solve some problems that happen with Impress.

(I also turned off the anti-aliasing... and that seems to really help with rotated text boxest and stuff like that)

---

### Post by mattman85 on 2010-12-06
> OpenOffice 3.2.1 is now out.

Firstly, go to the OpenOffice website: [http://download.openoffice.org/](http://download.openoffice.org/) and download the Linux .deb file to your desktop

Once you have done that, extract the .deb file, 

OOo_3.2.1_LinuxIntel_install_en-US_deb.tar.gz

Then you'll see a file called OOO320_m18_native_packed-1_en-US.9502

You can remove the existing version of OpenOffice if you wish with this command: 


Quote:
sudo apt-get remove openoffice*.*  



Then paste this command:


Quote:
sudo dpkg -i ~/Desktop/OOO320_m18_native_packed-1_en-US.9502/DEBS/*.deb  



Then paste this command: 


Quote:
sudo dpkg -i ~/Desktop/OOO320_m18_native_packed-1_en-US.9502/DEBS/desktop-integration/openoffice.org3.2-debian-menus_3.2-9502_all.deb  



Once you've done that you'll find OpenOffice 3.2.1 in Office.


I followed the two dpkg statements, and I get error messages:

dpkg: regarding .../openoffice.org3.2-debian-menus_3.2-9502_all.deb containing openoffice.org-debian-menus:
 openoffice.org-common conflicts with openoffice.org-debian-menus
  openoffice.org-debian-menus (version 3.2-9502) is to be installed.
dpkg: error processing DEBS/desktop-integration/openoffice.org3.2-debian-menus_3.2-9502_all.deb (--install):
 conflicting packages - not installing openoffice.org-debian-menus
Errors were encountered while processing:
 DEBS/desktop-integration/openoffice.org3.2-debian-menus_3.2-9502_all.deb


any ideas? OOo 3.2.1 isn't showing up in Office Applications menu..

---

### Post by uRock on 2010-12-06
I have found that OpenOffice runs slow and locks up until you save the file. The reason it does so is because it is trying to back up what you have done but can't do so. That said, when I start a new file I save it, then start typing and it runs fine.

You may also want to try installing 3.2.1 from [their web site.]("http://download.openoffice.org/")

---

### Post by Subito Piano on 2010-12-06
Thanks, uRock!

---

### Post by Hagar Delest on 2010-12-06
@ mattman85: check that there is no OOo package with the 'ubuntu' string in their version number (in Synaptic).

---

### Post by snapback877 on 2010-12-12
I also have the same problem, Impress is soo slow. Tried all the things posted here, and I can say switching off anti-aliasing really speeds up things. Still is gets slow e.g. when moving a simple text box over the place where it is located (but only there, not in other regions of the slide). Then CPU just goes crazy. Also when expanding a text box it gets slow.
Tried to switch off View>Toolbars>Options>Modify objects with attributes, so it won't show the text while dragging, but still the same thing.

---

### Post by aust_paul on 2010-12-30
> **snapback877 said:**
> I also have the same problem, Impress is soo slow. Tried all the things posted here, and I can say switching off anti-aliasing really speeds up things. Still is gets slow e.g. when moving a simple text box over the place where it is located (but only there, not in other regions of the slide). Then CPU just goes crazy. Also when expanding a text box it gets slow.
Tried to switch off View>Toolbars>Options>Modify objects with attributes, so it won't show the text while dragging, but still the same thing.

I am having the same issue too on Lucid with OpenOffice Impress 3.2.0. I don't understand why I can smoothly do other things like edit video and use GIMP, yet OOo Impress gets all slow when I try to do something as simple as move around a few text boxes. I've also tried switching off anti-aliasing but am still getting the same issues. I hope someone has some more ideas. Thanks anyway for all the support in this thread.

---

### Post by jorenheit on 2012-08-08
For anyone who is using 3.2 and still having problems (e.g. when you're running Debian stable like I do), download the latest version (3.4 as I am posting this) from
[http://www.openoffice.org/download/other.html](http://www.openoffice.org/download/other.html)

Remove your old version and install all the .deb packages like scouser73 suggested and you'll be fine! 
Worked for me :-)

---

