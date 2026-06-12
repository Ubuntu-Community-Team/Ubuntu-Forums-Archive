---
title: "ping &amp; bash"
date: 2009-08-15
forum: General Help
---

### Post by andru183 on 2009-08-15
im just getting to grips with bash and its getting frustrating, i need a thing to run and count ping and i got it to do it once but nomore

#!/bin/bash
ping -c 64.233.161.99 -i 400 
if [ $? -eq 1 ]
then
    zenity --info --text "Failed to reach google, panic!"
fi

i got that from another forum cause my one didnt do anything, any help ill love you or if you have anything better to trow cool

---

### Post by kaibob on 2009-08-15
I believe the ping command should be more in the format of the following. The -c option has to have a value. You have set an -i (interval) value of 400 seconds.

```
ping -c 2 -i 1 64.223.161.99
```

Your shell script has to be modified as follows to work. You need to change the -c and -i options to meet your needs. If you are going to run this script from a terminal window, then I would just echo the good or bad results as suggested by bchurchill in the next post. Otherwise, the zenity dialog is probably needed. 

```
#!/bin/bash
ping -c 2 -i 1 64.223.161.99
if [ $? -ne 0 ] ; then
   zenity --info --text "Failed to reach google, panic!"
fi
```

---

### Post by bchurchill on 2009-08-15
I think this is what you want:

```

#!/bin/bash
ping -c 1 -q 64.223.161.99
if [ $? -eq 0 ]; then
    echo "good"
else
    echo "bad"
fi

```

The -c option specifies the count, which must immediately follow
the -i option specifies an interval, which you probably don't need
the -q suppressed output, which you probably want.

---

