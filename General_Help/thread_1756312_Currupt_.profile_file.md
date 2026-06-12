---
title: "Currupt .profile file"
date: 2011-05-12
forum: General Help
---

### Post by Nick Hopton on 2011-05-12
I've installed 11.04 on my laptop and use the Classic desktop. Yesterday I installed TeX Live 2010, which was fine, but I also had to add the path to Tex Live to my .profile file.

I did this, but owing to a lapse on concentration I edited the file with Gwrite instead of Gedit and now I can't log in to Ubuntu at all. My stupidity of course, I'm not fit to be at large, but can anyone offer me advice about where to go from here? Your suggestions would be gratefully received.

Regards, Nick.

---

### Post by anaconda on 2011-05-12
Not sure, but I think.. if you log to recovery mode, and delete the profile -file. Then at next login you will have the default .profile file re-created.

But anyway. You can log to recovery mode, and edit your profile-file with eg. editor called nano.... and correct your mistake.

If you don't want to work in terminal, you can boot to recovery mode, and start x with: 
startx

(but then you will be running x as root user...)

---

### Post by Nick Hopton on 2011-05-12
Ah, but I can't even log in via the Recovery Console, trying to just returns me to the log-in dialogue.

Regards, Nick.

---

### Post by anaconda on 2011-05-12
well. then you can boot with a liveCD or USB, and edit the profile file from there...
(or copy the liveCD:s .profile -file...

the recovery console should work, because it doesn't use users .profile file...

---

### Post by Nick Hopton on 2011-05-12
Thanks for the help anaconda. In the end I logged in as a different user and then made myself superuser. From here I used nano to remove the HTML tags from .profile and things are back to what passes for normal in this household. Many thanks too for the nano tip (it's a nice little utility).

Regards, Nick.

---

