---
title: "synaptic: what is it?"
date: 2006-01-28
forum: General Help
---

### Post by rjcoolpix880 on 2006-01-28
I just used synaptic to install amarok and was curious about it. my questions are
1.what is it? (other than a program used to d/l and install more programs)

2. why did i add the following line to it to get more?
deb [http://kubuntu.org/packages/amarok-1.3.8](http://kubuntu.org/packages/amarok-1.3.8) breezy main

im trying to understand what im doing. so i can use linux better.

---

### Post by Irony on 2006-01-28
Each linux distro needs to have programs compiled from source to binary, you download these pre-compiled programs via synaptic (or apt-get in terminal) from repositories.

Some of these repositories are official ones for things like kernel updates and security updates and are thus well tested. Other repositories are not official but you can get things like windows codecs (or you used to be able to before copyright issues).

Some programs like Blender you can just download from the Blender sight and unzip (or untar) and they work straight off. Others you have to compile from source and they can be a pain.

Repositories are where you download precompiled programs. The line you added to your sources.list in /etc/apt folder is presumably a repository for KDE amarok packages.

---

### Post by psomas on 2006-01-28
1)i can't understand what you mean...
synaptic is exactly what you say...
it downloads and installs deb packages for you
of course you can do the same thing using the command apt-get in command mode...
synaptic can also tell you which libraries,or any other files a program(you are going to install) needs in order to run...
2)synaptic downloads these deb packages from "places" on the net that contain such packages...these "places" are called repositories...
so you added a repository that contained amarok...
synaptic isn't the only way to download and install new programms...
you can donwload a deb package(i.e from a site) yourself and install it using the dpkg command...
or even you can download only the source and compile the program yourself... 
see this site for more information on installing software: [http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)
i had the same questions and that site helped me a lot...
and check this about repositories: 
[http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)
i think that ubuntuforums have a special category about repositories...
EDIT: IRONY,i saw your post after posting mine...

---

### Post by Irony on 2006-01-28
I think rjcoolpix880 probably didn't know what repositories are. When I first started Ubuntu I was puzzled as to how synaptic knew where to get Blender from - how did it know Blender was at the Blender site.

I realised later that it didn't get it from the Blender site but from repositories. Blender for example is still at 2.36 in the repositories whereas the latest version is 2.40 - thus I download the file by directly going to the Blender site.

A self contained program like Blender is already pre-compiled at the Blender site so works on pretty much any platform. Whereas something like OpenOffice (which may not be the latest version) is best downloaded from the repositories because it depends on other programs (libraries and such).

> synaptic can also tell you which libraries,or any other files a program(you are going to install) needs in order to run...

That's a good point, when I updated to Breezy, Totem wouldn't play some stuff so I uninstalled one of the gstreamer files and that sorted the problem.

---

### Post by Irony on 2006-01-28
Just noticed Blender is at 2.37a in the repositories!!

---

### Post by Irony on 2006-01-28
Come to think of it, I'm surprised Microsoft hasn't come up with a similar system whereby vendors sell their stuff via a central Microsoft repository - in this case the repository would simply redirect programs from the vendors; from the users viewpoint it would look like its all coming from one place.

The linux repository system is much better than the Windows buy a cd and wait for it to be delivered system.

---

### Post by thespazzz on 2006-01-28
I agree one of the things I like about Linux is that I don't usualy have to "hunt" for a program to do somethign that I need.  I just type in... well AIM and I get KOPETE, and GAIM and a few others.  FTP gives me a bunch of results.  I type in Flight Simulator and I get Flight Gear.

Click.. Download, Installed.

A lot less of a pain then windows can be

---

### Post by psomas on 2006-01-28
[QUOTE=thespazzz]I agree one of the things I like about Linux is that I don't usualy have to "hunt" for a program to do somethign that I need.  I just type in... well AIM and I get KOPETE, and GAIM and a few others.  FTP gives me a bunch of results.  I type in Flight Simulator and I get Flight Gear.

Click.. Download, Installed.

A lot less of a pain then windows can be[/QUOTE]
but if you don't find a deb package that you want, you must download source, and then compile it....... :-#  and things get more complicated

---

### Post by alinuxfan on 2006-01-28
still

./configure 
make
make install

isn't really all taht hard once you've done it a few times
i'll admit i was scared by it at first 
*gulp* command line *gulp*
now it's just another thing and i just started actively using linux a couple months ago (before it was just my IPMASQ machine that i never touched)

---

