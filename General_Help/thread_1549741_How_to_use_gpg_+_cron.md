---
title: "How to use gpg + cron?"
date: 2010-08-10
forum: General Help
---

### Post by joseba on 2010-08-10
Hello, I have this script:

#!/bin/bash

## cifro un fichero
/usr/bin/gpg --encrypt --batch --no-tty --yes --recipient Mypubkey /home/joseba/salida.txt > /home/joseba/logcronjob.txt
#EOF

If I use the line 

joseba@server$ /usr/bin/gpg --encrypt --batch --no-tty --yes --recipient Mypubkey /home/joseba/salida.txt > /home/joseba/logcronjob.txt

I dont have problems, salida.txt has encrypted

But by crontab -e (for user joseba) dont work and dont encrypt nothing
If I use 'sudo crontab -e' same result, dont work

Mypubkey exists

On logcronjob.txt nothing, 0 bytes

I think env its ok for the users


Any idea please?


Sorry for my english!
Juanjo A.

---

### Post by DaithiF on 2010-08-10
I don't know, but would suggest you capture stderr output in addition to stdout to see if any errors are being output.
so change the 
```
> /home/joseba/logcronjob.txt
```
to
```
&> /home/joseba/logcronjob.txt
```

---

### Post by joseba on 2010-08-10
> **DaithiF said:**
> I don't know, but would suggest you capture stderr output in addition to stdout to see if any errors are being output.
so change the 
```
> /home/joseba/logcronjob.txt
```
to
```
&> /home/joseba/logcronjob.txt
```
Ok but /home/joseba/logcronjob.txt = 0 bytes
No error detected

Thx. 
Juanjo A.

---

### Post by DaithiF on 2010-08-10
works fine for me from cron and from command line.  is you cron working ok, e.g. if you put in a simple job like this:
```
* * * * * echo "testing" > /home/joseba/crontest.out
```
does it create the crontest file?

---

### Post by joseba on 2010-08-10
> **DaithiF said:**
> works fine for me from cron and from command line.  is you cron working ok, e.g. if you put in a simple job like this:
```
* * * * * echo "testing" > /home/joseba/crontest.out
```
does it create the crontest file?
Yes, the script is more complex.
The only part that does not work is the command gpg ...
From command line the script is ok.

Thx
Juanjo A.

---

### Post by joseba on 2010-08-11
I think the problem is the key. In this example I use a key without Spanish characters (ñ, accents, ...) but in the real script, the key has accents.

Un saludo
Juanjo A.

---

