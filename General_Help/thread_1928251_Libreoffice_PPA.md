---
title: "Libreoffice PPA"
date: 2012-02-19
forum: General Help
---

### Post by Welly Wu on 2012-02-19
I added the Libre Office PPA to my Ubuntu 11.10 64 bit system and I am wondering when Libre Office 3.5 will be included in the PPA. How long will it take before this PPA is currently up to date?

---

### Post by Leppie on 2012-02-19
to me it looks like 3.5 is already in the ppa:
>                  libreoffice                                               1:3.5.0-1ubuntu1~ppa2                                                                  [Björn Michaelsen]("https://launchpad.net/%7Ebjoern-michaelsen")                                      (6 hours ago)                                  

---

### Post by duke.tim on 2012-02-19
The PPA is for libre office is stated as mainly for testing before it is released for the distribution.

It looks like about 6hours ago (from when this was posted) that packing has begun

[https://launchpad.net/~libreoffice/+archive/ppa/+builds?build_state=building](https://launchpad.net/~libreoffice/+archive/ppa/+builds?build_state=building)

It appears the goal is to release the next version around the next Ubuntu release

[https://blueprints.launchpad.net/ubuntu/+spec/desktop-p-libreoffice-packaging](https://blueprints.launchpad.net/ubuntu/+spec/desktop-p-libreoffice-packaging)

---

### Post by Welly Wu on 2012-02-19
Update Software and sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade does not download and install the new Libre Office 3.5 software packages. How do I get Libre Office 3.5 installed on my Ubuntu 11.10 64 bit system through the PPA? I would rather not download and install the individual .DEB packages from the Libre Office website every time that there is a newer version or update.

---

### Post by Welly Wu on 2012-02-19
I will have to wait for Ubuntu 12.04 64 bit LTS to be released for Libre Office 3.5.

---

### Post by duke.tim on 2012-02-19
Libre office should be included in the default ubuntu repositories, meaning that libre office will be automatically updated when a new version is released.

There will be some delay in the release of new versions of software for testing purposes to ensure compatibility with the operating system, and for bug fixes.

If you want the newest version you might be able to alter the PPA that you added to use "Precise" instead of the version you currently have oneiric

```
deb http://ppa.launchpad.net/libreoffice/ppa/ubuntu oneiric main 
```

There is the possibility for bugs and incompatibility if you do this.

---

### Post by Welly Wu on 2012-02-20
If I switch from oneiric to precise, then will it definitely screw up my Libre Office on Ubuntu 11.10 64 bit? Has anyone else tried this yet?

---

### Post by Welly Wu on 2012-02-20
I tried the precise instead of oneiric and it does not work. I switched it back to oneiric and re-installed Libreoffice-core.

---

### Post by duke.tim on 2012-02-22
Sorry that it didn't work :(

I switched back to 32 bit because some programs I use have been slow to update to 32bit, So I can't test the 64bit stuff right now :/  .
I guess you just have to wait or download it from the webpage.

---

### Post by TuxHerder on 2012-02-24
The Libreoffice ppa update for Lucid 32 just failed.  Appears to be a broken help system deb.

---

### Post by TuxHerder on 2012-02-25
> **TuxHerder said:**
> The Libreoffice ppa update for Lucid 32 just failed.  Appears to be a broken help system deb.

Additionally, in Libreoffice 3.5, Calc is completely broken.  Cut and paste is non-functional; the down arrow key will not move the selection down to the next cell.  I haven't had time to look at it too closely, but it's completely unusable.

I badly need to go back to 3.4 from 3.5 - because I need Libreoffice to actually work, but have no idea how to do this - or even if it's possible to go back to the last working version (3.4) since the current version is useless.

---

### Post by TuxHerder on 2012-02-25
> **TuxHerder said:**
> Additionally, in Libreoffice 3.5, Calc is completely broken.  Cut and paste is non-functional; the down arrow key will not move the selection down to the next cell.  I haven't had time to look at it too closely, but it's completely unusable.

I badly need to go back to 3.4 from 3.5 - because I need Libreoffice to actually work, but have no idea how to do this - or even if it's possible to go back to the last working version (3.4) since the current version is useless.


Found a solution to the 'down arrow' key not working in Calc:

Go into the Tools menu, select Customize then click on the Keyboard tab.  In the Shortcuts box the Down key should have Move Down as its  function.

And the cut/paste issue has disappeared.  [Sigh.]

---

### Post by duke.tim on 2012-02-25
If you need the stable version (3.4) first remove the old one

```
sudo apt-get purge libreoffice
```

Then set the PPA back to the original, or alternatively remove it entirely from your sources. Where oneiric is your version of ubuntu

```
deb http://ppa.launchpad.net/libreoffice/ppa/ubuntu oneiric main
```

*if in doubt Use the libreoffice package in the main repositories (e.g. the repositories you get without having added any sources)

You can do this by searching in the software center or by

```
sudo apt-get install libreoffice
```

---

### Post by vasa1 on 2012-02-25
> **TuxHerder said:**
> ...
I badly need to go back to 3.4 from 3.5 - because I need Libreoffice to actually work ...

Buried deep in their [announcement ]("http://nabble.documentfoundation.org/LibreOffice-3-5-the-best-free-office-suite-ever-td3743387.html")is this nugget: > The Document Foundation invites power users to install LibreOffice 3.5,
and** more conservative** users to stick with LibreOffice 3.4 branch. 
I'm on 3.4.4 and will stay on that till a higher version is pushed to me from "main". I'm not adding a ppa to get the latest and greatest in office ware.

---

### Post by cottfcfan on 2012-02-26
Another problem is that LO 3.5, will not open any password protected docs, that were passworded with 3.4 & below.
Best to stick with the Oneriec Main one me thinks.

---

### Post by Krytarik on 2012-02-26
> **cottfcfan said:**
> Another problem is that LO 3.5, will not open any password protected docs, that were passworded with 3.4 & below.
Actually not; LibreOffice 3.5 is downward compatible reg. the encryption:

[http://wiki.documentfoundation.org/ReleaseNotes/3.5#Different_Encryption_Algorithm](http://wiki.documentfoundation.org/ReleaseNotes/3.5#Different_Encryption_Algorithm)

Regards.

---

### Post by cottfcfan on 2012-02-26
> **Krytarik said:**
> Actually not; LibreOffice 3.5 is downward compatible reg. the encryption:

That maybe so, but a number of people, self included, cannot open documents in 3.5, that have been passworded with 3.4 & previous.
It's a known bug by the looks of things.

---

### Post by kurt18947 on 2012-02-26
> **cottfcfan said:**
> That maybe so, but a number of people, self included, cannot open documents in 3.5, that have been passworded with 3.4 & previous.
It's a known bug by the looks of things.

I wonder if the bug has to do with the distro?  I have a password protected .odt file that was created 3 or 4 years ago and opens fine with LibreOffice3.5 running on Precise P.  Perhaps 3.5 doesn't like older distros?

---

### Post by TuxHerder on 2012-02-26
> **duke.tim said:**
> If you need the stable version (3.4) first remove the old one


Thanks,

I tried something similar - but since I'm using Lucid, I tried to revert to OpenOffice (which has its own set of issues, and gave up after trying to track down all the dependencies and reinstalled Libreoffice from the ppa).  After removing and reinstalling, the cut/paste problem vanished (no clue why, but I'm happy it's gone) and I figured out how to make the down arrow key work.

The US English help package for Libreoffice 3.5/Lucid is still broken, I also tried to install the British English help package but it's broken too.  The upside is that the help package doesn't appear to be needed.

---

### Post by Krytarik on 2012-02-26
> **cottfcfan said:**
> That maybe so, but a number of people, self included, cannot open documents in 3.5, that have been passworded with 3.4 & previous.
**It's a known bug** by the looks of things.
Do you have a link to a bug report then, by chance?

---

### Post by cottfcfan on 2012-02-26
Bug reports:
[https://www.libreoffice.org/bugzilla/show_bug.cgi?id=45171](https://www.libreoffice.org/bugzilla/show_bug.cgi?id=45171)
[http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/022ac863901bc938/e6516dc7021ed567?lnk=raot](http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/022ac863901bc938/e6516dc7021ed567?lnk=raot)
[http://lists.debian.org/debian-openoffice/2012/02/msg00066.html](http://lists.debian.org/debian-openoffice/2012/02/msg00066.html)

---

### Post by TuxHerder on 2012-02-26
They just pushed out a new update for LO 3.5/Lucid - and the US English help package installed this time :)

Unfortunately, it also seems to have screwed up the key bindings in Calc again - because 'backspace' isn't doing what it used to/is supposed to do.

---

