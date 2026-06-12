---
title: "Conky eventually fails after upgrade to Karmic"
date: 2009-11-19
forum: General Help
---

### Post by phydeaux98038 on 2009-11-19
As the title says, my Conky instances will eventually fail.  This came up only after I upgraded to Karmic about a week ago or so.  I've got four different conkyrc files, which all worked well previously.  And they don't all fail at the same time.  They all seem to drop off one by one after some unknown length of time.  Two of my rc files are calling external scripts, one is a template format for weather, and the final one is using just internal conky calls, nothing external or templated (if that's a word...).

Looking through the .xsession-errors, I find a few lines like this:

```
Conky: X Error: type 0 Display 8c4b7c8 XID 115343361 serial 16122 error_code 9 request_code 62 minor_code 0 other Display: 8c4b7c8
```The display, XID, or serial may differ, but the general error is the same.  Not sure what that is, or if it's even related.

Tell me what else I need to supply to help figure this out, and it's yours.

---

### Post by daFlo on 2010-02-24
It seems that conky 1.7.2 has problems with the version of gnome running at 9.10. I had exactely the same errormessage and for me an update to the newest version of conky helped.

[https://launchpad.net/~norsetto/+archive/ppa/+sourcepub/941558/+listing-archive-extra](https://launchpad.net/~norsetto/+archive/ppa/+sourcepub/941558/+listing-archive-extra)

---

### Post by phydeaux98038 on 2010-02-25
> **daFlo said:**
> It seems that conky 1.7.2 has problems with the version of gnome running at 9.10. I had exactely the same errormessage and for me an update to the newest version of conky helped.

[https://launchpad.net/~norsetto/+archive/ppa/+sourcepub/941558/+listing-archive-extra]("https://launchpad.net/%7Enorsetto/+archive/ppa/+sourcepub/941558/+listing-archive-extra")

Looks like that's not a stable release, correct?

---

