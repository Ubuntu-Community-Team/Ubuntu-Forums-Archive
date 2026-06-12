---
title: "Firefox Startup"
date: 2009-08-09
forum: General Help
---

### Post by paranoidandroidz on 2009-08-09
I have firefox to run at startup but it starts before my netowrk is connected.

Is there a way of delaying the start of firefox?

Many thanks

---

### Post by paranoidandroidz on 2009-08-09
the inevitable, as soon as I post I find the answer


Name: Firefox
Command: sh -c "sleep 30 && firefox &"

---

### Post by gamblor01 on 2009-08-09
There sure is -- you just need to make a script that tells the system to wait some specified amount of time before it launches.  For example, put a script like this somewhere (in your home directory, or create a directory...whatever you want):

```

#!/bin/bash

sleep 30
firefox &

```

Now have Ubuntu call that script on startup (though you need to make sure it's executable so use something like chmod +x <script_name>).  The script will do nothing for 30 seconds and then it will kick off firefox.

---

### Post by gamblor01 on 2009-08-09
Or yeah...your answer there is probably easier.  ;)

---

### Post by Narada on 2009-08-09
Can you paste the relevant lines of your startup script for us? You probably can get away with just adding a sleep <#>.

-edit-
Nevermind, already taken care of. :P

---

