---
title: "Bootup hangs when trying to mount NFS shares"
date: 2010-06-11
forum: General Help
---

### Post by bergamot on 2010-06-11
I have this in my /etc/fstab:
store:/linux_exe	/usr/local	nfs4	_netdev,ro,hard,bg,intr 0 0

It mounts OK on the fly (mount /usr/local) but when you reboot, it hangs, presumably forever, saying that "The disk drive /usr/local is not ready, S to skip, M for manual".

Pressing S or M does nothing. I then have to turn the machine off, boot off a CD, mount the HD's / partition and remove the fstab entry before I can successfully boot the OS.

Having looked at various forums, I have tried some different things like removing the "0 0", putting "auto" in the options. Unsurprisingly perhaps, these made no difference.

This behaviour was noticed on 10.04, but having tested it on 9.10 it does a similar thing on that version too, although on that one you can actually enter a shell at the hang point and edit your fstab.

Anyone managed to fix this or workaround it?

Thanks very much

---

### Post by prupert on 2010-06-11
I had a similar problem to you with samba shared mounted at boot. I ended up deleting all my network fstab mounts. It seems fstab is now designed for local drives only, not network drives, because of the new faster boot process. From what I can see, fstab is read before the network is enabled, thus any network drives will fail. Ironically, there is no alternative file to put your network mounted drives in as an alternative...

The only way round this, I found, was to put the mount command in your /etc/rc.local file, so it is run after boot, to mount the folders - be warned though, the command that you need to be use is slightly different when using mount, as opposed to when putting it in fstab. A simple Google search should explain what you need.

This is becoming more and more prevalent in Ubuntu. Old and well understood practices are being ignored in favour of new features (the re-purposing of fstab, moving the windows icons etc). It makes me worry that the direction Ubuntu is taking sometimes is totally the wrong one.

---

### Post by bergamot on 2010-06-11
I agree with you. As a Unix/Linux admin I expect basic things like this to work, because they are an essential part of the system I've been used to for many years.

Ubuntu has introduced many changes to the traditional ways of doing things. Perhaps the Ubuntu people feel this is necessary to make it more popular, and maybe they are right. I think as a standalone desktop system it's really very good, but I've found that when trying to integrate it into a network it throws all sorts of unexpected spanners into the works because a lot of stuff is missing from the distro or, like in this case, just doesn't work.

---

### Post by stevanbt on 2010-06-11
Hi,
I had the same problem a while back, I got round it by installing autofs ([https://help.ubuntu.com/community/Autofs]("https://help.ubuntu.com/community/Autofs")).  Basically it only mounts the remote drive when you first access it.

Thanks, Steve.

---

### Post by mushusker on 2010-07-31
[QUOTE=bergamot;9444667]
It mounts OK on the fly (mount /usr/local) but when you reboot, it hangs, presumably forever, saying that "The disk drive /usr/local is not ready, S to skip, M for manual".

Pressing S or M does nothing. I then have to turn the machine off, boot off a CD, mount the HD's / partition and remove the fstab entry before I can successfully boot the OS./QUOTE]

I noticed that none of the "letter" keys on my keyboard work, but the numeric keypad does and I can Ctrl-Alt-Del to reboot.

I had previously modified /etc/init.d/mountnfs.sh  [as described here]("http://ubuntuforums.org/showthread.php?t=951722") when I had upgraded to 9.04. I notice now that mountnfs.sh has been renamed mountnfs.sh.dpkg-old. It seems others have been having a similar problem (see Ubuntu Bug #504224). Is mountnfs no longer used in Lucid? Googling, I don't see many references to mountnfs.sh. Has it been previously deprecated in favor of something else?

I'm not really sure what do. I guess I'll switch to using autofs5, as suggested. It's just VERY disappointing that something so basic causes a box upgraded from 9.10 to 10.04 to fail so badly.

---

### Post by graemev on 2010-08-31
I have also just hit this. ... I now recall swearing NEVER to upgrade my laptop (which was running karmic sweetly) after I had it working ... too late.

So what is happening?  (I have NFS soft mounts) this used to work fine in karmic (I copied the line from the old fstab) but now I get these hangs. I am doing this on a laptop (after installing the  backport WifFi Drivers) and I get the hang. If I plug in the Ethernet cable it comes up fine. I'm assuming therefore  this is because the WiFi is not started until the desktop is up ...so the mounts need to be deferred (somehow ) until the desktop is up (or WifFi needs moving earlier) ... so this seems totally broke, there can often be situations where the mounts can't be done yet.

What are the developers thinking here? Network drives in fstab is pretty normal behavior

---

