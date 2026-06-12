---
title: "Can't boot past GNU GRUB (Pretty sure I'm screwed)"
date: 2010-03-21
forum: General Help
---

### Post by An Exile on 2010-03-21
Okay; this isn't the end of the world, though it does make it more difficult; but I'm quite sure that I messed this up royally. I'd be happy if I could just get my files back without having to go through the myriad back-up locales I've used.

I managed to download and install Ubuntu using the Wubi installer. It didn't work the first time, but the second time all went well. I entered Ubuntu and began to migrate my files from Windows to Ubuntu (documents, pictures, etc).

Then the update began downloading. Things got a bit choppy and I learned that after a moment or two of no activity the screen would go dark but the monitor hadn't gone to sleep, simply moving the mouse or clicking would reactivate it. I was in the middle of finishing up the migration when everything froze. I mean everything. I waited for ten minutes without any response. Here I think I made my first mistake. I manually shut down the computer, and rebooted to Ubuntu. However, I couldn't get past the log-in screen. I perhaps should have waited longer. My second (or first) mistake was to run Linux recovery at boot instead of coming here and asking what to do.

Now here's where I think the crap really hit the fan. The recovery worked alright, I suppose, though I can't be a good judge as I'm not code-literate, especially not in Linux. However, once it finished, I read the script and saw "reboot is necessary" or something to that effect. So, with a foolish thoughtlessness I can't really comprehend, I manually shut down the computer again (though I'm not totally sure I am at fault for that - for all I know, Linux recovery is meant to bring up GRUB; but I'm going with "Me=Fail" for the moment.).

Now when I try to boot Ubuntu, I get to this screen: GNU GRUB Version 1.97beta. There is additional text about how TAB reveals commands and such. Exploration of the commands has not revealed anything helpful right off. Any help in getting back onto Ubuntu, or will I need to suck it up and reinstall from Windows and bring back the files from their back-up positions?

---

### Post by soltanis on 2010-03-21
Sounds like you had a kernel crash and GRUB never was properly installed.

When you get to GRUB, try this:
```

rootnoverify (hd0,0)
makeactive
chainloader +1
boot

```

Does that get you into Windows? Also, how many hard disks do you have, and do you remember where Ubuntu said it was installed?

---

### Post by An Exile on 2010-03-21
> **soltanis said:**
> Does that get you into Windows? Also, how many hard disks do you have, and do you remember where Ubuntu said it was installed?

As far as I know, I have only one. Ubuntu is actually installed on the C: disk in Windows, I hadn't actually gotten to the point of seeing if I could partition the disk between them.; that's how I can get into Windows, but not into Ubuntu.

---

### Post by raymondh on 2010-03-21
Is this a wubi install or is ubuntu installed in its' own partition?  

If WUBI.... the [wubiguide]("https://wiki.ubuntu.com/WubiGuide")

Am glad to know you have a back-up of your files :)

---

