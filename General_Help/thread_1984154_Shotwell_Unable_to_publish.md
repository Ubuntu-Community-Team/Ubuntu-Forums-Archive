---
title: "Shotwell Unable to publish"
date: 2012-05-21
forum: General Help
---

### Post by pooky2483 on 2012-05-21
This problem has only just showed up, I cant publish video's or pictures to facebook.
I have tried a re-install in my Synaptic Package Manager but that didnt fix anything so I went over to [Shotwell's]("http://www.yorba.org/") site and found a reference to [Vala]("https://launchpad.net/%7Evala-team/+archive/ppa") and added the PPA  'sudo add-apt-repository ppa:vala-team' just co cover myself on that angle. As well as obviously checking that I have Shotwell added to my PPA 'sudo add-apt-repository ppa:yorba/pp'.
I don't know what else to do, unless it's a new bug thats just appeared with Shotwell?

---

### Post by eric-yorba on 2012-05-21
What version of Shotwell are you running?

Also: just to be clear, Vala is a compiler.  Unless you're compiling Shotwell from source, you don't need to install it.

---

### Post by pooky2483 on 2012-05-21
I'm using version 0.12.3+trunk of Shotwell.
Thanks for that, I will now uninstall vala.

---

### Post by eric-yorba on 2012-05-21
What error are you seeing (if any) when you try to publish?

Also, if you log into Facebook and go to this page, does "Shotwell Connect" show up on the list?
[https://www.facebook.com/settings?tab=applications](https://www.facebook.com/settings?tab=applications)

---

### Post by pooky2483 on 2012-05-21
> **eric-yorba said:**
> What error are you seeing (if any) when you try to publish?

(See attachment)

> Also, if you log into Facebook and go to this page, does "Shotwell Connect" show up on the list?
[https://www.facebook.com/settings?tab=applications](https://www.facebook.com/settings?tab=applications)
I can't get on the web page as it says page not found, but I have managed to 'like' the page.

---

### Post by eric-yorba on 2012-05-22
This could be a bug in our packaging.  We're looking into it.

---

### Post by eric-yorba on 2012-05-22
By the way, have you tried uninstalling the daily build and installing 0.12.3 from our PPA?  That should do the trick for now.

---

### Post by MrWylbur on 2012-05-22
> **eric-yorba said:**
> By the way, have you tried uninstalling the daily build and installing 0.12.3 from our PPA?  That should do the trick for now.
Rolling back to the Ubuntu supplied version also cleared up the issue.  Thanks!

---

### Post by pooky2483 on 2012-05-24
> **MrWylbur said:**
> Rolling back to the Ubuntu supplied version also cleared up the issue.  Thanks!

Sorry I've not replied sooner, I've been a bit busy. Thanks for the help, I will give them a go and get back to you on how I fixed it (hopefully).

---

### Post by pooky2483 on 2012-05-24
Is it safe to uninstall from the Ubuntu Software Manager as I get this message and dont want to screw up my desktop?

---

### Post by Derek Karpinski on 2012-05-24
> **pooky2483 said:**
> Is it safe to uninstall from the Ubuntu Software Manager as I get this message and dont want to screw up my desktop?


No........stop!!

Since you've installed shotwell from a PPA, you need to do this:

```
sudo apt-get update && sudo apt-get install ppa-purge
```

Then:
```
sudo ppa-purge ppa:yorba/ppa
```

This should downgrade shotwell to the Ubuntu version.

---

### Post by pooky2483 on 2012-05-24
Did all that and now it will not run so I had a go at forcing a reinstall in Synaptec Package Manager and got this;

(Reading database ... 515925 files and directories currently installed.)
Preparing to replace shotwell 0.11.6-0ubuntu0.1 (using .../shotwell_0.11.6-0ubuntu0.1_amd64.deb) ...
Unpacking replacement shotwell ...
Processing triggers for gconf2 ...
Processing triggers for menu ...
Processing triggers for libglib2.0-0:i386 ...
warning: undefined reference to <schema id='org.gnome.glabels.locale'/>
warning: undefined reference to <schema id='org.gnome.glabels.objects'/>
warning: undefined reference to <schema id='org.gnome.glabels.history'/>
warning: undefined reference to <schema id='org.gnome.glabels.ui'/>
Processing triggers for libglib2.0-0 ...
warning: undefined reference to <schema id='org.gnome.glabels.locale'/>
warning: undefined reference to <schema id='org.gnome.glabels.objects'/>
warning: undefined reference to <schema id='org.gnome.glabels.history'/>
warning: undefined reference to <schema id='org.gnome.glabels.ui'/>
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Setting up shotwell (0.11.6-0ubuntu0.1) ...
Processing triggers for menu ...
------------------------------------------------------------------------------------------------------------------
Any ideas?

---

### Post by pooky2483 on 2012-05-25
I have been unable to import my pictures from my camera even just connecting it via USB, it did not 'see' it so I had an idea to install another picture importer program to see if it 'fixed' the problem and it did. I am still unable to get Shotwell working. How can I completely 'safely' remove it and try a new install?

---

### Post by Derek Karpinski on 2012-05-26
Did you try?

```
sudo apt-get update && sudo apt-get install --reinstall shotwell
```

---

### Post by pooky2483 on 2012-05-26
Just tried that command but it didn't work for some reason.
 I plugged in my camera and it opened nautilus and in the top right corner it says 'Open Shotwell Photo Manager' but when I click on that, nothing happens..

---

