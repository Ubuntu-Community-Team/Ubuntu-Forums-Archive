---
title: "I still haven't received 10.04.1"
date: 2010-08-28
forum: General Help
---

### Post by fordguydude on 2010-08-28
This comes via the update manager, correct? 

I still haven't gotten the update. Is Ubuntu deploying this slowly?

---

### Post by Elfy on 2010-08-28
If you are completely updated then you have it.

10.04.1 is just the updated 10.04 - so if you download today it will be more up to date than it would have been in April.

---

### Post by fordguydude on 2010-08-28
> **forestpiskie said:**
> If you are completely updated then you have it.

10.04.1 is just the updated 10.04 - so if you download today it will be more up to date than it would have been in April.

Wouldn't it show 10.04.1 under System Manager 'System' tab?

---

### Post by plucky on 2010-08-28
> **fordguydude said:**
> Wouldn't it show 10.04.1 under System Manager 'System' tab?

Do you mean System Monitor 'System' tab? 

Mine says 10.04

Try from a terminal ```
lsb_release -a
``` and see what that says.

Good Luck

---

### Post by fordguydude on 2010-08-28
> **plucky said:**
> Do you mean System Monitor 'System' tab? 

Mine says 10.04

Try from a terminal ```
lsb_release -a
``` and see what that says.

Good Luck

Under description it does say 10.04.1

So I guess I have received the update.

---

### Post by Mark Phelps on 2010-08-29
> **fordguydude said:**
> Wouldn't it show 10.04.1 under System Manager 'System' tab?

It might.

But in terms of Update Manager, probably not.  Version 10.04.1 is just a more recent compilation of the components that make up Lucid Lynx.

Updates are delivered via the Update Manager as individual packages.

The only time you'll see a version update is when an entirely new version (i.e., 10.10) becomes available.

---

### Post by Ginsu543 on 2010-08-29
On my machine (with all updates installed through Update Manager), the lsb_release -a command gives me Lucid 10.04.1 but System Manager still says 10.04. I'm not too worried about it though... I know the OS is the latest and greatest I can have and just because System Manager doesn't keep up doesn't make it not so.

---

