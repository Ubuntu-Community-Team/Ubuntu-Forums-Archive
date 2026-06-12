---
title: "Kubuntu prints, Ubuntu doesn't."
date: 2010-10-12
forum: General Help
---

### Post by baronsamedi on 2010-10-12
I went through some trouble a few weeks ago to install a HP-P2014 printer in a Ubuntu 10.10 box. The fix I found is here:

[http://ubuntuforums.org/showthread.php?t=1576204](http://ubuntuforums.org/showthread.php?t=1576204)

Now, it was not actually fixed, because the printer prints very light (gray even suppossedly black patches). It took me some time to realize that the problem was not in the printer but again somewhere in the software.

The thing is I have another box with Kubuntu, installed at the same time. Connecting the printer to that box gets perfect printouts.

I have tried to strip the Ubuntu system of everything I could find related to the printer (CUPS, HPLIPS, ...) to manually install all the packages in the Kubuntu box (again: what I could find: I'm no expert). As far as I can tell, both machines are identical in that respect, but I still can get Ubuntu to print properly (in fact, it is not printing at all: it just keeps spitting blank pages out).

Just for what it might be worth, I include the last lanes of the error messages in the printer diagnostic:

```
D [12/Oct/2010:16:35:40 +0200] cupsdReadClient: 13 1.1 Cancel-Subscription 1
D [12/Oct/2010:16:35:40 +0200] Cancel-Subscription /
D [12/Oct/2010:16:35:40 +0200] cupsdIsAuthorized: requesting-user-name="ax"
D [12/Oct/2010:16:35:40 +0200] cupsdMarkDirty(-----S)
D [12/Oct/2010:16:35:40 +0200] Returning IPP successful-ok for Cancel-Subscription (/) from localhost
D [12/Oct/2010:16:35:40 +0200] cupsdSetBusyState: Dirty files
D [12/Oct/2010:16:35:40 +0200] cupsdAcceptClient: 18 from localhost (Domain)
D [12/Oct/2010:16:35:40 +0200] cupsdReadClient: 18 GET /admin/log/error_log HTTP/1.1
D [12/Oct/2010:16:35:40 +0200] cupsdSetBusyState: Active clients and dirty files
D [12/Oct/2010:16:35:40 +0200] cupsdAuthorize: No authentication data provided.
```Please help?!

---

### Post by searchfgold6789 on 2010-10-12
You might try printing from Ubuntu to the Kubuntu printer, by sharing the Kubuntu printer.

---

### Post by baronsamedi on 2010-10-12
> **searchfgold6789 said:**
> You might try printing from Ubuntu to the Kubuntu printer, by sharing the Kubuntu printer.


And that is done how? I have been way out of my depth for weeks now with this.

---

