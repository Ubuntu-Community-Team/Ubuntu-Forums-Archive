---
title: "How to change the permission setting for a folder"
date: 2010-08-25
forum: General Help
---

### Post by Seb855 on 2010-08-25
Im trying to run Wow with Wine , But its telling me i need to give to the wow folder write access , so im right clicking on the folder , then Permissions , And it has create or delete folder already on , but right below im selecting Read and Write but it doesnt let me do it :/ just goes back to blank .

---

### Post by TeoBigusGeekus on 2010-08-25
```
sudo chown yourusername /path/to/folder
```

---

### Post by Vaphell on 2010-08-25
can you drop to terminal
and do
**ls -la ~/.wine/drive_c/Program\ Files/WoW** (or whatever the proper path is, use tab to autocomplete chunks of the path after first few letters so you don't have to type everything)

---

### Post by Seb855 on 2010-08-25
not sure if i did it right but its not working , im using ubuntu since 2 days , and got no idea about what are these commands , its only asking me to go into program files , and selecting the wow folder and giving it write access

---

### Post by Vaphell on 2010-08-25
so when you right click the wow directory - who is listed as the owner in dir properties? root or you?

---

### Post by claracc on 2010-08-26
> i need to give to the wow folder write access 

From console, applications --> accesories ---> terminal you go to the directory where wow folder is and write: sudo chmod +w wow, in this way you give write permissions to this folder.

---

