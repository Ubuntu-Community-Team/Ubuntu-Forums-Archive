---
title: "Openoffice 3 for hardy 8.04"
date: 2009-09-13
forum: General Help
---

### Post by michael37 on 2009-09-13
[Openoffice ppa]("https://launchpad.net/~openoffice-pkgs/+archive/ppa") used to provide openoffice 3 builds for Hardy.  The packages worked fairly well for me.

Very recently, they removed all builds except for Jaunty.  Is there any place where builds for Hardy is located?  I needed to reinstall and am now stuck with well outdated version 2.4...

---

### Post by running_rabbit07 on 2009-09-13
Have you tried this [site]("http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04")?

---

### Post by michael37 on 2009-09-13
More specifically, the site used to have lpia builds, and that's what I am looking for.   Yes, one can use i386 on lpia, but since I already had lpia working, I'd rather have those.

---

### Post by dppowell on 2009-10-01
> **michael37 said:**
> Very recently, they removed all builds except for Jaunty.  Is there any place where builds for Hardy is located?  I needed to reinstall and am now stuck with well outdated version 2.4...

Just made the same unpleasant discovery and need to upgrade OO.org so I can use a particular extension.  I guess maybe not everyone is on board with the whole "supported for 3 years" thing.  Meh.

---

### Post by michael37 on 2009-10-01
> **dppowell said:**
> Just made the same unpleasant discovery and need to upgrade OO.org so I can use a particular extension.  I guess maybe not everyone is on board with the whole "supported for 3 years" thing.  Meh.

If you really need OO 3.1, you can (theoretically) go to [http://download.openoffice.org/other.html#en-US](http://download.openoffice.org/other.html#en-US) and then download a Linux 32-bit DEB or Linux 64-bit DEB from there... However, it's a very generic build and I would prefer a build that is properly designed for my environment (and maintained via standard upgrade service).

For now, it looks like we'll be waiting till openoffice-pkg maintainer has more time.

---

### Post by wilee-nilee on 2009-10-01
About 5 days ago I used Ubuntu Tweak to install 3 on a friends computer, I think though that it is the scribblers ppa, Try this. [http://download.openoffice.org/other.html](http://download.openoffice.org/other.html)

---

### Post by scouser73 on 2009-10-02
Firstly, go to the OpenOffice website: [COLOR="Red"]**[http://download.openoffice.org/other.html](http://download.openoffice.org/other.html)**[/COLOR] and download the **Linux .deb** file.

Once you have done that, extract the .deb file, **OOo_3.1.1_LinuxIntel_install_en-US_deb.tar.gz** then you'll see a file called **OOO310_m19_native_packed-1_en-US.9420**

You can remove the existing version of OpenOffice if you wish with this command: **sudo apt-get remove openoffice*.***

Copy and paste **OOO310_m19_native_packed-1_en-US.9420** onto the desktop then open Terminal and paste this command: **sudo dpkg -i ~/Desktop/OOO310_m19_native_packed-1_en-US.9420/DEBS/*.deb**

Then paste this command: **sudo dpkg -i ~/Desktop/OOO310_m19_native_packed-1_en-US.9420/DEBS/desktop-integration/openoffice.org3.1-debian-menus_3.1-9420_all.deb**

Once you've done that you'll find OpenOffice 3.1.1 in Office.

---

### Post by japhyr on 2009-10-07
I tried to follow the directions in the last post.  When I unpack the tar file I see a directory called "OOO310_m19_native_packed-1_en-US.9420", but I can't find any file by that name.  I can't sudo dpkg this because it is a directory.

Where do I find the file to use dpkg on?

---

### Post by japhyr on 2009-10-07
I figured it out, thanks to a post [here]("http://ubuntuforums.org/showthread.php?t=1162315&highlight=dpkg-split+error+reading+is+a+directory").  I cd'd into the OOO310_m19... directory on the desktop, and then ran
```
sudo dpkg --install *.deb
```
This worked, and then I was able to follow the last step to install the shortcuts.

---

### Post by dppowell on 2009-10-10
Thanks for the new replies, everyone.  I found another way to handle the job I needed to do, but the information remains useful.

---

