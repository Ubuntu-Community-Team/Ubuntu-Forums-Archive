---
title: "shell script with an auto shutoff"
date: 2011-08-21
forum: General Help
---

### Post by Fenderian_Mayhew on 2011-08-21
I want to make shell scripts that auto kill after a certain amount of time, or at a certain time. if this is possable, what should i use in the script.

---

### Post by spiky001 on 2011-08-21
You can use ```
sleep 10
``` has to be positive

---

### Post by raja.genupula on 2011-08-21
> **spiky001 said:**
> You can use ```
sleep 10
``` has to be positive

didn't get it . can you please elaborate it .

---

### Post by spiky001 on 2011-08-21
I dont know shell scripting sorry, but I heard of the sleep command I found an example on google, [http://www.devdaily.com/blog/post/linux-unix/bourne-shell-script-that-shows-while-loop-sleep-command](http://www.devdaily.com/blog/post/linux-unix/bourne-shell-script-that-shows-while-loop-sleep-command)  also after the sleep command you could add "kill" what ever process you want to end.   Maybe post your script someone might help with it

---

### Post by spiky001 on 2011-08-21
I used this one for a problem I had
```

#!/bin/bash
 sudo ifconfig eth0 down
 sleep 5
 sudo ifconfig eth0 up
 firefox &
```

---

### Post by raja.genupula on 2011-08-21
oh i think your using the script for disconnecting your eth0 connection for 10 sec and re-enabling after 10 sec . nice script . ok i have a modem with connection name as " R " . so how can i down it . i have tried as you given . but i got as this .  



```
assassin@genupulas:~$ sudo ifconfig R down
R: ERROR while getting interface flags: No such device

```

thanks in advance , :D

---

### Post by spiky001 on 2011-08-21
That was an example for "sleep" command

---

