---
title: "Conky Sensors in Fahrenheit"
date: 2011-12-12
forum: General Help
---

### Post by 1inux on 2011-12-12
I am using conky with the code:

${exec sensors | grep 'temp1' | cut -c15-16}°C / ${exec sensors | grep 'temp1' | cut -c32-36 }

This displays the current and critical temperature of the CPU in celcius/centigrade. How would i change that to fahrenheit without messing up the way that it looks on my desktop?

---

### Post by shakabra on 2011-12-13
[http://bit.ly/rJfFeN](http://bit.ly/rJfFeN)

---

### Post by N00b-un-2 on 2011-12-13
to get mine working I had to install lmsensors and I wrote a script that I execi in my conkyrc.

```
sensors -f | grep -A 1 'temp1' | cut -c15-25 | sed '/^$/d' | awk '{ print $1 }'
```

---

### Post by N00b-un-2 on 2011-12-13
execute that command in terminal.  It should print your CPU temp.  if it works for you, save is as a .sh file and then call that script in your .conkyrc

${execi 2 /home/user/temp.sh}

---

### Post by 1inux on 2011-12-13
Thanks for helping! but, i already figured it out.

${exec sensors | grep 'temp1' | cut -c15-16 | awk '{print ($1*9)/5+32}'}

---

### Post by N00b-un-2 on 2011-12-13
glad you figured it out!  not all boards support output using temp1.  the weird thing about my script is that on three computers in my house it works perfectly, but on my other laptop, it prints two outputs.  I can't figure that one out for the life of me.

---

