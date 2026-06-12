---
title: "APT on CD..is it possible..!!"
date: 2010-05-24
forum: General Help
---

### Post by sunnyengineeer on 2010-05-24
Hello,
           Im using Ubuntu 10.04 alongwith Linux Mint & Windows XP.
A friend of mine who has the same computer configuration &  same hardware is planning to install Ubuntu 10.04.
        But he'll not be having internet connection at that place,,
So I was thinking of helping him by giivng a CD which will be having all the requried softwares on that which I have installed in my ubuntu 10.04 ....So that when he installs Ubuntu he just need to put the CD...

[COLOR=Blue]So is there someway thru which we can put our installed programs on the CD so that we can use them again when we don't have internet connection...??Like APT on CD...[/COLOR]

thnx
Sunny Sharma

---

### Post by gmargo on 2010-05-24
Try the **aptoncd** package.

[https://help.ubuntu.com/community/APTonCD](https://help.ubuntu.com/community/APTonCD)
[http://packages.ubuntu.com/lucid/aptoncd](http://packages.ubuntu.com/lucid/aptoncd)

"APT removable repository creator and package backup tool for Debian  based systems. 

This tool will allow you to create a media (CD or DVD) to use to install software via APT in a non-connected machine, as well upgrade and install the same set of softwares in several machines with no need to  re-download the packages again."

---

### Post by sunnyengineeer on 2010-05-24
Thnx for helping me out & solving it....
Thnx again...

Sunny Sharma :)

---

### Post by Perkins on 2010-05-24
The other useful thing is the Synaptic Package Manager menu commands to "create a download script" and "install downloaded packages"  The script can be run on nearly any other Linux machine and will download all packages necessary for whatever changes you have marked.  The packages can then be carried back to the original machine and installed with the "install downloaded packages" option.

The only (in my opinion serious) flaw is that there is no similar way to download updated versions of the repository indices...

---

