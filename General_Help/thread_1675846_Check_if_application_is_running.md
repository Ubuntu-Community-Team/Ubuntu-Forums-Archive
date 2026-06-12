---
title: "Check if application is running"
date: 2011-01-26
forum: General Help
---

### Post by grackleman on 2011-01-26
Hi
I'd like to know if there is a script that can check and see if an application has been closed (I don't know a great deal about bash programming).

I'm running an organ programme with this script.

/usr/bin/jackd -r -t5000 -dalsa -dhw:0 -r44100 -p1024 -n2 -P &
java -jar /home/user/jOrgan/jorgan.jar &
jack-rack -s space space &
jconvolver reverb.conf &
./connect.sh

I'd like to have a script killall jackd, jack-rack, and jconvolver after I close jOrgan. Jorgan can't be at the end of this script with no and sign because it has to be running before './connect.sh' is run.

Thanks
Peter

---

### Post by ajgreeny on 2011-01-26
Try ```
ps aux | grep <name>
```using the apps name (jorgan?) where I put <name> of course.

---

### Post by grackleman on 2011-01-26
Thanks
That certainly tells me if java is running!
Now I have to learn how to turn it into a script such as (in plain 'basic' type English)

sleep 5
if java running then return
killall jackd etc.

Lots of learning!

---

