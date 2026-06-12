---
title: "Any way to add/include folders from another PC?"
date: 2010-06-30
forum: General Help
---

### Post by sastusbulbas on 2010-06-30
Hi all,

When I had this PC upstairs with Windows I had added another location for my media and documents folders.
My main PC has a couple of TB of hard drives configured for sharing. Hence my upstairs PC when it had windows had those locations as my music and documents etc

IE if I clicked on My Documents, I had Documents C (upstairs drive) empty and Documents E (downstairs drive) would also be present and showing my documents. Though if downstairs pc was off this would not show.

How do I do such with Ubuntu?

---

### Post by pedro_orange on 2010-06-30
You'd need to mount the drive using Samba.

Presumably you're able to access it through a file explorer (Nautilus)? Then you'd just need to add the location to your /etc/fstab to have it automatically mount at boot.

---

### Post by sastusbulbas on 2010-06-30
Never done anything like this with Ubuntu, I can access the Drive/folder via network?

How in simple newbie terms do I start/run do this Samba stuff?

I did left click the selected drive/folder E and selected mount but don't know if it worked or was the correct thing to do (it now appears under places)?

I can see SBM? In XBMC but can't see folders of media to access?

---

### Post by steveneddy on 2010-06-30
Here's a Google search for you:

[http://www.google.com/search?hl=en&source=hp&q=samba+network+drive&aq=2&aqi=g10&aql=&oq=samba+network&gs_rfai=CFUDkxeArTLXsDpOapgTypKCGCwAAAKoEBU_Q_Q7q](http://www.google.com/search?hl=en&source=hp&q=samba+network+drive&aq=2&aqi=g10&aql=&oq=samba+network&gs_rfai=CFUDkxeArTLXsDpOapgTypKCGCwAAAKoEBU_Q_Q7q)

---

