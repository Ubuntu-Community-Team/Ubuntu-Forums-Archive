---
title: "Lil bash problem"
date: 2010-09-18
forum: General Help
---

### Post by J V on 2010-09-18
```
#! /bin/bash
count=500
if [ ( $count % 500 ) -eq 0 ]
then
echo woot
fi
```Can't get a woot... Not familiar with bash's evil syntax xD

---

### Post by J V on 2010-09-18
Experimentation ahoy:
```
#! /bin/bash
count=499
if [ $[$count%500] -eq 0 ]
then
echo woot
fi
```

---

