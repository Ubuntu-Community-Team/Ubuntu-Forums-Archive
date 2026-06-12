---
title: "Will ubuntu install see current bootable partitions?"
date: 2009-11-22
forum: General Help
---

### Post by nickapalooza on 2009-11-22
The drive started out with XP 32bit, then Vista 32bit, now Win 7 64bit. The boot loader of MS's will boot all three operating systems without a hitch.

If I do the "Install Ubuntu inside Windows" installation, will it give me a boot loader with all of the current partitions as well as it's own?

---

### Post by wilee-nilee on 2009-11-22
> **nickapalooza said:**
> The drive started out with XP 32bit, then Vista 32bit, now Win 7 64bit. The boot loader of MS's will boot all three operating systems without a hitch.

If I do the "Install Ubuntu inside Windows" installation, will it give me a boot loader with all of the current partitions as well as it's own?

I am always hesitant to answer 1st posts since there are known groups that love to make 1st posts with weird problems, that are not legitimate.

If you do a wubi install in the last windows install you should be okay, but get other confirmation of this before acting.

---

### Post by nickapalooza on 2009-11-22
Should be ok as in yes to my question, or what?

Need confirmation.

---

### Post by nickapalooza on 2009-11-23
Sorry to have to do this, but SOMEONE must know the answer. Can anyone give me a yes or no?

---

### Post by wilee-nilee on 2009-11-23
I think any of us are hesitant to give you a definitive yes being that you have 3 OS on there now, a mistake could mean a reinstall of all 3 and loss of any important data. If you have the W7 ultimate it will run XP stuff so you might consider do you need XP or Vista now.

If W7 was a upgrade for XP or Vista then once it is verified you can't use XP or Vist any more legally.

I am wondering why you would need 3 MS operating systems W7 is the best of the bunch, I have W7 on my computer.

---

### Post by nickapalooza on 2009-11-23
"If W7 was a upgrade for XP then once it is verified you can't use XP any more legally. 		                   		  		  		  		  		 		"

You've done good to confuse me so far...
I don't understand what you're trying to tell me here as well.
I have XP and W7 on two different partitions. I mentioned that.

---

### Post by wilee-nilee on 2009-11-23
> **nickapalooza said:**
> "If W7 was a upgrade for XP then once it is verified you can't use XP any more legally. 		                   		  		  		  		  		 		"

You've done good to confuse me so far...
I don't understand what you're trying to tell me here as well.
I have XP and W7 on two different partitions. I mentioned that.

Now to say yes go ahead and install with wubi inside one of 3 different MS OS is a tough call, we don't know if the W7 boot was installed in another MS OS it works this way with W7 installs, there is a 100Mib startup portion to W7 that could be installed anywhere. Again I ask why do you need 3 MS operating systems? Keeping all three makes it a get help from a professional sort of situation, basically in order to give you a yes requires a lot more information. 

You have 3 OS all with stuff in them probably that you don't want to lose, do you have, everything backed up or on a separate partition?

My other comment was that if W7 was a upgrade version for either XP or Vista then you can't use the original OS you upgraded from even if it is a fresh install in a clean partition. This is not known by some people.

I got a student upgrade for my XP so I had to do a Fresh install because I purchased the Pro version. Once I used the W7 key to verify I couldn't use XP anymore.

Last I will say I don't have enough expertise to analyze your set up to give you any better answers then I have so far.

---

### Post by louieb on 2009-11-23
A Wubi (inside widows) adds Ubuntu to the Windows boot loader. Also it does not install in its own partition. It creates a "virtual" file system inside a  widows partition.  

Another factor is the default way MS sets up multi booting - only one MS OS has a boot loader - did you just use the MS defaults when instating the 3 MS OSes?  Tech stuff:[Multibooters, Pictures here worth 1000 words]("http://www.multibooters.co.uk/multiboot.html")

If I had to give you an answer it would be - NO. When it boots you will continue to get the windows boot loader. 

This applies to a WUBI (inside windows) install only.

---

