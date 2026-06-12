---
title: "which Clamav antivirus modules?"
date: 2010-08-06
forum: General Help
---

### Post by BlackLab on 2010-08-06
Hi all,
I wish to try ClamAV, but when I search 'anti-virus' in 'provided by Ubuntu' section in Ubuntu Software Centre, I find there are several items with the name Clamav: Clamav, Clamav-base, Clamav-daemon, Clamav-Freshclam, etc

Which ones do I need to install to have anti-virus on Ubuntu?

---

### Post by inameiname on 2010-08-06
Just enter this into the terminal, and it'll all be installed:


sudo aptitude install clamav clamav-base clamav-daemon clamav-freshclam clamtk


And if you want a more up-to-date version, add the clamav repository to your sources.list:


deb [http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu) lucid main
deb-src [http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu) lucid main

---

### Post by BlackLab on 2010-08-06
Thanks, That is clever!
But before I go ahead I need answers to the following:
Do I need all of those Clamav modules?

I do want the most up to date version, but why are those not the ones installed first?

If I add the Clamav repository to my sources what does it do? does it keep it up to date automatically in the future?

---

### Post by ronnielsen1 on 2010-08-06
> Do I need all of those Clamav modules?
This is Linux. You don't need any of them. You won't get any viruses but you could use it to scan attachments before you send them to your Windows friends, but no, the packages that inameiname mentioned should be great

---

### Post by ronnielsen1 on 2010-08-06
> If I add the Clamav repository to my sources what does it do? does it keep it up to date automatically in the future?
Yes, but you might have to adjust the settings in klamav

---

### Post by BlackLab on 2010-08-06
> **inameiname said:**
> Just enter this into the terminal, and it'll all be installed:


sudo aptitude install clamav clamav-base clamav-daemon clamav-freshclam clamtk


And if you want a more up-to-date version, add the clamav repository to your sources.list:


deb [http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu) lucid main
deb-src [http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu) lucid main

Since Ronnielsen1's reply I went ahead.

However the terminal didn't like 'deb' and suggested 'debc' which required ?debscripts? to be installed. So I went ahead and installed that and tried again:
debc [http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu) lucid main

this came back:

debc: cannot find readable debian/changelog anywhere!
Are you in the source code tree?

Where do I need to be? (I think I was in the home/username directory)

---

### Post by ronnielsen1 on 2010-08-06
How did you try to install these repositories? I'm not in Ubuntu right now so I'm going on memory but enter sudo gedit /etc/apt/sources.list in a terminal to add to the repositories. Then enter the repos

> deb [http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu) lucid main
deb-src [http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu) lucid main 	

and save and exit

Back in the terminal
sudo apt-get update
sudo aptitude install clamav clamav-base clamav-daemon clamav-freshclam clamtk

You could also do this through synaptic

---

### Post by inameiname on 2010-08-06
Okay, let me clarify...

sudo aptitude install clamav clamav-base clamav-daemon clamav-freshclam clamtk

All are required (all part of what is Clamav) it seems from what I found out when first installing. Just do that first. They will be the most recent versions of those apps in the official repos from Ubuntu. Unfortunately, they tend to get a little out-of-date after an Ubuntu version has been out for a while, thus, the need to install another source, or repo, which will check and install more recent if any available. Oh, and no settings are required to be changed. And as mentioned, antivirus isn't necessary, but I keep it on as it can scan for Windows viruses (along with Linux ones) before you send something to somebody with Windows, so you don't accidentally infect theirs. hehe

To add the Clamav repo:

Instead of adding those two lines, do this:

sudo add-apt-repository ppa:ubuntu-clamav/ppa
sudo aptitude install clamav clamav-base clamav-daemon clamav-freshclam clamtk

Then you are done

---

### Post by BlackLab on 2010-08-07
Thanks! I'm pretty sure that all worked out ... 
How did you know these exact commands? Years of reading? man pages? Living and breathing Linux?

---

### Post by inameiname on 2010-08-07
Googling..... :P

Really I read from various sources that Clamav was the best, so I looked it up and inquired as to just what must be installed. And after looking at a few different sources, it seems all of those are what are required. The clamtk is the gui for clamav, so you don't have to use it solely through the terminal. That one actually isn't in the repo. You have to go to their website and download the most recent. Ah well. 

Finally, why yes, I do seem to live and breathe Linux. Good time-waster to appease boredom, and like tonight, a touch of insomnia. :P

---

### Post by WorMzy on 2010-08-07
Generally speaking, if you come across a bunch of similar packages like that, just choose to install the one with just the name (e.g. just the "clamav" package); if the other packages are required, they'll be installed too.

In this case, clamav is the main package, clamav-base sets up the clamav user, clamav-daemon is needed if you want to run clamav as a background task, and clamav-freshclam is the package that sets up the updater, so that you receive virus definitions updates. clamtk is a graphical front-end to clamav's features, in case you're not comfortable with using the command line interface.

---

### Post by BlackLab on 2010-08-07
> **WorMzy said:**
> Generally speaking, if you come across a bunch of similar packages like that, just choose to install the one with just the name (e.g. just the "clamav" package); if the other packages are required, they'll be installed too.

In this case, clamav is the main package, clamav-base sets up the clamav user, clamav-daemon is needed if you want to run clamav as a background task, and clamav-freshclam is the package that sets up the updater, so that you receive virus definitions updates. clamtk is a graphical front-end to clamav's features, in case you're not comfortable with using the command line interface.

ok, great, thanks . I did not realise it was running in the background now .. .. although . just testing ... it did not catch EICAR
[http://www.eicar.org/anti_virus_test_file.htm](http://www.eicar.org/anti_virus_test_file.htm) when I downloaded EICAR.COM

Clamav does identify it as virus when I manually choose to scan it, but no sign of it running in the background

---

### Post by BlackLab on 2010-08-07
> **inameiname said:**
> Googling..... :P

Really I read from various sources that Clamav was the best, so I looked it up and inquired as to just what must be installed. And after looking at a few different sources, it seems all of those are what are required. The clamtk is the gui for clamav, so you don't have to use it solely through the terminal. That one actually isn't in the repo. You have to go to their website and download the most recent. Ah well. 

Finally, why yes, I do seem to live and breathe Linux. Good time-waster to appease boredom, and like tonight, a touch of insomnia. :P

Keep up the good work then! .. your' time wasted' has saved me a ton of time ..
and that of many others I'm sure :D
cheers

---

### Post by WorMzy on 2010-08-07
> **BlackLab said:**
> ok, great, thanks . I did not realise it was running in the background now .. .. although . just testing ... it did not catch EICAR
[http://www.eicar.org/anti_virus_test_file.htm](http://www.eicar.org/anti_virus_test_file.htm) when I downloaded EICAR.COM

Clamav does identify it as virus when I manually choose to scan it, but no sign of it running in the background

Have you restarted, or enabled the daemon? I'm not sure if it starts running immediately after installing.

To enable the daemon, I believe that you need to run ```
sudo service clamav-daemon start
``` After it's running in the background, you can monitor it with ```
/usr/bin/clamdtop
```, and force the daemon to scan a particular file with ```
clamdscan
```

You can edit the daemon's setting by editing /etc/clamav/clamd.conf```
gksu gedit /etc/clamav/clamd.conf
``` or by running ```
dpkg-reconfigure clamav-base
``` You'll need to restart the daemon for the changes to take effect though:
```
sudo service clamav-daemon restart
```

---

### Post by BlackLab on 2010-08-07
haha, I got into all sorts of trouble there!
I ran this: sudo service clamav-daemon start
and it reported that the daemon was already running .. all good, fair enough.
I then ran: /usr/bin/clamdtop and that worked fine also.

Then I ran: gks gedit /etc/clamav/clamd.conf or the other one, and that's when it all went wrong.

I only went part way through configuration and gave up .. and that broke the deamon .. it was no longer working .. so I went to software centre and downloaded the wrong package .. although  now I can't find exactly what that was .. It was an altogether more complex AV scanner manager

Anyway after further blind alleys I went back to **inameiname's**I installation instructions, thinking the config would be reset as a result .. but no joy . I could not avoid** gksu gedit /etc/clamav/clamd.conf** and following through the configuration wizard, even though I was not sure what configuration options were correct.

.... but now i think I am back to where I was .. the daemon is working again .. but still it does not flag EICAR unless I manually scan it ... strange

---

### Post by WorMzy on 2010-08-07
```
sudo dpkg-reconfigure clamav-base
``` should have fixed the conf file up if it messed up; sorry I forgot to prepend sudo to the command the first time I posted it.

Also, I think the daemon just sits in memory and waits for you to tell it to scan something with ```
clam_d_scan
```

If you use ```
clamscan
``` to scan files, it needs to load the virus database every time. Since clam_d_scan is a daemon, it keeps the virus database loaded and ready to use, so your scans take less time to complete.

Which internet browser do you use btw? If you use Firefox, you can install an extension called [Download Statusbar]("https://addons.mozilla.org/en-US/firefox/addon/26/"), which allows you to run a virus scan after every download.

Just set "Anti-Virus program location" to ```
/usr/bin/gnome-terminal
``` and the "Arguments" to ```
--window-with-profile=hold -x [COLOR="Blue"]clamscan[/COLOR] -v [COLOR="DarkGreen"]-l /home/[/COLOR][COLOR="Red"]<USERNAME>[/COLOR][COLOR="DarkGreen"]/Clamscan_Firefox_Results[/COLOR] [COLOR="DarkOrange"]--move=/home/[/COLOR][COLOR="DarkOrange"][COLOR="DarkOrange"]<USERNAME>[/COLOR]/.infected[/COLOR] %1
```

That'll open a gnome-terminal with the "hold" profile (which you'll need to make) and run clamscan (replace with clamdscan if you want).

The scan results will be logged in your home folder, in a file named Clamscan_Firefox_Results.

Any infected files will be moved to a hidden folder in your home folder, called .infected (in case you downloaded them to an NTFS partition), where you can delete them safely, or move them where ever you want them (if you think that the virus was a false-positive).

For the gnome-terminal profile, just open gnome-terminal, go to edit -> profiles -> new, set the name to hold and the base to anything, then click OK. In the next window, click the Title and Command tab and set, "When command exits" to "Hold terminal open".

You may be able to substitute all this command line scanning for the clamtk GUI program. I don't use it, so I dunno if it allows you to use it like this.

If you use a different browser, then you'll need to find a different solution to autoscan downloaded files.

---

### Post by inameiname on 2010-08-07
No prob. Glad you have gotten it back to the way it was after your few tweaks. Oh, and nice info, WorMzy. I'll remember your suggestions whenever I feel like tweaking things with Clamav.

---

### Post by BlackLab on 2010-08-07
Thanks WorMzy, I do use Firefox browser, so by your method I should be able to set up the integration between it and clamav in the near future.

Thanks to all who have replied.

---

