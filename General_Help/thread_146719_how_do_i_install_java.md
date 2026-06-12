---
title: "how do i install java?"
date: 2006-03-18
forum: General Help
---

### Post by Nicktu on 2006-03-18
ive been trying to install java for awhile now, will someone help me

---

### Post by Jucato on 2006-03-18
There is a open-source version of java in the respositories (j2re1.4 and j2sdk1.4, or Blackdown Java). If you want the propriety version of java, check out this section of the wiki pages:

[https://wiki.ubuntu.com/RestrictedFormats#head-68565ae07a003332e82c9f23706638777396c249](https://wiki.ubuntu.com/RestrictedFormats#head-68565ae07a003332e82c9f23706638777396c249)

---

### Post by Nicktu on 2006-03-18
well im trying to get limewire to work, and it says i need java, and im not sure on how to do it, im kinda a beginner:cry:

---

### Post by Barrakketh on 2006-03-18
This is going off of my memory (which should be correct).  In short, you'll need:

The JRE/JDK you want to install.  You'll want the self extracting one.

The fakeroot and java-package packages.

Download the JRE/JDK.  Run "fakeroot make-jpkg jre_bin_package".  Then use dpkg -i to install the .deb it creates.  Run "update-alternatives --config java" as root.  The one you'll want to choose will appear similar to "/usr/lib/j2sdk1.5-sun/bin/java"

That should do it.  I don't use Limewire, but I use Eclipse and Azureus and they work perfectly.

---

### Post by Nicktu on 2006-03-18
run through that one more time. sorry like i said im new, some of this is gibberish to me

---

### Post by Cyril on 2006-03-18
I have always installed java using the method on [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats).

Has never failed me.

---

### Post by Jucato on 2006-03-18
I think the open-source Java will work perfectly fine with Azureus.

Either type this in a terminal (Konsole)
```
sudo apt-get install j2re1.4
```
or look for the j2re1.4 package in Adept.

---

### Post by Barrakketh on 2006-03-18
[QUOTE=Fenyx]I think the open-source Java will work perfectly fine with Azureus.

Either type this in a terminal (Konsole)
```
sudo apt-get install j2re1.4
```
or look for the j2re1.4 package in Adept.[/QUOTE]

Unless you're using the old version of Azureus included with Breezy, it won't work.  The updated versions require JRE 1.5.  You will get a warning upon launching Azureus if you aren't using it.

---

### Post by Jucato on 2006-03-18
oh I see... so I guess you do have to install Sun's Java. The wiki link I and Cyril gave is fairly easy to follow. So no worries there.

I have to warn  you though. Azureus can be a bit of a resource hog. Not only is it a resource hog itself, but JRE needs to run beneath it as well. So if you're a bit performance conscious, I'd recommend skipping on it. 

Also, there's a fine bittorrent client that integrates very well with KDE. It's called [KTorrent](http://ktorrent.pwsp.net/) and offers almost as much features as Azuresu (almost), you can set its resource usage (low, medium, high),  and has a built in browser that will let you search your top torrent sites. Unless you are using Azureus-specific features, then I suggest you give this a try, if you're interested. :D

---

### Post by Barrakketh on 2006-03-18
**<derail>**
[QUOTE=Fenyx]oh I see... so I guess you do have to install Sun's Java. The wiki link I and Cyril gave is fairly easy to follow. So no worries there.[/quote]
I gave him exactly what he needed to know in my post, and he has those links if he gets confused.
> I have to warn  you though. Azureus can be a bit of a resource hog. Not only is it a resource hog itself, but JRE needs to run beneath it as well. So if you're a bit performance conscious, I'd recommend skipping on it.
I only mentioned Azureus because it's a popular program: the OP didn't say anything about it. 
> Also, there's a fine bittorrent client that integrates very well with KDE. It's called [KTorrent](http://ktorrent.pwsp.net/) and offers almost as much features as Azuresu (almost)
Eh...I'm not a casual torrent user, and KTorrent is definitely too limited for me.  I've uploaded over 200 GiB, and the advanced features of Azureus such as the advanced queue/seeding options is something that I rely on.  It seems to be missing DHT and super seeding.  It lacks plugins like Stuffer.  It doesn't allow me to change my upload speed based on whether I'm currently downloading a torrent.  KTorrent doesn't come within a mile of touching Azureus when it comes to features.

Azureus uses a bit more memory than other applications.  That's fine with me: I have a gig, and I plan on taking advantage of it.
**</derail>**

---

### Post by Jucato on 2006-03-18
Well, maybe not a mile. but a few inches perhaps? :D
KTorrent has most of the things basic users will need. Most. Of course, it still has a long way to go. Not surprising, since it's still version 1.2. But to each his own. :D

Anyway, I'm not sure if the Blackdown Java version works well with LimeWire. It probably should, unless like Azureus, it specifically needs version 1.5.

---

### Post by skaboss on 2006-03-19
I think the simplest way to install Java is : 

```

apt-get install sun-j2sdk1.5

```

---

### Post by Jucato on 2006-03-19
Except that it's not in the main or universe repositories. Which repository is it from? And will it work with those apps needing JRE (not JSDK)?

---

### Post by skaboss on 2006-03-19
Sorry, i don't know which exact directory it is from, but here is my sources.list : 

```
deb-src http://archive.ubuntu.com/ubuntu breezy universe
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
 deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted
deb http://security.ubuntu.com/ubuntu breezy-security universe
 deb-src http://security.ubuntu.com/ubuntu breezy-security universe
deb http://archive.ubuntu.com/ubuntu breezy multiverse
 deb-src http://archive.ubuntu.com/ubuntu breezy multiverse
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

```

The jre is included in the jdk, allowing you to run all java-based apps ;)

---

### Post by Jucato on 2006-03-19
I'm definitely sure there's no package in the repository for the Sun Java (jre or sdk 1.5)
1. You can check the Ubuntu packages website to search for available packages in any section (main, restricted, universe, multiverse) [http://packages.ubuntu.com/](http://packages.ubuntu.com/)
2. Including Sun Java in the repositories will be violating Ubuntu's philosophy, not to mention probably break a few laws. :D

---

### Post by Barrakketh on 2006-03-19
It's not in either of those.  It's available though a PLF repository, but that version is Update 5, not Update 6 (which includes a few security fixes).  Alternatively, you can install it the way we already mentioned.

It's easy to check which repository a package is available from:
```
apt-cache showpkg package_name
```

In the versions section you can read the directory name to see which one it's available from.  For sun-j2sdk1.5:
> Versions:
1.5.0+update06(/var/lib/dpkg/status)
1.5.0+update05(/var/lib/apt/lists/ftp.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages)
When the section only has en entry that reads (/var/lib/dpkg/status) it means that you didn't install it from a repository.

---

### Post by jrib on 2006-03-19
[http://wiki.ubuntu.com/SeveasPackages](http://wiki.ubuntu.com/SeveasPackages)

Seveas's repos contain update06 in the java section

---

