---
title: "Wont boot anymore"
date: 2011-05-15
forum: General Help
---

### Post by Marfish on 2011-05-15
K, so I've got my dad's comp that he was running Ubuntu on. I've installed Ubuntu on my own comp plenty of times so I didnt think I'd have any trouble with his. I was reinstalling Ubuntu on his computer because I thought it might help with how slow it was being. The specification were fairly good, but the computer was so slow it could barely run a video in a browser. I reinstalled Ubuntu 10.04 LTS on it, not running into any problems other than the computer taking its time in the installation. Soon as its done and it reboots though, the thing had a severe problem. It could no longer boot past the first screen with the "press f12" for yada yada. Now even if I try to use this screen to mess with the boot up, it wont let me. it crashes and restarts without letting me even touch these settings. So, I'm wondering, is this a hardware problem, cause I can't seem to come to any other conclusion despite the thing being able to at least run before i tried reinstalling.

---

### Post by Hedgehog1 on 2011-05-15
We need to get a look at your install to get an idea what is going on.

Please boot off the LiveCD/LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the [noparse]```
 & 
```[/noparse] tags.

***The Hedge***

:KS

---

### Post by Rubi1200 on 2011-05-15
In addition to the boot script recommended by Hedgehog1 you should also post the full specifications for the computer so we know what we are dealing with.

And, while on the LiveCD, check the health of the drive from the Disk Utility program under System > Administration and let us know if it reports any problems.

Thanks.

---

### Post by Marfish on 2011-05-15
> **Hedgehog1 said:**
> We need to get a look at your install to get an idea what is going on.

Please boot off the LiveCD/LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the [noparse]```
 & 
```[/noparse] tags.

***The Hedge***

:KS
I'd love to, but it wont go past the first screen on boot-up, so it wont even load the disk. Even the first screen is frozen so i can't mess with the boot up. The computer is a Veriton V1000 that was running Ubuntu. [http://support.acer.com/acerpanam/desktop/0000/Acer/Veriton1000/Veriton1000sp2.shtml](http://support.acer.com/acerpanam/desktop/0000/Acer/Veriton1000/Veriton1000sp2.shtml)
Thats a link for the specifications.

---

### Post by Hedgehog1 on 2011-05-15
> **Marfish said:**
> I'd love to, but it wont go past the first screen on boot-up, so it wont even load the disk.

Frankly, I was half expecting you would say this.

If you cannot even run/load the LiveCD consistently, you are facing some issues.  I suspect that there were 'issues' on the system that forced your dad to replace it - and any hardware issues that caused Windows to act up will also interfere with Ubuntu running on it.

Perhaps you should look for other hardware?

***The Hedge***

:KS

---

### Post by Rubi1200 on 2011-05-15
I recommend you download and burn to CD a distro called Slax:
[http://distrowatch.com/table.php?distribution=slax](http://distrowatch.com/table.php?distribution=slax)

If you are able to boot the computer with it, report back and we can then give you further instructions.

---

### Post by Duncan Williams on 2011-05-15
**double check** all bios settings...
inc: aperture , S.M.A.R.T hard drive.
try it at default/failsafe

---

