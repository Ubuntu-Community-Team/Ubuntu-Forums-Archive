---
title: "Trouble with cd and variables?"
date: 2010-04-11
forum: General Help
---

### Post by NFblaze on 2010-04-11
[PHP]mobile:~$ cd /media/TOSHIBA\ EXT/Toshiba\ Support/recup_dir.2[/PHP]

cd into the directory to make sure it exists. Success.

[PHP]mobile:/media/TOSHIBA EXT/Toshiba Support/recup_dir.2$ blah=/media/TOSHIBA\ EXT/Toshiba\ Support/recup_dir.[/PHP]

It indeed exists. So, I set the path to equal the variable. I didnt use the number as this is suppose to be going into a script. Success.

[PHP]mobile:/media/TOSHIBA EXT/Toshiba Support/recup_dir.2$ cd $blah2
bash: cd: /media/TOSHIBA: No such file or directory[/PHP]

Use the variable, and manually add the number. Fails.

For some reason, it keeps cutting off at the backslash I used to escape the space. Is there a solution?

---

