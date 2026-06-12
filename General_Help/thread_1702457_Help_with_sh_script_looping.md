---
title: "Help with sh script looping"
date: 2011-03-07
forum: General Help
---

### Post by polardude1983 on 2011-03-07
So I was wondering is it possible to loop a script until i hit the Esc key? I have seen the do or while true thing. But any help would be appreciated here is the script

```
#!/bin/bash

sleep 5 &&
xdotool mousemove 650 600 click 3 &&
sleep 1 &&
xdotool key "4" &&
sleep 1 &&
xdotool click 3 &&
sleep 1 &&
xdotool key "3" &&
sleep 1 &&
xdotool click 3 &&
sleep 1 &&
xdotool key "2" &&
sleep 1 &&
xdotool key "Return"

```

---

### Post by Habitual on 2011-03-08
may be help here.
[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

---

### Post by aeiah on 2011-03-08
```
#!/bin/bash

[B]while [ 1 ]
do[/B]

sleep 5 &&
xdotool mousemove 650 600 click 3 &&
sleep 1 &&
xdotool key "4" &&
sleep 1 &&
xdotool click 3 &&
sleep 1 &&
xdotool key "3" &&
sleep 1 &&
xdotool click 3 &&
sleep 1 &&
xdotool key "2" &&
sleep 1 &&
xdotool key "Return"

**done**

```

---

