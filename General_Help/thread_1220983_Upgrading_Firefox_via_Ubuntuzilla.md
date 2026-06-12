---
title: "Upgrading Firefox via Ubuntuzilla"
date: 2009-07-23
forum: General Help
---

### Post by murphykieran on 2009-07-23
I wanted to upgrade to Firefox 3.5 but heard that it wouldn't be officially supported in Ubuntu till 9.10 comes out.

So I did a search and was able to install it via a utility called Ubuntuzilla.  It installed fine, it's working fine and I'm very happy with it.

However, every so often I get a message bubble from the system tray telling me that 3.5.1 is now available and to read these messages about how to install the upgrade.  When I move the mouse over the message, it just disappears and there's no icon or anything in the system tray that I can click on to run an upgrade or anything.

Does anyone know what I'm supposed to do to perform the upgrade?  I like to keep my webbrowser up to date with the latest upgrades and fixes.

---

### Post by Greenwidth on 2009-07-23
You should be able to by:

Close all running firefox instances.
"gksudo firefox &" from Terminal (without quotes)
In firefox: Help > Check For Updates

---

### Post by murphykieran on 2009-07-23
Thanks for that.  The command line worked, but for some reason the "check for updates" was and still is grey out and can't be clicked on.

---

### Post by Greenwidth on 2009-07-23
Strange, works for me after Ubuntuzilla install..

You could try looking in the forum:
[http://ubuntuforums.org/forumdisplay.php?f=251&order=desc&page=2](http://ubuntuforums.org/forumdisplay.php?f=251&order=desc&page=2)

I would be tempted to just run ubuntuzilla.py again, worth checking though.

---

### Post by murphykieran on 2009-07-23
Once I know I can upgrade it via the command line, I'm good.

Thanks for the help.

---

### Post by Johnny B on 2009-07-23
why use Ubuntuzilla?
i just installed it with
# sudo apt-get install firefox-3.5

---

### Post by murphykieran on 2009-07-23
I tried originally updating to 3.5 via Synaptic but it didn't actually do anything.  When I ran Firefox it was still 3.0.10 or whatever version I was using perviously, so when I did a Google search for installing 3.5 in Ubuntu 9.04, Ubuntuzilla was what I came across.

---

### Post by Greenwidth on 2009-07-23
When you install via Synaptic you have to change the launcher from
"firefox" to "firefox-3.5"
And in System > Preferences > Preferred Applications

---

### Post by nanotube on 2009-07-24
> **murphykieran said:**
> I wanted to upgrade to Firefox 3.5 but heard that it wouldn't be officially supported in Ubuntu till 9.10 comes out.

So I did a search and was able to install it via a utility called Ubuntuzilla.  It installed fine, it's working fine and I'm very happy with it.

However, every so often I get a message bubble from the system tray telling me that 3.5.1 is now available and to read these messages about how to install the upgrade.  When I move the mouse over the message, it just disappears and there's no icon or anything in the system tray that I can click on to run an upgrade or anything.

Does anyone know what I'm supposed to do to perform the upgrade?  I like to keep my webbrowser up to date with the latest upgrades and fixes.

there are upgrade instructions on the ubuntuzilla website - in short quit all firefox windows, then run firefox with gksudo, check for updates should be enabled then.

alternatively, just use ubuntuzilla install process again, to install the latest version.

---

### Post by Jo21 on 2009-07-25
> **nanotube said:**
> there are upgrade instructions on the ubuntuzilla website - in short quit all firefox windows, then run firefox with gksudo, check for updates should be enabled then.

alternatively, just use ubuntuzilla install process again, to install the latest version.

ubuntuzilla it's not working for me today i dont' know... it worked before but now i formated.

PASV ... couldn't connect to 204.152.184.196 port 15495: Connection refused
wget -c --tries=5 --read-timeout=20 --waitretry=10 [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5.1/linux-i686/en-US/firefox-3.5.1.tar.bz2.asc](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5.1/linux-i686/en-US/firefox-3.5.1.tar.bz2.asc)
Previous command has failed to complete successfully. Exiting.

---

### Post by nanotube on 2009-07-26
hi 
grab the latest version (4.6.3), try again.

---

### Post by dbslayer on 2009-07-28
> **Greenwidth said:**
> When you install via Synaptic you have to change the launcher from
"firefox" to "firefox-3.5"
And in System > Preferences > Preferred Applications

I did the line command Synaptic install (sudo apt-get install firefox-3.5) but could not change to firefox-3.5 under Preferred Applications. The only drop down was Firefox or custom.

I got around this by doing the following line commands:
 cd /usr/bin 
 sudo su root
 rm firefox
 ln -s firefox-3.5 firefox
 
I am more experienced with line commands, but not sure this was a good idea. But, it works with no change to Preferred Applications.

---

