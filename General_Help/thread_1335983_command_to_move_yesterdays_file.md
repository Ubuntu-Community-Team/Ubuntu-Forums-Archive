---
title: "command to move yesterdays file"
date: 2009-11-24
forum: General Help
---

### Post by terrordrone on 2009-11-24
Hello..

My aim is to add an entry in crontab which moves a file in folder 1 to folder 2 ..   compress it using bzip2 ..  

and then move it to folder three..


All im able findout is yesterdays date along with some modifications..

date --date="-1 days" +%Y%m%d | awk '{ printf "mylog.%d.log", $1;}'

This is giving the name of the file ..  and i can append the whole path later..  

however im not able collect the output of awk and pass it onto mv command as source file..  and then proceed..  

pardon my ignorance :|

Even though im asking a lot..  it would be of great help if someone writes down the crontab entry.. 

any pointers would also be helpful

Thanks

---

### Post by ghostdog74 on 2009-11-24
use find command. check its man page and look for -mtime option.

---

### Post by terrordrone on 2009-11-24
date --date="-1 days" +%Y%m%d | awk '{ printf "mylog.%d.log", $1; }' | xargs -I {} mv /dir1/{} /dir2/ 


that did the trick..  


another thing id like to know .. is..

once the log is moved..  which will take a minute or two..  i want to start of the compression...

also.. i want the bzip2 to create the new file in dir2 itself.. 

how do i do that ?

---

