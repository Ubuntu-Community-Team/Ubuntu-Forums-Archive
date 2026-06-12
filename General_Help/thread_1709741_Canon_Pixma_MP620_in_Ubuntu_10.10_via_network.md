---
title: "Canon Pixma MP620 in Ubuntu 10.10 via network"
date: 2011-03-18
forum: General Help
---

### Post by Mega_Mike on 2011-03-18
I finally have a nice clean way of installing the multifunction canon pixma mp620 via network with both print and scanning capabilities.  This website was very helpful

[http://mp610.blogspot.com/]("http://mp610.blogspot.com/")

but those packages are outdated and give dependency errors that are annoying to deal with.  

Instead I repackaged the .deb files into a universal architecture (both x86 and amd64) and removed the old cups dependencies that no longer exist.  Below are the packages and cups ppd file:

[http://dl.dropbox.com/u/18055299/bjnp_0.5.5-2_all.deb]("http://dl.dropbox.com/u/18055299/bjnp_0.5.5-2_all.deb")
[http://dl.dropbox.com/u/18055299/cnijfilter-common_3.00-1_all.deb]("http://dl.dropbox.com/u/18055299/cnijfilter-common_3.00-1_all.deb")
[http://dl.dropbox.com/u/18055299/cnijfilter-mp610series_2.80-1_all.deb]("http://dl.dropbox.com/u/18055299/cnijfilter-mp610series_2.80-1_all.deb")
[http://dl.dropbox.com/u/18055299/canonmp620-630en.ppd]("http://dl.dropbox.com/u/18055299/canonmp620-630en.ppd")

[LIST=1]
[*]Install the bjnp package first.  This is the network protocol used by the Canon printer.
[*]Install the cnij common package next
[*]Install the cnij mp610 package next
[*]Next goto System->Administration->Printing, then add button.  Open the network printer pulldown and after a little wait you should see the Canon printer on your network
[*]Ubuntu will attempt to automatically install drivers, wait for this to end and then select 'provide ppd file'.  Select the downloaded canonmp620-630en.ppd
[*]Thats it!  You can now print and use Simple Scan for documents
[/LIST]

---

### Post by KaiSkylerBliss on 2011-03-21
I love you! Thanks so much!

---

### Post by Old Old Duffers on 2011-03-22
FINALLY got mine going too!!  Thanks guys!!:)

---

### Post by noneofthem on 2011-03-25
THANK YOU SO MUCH!

I have been looking for a solution for more than a year! Awesome! Everything is working now.

---

### Post by LordNodens on 2011-05-02
Does the printer work after upgrading to 11.04?

---

### Post by Easy Meat on 2011-05-03
I am new to Linux and have the aforementioned printer.
I have just installed 11.04 on an old laptop and have been trying to get my printer to work. I have followed the steps above and at least my laptop can see the printer now, however when trying to print it does not work :confused: I don't know whether I have done anything wrong or whether these drivers do not work on the latest iteration.

---

### Post by LordNodens on 2011-05-03
> **Easy Meat said:**
> I am new to Linux and have the aforementioned printer.
I have just installed 11.04 on an old laptop and have been trying to get my printer to work. I have followed the steps above and at least my laptop can see the printer now, however when trying to print it does not work :confused: I don't know whether I have done anything wrong or whether these drivers do not work on the latest iteration.

Check this thread: [http://ubuntuforums.org/showthread.php?t=1747047](http://ubuntuforums.org/showthread.php?t=1747047)

---

### Post by bluTaz on 2011-05-04
great, been looking for a while to get this working. Thanks a ton.

Scanning seems to work flawlessly, only printing colors are not accurate.

Attached is a scanned copy of my test results after setup (by the now working mp620). The color doesn't [show correctly]("http://i.imgur.com/FSthi.jpg"). Is everyone else getting these results? If anyone can help with getting that straightened out, it'd be much appreciated.

---

### Post by Longstreet on 2011-05-06
Cool! Works like a champ! Been trying to solve this problem for a while.

Haven't tried scanning yet, but printing works just fine. Thanks to all who put this together.

---

### Post by bluTaz on 2011-05-08
any chance of getting an rpm for fedora?

---

### Post by ShaneL on 2011-09-02
Hi there, a helpful thread to find :-)

I have been battling with a MP600 on ubuntu 10.04. Got it working 12 months ago, but had to set up a new HDD/Box this week and had dramas. Tried your .deb packages with no nasty results, but still had to get a mp600-specific .deb and some hints from 
[http://theseekersquill.wordpress.com/2010/05/03/canon_mp610_ubuntu_1004_64bit/#comment-224](http://theseekersquill.wordpress.com/2010/05/03/canon_mp610_ubuntu_1004_64bit/#comment-224)

to deal with using the package on my 64 bit system.

I seem to have got communications happening, but some symlinks for the mp600 files to use 'newer' libraries etc are making print jobs just not happen, though CUPS seems to think it's all OK. this problem I solved previously but now for some reason at least one of my symlinks is not found/recognised by a cifmp600 executable.
see
[http://mp610.blogspot.com/2007/11/setup-canon-pixma-mp600-or-mp610.html](http://mp610.blogspot.com/2007/11/setup-canon-pixma-mp600-or-mp610.html)

for explanations of how/why I was playing with symlinks.

Anyway, FYI anyone with a MP600.
And Kudos to OP for the packages provided for 64-bit.

any tips appreciated. any progress I'll post back :-)

***UPDATE:*** 
solved my issue, was a case of making sure the libraries required were present  in the 32-bit directories on my system, and any links to newer versions had to be to the new 32-bit libraries in those directories too. making links to the general library directories was no good as they hold 64-bit versions. I used readelf and getlibs from the command line to help solve my issue. readelf checked what -bit my libs/links were, getlibs let me install any missing 32-bit versions of libs.
[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---

### Post by Kafflut on 2012-10-16
I'm looking for a Canon MP230 driver (and instructions to install). I have Ubuntu 12.04.  Your post was a long time ago-I'm straw clutching. I hope you can help.

---

### Post by pdc on 2012-10-16
I see this is a new printer; searching the Canon Asia and Canon Europe sites, there are no linux drivers yet for this; usually a programme called turboprint has support;

I suspect one could download the mp210 driver; and just edit it, to the MP230.......

that has linux support:

one would need to edit the .ppd file (to replace 210 with 230)

...........if you are willing to............

.....go here...........

[COLOR="Red"]AND LEAVE THE MP230 TURNED OFF [/COLOR]

[http://www.canon.co.uk/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MP_series/PIXMA_MP210.aspx?DLtcmuri=tcm:14-738151&page=1&type=download](http://www.canon.co.uk/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MP_series/PIXMA_MP210.aspx?DLtcmuri=tcm:14-738151&page=1&type=download)

and download the [COLOR="SeaGreen"]MP210_debian.tar[/COLOR] .......*downloads should go to your [COLOR="SeaGreen"]Downloads[/COLOR] directory by default* ........

using a terminal I would use the commands ([COLOR="SeaGreen"]copy and paste them[/COLOR]..)

> cd Downloads ....hit the enter key after each command.....

> tar -xvf MP210_debian.tar ....that will unpack the file and you should get what I got when I did the same on this file; next we install.......

> sudo dpkg -i cnijfilter-common_2.80-1_i386.deb.......enter your sudo password .......that installs the common filter.........

> sudo dpkg -i cnijfilter-mp210series_2.80-1_i386.deb .....that should be installed now

.....now to make some changes for the 230 to be recognised...........

> gksu gedit /etc/cups/canonmp210.ppd ......that opens the .ppd file .....use the control F function of gedit and replace 210 with 230 .......you will see it only appears in a small cluster at the very top of the ppd file

[COLOR="Red"]**SAVE AS**[/COLOR]: [COLOR="Blue"]canonmp230.ppd[/COLOR]          (it should be in the same directory as the 210 which should be /etc/cups/             obviously, this is most important)

then paste this into a browser window [http://localhost:631/printers/](http://localhost:631/printers/) and select the [COLOR="Magenta"]MP210[/COLOR] if it appears....... click on it ....select administration.....and [COLOR="Magenta"]delete it if it exists[/COLOR]......

......now we move to register the 230 ............

> sudo /etc/init.d/cupsys restart  ..restart cups........

[COLOR="Red"]NOW TURN MP230 ON[/COLOR] ..

...........*[COLOR="SeaGreen"]then you need to tell your system about this new MP230[/COLOR]*.......

> sudo /usr/sbin/lpadmin -p MP230 -m canonmp230.ppd -v cnij_usb:/dev/usblp0 -E

.........that should sort of make it work.......

go back to [http://localhost:631/printers/](http://localhost:631/printers/) if needed and configure there

......linux is for adults....all this advice is in good faith.....it should all be fine and can be deleted if needed......

---

### Post by dragonfly41 on 2012-10-16
I had recent experience in trying to install Canon drivers so I'll add my pennyworth ..

[http://ubuntuforums.org/showthread.php?t=2071142](http://ubuntuforums.org/showthread.php?t=2071142)

I'll just add to pdc suggestions ..

I would avoid older version of cnijfilter e.g. cnijfilter-common_2.80-1_i386.deb 
and go here ...

[http://www.iheartubuntu.com/2012/02/install-canon-printer-for-ubuntu-linux.html](http://www.iheartubuntu.com/2012/02/install-canon-printer-for-ubuntu-linux.html)

I suggest that you use Synaptic Package Manager and search "cnij" to see if you've got older filters installed .. if so "Mark for Upgrade" both filters.  That worked for me on an ip2600 after help from the forum.

---

### Post by oldos2er on 2012-10-16
Old thread closed.

If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

