---
title: "improving boot time and bootsplash appearance"
date: 2010-07-13
forum: General Help
---

### Post by lecterror on 2010-07-13
Hi everyone!

I have Ubuntu 10.04 installed and although I had some problems initially, everything works fine now. I'm just bragging about that. :p ;)

I do have some strange "issues" with my boot.

I know that Ubuntu is supposed to boot with only plymouth visible, but before I see plymouth I have a fairly long period of time when I see nothing but a console cursor (a.k.a. caret) blinking. I'm no expert in reading bootchart charts, so I'm attaching it for some feedback. I have no idea how and what to optimize. My boot is ~40 secs as noted on the bootchart, but it would be nice to cut some fat if possible.:rolleyes:

Also, my StartUp-Manager is displaying some veeery long boot options. It doesn't look nice. I guess he's reading /boot/grub/grub.cfg but I don't think I'm supposed to see all that.

Last but not least, no matter what I do in StartUp-Manager, my boot and shutdown screens are very low res and very ugly, often flickering on updates. I have 10.04 setup at work as a web test platform on a very old/crappy PC (Intel GFX) and bootsplash looks much nicer than on my home laptop.

Any tips would help. Thanks in advance!

---

### Post by krishnandu.sarkar on 2010-07-13
For the boot screen logo resolution problem refer to this : [http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

And ya remember to replace the resolution mentioned there with you monitor's native resolution.

Your start-up manager is showing everything perfect. We all also see all these.

---

### Post by libssd on 2010-07-13
By default grub (legacy or grub2) has a 10 second delay. You can edit the config file to use a lower number; I find 2 seconds still gives me plenty of time to hit the shift key and bring up the grub menu, if I feel a need. Don't forget to run sudo update-grub after making config changes.

---

### Post by lecterror on 2010-07-13
@krishnandu.sarkar: Damn, that was fast :) That actually did the trick, I finally have a nice bootsplash. Too bad about the long lines/options in SU-M, it really doesn't look nice.. :-&

@libssd: Do you mean the GRUB_TIMEOUT in /etc/default/grub? It is already set to 2, I'm guessing that shouldn't be a problem. Or did you mean something else?

---

### Post by krishnandu.sarkar on 2010-07-14
Well...Uncheck the box which says "Show Text During Boot"

---

### Post by lecterror on 2010-07-14
No, I'm afraid that's not it.

I don't actually see any *text*, I just see the cursor blinking for a while before the bootsplash appears.

Still, I've unchecked the option just in case and it had no effect :-(

---

