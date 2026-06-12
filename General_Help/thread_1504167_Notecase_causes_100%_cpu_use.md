---
title: "Notecase causes 100% cpu use"
date: 2010-06-07
forum: General Help
---

### Post by StuartN on 2010-06-07
Notecase 1.9.8 (from the repository) causes CPU use to rise to 100% on Ubuntu 10.4, even without a document loaded.

I can see no reason for this, and actually I have not noticed any ill-effects or sluggishness - I usually have Notecase tucked away in the background, so I am a little surprised.

Is this just a 10.04 feature, or is it the same in previous Ubuntus?

---

### Post by grv7 on 2010-06-22
You can try to disable "Minimize to tray" option on the "Global" tab. Seems it's helped me.

---

### Post by StuartN on 2010-06-22
> **grv7 said:**
> You can try to disable "Minimize to tray" option on the "Global" tab. Seems it's helped me.

Now that is an unusual bug - "Minimize to tray" was not checked, but checking and unchecking, and then restarting Notecase, has taken CPU usage down below 0.1%. (**Edit:** This causes Notecase to write out a revised ~/.notecase/notecase.ini with several settings that are not in the installation version).

This has a huge effect on, for instance, the speed of Gimp filters, which were very much slower if I did note close Notecase.

Eventually I am sure that I will have to find a maintained hierarchical outliner, but I have not yet found one with the features that I am using within Notecase (for instance launching a script or application from a note).

Many thanks.

---

### Post by grv7 on 2010-06-22
> **StuartN said:**
> Eventually I am sure that I will have to find a maintained hierarchical outliner, but I have not yet found one with the features that I am using within Notecase (for instance launching a script or application from a note).


Actually now I use Basket on my work ([http://basket.kde.org/](http://basket.kde.org/)). It can launch an application/script from a note. And I like it more than Notecase. Unfortunately Basket is not crossplatform application like Notecase (It's bad thing for me).

---

