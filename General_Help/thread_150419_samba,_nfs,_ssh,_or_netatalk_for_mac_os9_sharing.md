---
title: "samba, nfs, ssh, or netatalk for mac os9 sharing?"
date: 2006-03-26
forum: General Help
---

### Post by wanger123 on 2006-03-26
Ok, I've done the search thing but I'm still stuck. I need to retrieve files from a networked mac os9 computer. 

I know the IP address, name and password for the remote computer but how do I see it? 

I have tried installing and configuring samba, smb4k, netatalk etc etc but I just cant seem to connect to or even see the mac. 

I have set up file sharing on both kubuntu (although I dont really want to share anything from linux) and the mac with os9. I also cant see my computer from the mac (chooser --> network .........). Everyone else has no problem sharing with the mac os9 computer with their mac osx powerbooks using appletalk.

Please help, they are ridiculing me and linux in general.:confused: 

cheers
wanger[COLOR="black"][/COLOR][COLOR="Green"][/COLOR][COLOR="Green"][/COLOR][COLOR="green"][/COLOR][COLOR="green"][/COLOR][COLOR="green"][/COLOR]

---

### Post by Kadin2048 on 2006-03-26
Netatalk is the package that you want to install -- or rather, have installed -- to do the trick.

I think your best bet may be to set up Netatalk on the Linux machine so that it has a shared volume, and then mount that volume on the OS 9 Mac, and transfer your files that way. I think that is probably going to be easier than trying to mount an OS 9 share on the Linux machine (might not be, but I've never successfully done the latter).

There are a few caveats with Netatalk. If the network you are running it on is not secure (i.e. if you have to send packets across the internet at any time) you should be aware that the Debian and thus also Ubuntu precompiled binary version doesn't have any cryptographic support (well, it does, but the support it has doesn't work with what most Macs use). So if you want to do things securely, you'll need to build it from source using apt-get source, with the right options (I can provide you with the procedure I used and which worked for me, if you'd like).

Once you get it installed, it's just a matter of editing the /etc/netatalk/afpd.conf and AppleVolumes.default files for the volume you want to share. Then on the OS 9 machine you'd want to connect to the Linux machine by typing its IP address into the Chooser.

If you really must go the other way (Linux client to Mac file server) and can't get it working, you might want to ask the netatalk mailing list. I've found them pretty helpful in the past.

---

### Post by wanger123 on 2006-03-27
Hi Kadin, thanks very much for the detailed reply. Today I managed to network to an OS X iMAC in the lab via smb, and I can send and receive files. I guess for the short term I will appletalk between the os 9 and os X machines and then retrieve my files from the os X machine via samba. I will keep trying to configure netatalk as per your instructions. I think you are right about os9, I don't think it is possible to mount it (via smb anyway) on my linux box.

thanks again

wanger

---

### Post by wanger123 on 2006-03-29
SUCCESS!!!!!! YEE HAA!!!

A big thanks again to Kadin2048. I uninstalled, then reinstalled netatalk, setup my /etc/netatalk/afpd.conf and AppleVolumes.default files and the next thing you know, I was a local host on the Apple Talk network! Now I can network with OS9 via netatalk, and OSX via Samba (or netatalk I suspect - haven't tried yet).

Another problem off the list :mrgreen: 

wanger

---

