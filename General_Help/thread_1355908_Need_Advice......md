---
title: "Need Advice....."
date: 2009-12-15
forum: General Help
---

### Post by RazzyDaz on 2009-12-15
Ok I'm a newb, trying to update my firefox to 3.5.  I have downloaded the file and it's saved.  The file is / "home".  I have extracted the files, now what?  Is there something I'm missing?  I can't seem to get it to update.

Thanks

---

### Post by philinux on 2009-12-15
In ubuntu firefox will get updated automatically. It just takes a few more days after the official mozilla update for the devs to repackage it.

I'm currently running 3.5.5 are you wanting a later release?

---

### Post by RazzyDaz on 2009-12-15
Here is a little background....I was using Vista and spyware took over.  Needless to say, I tried to clean my hard drive and screwed up.  I would love to use Ubuntu, but I have a small problem.  My computer isn't recognizing my cd rom drive in the boot sequence.  So, I'm not able to use the live Cd.  I had an older copy of Ubuntu on my flash drive and was about to load Wubi, via safe mode.  

What I'm looking to do really is, load 9.10 ontop of wubi.  I can not get into vista, only in safe mode.  So, loading the live cd at startup is out of the question.  Is there a way to copy files from live CD onto my flash drive?

As for firefox, it will not automatically update.  I am getting all kinds of errors for extension and updates.  I was able to download the newest version, but not sure what to do, once it's on my computer.

thanks

---

### Post by Carborundum on 2009-12-15
I had the same problem (I'm running eeebuntu though). In the end I simply installed it manually. Try
sudo apt-get install firefox-3.5
That should do it.

---

### Post by ST3ALTHPSYCH0 on 2009-12-15
Does your mobo support boot from USB? You create a 9.10 or 9.04 live USB and install from there.

Conversely, you could try d/ling and running malwarebytes antimalware. It fixed my buddy's Vista install.

---

### Post by RazzyDaz on 2009-12-15
Honestly, I really don't want to use Vista anymore.  It's to much of a "hog."  I'm not exactly sure what a mobo is?  Is there a way to run the install via terminal inside of Wubi?  The cd rom drive recognizes the cd, just can't boot from it.  I know weird, huh!  

As for sudo apt-get install firefox-3.5, couldn't find package.

---

### Post by blues2use on 2009-12-15
Check this site...this is the method I've been using...

[http://tombuntu.com/index.php/2009/07/15/install-firefox-35-in-ubuntu-904-using-ubuntuzilla/](http://tombuntu.com/index.php/2009/07/15/install-firefox-35-in-ubuntu-904-using-ubuntuzilla/)

---

