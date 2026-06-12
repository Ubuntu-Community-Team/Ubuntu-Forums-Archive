---
title: "running a command in terminal upod start up?"
date: 2011-05-14
forum: General Help
---

### Post by Trimatrix on 2011-05-14
I am relatively new to linux but i need to run a command in the terminal so i can prevent wireless power save from happening every time i switch to battery power. I dont really want to go into the terminal every time i switch to battery mode so i want to be able to launch this command upon start up:

```
sudo iwconfig wlan0 power off
```

---

### Post by dcstar on 2011-05-14
> **Trimatrix said:**
> I am relatively new to linux but i need to run a command in the terminal so i can prevent wireless power save from happening every time i switch to battery power. I dont really want to go into the terminal every time i switch to battery mode so i want to be able to launch this command upon start up:

```
sudo iwconfig wlan0 power off
```

```
gksudo gedit /etc/rc.local
```

---

### Post by Trimatrix on 2011-05-14
thanks

---

