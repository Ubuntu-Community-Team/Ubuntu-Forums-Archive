---
title: "Conky and Temp"
date: 2010-02-09
forum: General Help
---

### Post by Mr Nemo on 2010-02-09
Acpitemp is not working in Conky. Any other way for conky to show temp?

---

### Post by VCoolio on 2010-02-09
Try this: install lm-sensors, then "sudo sensors-detect" and answer 'yes' to everything and see if it detects any sensors. Then get output in conky with lines like this:
${execpi 10 sensors | grep CPU | cut --characters 15-16}°C
or 
${execpi 10 sensors | grep CPU | awk '{print $3}'}

---

### Post by Mr Nemo on 2010-02-13
Installed im-sensors and did everything else. Those two lines of code don't do anything. Any other suggestions?

---

### Post by Mr Nemo on 2010-02-13
bump

---

### Post by VCoolio on 2010-02-14
Try sensors in a terminal, then import it in conky with lines like I gave. To check sensors in a terminal run "sensors", it should give a lot of output. Now get the pieces you want with grep / awk / cut etc like this:

sensors | grep CPU | cut --characters 15-16

which pipes the output of 'sensors' to grep, which takes only lines containing 'CPU', which should be just one line, then pipes that to cut which cuts characters 15-16 which should be the temp value.

If it doesn't work, post 'sensors' error output or be specific on what doesn't work. Have fun.

---

### Post by tad1073 on 2010-02-14
```
TEMP: ${acpitemp}C
```

---

