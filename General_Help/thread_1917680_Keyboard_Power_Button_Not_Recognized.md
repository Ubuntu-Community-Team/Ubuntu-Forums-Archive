---
title: "Keyboard Power Button Not Recognized"
date: 2012-01-30
forum: General Help
---

### Post by Rebelli0us on 2012-01-30
I have a USB remote, it’s basically a mouse **and** a keyboard in one device. It works fine in Windows but Ubuntu doesn’t respond to pressing the power key. The power key should have identical function as the power button on the chassis.

It’s a Home Theater PC (HTPC) so I want to be able to suspend and resume by pressing the power button. Any ideas how to make the power button work in Linux?

---

### Post by Rebelli0us on 2012-02-20
Is this the Power button event handler?

/etc/acpi/powerbtn.sh

How does one make the power button on the keyboard work?

---

### Post by sudodus on 2012-02-20
Would it work and would you be satisfied to use a ***hot-key*** combination for suspend and resume?

---

### Post by Rebelli0us on 2012-02-20
> **sudodus said:**
> Would it work and would you be satisfied to use a ***hot-key*** combination for suspend and resume?

Thank you. I have a hot-key that works for suspend, but USB remote device can't send hot-keys. Why not have the power button working properly?

---

### Post by sudodus on 2012-02-20
> **Rebelli0us said:**
> Thank you. I have a hot-key that works for suspend, but USB remote device can't send hot-keys. Why not have the power button working properly?

Yes, but now the problem is to understand how to do that in linux. Until you solve that problem, maybe, if you use ***sticky keys*** (normally used for handicapped people), you can press the key combination in sequence and send the hot-key.

---

