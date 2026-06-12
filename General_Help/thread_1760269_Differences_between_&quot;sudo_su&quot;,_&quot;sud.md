---
title: "Differences between &quot;sudo su&quot;, &quot;sudo -s&quot; and &quot;sudo -i&quot;?"
date: 2011-05-16
forum: General Help
---

### Post by 3602 on 2011-05-16
Usually when I need to chain-command sudo, I open a sudo -s so I don't have to type sudo all the time.
What is the big difference? Terminal output:
```
ME@ME-dv7:~$ sudo su
root@ME-dv7:/home/ME# exit
ME@ME-dv7:~$ sudo -s
root@ME-dv7:~# exit
ME@ME-dv7:~$ sudo -i
root@ME-dv7:~# logout
ME@ME-dv7:~$ 

```

Thank you.

---

### Post by sisco311 on 2011-05-16
Check out unutbu's post: [http://ubuntuforums.org/showpost.php?p=6188826&postcount=4](http://ubuntuforums.org/showpost.php?p=6188826&postcount=4)

---

### Post by 3602 on 2011-05-16
Ah tiens... So sudo -i all the way! Thank you!

---

