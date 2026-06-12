---
title: "Run script before/after suspend"
date: 2011-03-25
forum: General Help
---

### Post by wh1sp3r on 2011-03-25
Hello,
i have a problem with running script before/after suspend.

I tried to use pm-utils for that, i just added my script and script is executed but commands which i need not.

```

#!/bin/sh
##
## suspend-example.sh
##
case $1 in
   suspend)
     ## COMMANDS THAT YOU WISH TO RUN BEFORE SUSPEND
     killall -w -v rdesktop;
   ;;
   resume)
     ## COMMANDS THAT YOU WISH TO RUN AFTER RESUME     
     rdesktop 10.0.0.210 -u Username -p *password* -k cs -f -N -z -x l -P -5";
   ;;
   hibernate)
     ## COMMANDS THAT YOU WISH TO RUN BEFORE HIBERNATE
     
   ;;
   thaw)
     ## COMMANDS THAT YOU WISH TO RUN AFTER RESUME FROM SUSPEND TO DISK
     
   ;;
esac 

```Interesting thing is, when i use for example touch command, it created file , so i am sure, my script is executed .. this is not executed. Log did not say anything why it didn't executed. only success :)

Why i need it. When i am connectedd via rdesktop and i would like to go away from pc, PC automaticly turn PC into sleep, so i need to kill rdesktop . and after sleep, i would like to run it again. 

How to do it propertly ?

Thank you for help.

---

### Post by wh1sp3r on 2011-03-29
no reply 4 days, so bump ;-)

---

### Post by dfacto on 2011-09-18
Why is there are trailing " at the end of the rdesktop line?

---

