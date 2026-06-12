---
title: "Major Problems !"
date: 2009-10-21
forum: General Help
---

### Post by mrgreene on 2009-10-21
I just loaded Ubuntu 7.10 and it upgraded itself to 8.04 when completed, am now having problems viewing ANY type of web video content (Youtube, Redtube, etc). Also I would like toload and use Frostwire, but i cannot locate it in the system. Anyone to help? My chat IMs are open - th3Xfagtr (AIM) lostintranslation_again (Yahoo)

---

### Post by river226 on 2009-10-21
have you reinstalled the drivers/software, i know it shouldn't be that, but can't hurt to try

---

### Post by gjoellee on 2009-10-21
I would recommend upgrading to a even newer version of Ubuntu. I am talking about 9.04 or 9.10. Those versions seem to have a better flash and driver support.

---

### Post by jward3010 on 2009-10-21
First of all, Ubuntu will never update itself to the latest version without YOU doing it. You will be told in Update Manager that there's a new version available and you click install to initiate the process. 

What a version upgrade does in the process of installing is get rid of all user-added and non-standard repositories such as the ones you would have had to enable to get flash-player including the software thats not relevant to the install and all proprietary software like flash, MP3, WMA etc support, Adobe Reader, Google Earth etc. will be removed. Simply install the Medibuntu repository ([www.medibuntu.org](www.medibuntu.org) - it's a single command to copy and paste) or even in Software Sources (System > Administration > Software Sources) enable the universe repository and retry installation:
```
sudo apt-get install flashplayer-nonfree
```

Best one to really do is "Ubuntu-restricted-extras" package. That will sort out basically everything for you - flash player, MP3, WMA, WMV, MOV, DIVX, AVI support, the works.
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by jward3010 on 2009-10-21
> **mrgreene said:**
> My chat IMs are open - th3Xfagtr (AIM) lostintranslation_again (Yahoo)
The whole point in forums is where you can talk about problems in public and the whole discussion is seen. As much as possible discuss problems without IM, for the sake of everyone. It really helps create an open list of problems dealt with or in progress.

---

### Post by mrgreene on 2009-10-21
tried that already, am going to try to update the version and see what happens. thanks
> **river226 said:**
> have you reinstalled the drivers/software, i know it shouldn't be that, but can't hurt to try

---

