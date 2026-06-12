---
title: "creating folder"
date: 2012-06-08
forum: General Help
---

### Post by winzip on 2012-06-08
Is it possible to create folder name with timestamps in ubuntu ?


I want folders with name like this format ...

[COLOR=RoyalBlue]**2-june-2012:22:15:45**[/COLOR]

where 22 = hour , 15 =minute , 45 = seconds


Presently I  use  ..

```
curr_date=$(date+%e-%B-%Y}
```

This does not produce  hour , minute , seconds

What changes I need here ?

---

### Post by Blackbird_13 on 2012-06-08
Try
```
date +%e-%B-%Y-%T
```

---

### Post by winzip on 2012-06-08
> **Blackbird_13 said:**
> Try
```
date +%e-%B-%Y-%T
```

Thanks. Will check this out and let you know. 

BTW,  Does ubuntu allow such folder name ?

---

### Post by Blackbird_13 on 2012-06-08
The following worked for me:

```
mkdir 2-june-2012:22:15:45
```

---

