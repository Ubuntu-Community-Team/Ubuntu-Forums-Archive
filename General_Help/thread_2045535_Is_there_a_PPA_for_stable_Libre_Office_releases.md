---
title: "Is there a PPA for stable Libre Office releases"
date: 2012-08-21
forum: General Help
---

### Post by Paddy Landau on 2012-08-21
I see that there is a [PPA for the test releases of Libre Office]("https://launchpad.net/%7Elibreoffice/+archive/ppa/"); this is not recommended for normal use.

The PPA for Ubuntu, as you know, tends to fall out of date. It is currently 3.5 on Precise (and unlikely to progress from there), whereas the latest release is 3.6.

I have hunted around, and cannot find a PPA for the [latest stable release of Libre Office]("http://www.libreoffice.org/download/").

The only way that I can find to upgrade Libre Office it is to download the [FONT=Lucida Console].deb[/FONT] and install, and keep an eye out for when it is updated.

Do you know where the PPA for the stable Libre Office release would be?

---

### Post by BigJules on 2012-08-21
Well, I'm using "ppa:libreoffice/ppa" and this delivered me 3.6...?

---

### Post by Paddy Landau on 2012-08-21
> **BigJules said:**
> Well, I'm using "ppa:libreoffice/ppa" and this delivered me 3.6...?
Yes, it would, as that is the PPA for builds in testing mode. That PPA is not for general use:
> Most of the packages in this ppa have only experienced minor testing … before they are published into the distro proper. … this ppa is  _not_ for the average user to install without a closer look
I'm looking for the PPA that delivers the official releases, as provided on the main download page.

---

### Post by vasa1 on 2012-08-21
> **Paddy Landau said:**
> Yes, it would, as that is the PPA for builds in testing mode. That PPA is not for general use:

I'm looking for the PPA that delivers the official releases, as provided on the main download page.
Actually, there was a bit of disagreement a while ago as to whether the official download page should have shown 3.6 for general use. Oddly, I can't find the thread here ([http://nabble.documentfoundation.org/Users-f1639498.html](http://nabble.documentfoundation.org/Users-f1639498.html)) which is where I very distinctly remember reading about it.

---

### Post by BigJules on 2012-08-22
I don't know what you're looking for in 'stable', Paddy, but I find 3.6 so happy on my Precise that I've moved it via that ppa above into all (3) production machines which I earn my bread on. No dramas, no losses, no tears. Go for it!

---

### Post by Linuxisfast on 2012-08-22
3.6 runs fine here installed via libreoffice ppa.

---

### Post by mastablasta on 2012-08-22
> **BigJules said:**
> I don't know what you're looking for in 'stable', Paddy, but I find 3.6 so happy on my Precise that I've moved it via that ppa above into all (3) production machines which I earn my bread on. No dramas, no losses, no tears. Go for it!
 
ok but there is a point in this. and that is that 3.7 (or for example 4.0) might not run so well once the update is pushed via that PPA. i too am interested in stable PPA. And like Paddy i too had to use .deb files to update.

---

### Post by Linuxisfast on 2012-08-22
There is already an unstable ppa for testing where most latest versions are pushed first, also you have choice to remove the ppa after updating to the latest one of your choice. This will prevent pushing of any new version. Also Ubuntu LTS provides security updates so eventually your version will get updated but it will take time in case you don't wish the ppa route.

---

### Post by jimmac49 on 2012-08-22
Just like BigJules I have no problems with this PPA, I have been using it, since when I used 10.04, until now when using 12.04, it plays nice and friendly, but the doc that I installed from and still do has this warning:-
  	 	 	 	 	 	   **LibreOffice Now Available in ppa for Ubuntu 10.10 and 10.04**

 Fri, 01/07/2011 - 18:03 — txwikinger  
 Libreoffice is now available and installed easily for Ubuntu 10.10 and 10.04 by adding the libreoffice ppa.
 The following steps allow the addition of the ppa and the installation of LibreOffice:
 **Warning:** This installs from a ppa and not from the official Ubuntu repository, hence there still might be problems with either the software itself, or the installation process. The installation will remove OpenOffice.
This may be not of any help, just my Tuppence worth


jim

---

### Post by Paddy Landau on 2012-08-22
Thank you all for the replies.

I have added the PPA, run the updates, and disabled the PPA.

I have subscribed to the Announce mailing list to watch for when Libre Office is updated, and I'll repeat the process each time a new Libre Office is released (enable the PPA; update; disable the PPA).

Audacity takes the same approach — it's a real pain!

---

### Post by mastablasta on 2012-08-22
there haven't been any major changes in 3.x versions
 
but let't say they create a new version (for exmaple with ribbons :-P of some sort)  where plenty of things owuld still be alpha, the testing of that would not be cool if one only wants latest stable.

---

### Post by Paddy Landau on 2012-08-22
> **mastablasta said:**
> but let't say they create a new version (for exmaple with ribbons :-P of some sort)  where plenty of things owuld still be alpha, the testing of that would not be cool if one only wants latest stable.
Precisely! That's why I want a PPA for only the officially-released versions, which currently is 3.6.0.2. (I am looking forward to 3.6.0.4, as it fixes a bug that causes me problems.)

---

