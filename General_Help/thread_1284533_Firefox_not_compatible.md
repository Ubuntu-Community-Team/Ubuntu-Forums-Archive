---
title: "Firefox not compatible"
date: 2009-10-06
forum: General Help
---

### Post by NoBugs! on 2009-10-06
I just tried to install the latest Firefox for Windows from the Firefox site. It seems to install ok, but it will not run, it just shows a "firefox crashed" dialog.

This is on 9.04 with Firefox 3.5.3 and wine 1.1.30.

Is there another Windows Firefox that will run in Linux?

---

### Post by Scunizi on 2009-10-06
How about the linux Firefox? 3.5 I believe is in Jaunty 9.04 and if it isn't it will be in 9.10.  IN the interim 3.5 is available through Synaptic Package Manager as a separate install alongside whatever version you currently have.

---

### Post by lovinglinux on 2009-10-06
I agree with the previous poster.

just run this:

```
sudo apt-get install firefox-3.5
```

Anyway, the 4 most popular methods of installation of Firefox 3.5 (Psychocats, Ubuntuzilla, Repository, Shiretoko/Swiftfox) are available in the "Install Other Versions" section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567). 

There is also a detailed explanation of each installation method provided, comparing the most important differences. I personally tested all of them and they work like a charm.

---

### Post by NoBugs! on 2009-10-06
I already have that Firefox 3.5 for Linux, I only need the Windows Firefox to run some Windows-only plugins. Unless there is some way to make Windows Firefox plugins work without it?

---

### Post by Scunizi on 2009-10-07
What plug-ins are you referring to?  If they deal with active x or some asp scripts, forget it.. you might be better off running a version of windows in a VM with virtualbox

---

