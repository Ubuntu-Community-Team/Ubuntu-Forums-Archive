---
title: "USB Ext HD not detected"
date: 2009-08-27
forum: General Help
---

### Post by colintivy on 2009-08-27
I have and external HD which used to house Win98SE on my laptop. I have checked using another Win machine that it is all in place as before. I want to use it as a  back-up to my Hardy machine but cannot find out how to get the OS to know that the drive is there so that I can reformat it to Ext3. Any clues about what I am missing???

colintivy :confused::confused:

---

### Post by c0mput3r_n3rD on 2009-08-27
Open a terminal and cd to your /media directory.
```

cd /media

```

Tell me if you see the name of your HDD's name.  If you do, mount the drive;
```

mount hdd_name

```

---

### Post by scouser73 on 2009-08-27
Please follow the instructions set out in this tutorial: [[COLOR="Red"]**Mount External Hard Drives**[/COLOR]]("https://help.ubuntu.com/community/Mount/").

---

