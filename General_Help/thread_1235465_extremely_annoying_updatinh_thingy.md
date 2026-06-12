---
title: "extremely annoying updatinh thingy"
date: 2009-08-09
forum: General Help
---

### Post by phr33k-dc on 2009-08-09
can someone fix or at least interpret the window for me?

---

### Post by phr33k-dc on 2009-08-09
404 not found?

---

### Post by stwschool on 2009-08-09
Well I'd say that the update routine is looking for the file at the URL specified and can't find it. Possible reasons include no internet connection or server problems. As you can post here, I'll assume the latter rather than the former. I tend to skip the chromium updates (by unticking the box) and do it once every 3-4 days on my slower home connection anyway as 17MB every day is a bit annoying.

---

### Post by stwschool on 2009-08-09
I stuck [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/pool/main/c/chromium-browser/chromium-browser_3.0.198.0-svn20090806r22605-0ubuntu1~ucd1~jaunty_amd64.deb](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/pool/main/c/chromium-browser/chromium-browser_3.0.198.0-svn20090806r22605-0ubuntu1~ucd1~jaunty_amd64.deb) in my browser and the file's not on the server, so maybe a problem there (unless I spelled that wrong)

---

### Post by phr33k-dc on 2009-08-09
haha ye maby, but what about the other issue in the screenshot?

---

### Post by 3rdalbum on 2009-08-09
The screenshot only shows one problem, with two files.

I notice that they are "chromium-daily" and "mozilla-daily" repositories, meaning that they build a new version of Chromium/Firefox every day from the latest, up-to-the-minute source code. Your package information is probably outdated and looking for the Chromium and Firefox from yesterday, which of course is gone.

Hit the Check button in Update Manager, or Reload in Synaptic, to get the latest package information.

---

### Post by stwschool on 2009-08-09
3rdalbum's right.. bugger why didn't I think of that! Yep, check then update as he said.

---

### Post by phr33k-dc on 2009-08-09
cheers lads great help.... one more question. if i was to do another install of ubuntu, ho would i save my sources and authentication keys so as not to go and look for them all over again? save them on to a usb for example?

---

### Post by stwschool on 2009-08-09
There's a file for your sources at /etc/apt/sources.list which will contain all your sources. Simply backup to memory stick and restore to the other computer when you're ready. In fact you can even get a list of installed apps with an auto-installing script to replicate that on another machine but I haven't got the command to hand (I'm sure others who are more organised than me will do).

Authentication keys, I can't recall exactly but it may be wise to just copy the entire /etc/apt directory and restore that, as I see some files referencing keys there, so that ought to do a job.

---

### Post by phr33k-dc on 2009-08-09
thanks for that . but there is i think some reference to keys with a file called 'trusted' or somethin, but its encrypted. any ideas where i can get the packages list and installing script? cheers

---

### Post by stwschool on 2009-08-09
Ok packages.. Creating the backup. In the terminal you'll want to do this (there's probably a GUI way but this way's a piece of cake).

sudo dpkg --get-selections > ~/Desktop/mypackages

What this does is run dpkg which deals with all your packages, and --get-selections gets a list of what's selected. > pipes the output to a file somewhere and the bit afterwards is where it's going (~ means /home/yourname so /home/yourname/Desktop/mypackages).

This can be used to install your packages via synaptic (File -> Read Markings as I recall).


Keys I'm looking in /etc/apt and the following files are in that folder on my machine.

apt.conf.d   sources.list    sources.list.save  trusted.gpg
secring.gpg  sources.list.d  trustdb.gpg        trusted.gpg~

I'll bet money that copying that lot to a memory stick and restoring it all to the same location will restore your sources list and your keys.

Good luck :)

PS when copying files back in you might need to be root (the boss) in which case you'll need to Alt-F2 and type 'gksudo nautilus' to use Nautilus file manager as root).

---

### Post by phr33k-dc on 2009-08-09
thanks for that. i am looking how to do this as i want to do an install of the alternate cd and encrypt me hdd. what would you reccommend as the best password? like random digits or /.a'cdmq';e;.'/ something like that?

---

### Post by stwschool on 2009-08-09
Passwords.. well letmein would be crap. letmein2827 is better but still crap. #$l3tm31n9828827hhHG7^^4$) is better. Basically, in terms of security go non-dictionary, mix upper and lower case letters with numbers and symbols, and make it long. Just don't make it so long that the only way to remember it is to write it down, as at that point security goes right out the window.

---

### Post by phr33k-dc on 2009-08-09
ha ye i know wat you mean. also how do i copy those files from etc/apt/ to my usb as it says permission denied. also putting them back in an install?

---

### Post by martinbaselier on 2009-08-09
use
sudo cp

or if you prefer a gui

sudo nautilus
close it after copying the files, cause you will have root access and any file you create will make root the owner of it. 

use with care

---

### Post by phr33k-dc on 2009-08-09
that doenst work (sudo nautilus) as in it works- window pops open and i drag it to my usb icon but it still says permission denied. can you tell me the commend for doing sudo cp? also see my screen shot of my terminal when i type sudo nautilus...

---

### Post by phr33k-dc on 2009-08-09
after...

---

### Post by stwschool on 2009-08-10
Shouldn't be saying permission denied, sudo makes you the boss. Whatever you say goes, and the computer doesn't get a say in that. To be honest I can't honestly say how that's happening. Btw I already told you how to copy the files when I told you alt-f2 -> gksudo nautilus.

---

