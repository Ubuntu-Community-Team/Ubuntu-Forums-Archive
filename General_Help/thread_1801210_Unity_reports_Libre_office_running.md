---
title: "Unity reports Libre office running??"
date: 2011-07-10
forum: General Help
---

### Post by tropdoug on 2011-07-10
When I try to start any Libre office app from a terminal (because the panel will not start them at all) I get this (attached)

I open System Monitor and check processes and according to that Libre Office is not running. 

Can anyone explain what Unity is doing? and how to fix it.

---

### Post by grahammechanical on 2011-07-10
Unity is not doing anything. It is Libreoffice that is saying that it cannot access the personal settings. Is it telling the truth? What is M61PME -S2P? Is that the name of another computer on the network? Do you have more than one terminal open? 

If you open your home folder in the file manager and select Show hidden files from the View menu then in the home folder you will see a folder called .libreoffice. I would suggest that you uninstall Libreoffice and then rename the folder .libreoffice to something else and then re-install Libreoffice.

The dot indicates a hidden folder. Something is messed up in your Libreoffice settings and as the .libreoffice folder is in your home folder then a new installation of Libreoffice will use the old settings and you will still have the old problems. You need to rename it. Then the new install will create a new, clean folder.

This is only a suggestion. 

Regards.

---

### Post by tropdoug on 2011-07-12
Thanks - I will try that and post the result. The M61 etc is my computer name,

---

### Post by tropdoug on 2011-07-12
I renamed the folder, but then decided to see what would happen if I just started calc. A new folder was created, the program opened from the panel (which it has never done since the natty install) and voilà I am off an running. Thanks. I can now mark this solved and also another thread asking about the launching from the panel -- 2 in 1 thanks to your clear and knowledgeable reply grahammechanical. Cheers

---

