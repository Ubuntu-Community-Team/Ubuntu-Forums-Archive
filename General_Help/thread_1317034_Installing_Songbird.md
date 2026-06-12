---
title: "Installing Songbird"
date: 2009-11-06
forum: General Help
---

### Post by Butterknife on 2009-11-06
I'm trying to install Songbird and have followed the instructions outlined here - [http://www.cyberciti.biz/faq/install-tarballs/](http://www.cyberciti.biz/faq/install-tarballs/) but this is what I'm getting:

```
ana@Cortana:~$ cd /home/ana/Desktop
ana@Cortana:~/Desktop$ tar zxf Songbird_1.2.0-1146_linux-i686.tar.gz
ana@Cortana:~/Desktop$ cd Songbird
ana@Cortana:~/Desktop/Songbird$ ./configure
bash: ./configure: No such file or directory
ana@Cortana:~/Desktop/Songbird$ make
make: *** No targets specified and no makefile found.  Stop.
ana@Cortana:~/Desktop/Songbird$ 

```

What am I doing wrong?

---

### Post by aysiu on 2009-11-06
Why don't you go to GetDeb, download the appropriate .deb file, and then double-click it?
[http://www.getdeb.net/app/Songbird](http://www.getdeb.net/app/Songbird)

More details here:
[https://help.ubuntu.com/community/Songbird](https://help.ubuntu.com/community/Songbird)

P.S. ./configure doesn't work because Songbird's .tar.gz is a compressed file with a precompiled binary inside. It is not source code to be compiled.

---

### Post by Butterknife on 2009-11-06
Thank you for the tip, I wasn't aware of that website. It won't load at the moment for whatever reason, but once it does, I'll make full use of it.
Thanks again!

---

### Post by scouser73 on 2009-11-06
You'll need to remove **libvisual-0.4-plugins** from Synaptic Package Manager for Songbird to start, the reason being is that there is a conflict with Songbird and libvisual-0.4-plugins which has been well documented un the Songbird forum: [[COLOR="Red"]**Songbird - Libvisual Plugin problems**[/COLOR]]("http://getsatisfaction.com/songbird/topics/songbird_wont_open_in_ubuntu_for_me")

---

### Post by gdonwallace on 2009-11-06
I am running Songbird currently on Koala.  

I downloaded from their website, unpacked the tar-ball that was saved to my system.  To get it to run all I had to type was ./songbird  All worked perfectly.  I had to manually create the shortcut on my panel, but other than that no problems.

---

### Post by northwestuntu on 2009-11-06
is there a repositories for songbird? i know they released a beta 1.4.

---

### Post by scouser73 on 2009-11-06
There is a PPA for Songbird, which is a daily build.  You will need to open up **Software Sources** click **Third Party** tab and add the following two lines.

**> deb [http://ppa.launchpad.net/songbird-daily/ppa/ubuntu](http://ppa.launchpad.net/songbird-daily/ppa/ubuntu) jaunty main**

**> deb-src [http://ppa.launchpad.net/songbird-daily/ppa/ubuntu](http://ppa.launchpad.net/songbird-daily/ppa/ubuntu) jaunty main**

Once you have added them to the **Third Party** tab, click **Close**, then click **Reload**.  At this point you may encounter an error, don't worry as this is normal.  Once completely out of Software Sources go to **Terminal** and enter this command:

**> sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 5719E347**

Then enter this command in **Terminal**:

**> sudo apt-get update**

Now go to **Synaptic Package Manager** and click **Mark All Upgrades**, then click **Apply**

You will then find Songbird in the **Sound & Video** sub-menu.

---

### Post by northwestuntu on 2009-11-08
thanks

---

### Post by iBurger on 2010-01-02
As of now (Jan 2010), I had to manually remove the following libs from my install directory, eg. /opt/Songbird

"Remove all files from the Songbird/lib directory that start with libgst:
```

libgstaudio-0.10.so
libgstinterfaces-0.10.so
libgstrtp-0.10.so
libgstbase-0.10.so
libgstnet-0.10.so
libgstrtsp-0.10.so
libgstcdda-0.10.so
libgstnetbuffer-0.10.so
libgstsdp-0.10.so
libgstcontroller-0.10.so
libgstpbutils-0.10.so
libgsttag-0.10.so
libgstdataprotocol-0.10.so
libgstreamer-0.10.so
libgstvideo-0.10.so
libgstfft-0.10.so
libgstriff-0.10.so" 
```

Was mentioned *[here]("http://getsatisfaction.com/songbird/topics/songbird_fails_to_start_on_fedora_11_with_undefined_symbol_in_libgstdeinterlace_so")* by **chokeumut**.

---

### Post by jofwooster on 2010-10-22
To get it to work for me (Ubuntu 10.04), I went here:

[http://developer.songbirdnest.com/builds/trunk/latest/](http://developer.songbirdnest.com/builds/trunk/latest/)

(Listed in the "Solved" Thread about Songbird)

1. Downloaded the "Songbird_1.10.0a-1859_linux-i686.tar.gz" file
2. Extracted to Desktop
3. Double click on the "songbird-bin" file

After it installs, you can delete the extracted folder form your desktop!

...so glad I wiped Vista from my Toshiba! :guitar:

---

### Post by The Bushman on 2010-10-26
Had the same problem then I saw this video on you tube. [http://www.youtube.com/watch?v=1t2Q_MXSzDY](http://www.youtube.com/watch?v=1t2Q_MXSzDY) solved the problem.
Also before I did the above I un-installed songbird completely using synaptics. Restarted. Then did what the video suggests. Worked like magic. Am using maverick.:P

---

