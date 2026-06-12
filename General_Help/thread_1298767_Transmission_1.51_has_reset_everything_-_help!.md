---
title: "Transmission 1.51 has reset everything - help!"
date: 2009-10-23
forum: General Help
---

### Post by sirsmegalot105 on 2009-10-23
Hey,

OK to cut a long story short, I was using VirtualBoxOSE and for some reason it filled up my entire Home drive (Ubuntu 9.04) which is the drive that Transmission 1.51 uses. It was down/uping at the time so I can only assume that this is the cause of my problems

Basically I had everything going into a folder called BT Downloads, hundreds of things that I was seeding etc. When I open up Transmission now, it seems to have completely reset it self - all the torrents are sitting at 0% (as if they are brand new), port number and other options have reverted back to default etc AND all torrents are also appearing on my desktop, which is default for Transmission upon installation.

The good thing is that it appears everything physically there that was up/downing is still there (the files). I have a few questions though, your advice would be appreciated so I can start seeding again:

1) If I change the download location back to the original one, will that fix this or will it effectively wipe out my completed torrents (since everything has reverted back to 0% and is using Desktop to download to)

2) Any other way I can resolve this issue, such as maybe importing my torrents in to another Linux BT client or something (or even just fixing Transmission?).

3) Will this permanently stop me from seeding back items which I have downloaded or is there a way to get Transmission back to how it was and keep the consistency.

Again I appreciate the help, scared to open Transmission here in case it does more damage :-(

---

### Post by lovinglinux on 2009-10-23
> **sirsmegalot105 said:**
> The good thing is that it appears everything physically there that was up/downing is still there (the files). I have a few questions though, your advice would be appreciated so I can start seeding again:

1) If I change the download location back to the original one, will that fix this or will it effectively wipe out my completed torrents (since everything has reverted back to 0% and is using Desktop to download to)

I theory you just need to change the destination folder and do a re-check. Transmission should be capable of checking if the files have been already downloaded. Nevertheless,  I would copy some files already downloaded to a third location, then change the destination directory in Transmission to use that directory, just to check if it will overwrite the destination files or simply do a re-check. Just to be safe. If you have enough space, you could also move all downloaded files to the current destination directory, then do a re-check, then move them back to the new destination folder.

> **sirsmegalot105 said:**
> 2) Any other way I can resolve this issue, such as maybe importing my torrents in to another Linux BT client or something (or even just fixing Transmission?.

In fact, this is a good opportunity to try other BitTorrent clients. I personally recommend Deluge or Ktorrent. Setup the new client to save the content were you have the completed files, then add the .torrents to the new client. It will check if the files already downloaded and will start seeding them. Take a look at the [BitTorrent optimization and troubleshooting guide](http://ubuntuforums.org/showthread.php?t=1259923) for tips on how to configure Deluge.

Either way, your seeding ratio will be reset. So all torrents will be counted as 100% downloaded, but they will appear as if you didn't uploaded anything.

> **sirsmegalot105 said:**
> 3) Will this permanently stop me from seeding back items which I have downloaded or is there a way to get Transmission back to how it was and keep the consistency.

In fact is the opposite, as already explained above. Transmission will consider that you haven't uploaded anything, so it will seed all torrents by default. Anyway, you can always override that manually.

---

### Post by sirsmegalot105 on 2009-10-23
Thank you very much for that you have been a big help. I took your advice and got Deluge, it is a lot better than Transmission. My torrents are now re-hashing like you said :popcorn:

Yeah so cheers for the good advice, and slightly OT I know but what would you consider a minimum ratio to be on public or private trackers, 1.1 or something before you can stop seeding?

---

### Post by lovinglinux on 2009-10-23
> **sirsmegalot105 said:**
> Thank you very much for that you have been a big help. I took your advice and got Deluge, it is a lot better than Transmission. My torrents are now re-hashing like you said :popcorn:

Yeah so cheers for the good advice, and slightly OT I know but what would you consider a minimum ratio to be on public or private trackers, 1.1 or something before you can stop seeding?

You are welcome.

The recommended minimum seed ratio 1:1, but on private trackers it might be higher, otherwise you won't get great download speeds. I never used a private tracker tho.

---

