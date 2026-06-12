---
title: "Bluetooth"
date: 2012-10-02
forum: General Help
---

### Post by mgeorge94 on 2012-10-02
Hi! I use Ubuntu 12.04 on a Toshiba Satellite C660. I want to desactivate the bluetooth but I don't know how. Even if I turn off the bluetooth, at the next restart is on again. Plese help and sorry for my bad language.

---

### Post by raja.genupula on 2012-10-02
Remove bluetooth service from startup applications , i think you might have some hardware switch to control

---

### Post by mgeorge94 on 2012-10-02
No, I tried but there is empty.

---

### Post by raja.genupula on 2012-10-03
open your terminal and type this 

```
sudo apt-get install bum
```

there you can manage all your services .

---

### Post by jerrrys on 2012-10-03
Hi raja :)

@OP:  Should just be able to uncheck from [auto start list]("https://help.ubuntu.com/community/AddingProgramToSessionStartup#To_stop_an_application_from_running_at_startup").

---

### Post by raja.genupula on 2012-10-03
> **jerrrys said:**
> Hi raja :)

@OP:  Should just be able to uncheck from [auto start list]("https://help.ubuntu.com/community/AddingProgramToSessionStartup#To_stop_an_application_from_running_at_startup").

hi @Jerry 

Jerry , but Bum some what advances one .may be he could get some more information from them .

---

### Post by SlugSlug on 2012-10-03
```
sudo update-rc.d -f bluetooth remove
```

---

