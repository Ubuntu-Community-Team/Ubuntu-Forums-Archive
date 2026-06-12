---
title: "Ubuntu 9.10 and Canoscan fb320p"
date: 2010-04-02
forum: General Help
---

### Post by bafranksbro on 2010-04-02
Ok first of all I should've probably done this before choosing 9.10 to put on my USB key but here is what I'm trying to do. I've got this old scanner, Canoscan FB320P, and I saw it was usable in Ubuntu with this sane thing cause there isn't a new driver for it in Win7. I have very limited Linux experience, I've tried running it on multiple occasions and so when trying to figure out how to get my scanner working....... I got lost and I'm am thoroughly confused by this point. But my confusion might be because it doesn't work too well or at all correctly in Ubuntu 9.10 and so I'm asking a variety of questions.

1. Is it possible to get the Canoscan FB320P working in Ubuntu 9.10? If so how?

2. Is there a different version or flavour of Ubuntu that this process would work more easily or one where it might work right straight out of the door?

I've tried following some how to I found but doing what it said just doesn't provide me with the same results. I was able to get xsane to recognize it once with a gksudo, which to be honest I'm still not sure of the difference between all these different types of sudo things. Once it was selected in xsane it then started using the scanner when I click preview but then it froze and I can't get that far any more, even doing the same steps.

So I'm just wondering if anyone can help me to get this scanner working in any flavour of linux at all, I'm running them off a usb key by the way.

Thanks,
Rob :)

---

### Post by bafranksbro on 2010-04-03
Well I found a solution on my own if anyone is interested. I found a live cd version of Feisty Fawn 7.04 and put it on a USB stick, the OS it's self doesn't work as well as the live version of 9.10 but the scanning works quite well once you do a few steps.

First I uncomment canon_pp in the dll.conf file that's in the sane.d directory.

Then I uncomment 'force-nibble' in the canon_pp.conf file and I also uncomment the line line that's right for my scanner and put a comment next to the one that was defaultly uncommented.

Then I do a sudo -s and run xsane. Sometimes the scanner needs to have it's power reset a couple times right before you run xsane and sometimes it'll crash and you have to close down xsane and reset the scanner a couple times again. Also it can't preview a scan in color, you preview in grayscale to setup your scan area and then scan in color. But other than that it works and works quite well. :D

Also incase anyone is interested the version of xsane in Feisty Fawn 7.04 is version 0.991, which I read somewhere works well with these canon scanners that use canon_pp.conf.

---

