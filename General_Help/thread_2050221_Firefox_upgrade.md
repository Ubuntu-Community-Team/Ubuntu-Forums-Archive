---
title: "Firefox upgrade"
date: 2012-08-30
forum: General Help
---

### Post by seubill on 2012-08-30
One of my boxes is running Ubuntu 8.10 Intrepid with Firefox 3.0.19.

I have downloaded the latest version of Firefox and need help getting the package installed.

It's saved to my desktop as "firefox-15.0.tar.bz2".  When I try to open the package it goes to Archive manager and shows a long list of files. I don't know what to do.



Thank you very much for any help.

---

### Post by Irony on 2012-08-30
Simply right click on it and click extract - then navigate to the firefox binary in the folder and double click it and firefox should start up.

This assumes that 8.10 has the necessary dependencies for firefox 15 or else nothing will happen when you double click firefox.

---

### Post by ranger1021994 on 2012-08-30
Check the contents of the archive,you might have downloaded source code.

---

### Post by seubill on 2012-08-30
Not sure what you mean by Firefox binary.  I extracted the downloaded package on the desktop and now there is a folder that says Firefox. Double clicking that opens a file with a lot of other stuff.

Am I doing something wrong, or perhaps need to get dependencies as you mentioned?

---

### Post by GreatDanton on 2012-08-30
I just tested it (but I am using 12.10). When you extract the files you will get one folder called firefox. Inside that folder find firefox-bin. Right click on it and click on properties. After that tick the box: allow executing as program. After that when you double click on firefox-bin you should be able to use firefox.

Since you use Ubuntu 8.10 this may be different. Also keep in mind that Ubuntu 8.10 it's not supported anymore, therefore you will not receive any security updates, so make a fresh install as soon as possible (12.04).

Regards.

Edit: I made the same with firefox file (not firefox-bin). It also open firefox, so now the question is what is the difference?

---

### Post by Karandras on 2012-11-12
> **GreatDanton said:**
> I just tested it (but I am using 12.10). When you extract the files you will get one folder called firefox. Inside that folder find firefox-bin. Right click on it and click on properties. After that tick the box: allow executing as program. After that when you double click on firefox-bin you should be able to use firefox.

Since you use Ubuntu 8.10 this may be different. Also keep in mind that Ubuntu 8.10 it's not supported anymore, therefore you will not receive any security updates, so make a fresh install as soon as possible (12.04).

Regards.

Edit: I made the same with firefox file (not firefox-bin). It also open firefox, so now the question is what is the difference?

I am having a similar problem in Xubuntu 12.04. I use the latest version of firefox for regular browsing then I have a folder in my home directory that has firefox 10 in it so if there is a video I like on youtube, i can just cache it up then copy it out of firefox 10's cache folder (since i cant find the cache folder for firefox 16, and i find it easier then using a plug-in which i have done but always seemed to be more work for me). Anyways, when I double click the firefox icon or firefox-bin icon nothing happens, and I have set them to be run as an executable file. Is there a program I'm missing or what program should I direct the files to open with? 

Double clicking the firefox 10 icon use to work before when I upgraded my OS from Ubuntu 10.04 to Xubuntu 12.04. Now that I recently did a fresh install of Xubuntu 12.04 64bit, firefox 10 will not open for me and I cant find any answers to my question when I google it.

My last resort would be to do a fresh install of Ubuntu 10.04, see if firefox 10 works there. If it does work, then install Xubuntu 12.04 and write myself a huge note to not mess with my OS again.

---

