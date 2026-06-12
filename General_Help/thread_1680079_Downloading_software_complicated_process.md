---
title: "Downloading software complicated process"
date: 2011-02-01
forum: General Help
---

### Post by avocadorange on 2011-02-01
I can't understand the downloading process in [COLOR="DarkSlateBlue"]Ubuntu 10.04.[/COLOR]..
This happens almost every time I try to download something. For example today I tried to install the latest version of [COLOR="SeaGreen"]Open Office. [/COLOR]
1) I click on download on the OpenOffice site. 
2) My browser is [COLOR="Red"]Google Chrome[/COLOR], so the software icon appears on the bottom of my screen. I click on "open"
3) My system opens up a page in archive manager that I can't understand very well, being computer illiterate as I am:[COLOR="DarkOrchid"] See screenshot #1[/COLOR].
4) I click on this folder and am taken to this page (see [COLOR="Olive"]Screenshot #2[/COLOR]). I get even more confused and give up.

This happens to me very often. What am I doing wrong?
[FONT="Comic Sans MS"]Thanks in advance [/FONT]for your replies

---

### Post by marshmallow1304 on 2011-02-02
It is recommended to install software through the [Ubuntu Software Center]("https://help.ubuntu.com/community/SoftwareCenterFAQ").

---

### Post by oldos2er on 2011-02-02
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by avocadorange on 2011-02-02
Thanks -- I followed your suggestions and attempted to download the OpenOffice suite in software center. The download failed though. I received this message; also I am attaching a screen shot...  What's next?

Failed to fetch [http://jp.archive.ubuntu.com/ubuntu/pool/main/t/tomcat6/libservlet2.5-java_6.0.24-2ubuntu1.5_all.deb](http://jp.archive.ubuntu.com/ubuntu/pool/main/t/tomcat6/libservlet2.5-java_6.0.24-2ubuntu1.5_all.deb) 404  Not Found

---

### Post by drewsus on 2011-02-02
From your first two pictures, you are downloading the file from source. You shouldnt open that file. You should save as and then go to the folder, then extract the contents of the source archive you just downloaded, go to the newly extracted folder and build from source using various methods (usually found by reading contained readme files). 

From your second post (3rd screen shot) it seems that a file is just not being downloaded. This could mean problems with your connection, or the repository that you are downloading from. 

But why are you trying to install something that is installed by default?

---

### Post by luigi_mb on 2011-02-02
> **marshmallow1304 said:**
> It is recommended to install software through the [Ubuntu Software Center]("https://help.ubuntu.com/community/SoftwareCenterFAQ").

I suggest you use Synaptic. The Software Center seems to be unreliable, as reported in these forums over and over again.

/luigi

---

### Post by 3rdalbum on 2011-02-02
Go to Synaptic Package Manager (it's in the System > Administration menu) and click the Reload button. After it's finished loading the list of packages, try the download again. Maybe a new version of that package was uploaded and you've still got the old version listed.

Or, maybe that package actually hasn't reached your local mirror yet, and you need to give it an hour or so.

If problems persist, try changing the mirror from the regular Japanese mirror to the "main server" or to a different one in Japan/Asia. You can do this from Settings > Repositories in Synaptic Package Manager.

---

### Post by Noah0504 on 2011-02-02
> **drewsus said:**
> But why are you trying to install something that is installed by default?
This is what I'm trying to figure out.

Anyway, in your download, there should be packages .deb files somewhere.  Those can be installed by just double-clicking them or from the terminal.

---

### Post by avocadorange on 2011-02-04
Thanks everyone for your responses and suggestions. I'm going to try out your recommendations and I'll let you know the results.
[I]
Why[/I] am I trying to download something that is pre-installed? I had some problems with spell check and it was suggested on an OpenOffice support site that my file was corrupted, so I might get better results if I installed the latest version...

---

### Post by uRock on 2011-02-04
Edit: To install the package you have already downloaded, right click the package, select to Extract here, then right click the .deb and select to install with Ubuntu Software Center.

Cheers,
uRock

---

### Post by avocadorange on 2011-02-04
> **uRock said:**
> Edit: To install the package you have already downloaded, right click the package, select to Extract here, then right click the .deb and select to install with Ubuntu Software Center.

Cheers,
uRock

Thanks uRock. Followed your suggestion but then I don't see any .deb to right click on.
 

I'm going to try to download it from synaptic pkg mnger

---

### Post by avocadorange on 2011-02-04
> **luigi_mb said:**
> I suggest you use Synaptic. The Software Center seems to be unreliable, as reported in these forums over and over again.

/luigi

I tried using the synaptic manager but *[COLOR="RoyalBlue"]got this error[/COLOR]*. I don't know if it's that important. (see screenshot)

Also, I think I finally was able to find a .deb file to click on. I tried that and got the package installer but got this error. (see other screenshot)

Maybe I need to thoroughly scrub this computer of any traces of the previous open office files and then retry the download? I'm a totally untechnical person. Just thinking out loud.

---

### Post by uRock on 2011-02-05
Before you can install the New OO.org, you will have to use Ubuntu Software Center to remove the current version. If you use Synaptic Package Manager for this, you will stand a chance of uninstalling the whole ubuntu-desktop package, which will leave you without a GUI.

---

### Post by avocadorange on 2011-02-07
> **Noah0504 said:**
> This is what I'm trying to figure out.

Anyway, in your download, there should be packages .deb files somewhere.  Those can be installed by just double-clicking them or from the terminal.
I removed all versions of OpenOffice in the Software Center, per URock's suggestions. Now, I am really struggling to understand what to do with the .deb files...

I download the package from the Web site, right click and select extract, then I end up with the following (see screen shots)...I usually click on the DEBS folder and end up with what you see in the second screenshot. NO idea how to proceed. [COLOR="DarkRed"]*Keep in mind I am just technical enough, just brave enough to use Ubuntu. Not more.*[/COLOR]

This is frustrating...Can anyone help?

---

### Post by avocadorange on 2011-04-03
I found a solution here: 

[http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=38224](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=38224)

---

### Post by linuxnewb2 on 2011-04-03
Ahhh learning from other people mistakes is one of lifes true joys, lol. Thanks to this brief interaction. I've now learned how to download and install programs, outside of the ubuntu repositories ... nice. :D

---

