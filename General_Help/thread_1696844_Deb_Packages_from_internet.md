---
title: "Deb Packages from internet"
date: 2011-02-28
forum: General Help
---

### Post by satish_j on 2011-02-28
I wanted to know whether there is any possibility of the Deb packages available on Internet(other than official Ubuntu Repositories) containing Virus,just like exe files in windows.
Iam currently not using any AV on Ubuntu.
In windows,there is this 'scan' feature in right-click menu context menu for scanning the files.Does Ubuntu also provide similar feature if i install AV.
Also,can you suggest me some good options for AV Software on Ubuntu?

---

### Post by Krytarik on 2011-02-28
Yes, of course you can get a malicious executable with those deb-packages.

I recommend "avast" and "ClamAV", in that order, the latter is very slow in scanning files, but is better integrated into the desktop, I don't remember if those even provides a context-menu option.

---

### Post by nomko on 2011-02-28
A very good scanner is Esed NOD32 for Linux. It's not only a virusscanner, but it's also the only one with a spyware scanner build in. You can find it here: [http://beta.eset.com/linux](http://beta.eset.com/linux). A manual can be found here: [http://download.eset.com/manuals/ESET_EAVLIN_4_UserGuide_ENU.pdf](http://download.eset.com/manuals/ESET_EAVLIN_4_UserGuide_ENU.pdf)

---

### Post by dcstar on 2011-02-28
> **satish_j said:**
> I wanted to know whether there is any possibility of the Deb packages available on Internet(other than official Ubuntu Repositories) containing Virus,just like exe files in windows.
.......

No "Anti Virus" package will find anything in .deb packages - because **all** AV packages scan for things that can infect vulnerable OSs - and that means Windows.

If **you** install .deb packages from untrusted sources then **you** do that at your own risk - no AV package can protect **you** from **your** own actions.

---

### Post by satish_j on 2011-02-28
> **dcstar said:**
> 
If **you** install .deb packages from untrusted sources then **you** do that at your own risk - no AV package can protect **you** from **your** own actions.
I would first scan the deb package before installing it.
Wouldn't that be protective??
Also,any feedback from those running AV on ubuntu..i mean..do they have 'scan for virus' feature in File-->right-click menu??

---

### Post by nomko on 2011-03-01
> **satish_j said:**
> I would first scan the deb package before installing it.
Wouldn't that be protective??
Also,any feedback from those running AV on ubuntu..i mean..do they have 'scan for virus' feature in File-->right-click menu??
 
For me this sounds really strange. Why scanning .deb files? You're afraid of finding Windows virusses/malware/spyware? As long you download from trusted sites, there will be no problem. If you start downloading packages from obscure sites, well...then you migth get some trouble. But that trouble is more like buggy, unstable programs instead of virusses/malware/spyware. Or do you have some Windows formatted usb drives mounted? Then you should be carefull with files whch migth contain virusses/malware/spyware especially ment for Windows systems. But else there's no reason to assume that every .deb file contains virusses. In fact, the change of getting a Linux virus is comparable with the change of finding ET on Mars :)

---

### Post by nothingspecial on 2011-03-01
The only truly rock solid way of ensuring you never ever get any dodgy stuff on your computer is to look at the source code then compile it yourself.

But that would be silly.

---

### Post by Krytarik on 2011-03-01
Honestly, I have avast installed at my system, but I don't really use it unless I need to check something I downloaded for use in Windows, usually for other people, because I don't even have it installed at my machine currently.

---

### Post by nomko on 2011-03-01
> **Krytarik said:**
> Honestly, I have avast installed at my system, but I don't really use it unless I need to check something I downloaded for use in Windows, usually for other people, because I don't even have it installed at my machine currently.

I don't run a virusscanner anymore. And normally all the people around me who's using a Windows System downloads their own stuff.

---

### Post by Krytarik on 2011-03-01
> **nomko said:**
> I don't run a virusscanner anymore. And normally all the people around me who's using a Windows System downloads their own stuff.
Normally, yeah, unless I'm preparing an install for them, or such.

---

### Post by nomko on 2011-03-01
> **Krytarik said:**
> Normally, yeah, unless I'm preparing an install for them, or such.

Ahh okay, that change the things a little bit..

---

### Post by Animal X on 2011-03-01
virus scanners? hahahaha, yeah right....

---

### Post by Krytarik on 2011-03-01
> **Animal X said:**
> virus scanners? hahahaha, yeah right....
Hey, a little more compassion with the Windows users! :P
:popcorn:

---

