---
title: "File permissions for entire folder"
date: 2010-09-02
forum: General Help
---

### Post by Scooter777 on 2010-09-02
I'm running WoW through wine. In order to install addons I need to give all the files in the program permission to execute as a program. the problem is I can't (dont know how) just right click the folder and give everything inside permission i have to open each one and give them all permission, which can quickly turn into hundreds depending on the addon.
If anybody knows how to give permission to execute as a program to all the files in a folder at once it would save me a lot of clicking and time.

thanks for any help

---

### Post by redfox1160 on 2010-09-02
> **Scooter777 said:**
> I'm running WoW through wine. In order to install addons I need to give all the files in the program permission to execute as a program. the problem is I can't (dont know how) just right click the folder and give everything inside permission i have to open each one and give them all permission, which can quickly turn into hundreds depending on the addon.
If anybody knows how to give permission to execute as a program to all the files in a folder at once it would save me a lot of clicking and time.

thanks for any help

I think this will give permissions for all users (owner, group, world) to execute all files in the folder.
```
chmod a+x -R THEFOLDER/
```
Make sure you are in the directory the folder is in.
This might not be what you want to do though. You might only want to give owner, group, or world permission to execute.
Also, make sure this is really what you want to do before you do it.

---

### Post by Scooter777 on 2010-09-02
Thank you very much it worked. :D

---

