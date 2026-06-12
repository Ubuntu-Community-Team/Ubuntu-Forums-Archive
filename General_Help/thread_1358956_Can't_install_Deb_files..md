---
title: "Can't install Deb files."
date: 2009-12-19
forum: General Help
---

### Post by OsakaWilson on 2009-12-19
I just upgraded to 9.10 and the application Devede stopped working saying that mplayer and mencoder weren't installed, but they were. I found a [Solved] thread and followed the instructions, but the last thing was to install Devede from .deb. 

So I went to their web page and tried to install the .deb file there. I got a "Launch Application" message saying, "This link needs to be opened with an application. Send to:" and it gave me a button to browse my system for whatever application opens .debs. 

I don't know what that would be.

So, I went to GetDeb.net and tried to get the file. And I get the message, "Firefox doesn't know how to open this address, because the protocol (apt) isn't associated with any program."

Can someone help?

---

### Post by jmate24 on 2009-12-19
the getdeb.net installer has to use your installed apt manager and not the apturl. 

when you are ready to install...

select the choose application... and navigate to: /usr/bin/**apturl-gtk** select it and press the **open** button down at the bottom right of the window.

then when the launch application reappears then click the check box under the white space so that it will always use the application.

then install and enjoy...

jmate24--

---

### Post by stinkeye on 2009-12-19
The apt protocol is associated with apturl.
Some help here...[_[COLOR="DarkRed"]https://help.ubuntu.com/community/AptURL[/COLOR]_]("https://help.ubuntu.com/community/AptURL")

---

### Post by OsakaWilson on 2009-12-19
I used apturl-gtk and got this message:

Invalid url: '/home/wilson/Desktop/devede_3.15.2-0~rastersoft1_all.deb' given, exiting

No ':' in the uri

---

### Post by 3rdalbum on 2009-12-19
> **OsakaWilson said:**
> I used apturl-gtk and got this message:

Invalid url: '/home/wilson/Desktop/devede_3.15.2-0~rastersoft1_all.deb' given, exiting

No ':' in the uri

So you've got a Debian package there. Save it to your hard disk and then double-click on it to open it in GDebi.

---

### Post by coffeecat on 2009-12-19
Devede is in the Karmic repos. Why not simply open Synaptic and mark it for re-installation? If there are any broken packages or dependencies they will hopefully be resolved.

---

### Post by 3rdalbum on 2009-12-19
> **coffeecat said:**
> Devede is in the Karmic repos. Why not simply open Synaptic and mark it for re-installation?

It's worth a try - but it's rare that reinstalling a program will cause it to work, because most of the time the copy of the program on disk is identical to the copy of the program in the repositories.

If there are broken packages (which theoretically shouldn't happen anyway) then reinstalling Mplayer might solve it.

---

### Post by terry_gardener on 2009-12-19
i had this problem. 

goto the following and download the file in post #8 and extract to home directory. 

[http://ubuntuforums.org/showthread.php?t=1343306]("http://ubuntuforums.org/showthread.php?t=1343306")

reboot and it should be ok.

---

