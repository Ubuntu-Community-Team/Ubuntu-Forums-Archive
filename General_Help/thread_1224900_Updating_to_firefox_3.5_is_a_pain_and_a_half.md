---
title: "Updating to firefox 3.5 is a pain and a half"
date: 2009-07-27
forum: General Help
---

### Post by Yellowbelly on 2009-07-27
This is the reason why I REALLY ABHORE linux, for times like these. Basically, FF 3.0 sucks. Drains memory cpu, and looks MASSIVE on my 10" netbook screen. I want 3.5. Bad. So I downloaded it and installed it just like one tutorial said. But the problem is that it was saved to my home folder and I have to go in there and click on it to open it every time instead of going through menus or gnomedo. Well that's not very cool. I realize its installed side by side with 3.0. So I try changing preferred applications. No go. Then I go to uninstall 3.0 so it can't ever come back, so the defualt browser would have to be 3.5. Somehow, 3.0 still exists. I purged the sucker and it still exists. Awesome. It's a disease that won't go away and update manager is bugging me to update 3.0 when I HAVE 3.5. Then I go to synaptic and install it that way, and guess what, 3.0 is still there and 3.5 is no where to be found. This is the point where I have no other options but to freshen my ideas in my head...with a bullet. 

The first install of 3.5 was somehwat of a pain. I looked up ubuntuzilla and that looked overly complicated for one measely program.

Holy Hell this is ridiculous.

Thank you.

---

### Post by QIII on 2009-07-27
3.5 (currently branded Shiretoko until Karmic comes out) is available in the repos.

---

### Post by gunksta on 2009-07-27
Unfortunately, the FF3.5 in the repos drags in a bunch of annoying dependencies for anyone not wanting the ubuntu-desktop. FF3.0 installs cleanly (minimal requirements) but 3.5 drags in Add/Remove and multiple gnome dependencies. I'm not installing nearly 90 MB of stuff just to get a web-browser.

---

### Post by michaelzap on 2009-07-27
The symbolic links that launch most Ubuntu applications are in /usr/bin. So if you want the link in there called "firefox" to point to "firefox-3.5", all you need to do is to delete the original and create a new one. For example:
```

sudo rm /usr/bin/firefox
sudo ln -s /home/username/firefox/firefox-3.5 /usr/bin/firefox
```
That will delete the existing firefox symbolic link and create a new one that points to a "firefox-3.5" executable in your home directory (change the path and file name as necessary). After that, any program that runs "firefox" will be running that file.

I just installed firefox-3.5 from the Jaunty repos, so all I needed to do is delete the existing "firefox" link and create a new one to the "firefox-3.5" link that's already in /usr/bin:
```
cd /usr/bin
sudo rm firefox
sudo ln -s firefox-3.5 firefox
```

---

### Post by QIII on 2009-07-27
> **gunksta said:**
> Unfortunately, the FF3.5 in the repos drags in a bunch of annoying dependencies for anyone not wanting the ubuntu-desktop. FF3.0 installs cleanly (minimal requirements) but 3.5 drags in Add/Remove and multiple gnome dependencies. I'm not installing nearly 90 MB of stuff just to get a web-browser.

If you don't want the dependencies, install from the terminal.  Don't install gnome-support.  Remove xulrunner if you want.  You can get a clean install of just FF3.5.

---

### Post by aysiu on 2009-07-27
Just forget about all that complicated stuff and do this:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

One command pasted into the terminal with your mouse and it's all done.

---

### Post by QIII on 2009-07-28
Assuming you download the .tar first. I'm not sure how that is much easier than

```
sudo apt-get install firefox-3.5 && sudo apt-get install firefox-3.5-gnome-support

```

especially when getting rid of it is as simple as using remove...

---

### Post by nanotube on 2009-07-28
> **Yellowbelly said:**
> 
The first install of 3.5 was somehwat of a pain. I looked up ubuntuzilla and that looked overly complicated for one measely program.


just install the .deb and then run ubuntuzilla... if you'd tell me what you think could be improved, to make it friendlier, i'll certainly take your feedback into account.

---

### Post by nanotube on 2009-07-28
> **aysiu said:**
> Just forget about all that complicated stuff and do this:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

One command pasted into the terminal with your mouse and it's all done.

hey aysiu, how goes it? :) looks like with the release of ff3.5, there's once more a lot of interest in installing the mozilla build, eh? :)

---

### Post by aysiu on 2009-07-28
> **nanotube said:**
> hey aysiu, how goes it? :) looks like with the release of ff3.5, there's once more a lot of interest in installing the mozilla build, eh? :)
It goes well. Glad to see you're still carrying on with UbuntuZilla. It seems to have become quite robust.

---

### Post by nu2this on 2009-07-28
I'm curious to know can one do this:
1.retain the Ubuntu version of Fx then place it's icon in another folder
2. install the Mozilla version(place its icon on Desktop) & use it without messing up the Ubuntu Fx & the Gnome dependencies that come with it? As well as vice versa?

---

### Post by dbslayer on 2009-07-28
This worked for me from Applications Accessories Terminal window:

sudo apt-get install firefox-3.5
sudo apt-get install firefox-3.5-gnome-support
cd /usr/bin
sudo su root
rm firefox
ln -s firefox-3.5 firefox
exit

---

### Post by colin.p on 2009-07-28
> **aysiu said:**
> Just forget about all that complicated stuff and do this:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

One command pasted into the terminal with your mouse and it's all done.

I have to add my +1 to this as I followed the directions and 3.5 installed perfectly. I was able to update to 3.5.1 and even when 3.0.11 wanted to update to 3.0.12 it did and didn't affect 3.5.1 at all.
Very easy, alot easier than most of the ways that people were doing the upgrade. But I suppose that in the end, no matter how you do it, if it works....

Colin

---

### Post by gunksta on 2009-07-28
> **QIII said:**
> If you don't want the dependencies, install from the terminal.  Don't install gnome-support.  Remove xulrunner if you want.  You can get a clean install of just FF3.5.

I nearly always install via the command line and in this case it's not as clean as I would like it.  When I try to install 3.5, (apt-get install firefox-3.5) I am told that I will need to install 130 MB of stuff! My repos are updated and do include the final version of 3.5 as currently published in the Ubuntu repositories. I generally prefer to keep my systems "clean" and I tend to resist installing stuff that's not in the repos (unless I compile it myself) but I may look into one of these alternative methods that installs a vanilla firefox from mozilla. 

**EDIT:** the list below lists hard dependencies. I'm not installing anything from recommends.

The following NEW packages will be installed:
 apturl 
docbook-xml firefox-3.5 
firefox-3.5-branding 
gamin 
gksu
gnome-app-install 
gnome-icon-theme 
gnome-keyring 
gnome-mime-data 
gnome-mount
gvfs 
gvfs-backends 
libavahi-glib1 
libbonobo2-0 
libbonobo2-common
libbonoboui2-0 
libbonoboui2-common 
libcairo-perl 
libcanberra0 
libcdio-cdda0
libcdio-paranoia0 
libcroco3 
libgail-common 
libgail18 
libgamin0 
libgcr0
libgksu2-0 
libglib-perl 
libgnome-keyring0 
libgnome2-0 
libgnome2-canvas-perl
libgnome2-common 
libgnome2-perl 
libgnome2-vfs-perl 
libgnomecanvas2-0
libgnomecanvas2-common 
libgnomeui-0 
libgnomeui-common 
libgnomevfs2-0
libgnomevfs2-common 
libgnomevfs2-extra 
libgp11-0 libgsf-1-114
libgsf-1-common 
libgtk2-perl 
libgtkhtml2-0 
libgtop2-7 
libgtop2-common
libgvfscommon0 
liblaunchpad-integration1 
libpam-gnome-keyring
libpolkit-gnome0 
libproxy0 librsvg2-2 
librsvg2-common 
libscrollkeeper0
libsoup-gnome2.4-1 
libsoup2.4-1 
libtdb1 
libvte-common 
libvte9
policykit-gnome 
python-cairo 
python-gconf 
python-glade2 
python-gst0.10
python-gtk2 
python-gtkhtml2 
python-launchpad-integration 
python-pyorbit
python-sexy 
python-vte 
scrollkeeper 
sgml-data 
software-properties-gtk
synaptic 
ubufox 
xulrunner-1.9.1

On my home system, it's just a mildly annoying waste of space and a few extra menu items I don't want or need. On my work system which is pretty tight for space, it's unacceptable.

---

### Post by Zorael on 2009-07-28
I always install firefox with aptitude's --without-recommends, and at the same time tell it to leave ubufox and pulseaudio the hell alone, which it always seems to want to pull. Dang gnomeys!
```
$ sudo aptitude install --without-recommends -P firefox-*n.n* pulseaudio_ ubufox_
```
Then, if it still seems to want to pull a whole lot of unneccessary stuff, I try to add more (of the listed) packages to be exempted with **packagename_**. If it freaks out and says it can't be done, I'll back off and try another package. Until it's slim enough.

Would love to see a kubufox. :<

edit: Hmm, perhaps I'm mistaken about pulseaudio? Regardless, gksu_, synaptic_ policykit-gnome_; anything gnomey that I *know* isn't quintessential for Firefox to run.

---

### Post by gunksta on 2009-07-28
Thanks Zorael.

It appears that my apt-get-fu is not what it should be. I thought apt-get would only install recommended packages when I explicitly ask it to. I am clearly incorrect.

```
sudo apt-get install --no-install-recommends firefox-3.5
```

will install a perfectly clean FF 3.5 and doesn't come with all of the other cruft. No need to explicitly exempt any packages (at least, none that aren't already there because of FF 3.1)

As for a kubufox, I agree. It would be nice.

---

### Post by speedwell68 on 2009-07-28
All I did was download the current tar.bz file from the Mozilla website, Created a folder below /home/.mozilla called firefox 3.5 and extracted the tar.bz file to it. Then created a desktop and menu launcher manually.  On first launch it found my existing FF 3.0.x profile by itself and prompted me to make it the default browser.  I have left the default FF 3.0.x install in place as Songbird appears to rely on it's dependencies.

---

### Post by moster on 2009-07-28
I usually surf with firefox 3.5, full screen (F11) and autohide taskbar 
Like that it is bearable :)

---

### Post by running_rabbit07 on 2009-07-28
I just started playing with Karmic Alpha 3 and it doesn't have FF3.5 yet either.

---

### Post by deathsshadow77 on 2009-07-28
my problem is that there is no ppa in existence that will install the mozilla branded firefox. Shiretoko has issues simply because it is not called firefox. For instance, Facebook chat refuses to work because of this.

---

### Post by aysiu on 2009-07-28
> **deathsshadow77 said:**
> my problem is that there is no ppa in existence that will install the mozilla branded firefox. Shiretoko has issues simply because it is not called firefox. For instance, Facebook chat refuses to work because of this.
Not a problem if you paste in that one line from the page I linked to... or if you use the UbuntuZilla script.

---

### Post by speedwell68 on 2009-07-28
> **deathsshadow77 said:**
> my problem is that there is no ppa in existence that will install the mozilla branded firefox. Shiretoko has issues simply because it is not called firefox. For instance, Facebook chat refuses to work because of this.

Why bother with the PPA?  Just do what I did, Firefox will happily manage it's own upadates.

> **speedwell68 said:**
> All I did was download the current tar.bz file from the Mozilla website, Created a folder below /home/.mozilla called firefox 3.5 and extracted the tar.bz file to it. Then created a desktop and menu launcher manually.  On first launch it found my existing FF 3.0.x profile by itself and prompted me to make it the default browser.  I have left the default FF 3.0.x install in place as Songbird appears to rely on it's dependencies.

---

### Post by nanotube on 2009-07-29
> **aysiu said:**
> It goes well. Glad to see you're still carrying on with UbuntuZilla. It seems to have become quite robust.

heh, indeed... but at the end of the day, it's nothing more than a bunch of bells and whistles around the basic core which you have in your "one-liner" command. :)

---

### Post by fcuk112 on 2009-07-29
personally i found firefox 3.5 made the browser sometimes go unresponsive (i.e. dimming all the time), that's why i switched back to FF3.0.  anyone else experienced this?

---

### Post by samib on 2009-07-29
Have had constant problems starting up firefox browser and thunderbird email on same computer. Messages saying not shut down resulting in new profile needed.
I still like Thunderbird so gave up on Firefox and installed a simpler browser. 
Now no problem except if i need to do a reinstall then Firefox automatically installed so just have to uninstall it.
Doing this and all my problems have ceased.

---

