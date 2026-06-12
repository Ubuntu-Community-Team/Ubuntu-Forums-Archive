---
title: "Scanning function not working on Brother MFC215-c"
date: 2009-08-11
forum: General Help
---

### Post by wordsmyth on 2009-08-11
My Brother MFC215-c works fine as a printer, but Ubuntu 9.04 doesn't recognise the scanning function- DEVICE NOT FOUND. I've downloaded t& installed the appropriate SCAN SOFTWARE from Brother - SCAN KEY & DRIVER - to no avail. The scanning function still is not recognised. Any advice out there?:(

---

### Post by plucky on 2009-08-11
> **wordsmyth said:**
> My Brother MFC215-c works fine as a printer, but Ubuntu 9.04 doesn't recognise the scanning function- DEVICE NOT FOUND. I've downloaded t& installed the appropriate SCAN SOFTWARE from Brother - SCAN KEY & DRIVER - to no avail. The scanning function still is not recognised. Any advice out there?:(

Check driver installed correctly.Open a terminal and ```
$ dpkg -l | grep Brother
ii  brscan2                                    0.2.4
      Brother Scanner Driver
$

```

Did you alter the permissions for USB devices? See [link](http://solutions.brother.com/linux/en_us/instruction_scn1c.html#u9) to change permissions for USB devices in Ubuntu 9.04.


Good Luck

---

### Post by wordsmyth on 2009-08-26
> **plucky said:**
> Check driver installed correctly.Open a terminal and ```
$ dpkg -l | grep Brother
ii  brscan2                                    0.2.4
      Brother Scanner Driver
$

```

Did you alter the permissions for USB devices? See [link](http://solutions.brother.com/linux/en_us/instruction_scn1c.html#u9) to change permissions for USB devices in Ubuntu 9.04.


Good Luck

Tried this. Message said files already installed. And sure enough, I checked synaptic and found them there. But scanning still won't work. Grrrrrrrrrrr

---

### Post by plucky on 2009-08-26
> Tried this. Message said files already installed. And sure enough, I checked synaptic and found them there. But scanning still won't work. Grrrrrrrrrrr

What about the second part > Did you alter the permissions for USB devices? See link to change permissions for USB devices in Ubuntu 9.04.

Also add your <username> to the scanner group using **System > Administration > Users and groups** Then either logout and login or reboot.

Open a terminal and post output of ```
scanimage -L
```


Good Luck

---

