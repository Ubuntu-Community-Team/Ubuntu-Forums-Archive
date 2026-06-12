---
title: "default ooo icons"
date: 2010-08-19
forum: General Help
---

### Post by Scooter_X on 2010-08-19
So anyway, I want to change my Open Office icons. Not the ones for the individual launchers, but the ones for an .odt or an .ods or .doc or whatever. I can change the icons for each individual file after having created it, but can't find out where to change it for all of them so they show up automatically like I want them the instant they're created.

Any ideas?

---

### Post by Ginsu543 on 2010-08-19
Try looking in /home/<your home folder>/.icons/<icon theme you're using>/scalable/mimetypes.

---

### Post by Scooter_X on 2010-08-19
> **Ginsu543 said:**
> Try looking in /home/<your home folder>/.icons/<icon theme you're using>/scalable/mimetypes.

Mine only goes as far as  /home/<your home folder>/.icons/ and then it's empty. I checked for hidden files as well. Nothing.

---

### Post by Ginsu543 on 2010-08-19
Okay, that means that you are using one of the default themes. Are you using Humanity? Assuming you are, check out /usr/share/icons/Humanity/mimes/48. If you're using another theme, just replace "Humanity" for the name of your theme. If changing the icons in 48 doesn't work, try the other size folders.

Just a heads-up, you will need root privileges to change these files.

---

### Post by Scooter_X on 2010-08-20
Alright, I'll give it a try once I get a chance. Thanks, I'll let you know how it went.

---

### Post by Scooter_X on 2010-08-25
Sweet, that's where they were. Thanks for the help.

---

