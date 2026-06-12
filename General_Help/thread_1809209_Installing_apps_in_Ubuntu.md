---
title: "Installing apps in Ubuntu"
date: 2011-07-21
forum: General Help
---

### Post by DEdesign57 on 2011-07-21
I have not been able to figure out how to install apps in Ubuntu. I know how to install things from the software center of course, but that's not what I mean. For example, I went to download the new Firefox browser(Im using chromium btw) and When I download it and open it, it brings me to this place called archives. But I dont know what to do from here. I dont see an install package or file that I can recognize. And it only confesses me to see all the files that came with the download and their unfamiliar extensions. And this problem is the same for all downloads that the software center does not have already. Can anyone help me with this?

---

### Post by snowpine on 2011-07-21
Firefox is in the Ubuntu repositories and can easily be installed through the Software Center.

Once you go outside the Ubuntu repositories or "repos" then there is no standard method of distributing software. It could be source code you have to compile, it could be a .deb package, it could be an executable binary, etc.

In Firefox's case, it is distributed as a tar.bz2 (archive or "tarball") containing an executable binary. So you simply unpack the archive using your favorite archive manager and double-click the "firefox" file. It is ready-to-run (like an .exe in Windows) and doesn't need to be "installed." (But why would you do it "the Windows way" when Firefox is already installed by default in Ubuntu?)

This tutorial covers the topic far better than I ever could: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Frogs Hair on 2011-07-21
The first two links are for installing Firefox from the ppa . I was not sure what version of Ubuntu you are using . The other is a general guide for installing tar .gz packages .

[http://www.webupd8.org/2011/06/firefox-5-lands-in-firefox-stable-ppa.html](http://www.webupd8.org/2011/06/firefox-5-lands-in-firefox-stable-ppa.html)

[http://www.webupd8.org/2011/06/install-firefox-5-in-ubuntu-1104.html](http://www.webupd8.org/2011/06/install-firefox-5-in-ubuntu-1104.html)

[http://www.ubuntugeek.com/how-to-install-source-files-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-source-files-in-ubuntu.html)

---

