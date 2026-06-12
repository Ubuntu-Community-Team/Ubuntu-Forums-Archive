---
title: "/etc/init.d/gdm stop &lt;-- does not work"
date: 2010-03-17
forum: General Help
---

### Post by pinenut on 2010-03-17
I am trying to install the newest NVIDIA driver.

```

 2) press ALT+CONTROL+F1,
 3) sudo su
 4) password
 5) /etc/init.d/gdm stop
```But /etc/init.d/gdm stop does not work. I get a message that this is no longer a valid command or something to that effect. Then I was told to use the 'service' command.

```
 service gdm stop
```It does not work, either. 

How do I kill the active x-server?

---

### Post by ratcheer on 2010-03-17
I think it worked when you ran it from /etc/init.d/gdm. Those messages are just informing you of the new way to do it. Then, it failed the second time because it was already stopped.

Tim

---

### Post by ratcheer on 2010-03-17
If you really can't stop it, reboot to recovery mode and select "drop to a root prompt". Then, you can install the driver and reboot.

Tim

---

### Post by pinenut on 2010-03-17
> **ratcheer said:**
> If you really can't stop it, reboot to recovery mode and select "drop to a root prompt". Then, you can install the driver and reboot.

Tim

Thank you for your help.
/etc/init.d/gdm stop did not work because the driver installation program kept complaining about the x-server being active or something to that effect. I will try your second suggestion and will let you know how it goes. ;)

The second suggestion worked for me and I finally installed the driver.

---

