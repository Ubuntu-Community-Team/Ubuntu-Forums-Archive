---
title: "[Help] Script and Logs"
date: 2011-11-24
forum: General Help
---

### Post by chimi_12 on 2011-11-24
Hi all!

I've been doing a script to copy some files from a folder to other. I'll do this using crontab. This is the bash script code:

```

# Source Dir
ORIG=/data/data1/bases_datos/dia_1

# Dest dir
DEST=/data/data1/bases_datos/dia_2

LOG=/var/log/bck/sys.log

# Date & time
DYF=`date +%b" "%d" "%T`

echo -e "[$DYF] cp starts: dia_1 &#8594; dia_2 \n" >> $LOG
cp -pv $ORIG/* $DEST/ &>> $LOG
echo -e "\n[$DYF] cp ends copy task dia_1 &#8594; dia_2 \n\n" >> $LOG

```

The code is not complete, but this is for my question. I use the **"echo"** command to log the start and end of the copy, but I found that the start time and end are exactly the same time. See that the DYF variable is: ```
date +%b" "%d" "%T
``` and is called for the command echo. When the script ends the two echo commands are run at the same time (when cp ends) and this causes that the output of ```
date +%b" "%d" "%T
``` is exactly the same... hour, minute and second.

The question is: How can I log the real time for the first echo and second? What I want is to record the time when cp started and then when it ends. I tried the script, copying 100 MB sized files and using the tail -f command I could see that all outputs (both cp and echo commands) were written at the same time. 

I hope I explained correctly. Thanks in advance for all help you can give me.

---

### Post by matt_symes on 2011-11-24
Hi

```
<snip>
echo -e "[$(date +%b" "%d" "%T)] cp starts: dia_1 &#8594; dia_2 \n" >> $LOG
<snip>
echo -e "\n[$(date +%b" "%d" "%T)] cp ends copy task dia_1 &#8594; dia_2 \n\n" >> $LOG
```

Kind regards

---

### Post by San_SS! on 2011-11-24
matt is correct. The problem you are having is that the execution of the command to grab the datetime is only being executed once, in this line:
```
DYF=`date +%b" "%d" "%T`
```

Then you are just using the result of that execution which was stored in the variable DYF.

---

### Post by chimi_12 on 2011-11-25
Thanks matt and San!! I'll apply the changes to the script.

Kind regards!

---

