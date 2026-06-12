---
title: "Firefox will not start"
date: 2011-03-27
forum: General Help
---

### Post by jarome on 2011-03-27
On 10.04 running on my HP 2133, I tried to update Firefox to 4.0. I had the beta working before. But now, I always get the message 
libxpt:bad magic header in input file; found '', expected 'XPCOM\nTypeLib\r\n\032'

I found a lot of old posts on this problem, but no solutions.
I uninstalled 4.0, reinstalled 3.6, but still get this error.

Help please,
Jim

---

### Post by lovinglinux on 2011-03-27
Try to reinstall xulrunner.

---

### Post by jarome on 2011-03-27
I tried downgrading to .16 from .17, and it made no difference. Uninstalling xulrunner also uninstalls a bunch of things with it, so I am reluctant to do that.

---

### Post by lovinglinux on 2011-03-27
> **jarome said:**
> I tried downgrading to .16 from .17, and it made no difference. Uninstalling xulrunner also uninstalls a bunch of things with it, so I am reluctant to do that.

Don't remove it. Go to synaptic, select the installed xulrunner package and then the option to reinstall. Click "Apply".

---

### Post by jarome on 2011-03-27
> **lovinglinux said:**
> Don't remove it. Go to synaptic, select the installed xulrunner package and then the option to reinstall. Click "Apply".

I tried that too. Still the same.

---

### Post by lovinglinux on 2011-03-27
Try starting Firefox in safe mode:

```
firefox -safe-mode
```

If it works, then is probably an extension causing the problem. I have seen reports of Colorzilla being the culprit.

---

### Post by jarome on 2011-03-28
> **lovinglinux said:**
> Try starting Firefox in safe mode:

```
firefox -safe-mode
```

If it works, then is probably an extension causing the problem. I have seen reports of Colorzilla being the culprit.

That worked, thanks! But I was still on 3.6, even though package manager says I have 4.0 installed. So I downloaded the firefox 4.0 from Mozilla, put it in /usr/local, uninstalled the Ubuntu junk, and it works.

---

