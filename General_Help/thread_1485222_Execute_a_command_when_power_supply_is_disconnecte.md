---
title: "Execute a command when power supply is disconnected?"
date: 2010-05-16
forum: General Help
---

### Post by dementic on 2010-05-16
Is there a way to do that since the computer and OS is aware that the power supply is disconnected.

---

### Post by quadproc on 2010-05-16
> **dementic said:**
> Is there a way to do that since the computer and OS is aware that the power supply is disconnected.
It is possible to execute an epilog procedure as a result of a power failure if you have a UPS that can signal the computer when a power loss occurs and if you are running a daemon which watches for the power fail signal.  The daemon can then invoke code of your choice.

If you have a very quick executing epilog procedure then you might be able to execute it during the holdup time of the computer's power supply.  I would not attempt this without a real time operating system.

quadproc

---

### Post by dementic on 2010-05-16
I was thinking a laptop power supply. That means when the computer switches on battery. Maybe I didn't explained well. Thank you for your answer.

Because I have the problem of hard disk head loading/unloading too frequently when on battery. The hdparm -B passes from 254 to 128 once the cable is disconnected. So I want to execute the command:
```

(sudo) hdparm -B 254 /dev/sda
``` when the charger is disconnected.

---

### Post by StuartN on 2010-05-16
> **dementic said:**
> Is there a way to do that since the computer and OS is aware that the power supply is disconnected.

GKrellM should hook into all that signalling and allow you to run standard procedures or custom scripts: [http://members.dslextreme.com/users/billw/gkrellm/gkrellm.html](http://members.dslextreme.com/users/billw/gkrellm/gkrellm.html)

---

### Post by dementic on 2010-05-16
I was wondering is there was a file with predefined actions like for suspend or hibernate, or maybe a smaller daemon than GKrellM to keep a light system.

---

### Post by dementic on 2010-05-16
Ok I made a script with the help of acpi -a which gives the power status if someone need it :

```
#!/bin/sh
while [ 1 ]; do
dfds=$(acpi -a)
if [ "$dfds" = "Adapter 0: off-line" ]; then
{
   hdparm -B 254 /dev/sda
}
fi
sleep 10
done
```

Thanks

---

### Post by rmartin16 on 2010-05-23
I think this is the solution you were looking for

[http://ubuntuforums.org/archive/index.php/t-875263.html](http://ubuntuforums.org/archive/index.php/t-875263.html)

---

