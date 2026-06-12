---
title: "My computer sometimes locks up hard when booting"
date: 2012-04-22
forum: General Help
---

### Post by Erunur on 2012-04-22
This is a very sad love story about a boy and his computer :-({|= Its a story of love, joy, pain, suffering, depression, and anger. Side effects of viewing this may include back pain, vomiting, itchiness, swelling of the tongue, and some rash on your arm.


 I recently switched to Ubuntu11.10 and I love it a lot ( I'm a Linux man). But recently over the past month or so sometimes my computer locks up hard while booting.

1st I turn on my computer and let the BIOS flash by. Then The boot loader comes up and asks me what I want to boot (windows xp or Ubuntu). Then the screen goes completely purple (which is normal) then the Ubuntu logo comes up with all the progress dots red and fixed (not turning to white, which is also normal... I think).
     Then Here is where the moment of truth happens. After a few seonds of a fixed boot logo the login screen comes up and everything is fine. BUT when it does a hard lock up somwtimes, it just locks up at the boot logo and Just hangs there. Nothing seems to make it come out of that trans. All I can do is either stare at an absolutly beautiful boot logo or pull the plug out of the wall and turn it back on to boot fine again ](*,)

---

### Post by matt_symes on 2012-04-23
Hi

Check your log files after it does not boot. You can do this from a LiveCD/USB. They may contain some clues.

```
/var/log/syslog
```

```
/var/log/dmesg
```

Kind regards

---

