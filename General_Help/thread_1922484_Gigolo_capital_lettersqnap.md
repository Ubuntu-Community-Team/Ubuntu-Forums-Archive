---
title: "Gigolo capital letters/qnap"
date: 2012-02-08
forum: General Help
---

### Post by sleepyhollows on 2012-02-08
So Im trying to connect my xubuntu to qnap, using SMB

I create the gigolo bookmark, server "my-qnap", share "Public"

Public is fully open and requires no auth.

gigolo pops up asking me for auth.

Long story short, I cant connect. Console output of gigolo says "Can't connect to \\my-qnap\public"

It made the share lowercase!!

So sad :( lol

Any ideas?

Edit sorry I think this is a bug report hey. Not time right now :)

Actually can someone just delete this post. Its working now. 

Maybe by 2020 the cifs interface will be ironed out :)

Back in 1995, if you connected to a windows share and the windows machine was subsequently shutdown, the linux box would hang trying to remove the mount, and youd have to reboot linux. (Which back then was considered "the no need to reboot OS")

I digress.

---

### Post by ytene on 2012-03-06
Actually, your message is very topical. 

I've just bought a TS-459 Pro II to replace an existing Apple Time Capsule that was getting full and sounding terminally sick all at the same time...

For the TC, I was able to use a cifs mount and got everything to work effortlessly, with the ability to read and write data. 

For the QNAP, I tried to do exactly the same thing and at first it *seemed* to work. Then, as I was moving data from the TC to the QNAP, I got a total of 4 complete ubuntu system hangs in one day, on a machine (11.10, 64-bit ubuntu with KDE on top) that hasn't hung on me in *years*...

I reboot the same hardware running a 64-bit edition of Windows 7 (I have my bootable drives in removable caddy units) and everything worked perfectly and I was able to move about 650Gb  of data from the TC to the NAS without an issue.

I chatted with colleagues who have QNAP gear and they advised me to replace my CIFS connectivity with NFS, arguing that since the QNAP uses embedded Linux as it's OS, it would likely be more reliable that way... So I did... I pulled in nfs-common and portmap packages, experimented a little until I got both a command line and fstab format of a mount statement that would work, and gave it a go. 

I see, reliably, exactly the same failures as I did under CIFS. 

A big chunk of the 650Gb data I've moved to the QNAP is my iTunes library (I convert my CDs using AC4, it's not as compact as MP3) but with ubuntu I play this content using Rhythmbox. Since I'd moved the content, I needed to re-index my Rhythbox content. I deleted the relevant data structure from /home/{user}/.local/share/rhythmbox and re-launched. Pointed the app at the data via the new NFS mount. 

It managed to import 192 albums before crashing, *exactly* the same as the CIFS model. In both cases my ubuntu machine suffers a complete hang - even the mouse pointer freezes - and the only fix is the hardware reset switch. I don't get this under Windows 7, or under ubuntu if I use CIFS to my Time Capsule.

Over the weekend I patched the QNAP to the latest edition of it's firmware (3.6.1) and I'm running a fully patched 11.10/64-bit. 

I've never known something kill ubuntu so completely and utterly dead before. Figuring it was likely to be a kernel panic I checked /var/log but I can't find anything particularly unusual in any of the traditional log files. 

There's no appreciable degradation in performance, and I tried re-running this with a graphical system monitor running, watching CPU, Memory and Network traffic. Nothing. CPU is normal, memory (8Gb) doesn't even need swap space, and the network is showing the kind of bursty traffic you'd expect given the indexing that I'd asked for... 

I can surf the web and pull down large files without apparent problem, so I am suspecting it must be something in the protocol handshakes used with the QNAP. 

Does anyone know if there is common code shared by both CIFS *and* NFS? Can anyone suggest somewhere I can trawl or tail a log file to look for events? 

Perhaps most importantly of all, has anyone managed to get a reliably working connection to a QNAP TS-459 Pro II yet please? 

I am going to ask on the QNAP forums and will share any answers or fixes I get... 

Best

C

---

