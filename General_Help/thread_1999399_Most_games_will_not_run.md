---
title: "Most games will not run"
date: 2012-06-08
forum: General Help
---

### Post by gilthoniel on 2012-06-08
I'm aware that this is a pretty vague description, but it's the best I can do: When I try to open games through the applications menu, *nothing* happens. I've used top to check if any processes start running, but they don't. I've been trying Braid, Bastion and Nexuiz, and all have the same problem. Games like Aisleriot and Mines run just fine.

I believe it might have something to do with my graphics driver. I'm using an Acer Aspire 4820TG, which has a Radeon HD 5650. I've installed the proprietary driver through Additional Drivers, but cannot install the post-release updates - Additional Drivers just freezes at the end of the process when I try to do this. And all I get when I try fglrxinfo is this:

```
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12
```

Does anyone have any ideas? I can provide plenty more information if necessary, but at the moment I don't know which information I need to provide! Thanks.

---

### Post by roelforg on 2012-06-08
I know that problem.
 
First go to additional drivers and click on the non-post release ati driver and click activate/install. Reboot afterwards.
Because when the post-release install failed, games were still told to use a driver that wasn't installed (because of the failure).
 
--ATI Radeon HD 2400 XT here

---

### Post by darkenedday on 2012-12-26
I am having this same problem, has anyone found a solution?

---

