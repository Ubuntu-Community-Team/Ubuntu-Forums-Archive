---
title: "Understanding the CP command.."
date: 2011-04-26
forum: General Help
---

### Post by NetDoc on 2011-04-26
Which of these (if any) are correct? 

cp -r /var/www/vhosts/niftyfiftyparty.com/httpdocs/sites/all/modules/*.* /var/www/vhosts/keylargodivecenter.com/httpdocs/sites/all/modules/*

[COLOR="Blue"]
in /var/www/vhosts/niftyfiftyparty.com/httpdocs/sites/all/modules/[/COLOR]
cp -r *.* /var/www/vhosts/keylargodivecenter.com/httpdocs/sites/all/modules/*

[COLOR="blue"]in /var/www/vhosts/keylargodivecenter.com/httpdocs/sites/all/modules/[/COLOR]
cp -r /var/www/vhosts/niftyfiftyparty.com/httpdocs/sites/all/modules/*.* *

Both the source and destination folders are valid. There are several folders in the niftyfiftyparty modules folder that I need in the other one. Thanks in advance.

---

### Post by cek on 2011-04-26
```


cp -rpv /var/www/vhosts/niftyfiftyparty.com/httpdocs/sites/all/modules/* /var/www/vhosts/keylargodivecenter.com/httpdocs/sites/all/modules/


```

Will copy all files (recursively) from the first path to the second path, preserving names.  Will also show what is being copied in the console window while copying (which can be helpful for troubleshooting any issues).

---

### Post by NetDoc on 2011-04-26
So the problem I was having was using the *.* rather than just * 

Thanks.

---

