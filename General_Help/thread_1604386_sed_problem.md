---
title: "sed problem"
date: 2010-10-24
forum: General Help
---

### Post by heinemann on 2010-10-24
Hello,

I have an issue with sed:

I have to replace "motallyTrack($motally_params);"  with "//motallyTrack($motally_params);"
in the "functions.php" file in all /var/www/html/ folders.

that is the command line I'm using:
```
find . -name "functions.php" | xargs sed -i .old -e "s/motallyTrack\(\$motally\_params\)/\/\/motallyTrack\(\$motally\_params\)/g"
```

I receive the following error msg:
> 
sed: can't read .old: No such file or directory
sed: can't read ./oig_tmp/phpc/plugins/Page: No such file or directory
sed: can't read Counts.php: No such file or directory
sed: can't read ./oig_tmp/phpc/plugins/Browsers: No such file or directory
sed: can't read (Graphical).php: No such file or directory


Is there anything wrong with my command line? 

Thanks in advance

---

