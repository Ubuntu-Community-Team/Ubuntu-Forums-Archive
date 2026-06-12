---
title: "Conky restart after resume from sleep"
date: 2010-02-19
forum: General Help
---

### Post by bradrewalter on 2010-02-19
Hi everyone, been lurking for a while and found pretty much everything I need on here.  Thanks!

I'm having trouble getting conky to start automatically after resume from sleep.  I've tried putting a copy of my conky startup script into /etc/pm/sleep.d but nothing happened.  Any ideas?

My startup script:
[PHP]#!/bin/bash
sleep 20 && conky[/PHP]

---

### Post by Johnny B on 2010-02-19
that should read:
sleep 20 && conky **-c {path to conkyrc}**

---

### Post by bradrewalter on 2010-02-21
> **Johnny B said:**
> that should read:
sleep 20 && conky **-c {path to conkyrc}**

The script I posted is the script I use to have conky run when I start my computer and it works fine.  Will the suggestion posted get it to start on resume?  Should I post it in the /etc/pm/sleep.d folder?

---

