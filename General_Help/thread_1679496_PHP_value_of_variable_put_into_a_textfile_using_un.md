---
title: "PHP value of variable put into a textfile using unix."
date: 2011-02-01
forum: General Help
---

### Post by Jovenrp on 2011-02-01
How can I put a value of a php variable into a text file. I cant append or write the values into a text file. Help Please. :D

---

### Post by SeijiSensei on 2011-02-01
```

$var='something';
$fp=fopen("/path/to/the/file","w+");
fwrite($fp,$var);
fclose($fp);

```

You'll need to write the file some place where the user www-data has write permissions, since that's the user that Apache runs under.

---

### Post by Jovenrp on 2011-02-01
Thanks but I already found a way. Its also similar to yours. What I did is write the output of my html file to a text file and then read it again by my php code. Thanks anyway. :D

---

