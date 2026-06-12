---
title: "rotate resolution with ubuntu?"
date: 2010-08-30
forum: General Help
---

### Post by princeofnam on 2010-08-30
I used to be able to rotate the monitor resolution 90 degrees on my intel chipset card, but ever since i installed my nvidia 6800 i haven't been able to figure out how to rotate the resolution on the new panel. does anyone know if this is possible?

---

### Post by princeofnam on 2010-09-01
anyone

---

### Post by BobvanderPoel on 2010-09-01
> **princeofnam said:**
> anyone

does this work?

[https://nkour.wordpress.com/2006/12/13/rotating-the-screen-in-xorgnvidia/](https://nkour.wordpress.com/2006/12/13/rotating-the-screen-in-xorgnvidia/)

Now, can anyone tell me how to get my touchpad to work in the new mode?

---

### Post by princeofnam on 2010-09-02
sorry i'm a little confused did he grep that information for fun?

cat /etc/X11/xorg.conf | grep Rand -B 5 -A 5
even after running that

"xrandr -o left"
 doesn't work for me

sushi@Ragnarork:~$ xrandr -o left
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  154 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  14
  Current serial number in output stream:  14

---

### Post by BobvanderPoel on 2010-09-02
Not having tried this ... but I think the grep on the link I sent earlier shows what the file should look like. The important line appears to be

   Option "RandRRotation" "true" # for rotate to work

You will need to edit your xorg.conf file and add the above line in the required location. If you're not sure how/why you'll have to contact the guy on the linked site or google more for other examples.

Hope this helps :)

---

