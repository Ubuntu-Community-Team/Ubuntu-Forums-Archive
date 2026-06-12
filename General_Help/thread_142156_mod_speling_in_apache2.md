---
title: "mod_speling in apache2"
date: 2006-03-09
forum: General Help
---

### Post by pete on 2006-03-09
Greetings all--

I've got apache2 running fine on Breezy, and am now trying to get mod_speling working to deal with URL paths typed in the wrong case.

I ran "sudo a2enmod mod_speling", so now there's a link in /etc/apache2/mods-enabled to mod_speling in the /mods-available dir.  However, the mod itself doesn't seem to be working.

I'm assuming I have to put the "CheckSpelling = On" directive somewhere, but since there's no .conf file, I'm not sure where it should go.  Anybody know?

---

### Post by pete on 2006-04-04
I figured this out, so I'm updating the thread with the fix in case anyone else is looking...

1. Created speling.conf in /etc/apache2/mods-available containing the directive "CheckSpelling on".
2. Created a link in /etc/apache2/mods-enabled to the .conf file I created in step 1.
3. Restarted apache.


Voila!  URL paths and filenames are no longer case-sensitive.

---

