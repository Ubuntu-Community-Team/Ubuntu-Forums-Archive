---
title: "Another Wireless Issue (mac in deep sleep)"
date: 2010-09-21
forum: General Help
---

### Post by jokerj9 on 2010-09-21
First off, I have a Gateway c-140 tablet running 10.04 lucid and an Intel iwl3954 wireless card.

I have been having issues since installing Ubuntu with the wireless; I've looked around for answers, but nothing has worked (not even [http://ubuntuforums.org/showthread.php?t=1478523](http://ubuntuforums.org/showthread.php?t=1478523) or other solved threads).

Most of the times that I boot my computer (probably about 14/15 time) I see a flash of the error "...Mac is in deep sleep...".  After that, my internet connections just do not work.  In the network manager, if I right click it, the only option it has is VP whereas when the connections work, it has wireless and wired connections.  When I get lucky and reboot to find that my wireless works, I have no issues.  Also, most likely related, when my wireless is working and then I put the computer to sleep by shutting the lid, the wireless will not work when I awake it.

Thanks in advance for the help, and I will try to keep checking back so that the problem can be troubleshooted quickly.

-jokerj9

---

### Post by WanabeTux on 2010-09-21
I am running a Sony Vaio with iwl3945 as well. I had some sporadic issues with my wireless as well. I ran across this thread and it shed some light on the subject.

[http://en.gentoo-wiki.com/wiki/Iwlwifi](http://en.gentoo-wiki.com/wiki/Iwlwifi)

Pretty much I went to Synaptic package manager and reinstalled CRDA then I downloaded the iwlwifi-3945-ucode-15.32.2.9.tgz file and extracted it and followed the install instructions from the read me file that came with it. Copied the iwlwifi-3945-2.ucode file into /lib/firmware.

That was it, no problems since. Hope this helps.

---

### Post by jokerj9 on 2010-09-22
Thanks for the response.

I just tried doing what you suggested, but I had some hangups configuring the kernel as specified in the readme file that came with the tar file.  Still, I copied the ucode file into the /lib/firmware so I will see if anything is different.

Thanks again, and I will post later today with the outcome.

-jokerj9

---

### Post by jokerj9 on 2010-09-22
Unfortunately, the problem happened again.  Any suggestions?

Thanks in advance,

Jokerj9

---

### Post by WanabeTux on 2010-09-23
Yes, I had to follow the thread below to disable ivp6. 

[http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html](http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html)

And that was it. All I had to do with the iwlwifi package is have the archive tool extract it . Then I opened Nautilus up in root, sudo nautilus in the terminal. Go to the extracted iwl3945-2 ucode file and copy it then go to lib/firmware folder paste it. It will ask you if you want to overwrite file, click yes and your done. You can do it in the terminal too, by following the read me file. I got 22 years of Windows in me I'm trying to get out ! Right click, copy, paste. ](*,)

---

### Post by WanabeTux on 2010-09-23
Some more info that might be helpful. The CRDA version is 1.12 according to synaptic package manager. And I got iwlwifi-3945-ucode-15.32.2.9.tgz from here.

[http://www.intellinuxwireless.org/?n=Downloads](http://www.intellinuxwireless.org/?n=Downloads)

---

### Post by jokerj9 on 2010-09-24
Thanks again for the reply.  The problem still isn't resolved, but now it only happens about half of the time.  This is good enough for me.

-Jokerj9

---

