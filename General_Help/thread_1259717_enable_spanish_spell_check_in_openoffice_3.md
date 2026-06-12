---
title: "enable spanish spell check in openoffice 3"
date: 2009-09-06
forum: General Help
---

### Post by pythonscript on 2009-09-06
How do I enable spanish spell check in Open Office? I ran 

```
sudo apt-get install openoffice.org-help-es openoffice.org-l10n-es

``` but I still can't find the language. Any help here? Thanks!

---

### Post by jmszr on 2009-09-06
pythonscript,

You might try:```
sudo apt-get install myspell-es
```

This is what it says in Synaptic:> Spanish dictionary for myspell 
This is the Spanish dictionary for use with the myspell spellchecker
which is currently used within OpenOffice.org and the mozilla
spellchecker. It is based on ispell dictionary put together by
Santiago Rodriguez <srodri@fi.upm.es> and Jesus Carretero <jesus@fi.upm.es>.

Perhaps that will help.

---

### Post by pythonscript on 2009-09-07
That was actually the first thing I tried. I'll sheepishly admit that I simply forgot to restart openoffice... it's working beautifully now.

---

### Post by pythonscript on 2009-09-22
This just stopped working on me! No words are showing up underlined when I spell them wrong, and to my knowledge, I didn't change anything. Why isn't this working? My spell check in English works just fine, and when I open the spell check window (in English) I can select one of many Spanish options as the language and it'll check *the word spell check is currently highlighting  *in Spanish, but none others. 

I don't have access to Microsoft Office 2007, but I must be missing something! This was worlds easier in Windows. Any idea how I enable spanish spell check in open office? Thanks!

EDIT:  I just downloaded two dictionaries from an openoffice website, but they're .txt files, not .oxt files, so is there any way for me to install these? I'm using open office 3, where they've eliminated the Install Dictionaries wizard, apparently. Thanks for the help! This is a really serious problem with Linux if I can't do this in openoffice.

---

### Post by jmszr on 2009-09-24
pythonscript,

This is from another post - maybe it will help:

> NewlyHuman 

From what I recall, this is a bit finnicky.

In Tools > Options > Language Settings > Languages, is the default Western language Spanish, with a checkmark next to it?

The checkmark indicates the dictionary is properly installed.


---

### Post by peterthinking on 2009-09-24
Top part of this post has it step by step... just make sure you select the right dictionary.

Peter
-----------------------------------snip---------------------------------------------
 Some annoying things I've had to fix and kept notes on.
I can't take credit for all of them, credit goes to all the Linux community who have posted solutions all over the internet. I wish I kept names but I just cut and pasted the solutions.

These fixes apply to UBUNTU 9.04, If you've added stuff or deleted things from a standard install some things may not work but probably won't do any harm. Use at your own risk, I don't know enough to bail you out if you mess up your computer. Hey at least I'm honest.
--------------------------------------------------------------------
 To get a dictionary/thesaursus for OpenOffice 3.0 writer and enable spellcheck.
At the top of the OpenOffice writer navigate thru the menus...

Tools>> Language>> More Dictionaries Online...

 This opens a web page, Scroll down to your language and click on the blue name of the download to the right of your language.

 Another web page opens...click on "Get It"

 It downloads and a window pops up, click Ok to open it with OpenOffice.

 Another window pops up, this is the OpenOffice extension manager.

Agree again.

 Now in the open office writer navigate to here...

Tools>> Options>> Language Settings>> Writing Aids

Now make sure your "Available language modules" and "User defined dictionaries" are all checked off, also tick the "Check spelling as you type" in the bottom box.

Click "OK" at the bottom and restart OpenOffice writer.

Now when you type carot instead of carrot it will underline and give you a right click menu of possible words.
-------------------------------------------------------------------------
To save OpenOffice files in (GAG!!) Microsoft Office format to avoid compatability conflicts..

In terminal paste this and hit enter to get Microsoft fonts...

sudo apt-get install msttcorefonts && sudo fc-cache -fv

Start OpenOffice writer and navigate here in the OpenOffice writer window....

Tools>> Options>> Load/Save>> General

At the bottom of the page under "Document Type" 
Select the file type on the left then how to save it on the right.

Text Document - "Always Save As" - Microsoft Word 97/2000/XP
Spreadsheet - "Always Save As" - Microsoft Excel 97/2000/XP
Presentatiton - "Always Save As" - Microsoft Powerpoint 97/2000/XP

------------------------------------------------------------------------
To make wanda the fish work...
Right click on the bar at the top of your desktop

Add to panel>> Fish

This installs wanda, but sometimes she won't tell fortunes when you click on her.
In terminal type

sudo apt-get install cowsay

To get a Terminal up Navigate thru the menus like so....

Applications>> Accessories>> Terminal
--------------------------------------------------------------
To play DVDs on your computer

First install ubuntu restricted extras.

In Terminal type....

sudo aptitude install ubuntu-restricted-extras && sudo aptitude install w64codecs

Hit enter THEN...........

In terminal type...

wget [http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.5-1_i386.deb](http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.5-1_i386.deb)

Hit enter then type...

sudo dpkg -i libdvdcss2_1.2.5-1_i386.deb

Enter password or "y" for yes if prompted.

DVDs good to go.
-----------------------------------------------------------------
Got an old tower under the stairs? Wanna add a second drive you can  keep files on? Want recover the old files or just poke around?
Did you install it and you can see it but can't write to it?

You probably have to change permissions

Mount the drive...
On the top left of your desktop screen is "Places" you'll see it in there.
Go down the list to the new drive and give it one left click.
Right click on the drive icon that appears on your desktop.
File path is....
Properties-Volume-Settings-Mount point.

Now type "home" in beside Mount point you can give it a different mount point if you know what you're doing.

Then in terminal type...
sudo chown -R username:username /media/mountpointofthedrive

Substitute stuff as needed, my user name is peter and I used home so mine looked like this....

sudo chown -R peter:peter /media/home

To physically install the drive you have a few things to do.

Get a drive similar to the one you use now (same plugs on the back at least).
Unplug the tower.
Open the tower.
GROUND YOURSELF (touch the metal case before you touch anything in the case!)
Position the jumpers.
Mount the drive in the case.
Connect ribbon cables.
Plug in drive power.
Close it up.

 Look at the flat ribbon cable going to your current drive from the motherboard, it may have two connectors on it and your drive is hooked to one. Does the ribbon cable say "Master" and "Slave" near the plugs on it? 

If the cable isn't labled move the jumper to "Master" position on your UBUNTU drive and "Slave" position on your new (or reused) second drive and plug in the drives to the ribbon cable.

If the cable IS labled "Master"+"Slave" move the jumpers to "cable select" on both drives and plug in the drives to the ribbon cable.
Again "Master" is UBUNTU and "Slave" is the second drive.

Snake a power cable over to the drive from the power supply, there is usually a couple spares in the case not connected to anything. Don't worry about getting the wrong plug or putting it on backwards it only fits one way.

 To clarify the jumpers are little connectors that slip over pins on the *** end of the drive. How these are positioned determines how it works. You have to pull them off with a thumbtack or toothpick then just push them back on. Most drives have a little picture on it showing how to position them in the Master, Slave or Cable select positions. If yours don't have a pic google the drive model.

WRITE DOWN any jumper changes or cable changes you make to your main drive, if you can't get an old drive to work you'll want to change it back!

I also hook up the cables and try it out before I bother mounting the drive in the case, if the drive is fried at least I didn't waste time mounting it.

 If you need to change the partitions go to Add/Remove programs and get "Gnome Partition Editor". It will end up in the System>> Administration menu as "Partition Editor". My second drive is one 38.29 Gig ext2 partition with no flags. 

So that's that, you may have to mix it up a bit to get stuff to fit in the case, tuck the cords away from the fans and clean the processor heat sink and fan before you shut it up. I unbolt the fan and Qtip it and the heat sink.

And a little tip, you can unplug the box, pop open the case and unplug the power and ribbon to the second drive and all your files become invisible! Or just take it with you. Your computer still boots up without it.

 So dig out that old tower and make a frankenbox, while you're in there grab that second DVD burner or CD drive it's just a couple cables and it's easy!

Peter
-----------------------------------------------------------------
Have your computer make random beeps while it's locked and you're at lunch!

Cut and paste this into a terminal...

while true; do sleep $(($RANDOM/1000)) && beep -f 2000 -l $(($RANDOM/100)) ; done

Or for stranger beeps....

while true; do sleep $(($RANDOM/5000)) && beep -f $((RANDOM/10)) -l $(($RANDOM/100)) ; done

Then lock the terminal.

control c in terminal to stop it.
------------------------------------------------------------------
Flash not working? all choppy and pixeled?
Get rid of the old one....

In terminal type...

sudo apt-get remove --purge swfdec-mozilla mozilla-plugin-gnash flashplugin-nonfree adobe-flashplugin

Enable Canonical partner download, navigate here...

System> Administration> Software Sources> Third Party Software and then check on the Canonical partner boxes.

Get the new one...Type in terminal...

sudo apt-get install adobe-flashplugin


Done
-----------------------------------------------------------------
To browse files as root....you can do a lot of damage like this but if you need to it's possible.

In terminal type....

gksudo nautilus
------------------------------------------------------------------
To add the UBUNTU satanic edition screensavers, theme and wallpapers.

Get the key...

wget -q [http://ubuntusatanic.org/ubuntu-se-key.gpg](http://ubuntusatanic.org/ubuntu-se-key.gpg) -O- | sudo apt-key add -

Now we'll add the software repository to your system.

Go to System->Administration->Software Sources->Third Party Software->Add and enter the following APT line:

deb [http://ubuntusatanic.org/hell](http://ubuntusatanic.org/hell) jaunty main

click on install links go here....

[http://ubuntusatanic.org/installation.php](http://ubuntusatanic.org/installation.php)
----------------------------------------------------------------
To install GPG key and update sources and get some new themes.
First edit the /etc/apt/sources.list file

In terminal type...

sudo gedit /etc/apt/sources.list

Add these lines in the bottom of the window that pops up....

deb [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) jaunty main

Save then close.

In terminal type this...

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 1781bd45c4c3275a34bb6aec6e871c4a881574de

Update sources...Type this in terminal...

sudo aptitude update

And add themes, Type this in terminal...

sudo aptitude install zgegblog-themes

----------------------------------------------------------------
Got a new drive and it doesn't have the right partitions on it and UBUNTU won't install?
Get Puppy linux and run it as a live CD in a tower the drive is hooked up to.
mount the drive and run the partitioner to fix it.

I have a 40 Gig drive partitioned as follows.

/dev/sda1    ext3   (mount point) /     35.93 GB   (flags) boot

/dev/sda2  extended (mount point) none  1.34 GB    (flags) none

/dev/sda5 linux-swap(mount point) none  1.34 GB    (flags) none

If your drive is currently working I HIGHLY suggest you write your partitions down!!!! Saves you a ton of reading if you pooch your drive at some point!
-------------------------------------------------------------------------

Anyway I hope this helps someone, and saves you from some stumbling around in the dark.
Thanks again to anyone who thinks they may have written part or parts of this.

Peter

---

### Post by Hagar Delest on 2009-09-26
Does it help: [[Troubleshooting] Spell check in OOo 3.x](http://user.services.openoffice.org/en/forum/viewtopic.php?f=74&t=16512)?

---

### Post by pythonscript on 2009-09-26
> **Hagar de l'Est said:**
> Does it help: [[Troubleshooting] Spell check in OOo 3.x]("http://user.services.openoffice.org/en/forum/viewtopic.php?f=74&t=16512")?

Ok, so I downloaded the Spanish dictionary (not the mexico and/or venezuela one, just the plain spanish one) and I go under Tools -> Extensions Manager and select add. However, when I select the es_ES.oxt file, I get this error message:

[IMG]http://ubuntuforums.org/home/aaronkirkman/Desktop/Screenshot.png[/IMG][IMG]http://img200.imageshack.us/img200/9391/screenshoteib.png[/IMG]

Any ideas?

---

### Post by jmszr on 2009-09-26
pythonscript,

Try:```
sudo apt-get install openoffice.org-java-common
```

That will allow the .oxt to install.

---

### Post by Hagar Delest on 2009-09-27
If the java install doesn't work, try the Sun version: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by pythonscript on 2009-10-18
Spanish spell check in open office started working for me after I installed one of the dictionaries off their site, even though it only installed after several reboots. However, I ended up installing Office 2003 in wine and using that, because the spanish spell check in OO is relatively weak, to say the least. Thanks for all the help!

---

