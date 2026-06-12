---
title: "Ubuntu Update boxes grayed out - How to fix this?"
date: 2010-10-09
forum: General Help
---

### Post by website.reader3 on 2010-10-09
I switched from the Ubuntu repositories to a local repository mirror, but the Ubuntu Update boxes are grayed out, so the system cannot be updated.

Why are those boxes grayed out?

Here's what I got running the update command:

root@athlon:/etc/apt# apt-get update
Hit [http://server](http://server) lucid Release.gpg
Ign [http://server/](http://server/) lucid/main Translation-en_US
Ign [http://server/](http://server/) lucid/restricted Translation-en_US
Ign [http://server/](http://server/) lucid/universe Translation-en_US
Ign [http://server/](http://server/) lucid/multiverse Translation-en_US
Hit [http://server](http://server) lucid-updates Release.gpg
Ign [http://server/](http://server/) lucid-updates/restricted Translation-en_US
Hit [http://server](http://server) lucid-security Release.gpg
Ign [http://server/](http://server/) lucid-security/restricted Translation-en_US
Hit [http://server](http://server) lucid Release
Hit [http://server](http://server) lucid-updates Release
Hit [http://server](http://server) lucid-security Release
Hit [http://server](http://server) lucid/main Packages          
Hit [http://server](http://server) lucid/restricted Packages    
Hit [http://server](http://server) lucid/universe Packages
Hit [http://server](http://server) lucid/multiverse Packages
Hit [http://server](http://server) lucid/main Sources
Hit [http://server](http://server) lucid/restricted Sources     
Hit [http://server](http://server) lucid/universe Sources       
Hit [http://server](http://server) lucid/multiverse Sources     
Hit [http://server](http://server) lucid-updates/restricted Packages
Hit [http://server](http://server) lucid-security/restricted Packages
Reading package lists... Done

Are the "Ign" lines a problem or does Ign mean ignored?

I interpret the reload results above to mean that we're good to go, but the GUI doesn't think so.

---

### Post by dcstar on 2010-10-09
> **website.reader3 said:**
> I switched from the Ubuntu repositories to a local repository mirror, but the Ubuntu Update boxes are grayed out, so the system cannot be updated.
.........
Are the "Ign" lines a problem or does Ign mean ignored?

I interpret the reload results above to mean that we're good to go, but the GUI doesn't think so.

If there are **no** Updates to be done, then you will not get any option to Update. This will occur if the mirror is not updating.

"Ign" means "Ignored" as there is no special language translation for that Locale.

Do not ask the same question multiple times, that is a good way to be banned from a forum.

---

