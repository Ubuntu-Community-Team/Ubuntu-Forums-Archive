---
title: "Conky - Fan Stats"
date: 2011-12-12
forum: General Help
---

### Post by faixan on 2011-12-12
hi, new to conky, still figuring out most of stuff...
i downloaded a configuration, modified it a bit, every thing is working fine, except i can't seem to have the "fanspeed" OR "fanstat" in any way... i've checked up on google, nothing works... 
currently i've this line in .conkyrc for fanstate;
```
${color FFFFFF}${font caviar dreams:size=8}Fan State: ${acpifan}
```
it's output is:
```

Fan State: [color=red]no fans?[/color]

```
i've a Dell Inspiron 1545.

---

### Post by Frogs Hair on 2011-12-12
Do you have  lm-sensors installed ? ```
sudo apt-get install lm-sensors
```  ```
 sudo sensors-detect
``` Answer yes to all questions.

---

### Post by faixan on 2011-12-13
> **Frogs Hair said:**
> Do you have  lm-sensors installed ? ```
sudo apt-get install lm-sensors
```  ```
 sudo sensors-detect
``` Answer yes to all questions.

except this every thing is a **no**... :s


```

Intel Core family thermal sensor...                         Success!
    (driver `coretemp')

```

---

### Post by faixan on 2011-12-14
> **Frogs Hair said:**
> Do you have  lm-sensors installed ? ```
sudo apt-get install lm-sensors
```  ```
 sudo sensors-detect
``` Answer yes to all questions.


apologies, i didn't say "yes" to the last thing, /etc/modules update i didn't do earlier, here's the output after saying "yes" to that as well


```

[11:28 AM] user@ubuntu:~ $sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +53.5°C  (crit = +93.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +52.0°C  (high = +90.0°C, crit = +90.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +52.0°C  (high = +90.0°C, crit = +90.0°C) 

```

---

