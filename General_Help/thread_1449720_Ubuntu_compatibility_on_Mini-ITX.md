---
title: "Ubuntu compatibility on Mini-ITX"
date: 2010-04-08
forum: General Help
---

### Post by Dev.propicee on 2010-04-08
Hello all,

I am a newbie to Ubuntu forum and in my welcome post i am here to ask for your help guys :). 

I am currently using a Mini-itx (by VIA technology)system and I was wondering whether I can use Ubuntu for custom build mini-itx server. Also, want to know whether there is **any mini/portable version of Ubuntu available to run it from a flash/USB on Mini-itx ?** I am using VIA EDEN EBGA processor with Integrated VIA UniChrome pro AGP Graphics and  VIA CN400 North Bridge Chipset. 

Thanks for your help and look forward to finding some good answers for this question.

Regards.

---

### Post by mcduck on 2010-04-08
Ubuntu will work on any x86-compatible platform, the size doesn't matter. :D

So your motherboard and CPU are just fine, the only thing that might be a problem is the Via Unichrome graphics card, I'm not sure what's the situation with Via graphics drivers on Linux but you might not get too good performance from them. But since you were talking about a server, poor 3D-acceleration probably is not a problem.. :)

The normal Ubuntu CD functions as a live environment, and you can also use tools like unetbootin to turn the CD image it into a bootable USB drive.

---

### Post by Mighty_Joe on 2010-04-08
I run full Ubuntu Server 8.04 on a [VIA C3]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813153045").  See my posts [in this topic ]("http://ubuntuforums.org/showthread.php?t=1244304") for details.  
If I were running from flash, I'd opt for a full install rather than the "live flash" installs mcduck mentions.  I have a full install on an 8GB flash drive that's been pretty solid.  I posted links in [this topic]("http://ubuntuforums.org/showthread.php?t=1193680") to the procedure I used.  It includes optimizations to improve performance and reduce wear and tear (though it's not tailored to the Server edition).

---

### Post by 3rdalbum on 2010-04-08
I wouldn't recommend installing onto a flash drive. My Mini-ITX server ran off a flash drive for a few months; I did all I could to limit writes to the drive, but in the end the flash media completely failed. I don't know if it was just a faulty drive, or if running an operating system from the drive was a bad idea.

+1 about "You won't get good graphics capabilities from this". You won't be able to run Compiz on VIA graphics. But you'll be able to run a fine server with GUI (or without, it's up to you).

---

