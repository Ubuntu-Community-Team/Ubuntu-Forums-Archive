---
title: "How to convert NRG mixed-mode to BIN/CUE"
date: 2010-06-24
forum: General Help
---

### Post by Nathanael Culver on 2010-06-24
I've just spent the past two days trying to figure out how to convert an NRG image to BIN/CUE format. I've found all kinds of info on how to convert it to ISO. I've tried lots of different packages (K3B, Brasero, AcetoneISO...). No luck.

My NRG is an image of an old DOS game I want to play in DOSBox. The catch is that it's mixed-mode, so converting to ISO is not a possibility. DOSBox will mount BIN/CUEs, so that seems the route to go. But while K3B supports creating mixed-mode CDs, it doesn't read NRG images. And while AcetoneISO will mount the NRG, only the data track is accessible; the audio tracks aren't.

Can anyone help?

---

### Post by Nathanael Culver on 2010-06-25
I've managed to convert my mixed-mode NRG image to BIN/CUE format. Here's how I did it, but I still feel like there must be a better solution available.

Download and install the trial version of [COLOR="blue"]Nero Linux 4[/COLOR] ([**[COLOR="Red"]here[/COLOR]**]("http://www.nero.com/enu/linux4.html")). It's the only thing I could find that would recognize all tracks (data + audio) in my NRG image.

Using Nero Linux, [COLOR="Blue"]burn the image to a blank CD[/COLOR]. Nero Linux does have a burn-to-image option which I thought to use to create the BIN image directly[*]. Unfortunately, Nero only supports burning to NRG images. So I had to burn to a physical CD as an intermediate step.

Load and mount the CD I just created, then use [COLOR="Blue"]cdrdao[/COLOR][*] to create the BIN/TOC file. Finally, use TOC2CUE to convert the TOC to CUE. Open a terminal and paste the following commands:

```

cdrdao read-cd --read-raw --datafile rtz.bin --driver generic-mmc:0x20000 --device /dev/cdrom rtz.toc
toc2cue rtz.toc rtz.cue

```

As I said, I can't help feeling there's a better solution somewhere, especially one that doesn't involve having to burn an actual CD.

--Nathanael


[*]K3b was able to read the mixed-mode CD, and has a burn-to-image option which, momentarily, I thought would solve my problem. However, K3b only supports burning CD-Extra-style mixed-mode CDs to image (why?), and my disc is standard mixed-mode.

---

### Post by Jellby on 2013-01-27
Sorry to revive this old thread, but I could convert the image with [UltraISO](http://www.ezbsystems.com/ultraiso/). It's a Windows tool, but works fine with Wine. It can convert mixed-mode NRG to mixed-mode CUE/BIN (which can be split with bchunk) or directly extract the files or audio tracks.

---

