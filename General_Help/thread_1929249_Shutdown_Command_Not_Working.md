---
title: "Shutdown Command Not Working"
date: 2012-02-21
forum: General Help
---

### Post by w201 on 2012-02-21
When I  execute the shutdown command...

```
sudo shutdown now
```

It initiates, but comes to a dead stop on the splash screen with the blue sun. Shutdown through GUI works fine. Any tips on how to troubleshoot whatever is going on?

Thanks!

---

### Post by matt_symes on 2012-02-21
Hi

Try this.

```
sudo shutdown -h now
```

Kind regards

---

### Post by Khayyam on 2012-02-21
Matt ...

You need to provide the '-h' (halt/poweroff) switch

```
sudo shutdown -h now
```HTH ... khay

---

### Post by w201 on 2012-02-21
Awesome! That was an easy one. Thank you guys!

---

