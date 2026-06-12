---
title: "Trouble with file permissons"
date: 2012-04-28
forum: General Help
---

### Post by JayUK20 on 2012-04-28
I am trying to install Axjaxplorer (web based file manager) and even though I have run sudo chmod 777 file.name - the installer is still saying that the folders/files need to be writable.

```
One of the following folder should be writeable and is not : AJXP_DATA_PATH/plugins/conf.serial,AJXP_DATA_PATH/plugins/conf.serial/repo.ser,AJXP_DATA_PATH/plugins/auth.serial,AJXP_INSTALL_PATH/data/logs/,/opt/lampp/htdocs/test/data/cache
```

---

### Post by Steven D on 2012-05-03
i believe the command is chown
ex: i have a folder in my home named .skulltag which is owned by root. My user name is steve. To change the folder so I can write in it would be:
[COLOR=Sienna]sudo[/COLOR] [COLOR=DarkGreen]chown[/COLOR] [COLOR=Navy]-R[/COLOR] [COLOR=Red]steve:steve[/COLOR] .skulltag
Basically it's [COLOR=Sienna]superuserdo[/COLOR] [COLOR=DarkGreen]change ownership[/COLOR] [COLOR=Navy]recursive (all subfolders)[/COLOR] [COLOR=Red]user & group[/COLOR] target folder

---

