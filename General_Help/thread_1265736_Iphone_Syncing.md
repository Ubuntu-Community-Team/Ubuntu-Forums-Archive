---
title: "Iphone Syncing"
date: 2009-09-13
forum: General Help
---

### Post by HalfCrackedTech on 2009-09-13
Is there a way that I can sync my Iphone with ubuntu?

I am looing to get rid of my windows Partition and this is the only thing that I need Windows for.  If anyone can help me that would be greatly appreciated.

---

### Post by thegreatsnafu on 2009-09-13
Hi,

Currently, you can only sync music to your iPhone using Linux. Video, and App syncing are not supported at this time, sorry... :(

---

### Post by HalfCrackedTech on 2009-09-13
Well we all need to get on that> LOL

---

### Post by thegreatsnafu on 2009-09-13
Indeed

---

### Post by miatawnt2b on 2009-09-16
actually, if your iphone is jailbroken, you can scp the var/mobile/Library folder which contains all of your contacts, calendar events, notes, pics, etc. If you have to restore, you can do so, re-jailbreak and scp the various pieces back in.

-J

---

### Post by R_U_Q_R_U on 2009-09-17
But that does not allow to use the APP Store or manage apps, right?

---

### Post by PureLoneWolf on 2009-09-17
I use XP inside a VirtualBox PUEL installation and have no problems at all passing iPhones through..I have dealt with all of them, including the 3GS.

Maybe that could do it..you could use a minimal installation of XP and therefore recover most of your diskspace currently in use by the windows partition.

---

### Post by miatawnt2b on 2009-09-17
> **R_U_Q_R_U said:**
> But that does not allow to use the APP Store or manage apps, right?


Of course.

---

### Post by raymondh on 2009-09-17
> **purelonewolf said:**
> i use xp inside a virtualbox puel installation and have no problems at all passing iphones through..i have dealt with all of them, including the 3gs.

Maybe that could do it..you could use a minimal installation of xp and therefore recover most of your diskspace currently in use by the windows partition.

+1

---

### Post by miatawnt2b on 2009-09-17
> **PureLoneWolf said:**
> I use XP inside a VirtualBox PUEL installation and have no problems at all passing iPhones through..I have dealt with all of them, including the 3GS.

Maybe that could do it..you could use a minimal installation of XP and therefore recover most of your diskspace currently in use by the windows partition.

This also works. iTunes is the only way to sync AppStore apps and get music on the iPhone with FW 3.0+

---

### Post by steev182 on 2009-09-18
With the VirtualBox method, what are you doing to get your media into windows? An SMB Share? Also, what do you use to batch encode divx files to m4v?

---

### Post by PureLoneWolf on 2009-09-19
> **steev182 said:**
> With the VirtualBox method, what are you doing to get your media into windows? An SMB Share? Also, what do you use to batch encode divx files to m4v?

I access my music collection directly over Samba shares.  I have videora on my windows installation...and then itunes

---

### Post by Papiertiger on 2009-09-19
> **miatawnt2b said:**
> actually, if your iphone is jailbroken, you can scp the var/mobile/Library folder which contains all of your contacts, calendar events, notes, pics, etc. If you have to restore, you can do so, re-jailbreak and scp the various pieces back in.

-J

For pim data you can also sync with thunderbird\lightning or kontact using funambol. I wrote a howto and added it to [https://help.ubuntu.com/community/PortableDevices/iPhone/#Syncing contacts calendar notes]("https://help.ubuntu.com/community/PortableDevices/iPhone/#Syncing contacts calendar notes")

---

