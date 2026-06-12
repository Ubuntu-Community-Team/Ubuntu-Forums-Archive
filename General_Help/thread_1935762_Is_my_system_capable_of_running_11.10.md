---
title: "Is my system capable of running 11.10"
date: 2012-03-04
forum: General Help
---

### Post by #1 fisherman on 2012-03-04
Can someone help me find out if my system can run ubuntu 11.10 I have upgraded since 9.04 and now suddenly my performance is slow.I have used ubuntu for a few years now but i am not a bit head by any means.I just upgraded to 11.10 today mostly video playback with vlc and m player are slow and choppy and when they are running my machine all but freezes up.I do have a pretty old machine if i had to do a fresh install of an older version i would.Help would be greatly appreciated.

---

### Post by davidvandoren on 2012-03-04
open your system monitor and tell us how much ram you have.

The cpu speed is not that important, you'll need at least one gigabyte of ram.

And what's your video card?

---

### Post by #1 fisherman on 2012-03-04
it is 496.4 memory and nv05 x86/MMX+/3DNow!+/SSE graphic

---

### Post by davidvandoren on 2012-03-04
> **#1 fisherman said:**
> it is 496.4 memory and nv05 x86/MMX+/3DNow!+/SSE graphic

That's why your system is running slowly.

How much swap is your system currently using?

I am running ubuntu 11.04 right now and it uses 360 MB of ram with only two windows open. 

Once the system starts using swap everything gets really slow.

---

### Post by #1 fisherman on 2012-03-05
65.5 mib (3.4%) of 1.9 Gib

---

### Post by davidvandoren on 2012-03-05
> **#1 fisherman said:**
> 65.5 mib (3.4%) of 1.9 Gib

If that's your swap then that's why your system is getting slow.

You can go to System Preferences and then **Startup Applications **

And remove all programs you don't really need to run at startup.

Blue-tooth 
Update manager etc.

---

### Post by #1 fisherman on 2012-03-05
I know i need to upgrade to a new machine money is tight and i just need to get by for the moment 11.04 worked fine.With 11.10 the internet is a little slow but not to bad for what i need But avi files I have seem to not play good at all now.Possibly I should do a new installof 11.04

---

### Post by davidvandoren on 2012-03-05
> **#1 fisherman said:**
> I know i need to upgrade to a new machine money is tight and i just need to get by for the moment 11.04 worked fine.With 11.10 the internet is a little slow but not to bad for what i need But avi files I have seem to not play good at all now.Possibly I should do a new installof 11.04

No you should install a lighter desktop environment.

Maybe xubuntu 

```
sudo apt-get install xubuntu-desktop
```

Another option to free ram at times might be this.

```
sudo sh -c "sync; echo 3 > /proc/sys/vm/drop_caches
```

You can try this first if it works you could create a launcher on your desktop to execute it when you need it.

---

### Post by #1 fisherman on 2012-03-05
ok this is what i got 

denver@denver-desktop:~$ sudo apt-get install xubuntu-desktop
[sudo] password for denver: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xubuntu-desktop is already the newest version.
The following packages were automatically installed and are no longer required:
  libfolks-telepathy22 libpanel-applet-3-0 libpanel-applet-4-0 python-opengl
  gir1.2-json-1.0 libntfs10 libboost-regex1.42.0 libunity4 libnux-0.9-common
  diffstat gir1.2-vte-0.0 libnux-0.9-0 libindicator3 intltool-debian
  libboost-regex1.46.1 libseed0 libbluray0 libedataserverui1.2-11
  unity-place-applications patchutils g++-4.5 gir1.2-clutter-1.0 libibus2
  libboost-program-options1.42.0 libmono-simd2.0-cil libindicate-gtk2
  python-gtkglext1 lightsoff libcamel1.2-19 libapt-pkg-perl seed
  libboost-thread1.42.0 librasqal2 libseed-gtk3-0 libdvbpsi6
  libboost-serialization1.42.0 python-gtkspell libfolks22
  libnet-domain-tld-perl gettext libebook1.2-10 libgdata11 swell-foop
  libprotobuf6 libgwibber1 libecal1.2-8 libipc-run-perl libcrypto++8
  libnet-ip-perl vamps libstdc++6-4.5-dev libnet-dns-perl
  gir1.2-gnomegamessupport-1.0 libboost-iostreams1.42.0 libavfilter1
  gnome-js-common unity-place-files gir1.2-clutter-gtk-0.10
  gir1.2-appindicator-0.1 liboverlay-scrollbar-0.1-0 libedata-cal1.2-10
  gnome-panel-bonobo libedata-book1.2-8 mono-csharp-shell python-ubuntuone
  libio-pty-perl python-wsgi-intercept libunistring0 libmono-management4.0-cil
  gir1.2-cogl-1.0 libunity-misc0 libboost-filesystem1.42.0 libdigest-hmac-perl
  libemail-valid-perl libdmapsharing2 mkvtoolnix libmono-management2.0-cil
  libquicktime1 lintian libgtkglext1 libreadline5 libprotoc6
  libboost-system1.42.0 freeglut3 libmatroska3 gir1.2-panelapplet-4.0
  libboost-python1.42.0 libdigest-sha1-perl libavdevice52 mono-gmcs
  libntfs-3g79
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up ushare (1.1a-0ubuntu6) ...
/etc/ushare.conf: 6: desktop: not found
dpkg: error processing ushare (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 ushare
E: Sub-process /usr/bin/dpkg returned an error code (1)
denver@denver-desktop:~$

---

### Post by #1 fisherman on 2012-03-05
After running the 11.10 system for a while everything seems to be fine exept video playback the internet runs fast programs load fast as long as it is not too many things at once I like the look and feel of it all but something changed with the video from the new upgrade.I did install the xubuntu desktop started new sesion from login with xbuntu same problem with video playback its choppy and was great in 11.04 ubuntu I could install more ram if needed.thanks for the help.Oh and got rid of ushare

---

