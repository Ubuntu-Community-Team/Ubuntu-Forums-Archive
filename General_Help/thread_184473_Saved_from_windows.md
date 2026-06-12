---
title: "Saved from windows"
date: 2006-05-30
forum: General Help
---

### Post by jrd on 2006-05-30
I tried Kubuntu and I love it. No anti virus, anti spyware stuff running all the time.
I am really shocked that linux is this easy. I tried Suse and Xandros but I like Kubuntu the best. I have a few questions though...
I cant play Tactics arena ([www.tacticsarena.com](www.tacticsarena.com)) But I dont know why. I have flash installed and I'm using firefox as a browser. It worked when I tried Suse. Any thoughts?
Also, if someone could post a link about how to install software thats not in the pakage manager or a rpm I would be greatfull.
Well looks like I wont be getting Vista, I've found something more secure and stable (And free!).

---

### Post by oolunchbox on 2006-05-30
welcome to linux! I too am a recent convert and I've loved every day of being windows free.  as far as installing software thats not a rpm or in the package manager:
(K)ubuntu is debian based so instead of rpm files you should be looking for .deb files.

if you find something that is only available in rpm format you can try using alien to convert it to deb (i dont know exactly how just search for a tutorial) or some software lets you compile it from source which is above me right now.

hope that helps.

---

### Post by Randomskk on 2006-05-30
If you have a .tar.gz file to install, the basic procedure goes something like this:
1) (first time only) make sure you have build-essentials:
sudo apt-get install build-essentials

2) unzip the .tar.gz:
tar -xvf filename.tar.gz

3) don't always have to do this, change to newly made directory:
cd directoryname

4) configure the program for installing
./configure

5) compile program
make

6) install program
sudo make install

Then, you should be done, type the program name into a terminal to load it, or check your menus. In KDE, right click a menu, click edit, then the save icon and close to refresh them and show new applications.
Not all programs add a menu entry.

This procedure may be different for some apps, but should work for most .tar.gz programs.
(All commands entered into a terminal window, KDE --> System --> Terminal Program (Konsole)

---

### Post by warp99 on 2006-05-30
[QUOTE=jrd]
I cant play Tactics arena ([www.tacticsarena.com](www.tacticsarena.com)) But I dont know why. I have flash installed and I'm using firefox as a browser. It worked when I tried Suse. Any thoughts?[/QUOTE]

Do you have pop-up windows enabled for that site in Firefox? In Firefox go to Edit > Preferences > Web Features then click on allowed sites and add [www.tacticsarena.com](www.tacticsarena.com) to the list. :cool:

---

### Post by AaronThorpe on 2006-05-30
Hi Everyone!! I've been trying for literally two years to get linux up and running ....Long Story.....And finally got and absolutely love it. However, I'm an extreme n00b. So yea, with this post, how do I download and install .deb files, when I try to save files to /root it says not authorized, and Im not sure on what to do....](*,)

---

### Post by aysiu on 2006-05-30
[QUOTE=AaronThorpe]Hi Everyone!! I've been trying for literally two years to get linux up and running ....Long Story.....And finally got and absolutely love it. However, I'm an extreme n00b. So yea, with this post, how do I download and install .deb files, when I try to save files to /root it says not authorized, and Im not sure on what to do....](*,)[/QUOTE] Read this:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

