---
title: "Open Webpage at certain time"
date: 2010-01-14
forum: General Help
---

### Post by charlton2142 on 2010-01-14
Heya I wsa just wondering if it was possible to get ubuntu to automatically open Firefox to a particular webpage at a specific time monday through friday. The webpage in which i am referring to is not my homepage. Please keep in mind that I am completely unfamiliar with scripting 

thanks for any assistance that you can provide

---

### Post by Ahadiel on 2010-01-14
> **charlton2142 said:**
> Heya I wsa just wondering if it was possible to get ubuntu to automatically open Firefox to a particular webpage at a specific time monday through friday. The webpage in which i am referring to is not my homepage. Please keep in mind that I am completely unfamiliar with scripting 

thanks for any assistance that you can provide

You could [setup a cronjob](https://help.ubuntu.com/community/CronHowto) that runs the following command:
```
/usr/bin/firefox "http://link/to/website/"
```

---

### Post by charlton2142 on 2010-03-08
Thanks for your help

---

