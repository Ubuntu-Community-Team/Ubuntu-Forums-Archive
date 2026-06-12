---
title: "Upgrade 10.10"
date: 2010-11-01
forum: General Help
---

### Post by charlton2142 on 2010-11-01
Hey I have been waiting to upgrade to Ubuntu 10.10 for a while now so today I checked to see when it would be released and apparently it has been out for a while now. I would like to upgrade but my update manager is not asking if I would like to do so. I checked online and it also said to check to Synaptic Package Manager and i couldn't find the release there either. I do not have a dvd burner so i can't install it that way either please help me to get the Update Manager to recognize that there is an update available.

---

### Post by alexandari on 2010-11-01
If you wanna upgrade the distro

```
 sudo apt-get dist-upgrade 
```

---

### Post by ubunterooster on 2010-11-01
or ```
gksu update-manager -d
```

---

### Post by charlton2142 on 2010-11-01
It said there is no upgrade available

---

### Post by ubunterooster on 2010-11-01
post the result of ```
uname -a
```

---

### Post by cpmman on 2010-11-01
You may be on LTS releases only - check:-

System - Administration - Update Manager - Settings - Normal releases

---

### Post by charlton2142 on 2010-11-04
Thank you, I was only subscribing to lts releases

---

