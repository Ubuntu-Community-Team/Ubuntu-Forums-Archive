---
title: "automate a script"
date: 2011-06-19
forum: General Help
---

### Post by nos09 on 2011-06-19
hey guys i want to run a specific script after a particular 'uptime' say after 30min with root privileges. 

i looked on the Google but they gave me a 'crontab' results, i am a little familiar with it but not sure if that can do this since it would run on a actual specific time, right ?!

---

### Post by nothingspecial on 2011-06-19
Why not run it as a startup script and use sleep.

---

### Post by nos09 on 2011-06-19
> **nothingspecial said:**
> Why not run it as a startup script and use sleep.

can you explain the sleep part ?

---

### Post by prodigy_ on 2011-06-19
For root privileges you can run your script from **rc.local**. The sleep part is (assuming bash):
```

#!/bin/bash
sleep 30m # Wait for 30 minutes

<put your code here>

```

---

### Post by nothingspecial on 2011-06-19
You put sleep <number>

then m for minutes h for hours or d for days at the beginning of the script - it defaults to seconds

The script will wait for that amount of time before continuing.

so for your example of 30 minutes put

sleep 30m

at the beginning of your script.

Type ```
sleep 5; ls
```

in your terminal to see what I mean.

---

### Post by nos09 on 2011-06-19
> **nothingspecial said:**
> You put sleep <number>

then m for minutes h for hours or d for days at the beginning of the script - it defaults to seconds

The script will wait for that amount of time before continuing.

so for your example of 30 minutes put

sleep 30m

at the beginning of your script.

Type ```
sleep 5; ls
```

in your terminal to see what I mean.

thank you guys !!

---

