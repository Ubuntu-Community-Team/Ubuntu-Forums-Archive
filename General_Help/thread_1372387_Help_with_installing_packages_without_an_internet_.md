---
title: "Help with installing packages without an internet connection"
date: 2010-01-04
forum: General Help
---

### Post by pimpenn on 2010-01-04
I am a new user to linux. I downloaded and installed ubuntu 9.10 on my old desktop to try it out because i have always liked the idea of linux but have never really found the time to use or learn to use it. having had an old dos computer i can vaguely remember the idea of using a command line to change directories etc. so i just decided to wipe out xp on the desktop and install ubuntu lol. Installation went smooth but then i ran into some problems.... 

Unfortunately i use iphone tethering for access to the internet but ubuntu will only recognize my iphone as a picture storage device. so i did some research and found that i had to download and install some packages to set up tethering on ubuntu. so on my laptop running vista i downloaded libusb-1.0.6, cmake-2.8.0, libiphone-0.9.5, usbmuxd-1.0.0, and some other packages such as ifuse and libgpod. they were all .tar.bz2 files or .tar.gz files. I put these on a jump drive and took the jumpdrive and put it into my desktop. what i was wondering is if there is a way to install these packages from a usb jumpdrive? or is there a simpler way that i may have overlooked to establish an internet connection.

---

### Post by pimpenn on 2010-01-04
also i forgot to mention this but i dont know if it matters or not. my iphone is a jailbroken 3gs os 3.1.2. i have mywi installed along with the internet tethering patch. i have also used pdanet in the past.

---

### Post by bodhi.zazen on 2010-01-04
I advise you look at Aptoncd:

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by jamesisin on 2010-01-04
Obviously the easiest thing to do would be to travel to a location where you can attach to the Internet long enough to get your tethering working.  That would be my best recommendation.

---

### Post by t0p on 2010-01-04
Are the packages you want available through Synaptic?  If so, I *believe* you can do the following (note I have only read about this):

[LIST]
[*]Go to Synaptic (**System > Administration > Synaptic Package Manager**);
[*]Search for the required packages (using the Search button, *not* the Quick Search box);
[*]Select the required packages in the list and click "Mark for Installation".  Synaptic may bring up a list of other required packages (known as "dependencies") - if so, click to get them too;
[*]Once you've got all the packages you want "marked for installation", go to **File > Generate package download script**.  This will create a script that you can use on another computer with internet access to download the packages you want;
[*]When you've generated your package download script, stick it on a flash stick or something, and take it to a computer with internet access.  Run the script and it will download the packages.  Save them to your stick;
[*]Now you can transfer the packages to your computer.  Double-click on the package files and they will install.
[/LIST]
I read that you can run a package download script on a Windows computer, but I don't know that for sure - like I already said, I have never done this myself.  But it should solve your problem... assuming that the packages you want *are* available through Synaptic.
****EDIT**** Actually, I'm not so sure the script *can* be run on a Windows machine.  I checked the properties of a generated download script and filetype is reported as "shell script (application/x-shellscript)".  So I think you'll need to use an *Ubuntu* computer to download the packages you want.

If the packages are *not* available through Synaptic, and you can only get them in .tar.gz format, you'll need to download them to a computer with internet access, save them to a flash stick and transfer them to your Ubuntu computer.  Then you right-click on each .tar.gz archive and select "Extract here".  This will extract from the archive a folder containing the software you need.  How you run/install that software will depend on its format.  Check them out then post here the details and someone will advise you further.

---

### Post by jamesisin on 2010-01-04
t0p - Perhaps it's possible to run that script through Cygwin (on Windows) since Cygwin uses bash.

---

### Post by t0p on 2010-01-04
> **jamesisin said:**
> t0p - Perhaps it's possible to run that script through Cygwin (on Windows) since Cygwin uses bash.

Yeah, possibly.  I've never used a package download script myself - I didn't even know about it until I read a thread on it in these forums the other day.  I generated an example script and looked at it in a text editor: it's a shell script that uses wget to download the required packages.  So it needs a computer that uses bash (or Bourne, I guess).  Linux, *BSD, Unix, should all be fine.  Does Mac OSX use bash or Bourne shell?

**EDIT:** I've attached my example package download script if anyone wants to take a shuftie.  I made it to install Inkscape (and dependencies).

---

