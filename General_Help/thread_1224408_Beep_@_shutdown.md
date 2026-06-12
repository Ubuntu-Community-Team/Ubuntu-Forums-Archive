---
title: "Beep @ shutdown?"
date: 2009-07-27
forum: General Help
---

### Post by running_rabbit07 on 2009-07-27
Is there any way to stop the beeps at shutdown. They get right nerve racking when it beeps 3 or 4 times really fast when shutdown is started. 

Using 9.04JJ on AMD64 Lenovo System.

Thanks for the help.

---

### Post by t4thfavor on 2009-07-27
Inside of the sound preferences there is sometimes a mixer for system beep. I have in the past shut it off(muted) and the beeping stoped. Though I do believe there are boards that do not have this capability.

---

### Post by damis648 on 2009-07-27
Open a terminal and type the following:
```
sudo rmmod pcspkr
sudo su -c "echo 'blacklist pcspkr' >> /etc/modprobe.d/blacklist.conf"
```

(Yes, the sudo su -c is weird, but sudo does not accept '>>' directly)

---

### Post by t4thfavor on 2009-07-27
Explanation:
Removes the pcspkr module from the kernel (requires sudo for elevated privs.)
```

sudo rmmod pcspkr

```
Prevents the module pcspkr from getting loaded on boot by adding an entry to the file /etc/modprobe.d/blacklist.conf
```

sudo su -c "echo 'blacklist pcspkr' >> /etc/modprobe.d/blacklist.conf"

```

---

### Post by running_rabbit07 on 2009-07-27
Thanks to all for the fixes and thanks for the explanation.

---

### Post by running_rabbit07 on 2009-08-14
And this does work for Karmic, too.

---

