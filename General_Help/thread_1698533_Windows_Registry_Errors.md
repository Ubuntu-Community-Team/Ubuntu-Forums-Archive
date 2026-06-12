---
title: "Windows Registry Errors"
date: 2011-03-02
forum: General Help
---

### Post by JCollierDavis on 2011-03-02
Question:
What caused my registry to get corrupt immediately on a brand new install and how do I prevent it?

Discussion:
My Mom's computer wouldn't boot the other day so I'm drafted to help her get it back running.  She received this error:
Missing or Corrupt Registry
Windows\System32\config\system
0xc00000000f
(not copied exactly)
I booted to my live USB, copied her files onto a backup, ran clamscan and the long smartctl test.  Some SMART tests came back with errors and her HDD was making some noise so I got a new one, re-installed Vista and everything's good. I copied back all 3 Gb of her user data to a folder in her My Documents and turned the machine off.

Later I come back to show her where everything is and to my amazement the same registry error appears again. What happened?

I've read instructions [(Ubuntu Forums)]("http://ubuntuforums.org/showthread.php?t=624943") on simply copying backup registry files from:
Windows\System32\config\RegBak
into
Windows\System32\config\
I'm relatively comfortable that will fix it at least in the meantime.
Since it’s basically a brand new install, there’s shouldn't be much difference between the two, right? I’m most curious to find out what happened to mess it up the second time.

---

### Post by dandnsmith on 2011-03-02
Googling for that error number led me to [this site answer](http://taw.net/forums/p/47445/106665.aspx), but is doesn't sound entirely commensurate with the registry error you report.

Nevertheless I'd try the repair from the CD if it is available in Vista (haven't gone beyond XP for this sort of stuff, myself)

---

### Post by HermanAB on 2011-03-02
Hmm, the same problem?

a. The anti-virus could do it, if you are using the same anti-virus, so switch to a different one, eg ClamWin. (Lots of inexplicable Windows problems are caused by anti-virus programs).
b. The power supply may be causing spikes and processor errors. (If you have a spare PSU lying in your junk box, try it, or simply go and buy a new one, they don't cost much).
c. The motherboard may have worn-out capacitors causing power spikes and processing errors. (Look at the MB and see whether *any* capacitors (they look like little batteries and they pretty much are little batteries) are distended or spouting brown goop.  If so, then your Mom needs a new PC).

---

### Post by Mark Phelps on 2011-03-02
My guess is that it's malware of some sort.  Why?

Because the initial reinstall worked fine.  If there was a hardware problem, that would not have happened, or you would have started receiving errors shortly after install.

Then, you restored the user files -- from a location that is often used to hide malware.

And then, and only then, you started getting the failure.

My suggestion would be to do the following:
1) Reformat the partition and reinstall Vista -- again
2) Do NOT restore any user files just yet
3) Run Windows Update until no more updates are being offered
4) This is if you have an external drive or other partition you can use to image off the OS ...  download and install the free version of Macrium Reflect.  Launch MR and use it to image off the current Vista OS install. Also use the option to create and burn a rescue CD. This will allow you to quickly recover if infection happens again.
5) Google for and download MalwareBytes Anti-malware (MBAM) and SuperAntiSpyware.
6) Go to the Kaspersky website, download and burn the Free AV Rescue CD (v 10).
7) NOW, restore the user files
8) As soon as that is done, run MBAM and SuperAntiSpyware.
9) If they won't run, boot from the Kasperky CD, allow it to do the needed definition update, and run it.

Hopefully, one or more of the three will find something and remove it.

---

### Post by JCollierDavis on 2011-03-03
I never did get the thing to boot right.  
I’m think that it is a hardware issue.  Dell’s diagnostic CD found error 6600:0219 Which I googled and believe it has something to do with the webcam/usb.  

I advised re-installing Vista, the ATI and network drivers and keeping the user data on the backup for a while to see if that’s what corrupted anything.  I also recommended MS Security Essentials. 

In any case, a 5 year old inexpensive computer isn’t worth many hours of work when a new one is also so inexpensive.
Thanks for the help everyone.

---

