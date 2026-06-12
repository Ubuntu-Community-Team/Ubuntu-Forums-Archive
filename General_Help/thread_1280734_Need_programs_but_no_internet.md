---
title: "Need programs but no internet"
date: 2009-10-02
forum: General Help
---

### Post by espressobeanie on 2009-10-02
Hi, I don't have the internet for my computer running Ubuntu Jaunty. There are some programs I need to get like wine and vlc. I've downloaded the files for it, but then my computer said it can't do anything without the required dependencies for that file, and I have to get the dependencies for those files, and such. Is there some way for me to get one file that will just install the program and all those little dependencies like Windows does? I'd hate to have to chase thru 50 different little installers to make the main installer work.

---

### Post by undecim on 2009-10-02
Try [http://keryxproject.org/](http://keryxproject.org/)

I've never tried it personally, but I've heard others recommend it. It should do what you want.

---

### Post by dhughes on 2009-10-02
Any of your neighbours have wifi? ;)

---

### Post by espressobeanie on 2009-10-02
They all have an encrypted internet and I don't have a compatible wireless card to start "testing" them with Backtrack 3. The only connection I have is a library computer. Full access to someone else's computer is impossible to get.

---

### Post by onyxwolf on 2009-10-02
Make a download script of the programs you need. Go to System > Administration > Synaptic after it opens search and select the program you want, check "Mark for Installation". It will tell you dependencies it needs, click mark. Now go to file > Generate download script, name it and save it. This will be a simple script that will have the commands to only download all needed dependencies. Run this script on an internet connected computer (probably want it to in its own folder because thats where its going to copy all the files to). and there you go! Put that folder and all contents on thumb drive and install at the non-connected computer. Fun-times!

If the only internet connected machine you can use is a Windows :evil: machine just open the script in a text editor and each wget -c line will have the URL to download the files you need.

---

### Post by sedawk on 2009-10-02
This problem has bothered me for years ;-)
Either when there is need to install new software or
when you want to install security updates.

It is always the same story:
* You have an offline PC
* You need application XYZ, so you download it (on a PC not
  running GNU/Linux).
* Installation fails because of dependencies.

What you need is a proper shopping list; the delta of
what is already on your PC and what is needed to install
product XYZ.

As your offline machine doesn't have a up-to-date package
database the shopping list cannot be created there.
The best solution would be a web application that you
can feed with the list of installed packages on
the offline machine and that returns a web page
listing download links for all packages
you need (the "delta") - even including security updates (by default).

This would be nice if it even works for multiple
distros (Ubuntu,Fedora,...)

A more expensive but much simpler approach is to get
an external disk and mirror Ubuntu's "repositories" to that
disk regulary and connect it to the offline PC when needed.
But there are many companies that do not allow read-write
media to enter the companies building, so you need
the "delta" solution again ...

---

### Post by jward3010 on 2009-10-02
> **dhughes said:**
> Any of your neighbours have wifi? ;)
Ha Ha, i love neighbours with unprotected AP's, bloody idiots!

---

### Post by espressobeanie on 2009-10-02
There's a problem with doing a script from synaptic manager. It doesn't know the package list besides what the cd installed because it never connected to the internet. 
I fear that modern OS'es require computers to not be standalone to get updates anymore.
Also, I have a dependency logic probleem. Two dependencies require the other to be installed first before the other can. Wxwidgets and wxcommon, I believe. what do I do?

---

### Post by oldsoundguy on 2009-10-02
you failed to mention if this is a laptop or a desktop.
If the former, take a couple of bucks and your laptop and go to Starbucks and get your downloads that way. Or go hang out at the airport for a few hours in the main waiting room.

---

### Post by espressobeanie on 2009-10-02
Sorry. Its a desktop. If it was laptop, I'd get free wifi already.

---

### Post by DrMelon on 2009-10-02
On another computer, download all the .deb files you need for a particular program. You can find out what the dependencies are and download them at:
[http://www.getdeb.net/](http://www.getdeb.net/)

After that, just copy them to a USB disk and move them over, then double-click the deb files to run them.

---

