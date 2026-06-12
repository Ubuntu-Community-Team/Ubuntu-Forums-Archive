---
title: "Get back Bitdefender GUI back...? Pls. Help."
date: 2012-03-31
forum: General Help
---

### Post by farmerjohn73 on 2012-03-31
I recently installed bitdefender on my ubuntu 11.04 laptop.  After installing I enabled drag n drop file zone for scanning files by clicking "bdgui" file from /opt/bitdefender-scanner/ folder.

After a few days I wanted to get back to the gui mode but I cant get it.  whenever i click bdgui from the above folder, it is launching to the dragndrop mode only. 

I tried uninstalling and reinstalling but even when i am installing it again, it is launching the dragndrop zone mode only.

I tried this many times.

Can someone help me in disabling the option and get back the nice GUI back?

Please.

---

### Post by howefield on 2012-03-31
Try opening the file manager (Nautilus) and press Ctrl + H to show hidden files/folders.

Do you have one called .bitdefender ?

If so, rename it and restart Bitdefender. It will most likely start with a fresh "profile".

Once sorted you can delete the renamed folder or rename it back to the original file name to put you back where you started.

---

### Post by farmerjohn73 on 2012-03-31
thanks howefield,

but i dont find the file you mentioned in my home folder.  I searched other folders but didnt find it.

any other way please...

---

### Post by howefield on 2012-03-31
> **farmerjohn73 said:**
> but i dont find the file you mentioned in my home folder.  I searched other folders but didnt find it.

Try again, home folder, press Ctrl + H to reveal hidden files/folders and look in .config/

---

### Post by farmerjohn73 on 2012-04-03
thank you howefield,

I had to reformat my drive due to some other reason.  I loaded bitdefender again.

Now its working fine.

thank you verymuch for your help.

---

