---
title: "how to edit a file that is read only"
date: 2010-07-05
forum: General Help
---

### Post by ubunguy on 2010-07-05
i log in and went to the policy folder to erase the file prefernces.fdi and it would not let me delete this file /move it to the trash or even edit it it said something like you are not the owner ,so i could not change the permissions to overwrite this file.
 
what should i do i just want to be able to change this file to true so it will see my internal sc dar reader right now when i put in a sd card it does not show up.
 
i also tried changing this in the terminal there was a post on one blog that showed how ,but i was having trouble edit the xml file in the terminal so for me it would be easier to just overwrite the prefernces.fdi file since im a beginner.

---

### Post by ajgreeny on 2010-07-05
Backup first just in case it all goes wrong with ```
sudo cp /etc/hal/fdi/policy/preferences.fdi /etc/hal/fdi/policy/preferences.fdibackup
``` then ```
gksudo gedit /etc/hal/fdi/policy/preferences.fdi
``` edit, save and it's done.

If anything goes totally wrong you will now have the backup to restore if needs be.

---

### Post by ubunguy on 2010-07-05
okay i was able to change the values to true but my internal sd card reader is still  not working in ubuntu

is there anything else i can try?


would modprobe work?

---

### Post by ajgreeny on 2010-07-06
Sorry, I haven't got a clue about that!

---

