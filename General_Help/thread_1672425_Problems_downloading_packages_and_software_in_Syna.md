---
title: "Problems downloading packages and software in Synaptics and Software Centre"
date: 2011-01-20
forum: General Help
---

### Post by TJ1916 on 2011-01-20
Hi People,

I have been using Ubuntu 10.10 for a week or so now, having been converted after installing Edubuntu on a family member's laptop. That install was seamless, but I have encountered problems setting my native resolution (1920x1080) on my own machine. Today edited gdm Init Default and have finally fixed the problem. I was using a script but that made panel icons shift about.

I have another problem which is not simply cosmetic however, and I cannot find a permanent solution (let alone explanation) anywhere. The problem I am having is that when I download software (whether via Synaptics, Software centre *or *apt-get), the downloads regularly freeze up completely. I have tried simple  waiting, letting Ubuntu choose the best server, manually choosing different servers all to no avail. Sometimes after switching servers things can appear to improve short-term but they revert. Even manual downloads - with and without Down Them All in Firefox - from the Ubuntu package website fail intermittently. I am now stumped, and it is frustrating. I pay per gig for my bandwidth and I am currently wasting an inordinate amount simply updating Ubuntu and adding software.

I connect using a Huawei K3565 rev. 2 on the Vodafone UK prepay network. Regular web browsing seems fine. To recap - so as not to waste anyone's time - I have tried:

[LIST]
[*]Synaptics, Ubuntu Software Centre, apt-get and manual downloads from the Ubuntu Package website
[*]letting Ubuntu test for and choose the best source server/manually working through mirrors
[*]manually deleting part-downloaded (they never restart) packages from var/cache/apt/archives/partial and restarting from scratch
[/LIST]
there has often been some improvement after switching method, source or even after simple reboots. 

Thanks to anyone who took the time to read, and any suggestions would be gratefully received ;)

---

### Post by ksprasad on 2011-01-20
Hi,
 
Run this command: "sudo apt-get update"
 
Also you can try with editing /etc/apt/sources.list.
you can try specifying the country code for the mirror.
Refer the below link.
 
[http://www.linuxquestions.org/questions/linux-software-2/apt-get-downloads-extremely-slow-471202/](http://www.linuxquestions.org/questions/linux-software-2/apt-get-downloads-extremely-slow-471202/)
 
Regards,
ksprasad

---

### Post by 3rdalbum on 2011-01-20
> **TJ1916 said:**
> H
I connect using a Huawei K3565 rev. 2 on the Vodafone UK prepay network.

That's your problem - you're downloading big files on mobile broadband.

With excellent signal strength, you can indeed download big files... but if the signal is a bit patchy, the download can drop out when the modem changes speeds.

I've observed this behaviour on Windows and Linux with Huawei modems.

Solution? Get an ADSL or cable connection; mobile broadband is not reliable enough for large files.

The reason why web pages seem to be fine is because there are lots of small files in a web page.

---

### Post by TJ1916 on 2011-01-25
Sorry for the late reply and thanks for the responses. 

@ksprasad I tried the command and also have been editing the sources.list; if I change source I often get a fairly short-term improvement but usually short term.

@3rdalbum I have noticed in he past that mobile broadband isn't all too reliable with larger files, but if I boot into Windows it does seem slightly more robust. I can usually download anything below 100MB without any problems but I have observed flakey behaviour with files larger than 150MB. A lot of the downloads that freeze here on Ubuntu are less than 30MB. Could there be something not configured correctly on my Ubuntu install; are there any settings I should check? 

Many thanks

---

### Post by TJ1916 on 2011-02-23
After several weeks of using Synaptics package download scripts on another machine to retrieve software and updates, I added more hardware to my machine, wiped the original Ubuntu (installed via Wubi) and dedicated an entire drive to the x64 version. Because I switched from an x86 install I had to start at square one with updates and packages. After generating the initial package download script for all system updates I decided to try a different method; this method allowed me to download everything via my own tinpot broadband connection. This is what I did:

1. opened Synaptics package manager and clicked 'mark all upgrades'
2. went to file -> generate package download script. Closed Synaptics
3. right clicked the download script -> open with other application -> Firefox
4. used the Down Them All Firefox add-on to download all links 
5. once the downloads were complete added the folder using the 'add downloaded packages' option in Synaptics. Once the debs were added I exited Synaptics, then went to update manager and ran it.

All the updates were applied successfully. Update manager only needed to download a single update which was less than a mb. I have had no problems and the machine appears to be up to date.

It seems that using a regular download manager proved more robust than the regular Ubuntu method when it comes to downloading updates and software using mobile broadband.

**Does anyone know of any potential hazards using this method?**

---

### Post by TJ1916 on 2011-02-24
bump...

---

