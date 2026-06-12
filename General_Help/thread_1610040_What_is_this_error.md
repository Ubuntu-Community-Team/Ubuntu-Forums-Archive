---
title: "What is this error ?"
date: 2010-10-31
forum: General Help
---

### Post by binarylife on 2010-10-31
hi 
When I close then open the led of the laptop  , the screen sometimes freezes and it gives me this msg : 

GLib-WARNING **: getpwuid_r(): failed due to unknown user(0)
How can i fix it !!!!

---

### Post by SPr on 2010-10-31
If you want help it would be beneficial for everyone if you gave the real error message rather than "something like" the error message.

Could it be [GLib-WARNING **: getpwuid_r(): failed due to unknown user](http://www.google.co.uk/search?client=opera&rls=en-GB&q=GLib-WARNING+**:+getpwuid_r():+failed+due+to+unknown+user&sourceid=opera&ie=utf-8&oe=utf-8)?

---

### Post by binarylife on 2010-10-31
> **SPr said:**
> If you want help it would be beneficial for everyone if you gave the real error message rather than "something like" the error message.

Could it be [GLib-WARNING **: getpwuid_r(): failed due to unknown user](http://www.google.co.uk/search?client=opera&rls=en-GB&q=GLib-WARNING+**:+getpwuid_r():+failed+due+to+unknown+user&sourceid=opera&ie=utf-8&oe=utf-8)?

yes it is, and I did not understand anything ,,

---

### Post by Vigh on 2010-10-31
try re-installing glib/glibc libraries through synaptic, and update/upgrade to latest security/software/library patches, not 100% sure how to do this, as it has been awhile since I did anything with the glib packages

---

### Post by binarylife on 2010-10-31
> **Vigh said:**
> try re-installing glib/glibc libraries through synaptic, and update/upgrade to latest security/software/library patches, not 100% sure how to do this, as it has been awhile since I did anything with the glib packages

 alright , Thanks a lot.

---

### Post by Vigh on 2010-10-31
also try assigning your root user (your main administrator user account) permissions to all services through administration- users and groups

---

### Post by binarylife on 2010-11-03
> **Vigh said:**
> also try assigning your root user (your main administrator user account) permissions to all services through administration- users and groups

Nothing worked from this .
and the problem is still the same.
Any suggestion or help please ?
Thanks

---

### Post by Vigh on 2010-11-11
could be a bios problem, particular with power-management settings, S1 power-state/power-saving is alot more stable, S3 causes problems, unfortunately you can't change these settings with most laptops due to the bios being locked-down, could try a bios update from your official laptop website for your particular model, but make sure it is fully charged battery and plugged into the power. its either glib library based or hardware bios based issue you are having with respect to power-management

---

### Post by binarylife on 2010-11-12
> **Vigh said:**
> could be a bios problem, particular with power-management settings, S1 power-state/power-saving is alot more stable, S3 causes problems, unfortunately you can't change these settings with most laptops due to the bios being locked-down, could try a bios update from your official laptop website for your particular model, but make sure it is fully charged battery and plugged into the power. its either glib library based or hardware bios based issue you are having with respect to power-management

a bios update?first time in my life I hear something like this:) .
so let me assume it is a glib library issue, how can I even try to fix it ?...
and thanks a lot

---

### Post by Vigh on 2010-11-12
okay I have successfully fixed the exact same problem I had with my laptop, I did it by backing up the data, and installing 32-bit Ubuntu i386 10.10

turns out my laptop, although having a 64-bit capable CPU, didn't have a 64-bit capable BIOS, which was too much trouble to update, installing i386 Ubuntu solved all power-management problems for this particular laptop,

laptop = TOSHIBA L500D

---

### Post by binarylife on 2010-11-13
> **Vigh said:**
> okay I have successfully fixed the exact same problem I had with my laptop, I did it by backing up the data, and installing 32-bit Ubuntu i386 10.10

turns out my laptop, although having a 64-bit capable CPU, didn't have a 64-bit capable BIOS, which was too much trouble to update, installing i386 Ubuntu solved all power-management problems for this particular laptop,

laptop = TOSHIBA L500D

My laptop is HP550 T5470  @ 1.60GHz , I have the 32-bit version of ubuntu i386 10.10, and it is also 64-bit capable CPU .So i have the 32-bit and the problem is still on . thanks

---

### Post by HitmanNumber86 on 2010-11-13
I get a similar error message on startup, causing the startup to fail sometimes.

GLib-WARNING **:getpwuid_r(): failed due to unknown user id

Running 10.04 i386 on an Intel N450 Atom

Your help is appreciated, thank you.

---

