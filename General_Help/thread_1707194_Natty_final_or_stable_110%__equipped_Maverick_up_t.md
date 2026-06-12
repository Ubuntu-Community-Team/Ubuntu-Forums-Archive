---
title: "Natty final or stable 110%  equipped Maverick up to date"
date: 2011-03-15
forum: General Help
---

### Post by gdiloren on 2011-03-15
I just finished installing a new printer, fax and scanner capabilities to Maverick. I can print from pc now and my fax modem is now recognized by Linux. Emesene is working 100% like Windows Messenger and Skype is fine too. Everything runs well, the booting time is fast and much better than Vista six months ago. Security is supposed to be better than Vista with Ubuntu. That may be because it is more "geeky" to the rest of the common mortals. You need to know how to use the terminal although Synaptic Manager and Ubuntu Software Manager should make Ubuntu installs easier and understandable. I've spent hours if not nights to get the worth of a Windows 7  most expensive edition but it's better, it's Linux. I'm happy to have suffered a bit, now I know!
   All this, to tell I want to get always the most up-to-date version of Ubuntu (stable version) but I don't want to start from scratch every six months or so. It's unacceptable. I want to upgrade on April 28th from Update Manager without problems from 10.10 to 11.04 keeping my settings, packages and programs. Is this possible. If not, why not study a 11.04 setup where you can facultatively choose something like in Windows 95/98 CD-ROM dial-up networking, or fax etc... so we don't have to get geeky and search the internet to solve our problems. Fortunately, there is this Forum, but often you have to READ BETWEEN THE LINES because documentation (Wiki etc..) is old or outdated or the threads are not precise as some installations are complicated and difficult to remember and put in a thread. So I may have some packages that are not necessary to maintain but I have plenty of space (320 GB HD). 
   Now the question is: Will I risk all that work on Maverick since October to get the newest upgrade or will I stay with Maverick until April 2012?:KS:KS:)

---

### Post by Rasa1111 on 2011-03-15
Probably only a question you can answer. lol

I however, am going to be staying with 10.10 as long as possible. 

It's the most perfect OS Ive ever seen/used.

and 11.04 just does not seem worth it. 
Can't believe im saying that about something 'Ubuntu"..
but hey..

---

### Post by gdiloren on 2011-03-15
I agree and if it's supported until next year (April 2012) well there is no trouble, we'll get updates!:popcorn:

---

### Post by oldfred on 2011-03-15
As Rasa1111 said only you know.

I used to upgrade in place, but often had issues. So with 9.10 I went with a new install (and new hard drive) and  found it housecleaned a lot of old stuff out. So now I do clean installs of every new version, but always install to a new partition. I have at least 3 partitions that I rotate - Old, current & beta/RC/new version.

Doing a lot of installs and installing the same system to my portable, I found a few things to suggest.

I back up a list of all installed applications to make it easy to reinstall. (but you may want to edit to remove some old versions like OpenOffice being changed to LibreOffice.)

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
List Packages
dpkg --get-selections > ubuntu-files
Reinstall
sudo dpkg --set-selections < ubuntu-files && sudo apt-get dselect-upgrade

I also backup any system setting file in /etc (or all of /etc) that I have manually edited, but do not automatically reinstall unless the new version also needs the same settings. Sometimes old settings create more problems.

I only copy back parts of /home but not necessarily all.

If you have lots of drive space another 20GB for another / gives you a chance to test a new version without fully committing to it.

---

### Post by dnguyen1963 on 2011-03-15
My workhorse computer still runs 8.04 LTS without a hiccup so there is no reason for you not to keep your computer as is until 2012.

---

