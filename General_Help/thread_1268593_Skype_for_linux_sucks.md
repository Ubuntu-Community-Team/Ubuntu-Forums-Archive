---
title: "Skype for linux sucks?"
date: 2009-09-17
forum: General Help
---

### Post by valikor on 2009-09-17
I'm coming to the conclusion that Skype for linux sucks.

I used 2.0 for a few weeks. In most calls, after between 30 seconds and 5 minutes, my audio would cut out and I became unable to hear the other party. Sometimes it would come back on if I changed audio output from PULSE to HDA Intel MID (hw:MID,0).

But, if I started a call using these latter settings, it never worked.

They then released 2.1 beta, which initially solved this problem and it worked perfectly... for like 1 day. After this, I became unable to make any calls, since it stopped recording audio input (though sometimes it would record what sounded like a nuclear bomb)

By the way, my audio input settings were perfectly fine and could record in other programs flawlessly.

It also crashes all the time.

I'm basically ready to not use skype anymore, since they don't seem to care about their linux release. And seeing as how I just moved to the other side of the world, I need something that works consistently in order to stay in touch.

So, does anyone have any recommendations as to the best alternatives? (Or, miraculously, has anyone gotten skype to work well with ubuntu on a dell mini 12?)

Thanks in advance,

David

---

### Post by cmay on 2009-09-17
I had skype working perfect on an asus eeepc and I had to sell that because it was simply too small. I used skype almost everyday and when I got my new laptop I experienced the exact same problems as you describe. I created a thread in a other forum and the conclusion I came to was to file a bug report as It had most likely something to do with hardware.

---

### Post by khelben1979 on 2009-09-17
I would recommend you to [download Skype static version]("http://www.skype.com/intl/en-gb/download/skype/linux/choose/") to see if it works better.

You don't need to uninstall the current version which you have installed.

---

### Post by nikgare on 2009-09-17
Skype works really well here - I'm using the lastest version: 2.1.0.47

---

### Post by P4man on 2009-09-17
> **valikor said:**
> I'm coming to the conclusion that Skype for linux sucks.

I used 2.0 for a few weeks.

Then you may have downloaded it just days before the new (beta) came out. finally, 2 years after the previous release (!), native support for pulseaudio. You might want to give it another try, it works pretty well for me now.

---

### Post by shae on 2009-09-17
Have you considered disabling pulse audio?  I think that is the root of the problems with the 2.0 version and the fact that the 2.1 is a beta is probably cause for concern.

---

### Post by xx58 on 2009-09-18
:rolleyes:Never had any problems with Skype. Use only stable version and when Beta version become stable, then install it. BETA VERSION is beta VERSION AND DON'T FORGET that.

---

### Post by svaens on 2009-10-12
Hi all, 

I'm using the skype beta "2.1.0.47"

I have noticed that when i connect to a call, sometimes (i don't yet know when or why) immediately the mic input goes crazy with static in one of the 2 channels, and in the other , only silence. 
Othertimes, it works great. 
It happens as soon as the connection occurs, and not during the dial tone. 
I can see this using the pulse audio device chooser. 

Anyone also had this?

p.s. I would report this to skype, but i can't find where to do so, or if they accept public bug reports..

---

### Post by Ordes on 2009-10-12
yeah the last one really did suck in ubu 9.04... tried a lot of things to get the lag less.. but was never really stable...

however i am more than satisfied with the new beta release. 
[http://www.skype.com/download/skype/linux/](http://www.skype.com/download/skype/linux/)

no lag, good quality call, good video, running it with pulse audio.

---

### Post by dodle on 2009-10-12
I've got Jaunty's repository version installed and it has worked flawlessly for me.  The package is called skype-mid and says it's version 3.0.0.93.  Is that what everyone else is using?  What I do find annoying about it is that I cannot minimize it to the notification area & if skype is running I cannot shut down my machine.  I have to go into skype's options menu and close it from there, then I can shut down my compter.  

It does suck that the Linux version is so far behind the MacOS version and even further behind the Windows version.  But I think that Linux becomes more popular every day, and soon these companies will see that Linux ports of their software are just as profitable.

**Edit:** Do I understand this correctly, The equivalent to Skype 4.1 for Windows would be Skype 4.1 for Linux?  Or is Skype 2.1 for Linux pretty much the same as 4.1 for Windows and 2.8 for Mac?

---

