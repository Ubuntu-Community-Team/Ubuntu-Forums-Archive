---
title: "Upgrading Thunderbird"
date: 2006-05-31
forum: General Help
---

### Post by orsula on 2006-05-31
Hello,
I would like to upgrade the Thunderbird 1.0.8 that comes with the distro to the latest 1.5.0.2. But I don't know how to install the upgrade in the right location, over the old installation. The file from mozilla.org is extracted as a stand-alone folder which is no good if I would like to use all my previous configurations. 
Also, [FONT=Courier New]sudo apt-get install mozilla-thunderbird[/FONT] does not install the latest 1.5 version. 
Would anyone know how to use the tar.gz file from mozilla.org to install over the old version (i.e. in the correct foldr such as /var/lib, or /etc/ and so forth...)

Thanks much
:-k
Gideon

---

### Post by aysiu on 2006-05-31
Try this: [http://www.psychocats.net/ubuntu/thunderbird](http://www.psychocats.net/ubuntu/thunderbird)

---

### Post by orsula on 2006-05-31
[QUOTE=aysiu]Try this: [http://www.psychocats.net/ubuntu/thunderbird](http://www.psychocats.net/ubuntu/thunderbird)[/QUOTE]

Thanks - worked like a charm, although I had to migrate my profiles..

Gideon

---

### Post by aysiu on 2006-05-31
[QUOTE=orsula]Thanks - worked like a charm, although I had to migrate my profiles..

Gideon[/QUOTE] Weird--should have copied your ~/.mozilla-thunderbird to ~/.thunderbird... I'll take another look at the script...

**Edit**: Just realized I forgot a . in the script. You should have a folder called ~/thunderbird that really should be called ~/.thunderbird

---

### Post by mike_m on 2006-05-31
Thanks aysiu,
worked great!

---

