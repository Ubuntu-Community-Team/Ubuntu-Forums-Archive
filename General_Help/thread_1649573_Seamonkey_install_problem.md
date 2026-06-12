---
title: "Seamonkey install problem"
date: 2010-12-20
forum: General Help
---

### Post by whvw on 2010-12-20
I just installed Seamonkey, both at home and the radio station. One of the installs was sans e-mail, the other had it, but then it disappeared, before I even got a chance to set it up. (9.10). This is so wacky I don't know where to begin to look for a solution. Can anyone help?

---

### Post by luigi_mb on 2010-12-20
> **whvw said:**
> I just installed Seamonkey, both at home and the radio station. One of the installs was sans e-mail, the other had it, but then it disappeared, before I even got a chance to set it up. (9.10). This is so wacky I don't know where to begin to look for a solution. Can anyone help?

Which version did you install, and where did you get it?

A recent version is in the repos. You can also get a no-install version from Mozilla (seamonkey-2.0.11.tar.bz2). Just unpack it in your home folder, cd to ~/seamonkey, and execute ./seamonkey .

/luigi

---

### Post by whvw on 2010-12-21
Well, it seems that, as I recall, I got one from the Ubuntu Software Centre, and the other from the Seamonkey site. (as I remember, for awhile SM wasn't on the USC). Can one "repair" an installation by re-installing over it without trashing the whole thing? (I suspect not) Or, is there some little line in a configuration file somewhere that needs a friendly edit?

---

### Post by luigi_mb on 2010-12-21
Which version do you want to remove or update?

To update or remove the version in the Ubuntu repositories, simply use Synaptic. If you want to remove any traces (e.g. your profile) do a "complete removal."

To update or remove the binary version downloaded from Mozilla, simply delete the folder ~/seamonkey . If you also want to remove any profile you have created, remove the folder ~/.mozilla/seamonkey.

/luigi

---

### Post by whvw on 2010-12-21
This is related to an earlier post of mine about the Ubuntu Software Centre being broken here at home. I can't download anything, I keep getting an error about port 8080, invalid host name. Yes, I have set everything I can think of to "direct internet connection" but it doesn't help. Also, there seems to be something wrong with "mscorefonts". If I could just get a good copy of that file and be told exactly where it belongs, it might help. By the way, browsing and e-mail work just fine.
Is it possible to download an install file from a computer where the USC works to a USB device and then install it here at home? Perhaps that might serve as a temporary work-around until someone can figure out what the real problem is.

---

