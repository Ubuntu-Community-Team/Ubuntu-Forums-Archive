---
title: "Software Center died in 10.04"
date: 2012-02-27
forum: General Help
---

### Post by Andrew_P on 2012-02-27
A couple of weeks ago I decided to remove OpenOffice.org and install LibreOffice 3.4 in its place.  Removing OpenOffice.org with Ubuntu Software Center was messy and required removing the modules one-by-one, rather than the entire suite with a single command.  After I installed LibreOffice, Update Manager complained about numerous unsatisfiable dependencies.  I clicked on the "Check" button and had it reload the software sources, after which the dependencies messages were gone, *but Update Manager proceeded to uninstall LibreOffice!*  It also removed cups-pdf, and a few other things that it shouldn't have.  (I don't remember all the details of what it took out; it was on the order of 3-5 packages in addition to LibreOffice.)  I re-installed LibreOffice and cups-pdf, and it is now running fine, but when I tried running Ubuntu Software Center later that day, I found it to be crippled.

Software Center opens, but when I click on any of the categories under "Get Software" in the left panel, e.g., "Provided by Ubuntu", the right panel never gets populated and the mouse cursor shows as an animated spinner forever.  I have the Network Monitor applet installed in the lower panel, and it never shows any network activity during this time, which tells me that Software Center isn't contacting the Canonical servers to retrieve a list of available packages.  When I launch Software Center from the command line in a terminal window ("software-center"), no errors are displayed and the Software Center windows opens without problems, but it still displays the spinner cursor forever, as before.

Other things I've tried, without success:

[LIST=1]
[*]Removed/reinstalled software-center
[*]Purged/reinstalled software-center (This also removed ubuntu-desktop. When I reinstalled ubuntu-desktop, it also reinstalled software-center automatically.)
[*]Purge/reinstalled apt-xapian-index, per discussion at [forum thread 1359893]("http://ubuntuforums.org/showthread.php?t=1359893"):
   $ sudo apt-get purge apt-xapian-index
   $ sudo apt-get install apt-xapian-index
   (I did this because Synaptic Package Manager was crashing every time I tried searching.  It fixed this crashing issue, but it had no effect on Software Center.)
[*]Set up Ubuntu 10.04.3 on a spare hard drive and installed LibreOffice.  No problems encountered and Software Center still worked fine afterward.  This leads me to believe that LibreOffice installation isn't the problem as such.
[/LIST]
As it stands now, I have a functioning installation of LibreOffice, but broken Software Center, considerably hampering browsing for available applications for my system.  (There's an [online version of Software Center]("https://apps.ubuntu.com/cat/"), but it isn't quite the same, as it isn't aware of packages currently installed on one's system.)

I've found discussions outside the Ubuntu Forums describing this very same issue with Software Center in Lucid Lynx (10.04), but no solutions.  I'd like to avoid having to re-install the system from scratch, since I've been using it well over a year and have hundreds of customizations that would take weeks to re-create. It seems Ubuntu Software Center has forgotten how to connect to the Internet on my machine, but I haven't a clue why this is so.  Damaged/altered path environment variable?  Something else?  Help would be appreciated.

---

### Post by ajgreeny on 2012-02-27
My main comment would be to bin the **software centre** and start using **synaptic** instead; it is much more powerful and has a far better search ability.

I did exactly what you have tried unsuccessfully to do, but I had no problems at all, or not related to the switch from OOo to LO; Open Office was removed by synaptic and LO with all of its dependencies was found straight away and installed.  I renamed the old hidden **~/.openoffice.org** folder in my home to **~/.libreoffice** and thus kept all my old configuration.

My only minor problem has been with the recent upgrade from LO 3.4 to LO 3.5 where all my local configuration in **~/.libreoffice** was ignored and a new folder made and then used in **~/.config/libreoffice**, meaning all my toolbar configurations, local dictionaries etc etc were suddenly changed back to the LO defaults.  I quickly found the reason and copied my old configuration back in place of the new one that had been made by the system.

Incidentally I love LO.  It seems so much better than OOo was, though I admit I have not used OOo now for some time, so it may have caught up somewhat.

---

### Post by Andrew_P on 2012-02-27
> **ajgreeny said:**
> My main comment would be to bin the **software centre** and start using **synaptic** instead; it is much more powerful and has a far better search ability.

Unfortunately, Synaptic Package Manager is just a list of names, with next-to-zero description of what the software does.  Software Center categorizes the software packages by general function and describes them, and often includes hyperlinks to the developer sites.  It's useful as an on-line catalog of what's available.  (Ubuntu Software Center is a slightly modified version of the program from Debian Linux.  Last week I performed a test installation of Debian Squeeze (6.0.4), and Software Center looks almost identical to that in Ubuntu 10.04, minus the Ubuntu branding.)

> **ajgreeny said:**
> Incidentally I love LO.  It seems so much better than OOo was, though I admit I have not used OOo now for some time, so it may have caught up somewhat.

I do, too.  Even though the now somewhat smaller OOo team has been fixing some issues, Canonical has not been offering anything more than critical security patches, apparently as a part of the decision to abandon OpenOffice.org in favor of LibreOffice in later releases of Ubuntu.  LibreOffice 3.4 has fixed some issues from OpenOffice.org that probably will never get fixed in the Ubuntu 10.04 repositories.

---

### Post by ajgreeny on 2012-02-28
Whilst I accept that synaptic looks different from USC, and in its default does not give as much information about packages, I always change the preferences to show properties of packages in the bottom pane of the window.  This gives a lot more information.

However, having been using ubuntu since 2005, and having got so used to the ways of the OS and all the packages that are available, it may be that I do not need the information that is available in USC as much as you do.

I'm not sure I can help you with any other suggestions, particularly about USC as I never use it.  Sorry about that.

---

### Post by Andrew_P on 2012-03-08
> **ajgreeny said:**
> Whilst I accept that synaptic looks different from USC, and in its default does not give as much information about packages, I always change the preferences to show properties of packages in the bottom pane of the window.  This gives a lot more information.
Thanks for the tip.  I haven't fully explored all the ways that Synaptic Package Manager can be used, but I'll try it out.  From what I can see so far, it may be able to do everything that Software Center does, except that the screen presentation is a bit intimidating at first and one must explicitly click on the "Get Screenshot" button to see any associated graphics that would be automatically loaded in Software Center.  If Synaptic had an option for automatically displaying graphics while browsing, Software Center would be completely superfluous.

If I can get used to using Synaptic for browsing, I'll consider simply removing Software Center completely &#8212; sort of like removing the training wheels from a bicycle.  Even though Software Center is now broken in my installation, nothing else appears to have been affected. :)

---

### Post by cortman on 2012-03-08
> **Andrew_P said:**
> Thanks for the tip.  I haven't fully explored all the ways that Synaptic Package Manager can be used, but I'll try it out.  From what I can see so far, it may be able to do everything that Software Center does, except that the screen presentation is a bit intimidating at first and one must explicitly click on the "Get Screenshot" button to see any associated graphics that would be automatically loaded in Software Center.  If Synaptic had an option for automatically displaying graphics while browsing, Software Center would be completely superfluous.

If I can get used to using Synaptic for browsing, I'll consider simply removing Software Center completely — sort of like removing the training wheels from a bicycle.  Even though Software Center is now broken in my installation, nothing else appears to have been affected. :)

If I know the name of a program I want to install, I almost always either run it in the terminal or use the USC. I use Synaptic for figuring out dependencies.
The USC definitely is a very nice interface and I really wish it were more reliable; hopefully some bugs will get fixed in 12.04.
Most people I've helped with USC issues were able to uninstall and reinstall and have it work fine afterward. But it's whatever you choose to do.

---

### Post by Andrew_P on 2012-03-23
I gave up and decided to start again with another hard drive, installing Ubuntu 10.04.04LTS from scratch, along with all the applications, and copying 241GB of photos, music and documents over.:cry:  It was three days of grunt work, and several more of tweaking to make the myriad adjustments to get it the way I like it.  Consider it "spring cleaning".

There may have been a relatively simple solution to the problem, but we may never know.  Operating without the Software Center made me feel like I was flying at night in a cloud with partial instrument failure ...

---

### Post by wildmanne39 on 2012-03-23
Hi, it is a matter of what you are use to I myself never open software center I use synaptic or the tertminal, but syanptic is more powerful and I use it to read what a package does also, its just is not as pretty and it looks more intimidating then software center.

---

