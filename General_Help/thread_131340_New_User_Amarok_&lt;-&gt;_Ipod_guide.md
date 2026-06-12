---
title: "New User Amarok &lt;-&gt; Ipod guide"
date: 2006-02-16
forum: General Help
---

### Post by preyer on 2006-02-16
Hi,

I have read many forums and information and are really confused. I am trying to get Amarok 1.4 to access the database on my iPod mini.

Here is the results so far...
- I have managed to install Amarok version 1.4
- I can access the ipod via gtkpod

but I cannot access the database with amarok and thus sync files and playlists properly. Can someone please provide some help or the steps which need to be done to get it working. I am afraid that I have stuffed something up doing all the different things I have tried.

Any help is appreciated, thank you in advance.

---

### Post by nursegirl on 2006-02-16
Did you install from SVN using [URL="http://www.ubuntuforums.org/showthread.php?t=80492"]this process?
[/URL]

Particularly see post #104:
> To get the iPod support you need to get libgpod. The snapshot there builds clean here - but I have most of the dev packages, so YMMV. Once you download the snapshot use './configure --prefix=/usr && make && sudo make install' without the quotes to build it. When the script asks for extra flags use --with-mp4v2 --with-libgpod. Should build clean.

Use this version of libgpod (from source) rather than the one from the repos, and then try reinstalling Amarok 1.4

If this doesn't work, please post back with exactly what happens when you try to access your ipod with Amarok.

---

### Post by preyer on 2006-02-17
Hi,

Thanks for the repoy, read through most of the thread didn't help. All that happens when I try access my ipod via amarok is I get an error message saying...

> VFAT Devices cannot be manually configured. Ensure DBUS and HAL are running and your kioslaves were built with DBUS and HAL support. The device should be autodetected; click the "Manage Plugins..." suboption of the Configure button in the Media Device tab and choose the VFAT plugin for the detected device. Then ensure the device is mounted and click "Connect" again

that is what happens so far.

---

### Post by nursegirl on 2006-02-17
Hey,
Just want to confirm...did you:
1) Install libgpod from source (not from packages), and then
2) Install Amarok from SVN using the process in that thread?

If you didn't then I'm going to have to suggest that you
```
sudo apt-get remove amarok amarok-arts amarok-xine amarok-gstreamer
```

-then install libgpod from source, using the [link]("http://www.ubuntuforums.org/showpost.php?p=571652&postcount=104") from post #104
-then install Amarok from SVN

It worked for my nano, once I did it that way (it wouldn't until I had completely removed Amarox and installed in that order).

---

### Post by preyer on 2006-02-19
Thanks for the responses. I did install amarok form SVN source. 
I finally got it to connect to my ipod by installing version 1.3.8 over the top via synaptic and then uninstalling, then reinstalling the SVN version.

But after one good connection it won't connect again. It says there is no ipod mounted. But gtkpod can pick it up. 

Well I am almost there.

---

### Post by Aashammer on 2006-07-09
Hi

I get the same error with my iPod and amaroK 1.4. After managing to connect once, transfer files and so on, I get the error message "Media Device: No mounted iPod found" when I press the "connect" button in amaroK.

---

### Post by Sentinel on 2006-08-11
m undergoing the same problem as well

---

### Post by sinaen on 2006-09-06
how did you install the amarok 1.4 version?
i get this error after adding the latest amarok ubuntu repositories :P

 sudo aptitude install amarok amarok-engines
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  amarok amarok-xine
The following NEW packages will be automatically installed:
  python-qt3
The following packages have been kept back:
  compiz libssl-dev libssl0.9.8 python-netcdf testdisk
The following NEW packages will be installed:
  amarok-engines python-qt3
0 packages upgraded, 4 newly installed, 0 to remove and 5 not upgraded.
Need to get 17.2MB of archives. After unpacking 32.4MB will be used.
The following packages have unmet dependencies:
  amarok-xine: Depends: kdelibs4c2a (>= 4:3.5.3-1) but 4:3.5.2-0ubuntu18.1 is installed.
  amarok: Depends: kdelibs4c2a (>= 4:3.5.3-1) but 4:3.5.2-0ubuntu18.1 is installed.
          Depends: libvisual-0.4-0 (>= 0.4.0) which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

---

### Post by xyz on 2006-09-06
> **sinaen said:**
> how did you install the amarok 1.4 version?

I found it in Add/Remove or:
[http://amarok.kde.org/](http://amarok.kde.org/) "Download Amarok"

---

### Post by sinaen on 2006-09-06
> **xyz said:**
> I found it in Add/Remove or:
[http://amarok.kde.org/](http://amarok.kde.org/) "Download Amarok"

Ok there i found another apt-source :P seems ive been getting the wrong one :p
didnt work i only got the 1.3.9 er...
oops did forget to update.
checking again.
seems to work. seems that the amarok-arts package was keeping it down uninstalled that and seems to upgrade to 1.4.3

Now i really hope this works with my ipod. i havent been happy about it :/ it started messing about a while ago

[http://amarok.kde.org/wiki/Installation_HowTo#Which_Amarok.3F](http://amarok.kde.org/wiki/Installation_HowTo#Which_Amarok.3F)
This one was the one i found first, but i dont know if it works properly. anyway it did not do that when i tried the first uptillion times

---

### Post by SentientFluid on 2006-11-22
I haven't tried this but maybe this will help you:

[http://amarok.kde.org/files/articles/ipod_amarok_tux_june05.pdf](http://amarok.kde.org/files/articles/ipod_amarok_tux_june05.pdf)

---

### Post by TheCrook on 2006-11-23
I am using Kubuntu (Dapper) and Amarok 1.4.3 and have successfully managed to get my iPod connected. Here are the steps I took:

connected iPod on Firewire port
Kubuntu autodetected device and mounted it to /media/sdc2
Started Amarok
click on **Settings** then **Configure** - **Amarok**
in the left hand panel of the pop-up click on **Media Devices**
you should see sdc2 (or whereever you have mounted th iPod) in the list
open the drop-down for plugin
select **Apple iPod Media Device**

Enjoy 8)

---

### Post by stevo_srh on 2007-05-14
Apologies if this is a basic solution, but it was thwarting me.  I just changed the ipod settings in Amarok to reflect the name of my ipod, which I had previously changed from its default through itunes.  By changing the mount point to /media/XXXXX it fixed it.

Regards

Steve

---

