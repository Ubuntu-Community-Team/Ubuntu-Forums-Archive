---
title: "grub problem after installing to external hard drive"
date: 2011-03-19
forum: General Help
---

### Post by justjoe86 on 2011-03-19
Hello. I'd be really grateful if you could help me with my problem...

I recently found an ubuntu 9.10 disk lying around and since it was a rainy day i decided to try installing it to my external hard drive. Not sure what my thinking was behind this other than seeing what happened...

Anyway, I used my laptop which I use for work (and only had windows 7 on it) and installed to the external hard drive. It works fine - and can boot into windows OR ubuntu using grub.. 

HOWEVER, if the external hard drive isn't plugged in, i can't run windows, because the computer says it can't find grub. On top of this, it seems that both ubuntu and windows 7 start up and run slower now - something to do with the hard drive i guess.

So - I'm not sure what to do... I've tried booting up with an ubuntu cd and reinstalling to the main hard drive - but this doesn't work because a) i can't boot from a cd now unless the externall hd is plugged in, and b) if i boot from the cd with the external hd in, i can only install ubuntu onto the entire hard drive, wiping everything off it.

Please help!

Ideally what I'd like to do is rewind to the time when I had only windows on the computer, and then add ubuntu to the hard drive on a partition, but I can't see how to do it.

Thanks in advance, and please note, while I'm ok with both ubuntu and windows, and have experience using the terminal, i'm no expert so feel free to talk to me like a retarded child when it comes to offering instructions!

And one more thing - I completely respect all ubuntu purists, and would love to be one myself, but please don't advise me to forget windows altogether, as unfortunately I need it for work!

---

### Post by mikewhatever on 2011-03-19
When installing to an external hdd, you need to modify the default grub location and install grub to the MBR of the external hdd. So now, what you have to do is reinstall the Windows bootloader (however it's done in W7), then reinstall Grub from the live CD/USB and make sure it goes to the MBR of the external hdd.

---

