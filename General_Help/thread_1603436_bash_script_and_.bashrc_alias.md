---
title: "bash script and .bashrc alias"
date: 2010-10-22
forum: General Help
---

### Post by Hippytaff on 2010-10-22
For some reason, a bash script I wrote, which contains a word I use as an alias in .bashrc doesn't work...but just typing the alias-word in a terminal does...is this normal?

---

### Post by amauk on 2010-10-22
is this script run via cron?
if so, cron doesn't use your user's environment

---

### Post by Hippytaff on 2010-10-22
I was going to try the script with cron, but am just testing it first...so there will be more issues when I finally get it to work and then cron it? :-)

---

### Post by amauk on 2010-10-22
it's always best to avoid aliases and other such things in scripts
(It's a script, so the primary use of aliases, to avoid remembering a complex command, is negated anyway)

---

### Post by Hippytaff on 2010-10-22
> **amauk said:**
> it's always best to avoid aliases and other such things in scripts
(It's a script, so the primary use of aliases, to avoid remembering a complex command, is negated anyway)

Good point...also (I just realised) the script would only work with my .bashrc...honestly...

I'll get there one day :-)

---

