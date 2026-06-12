---
title: "Calculations in a shell script"
date: 2011-04-21
forum: General Help
---

### Post by LeonHuzen on 2011-04-21
Hi there,

I'm having some troubles with my backup script, i want to delete the folder that is 2 weeks old. The problem is that when is use the folowing code:

YEAR=(date +%Y)
```
#Remove old directories
TWOWEEKSAGO=$(date +%U)-2|bc
echo $TWOWEEKSAGO
#rm -r /home/[my home directory]/Backups/$YEAR/$TWOWEEKSAGO/
```The $TWOWEEKSAGO variable is [empty] and not 14, but when I remove the -2|bc and I use:

```
echo $TWOWEEKSAGO-2|bc
```It echo's 14.

I need help at the following: the weeknumber at this moment minus 2, I have to fix it when the weeknumber is 1 or 2 so the directory of the last year will be deleted, but I will fix that later if you don't know that. 

Thanks in advance.

All honor to SeijiSensei for helping.

His solution was to set the date of 2 weeks ago as $TWOWEEKSAGO
So for anyone who comes across this thread:

```
#Remove old directories
TWOWEEKSAGO=$(date +%U --date='2 weeks ago')
rm -r /home/[my home directory]/Backups/$YEAR/$TWOWEEKSAGO/
```

[COLOR=Red]After 30 minutes with some help I coded the following to delete the folders of last year:[/COLOR]

```
#Remove old directories
TWOWEEKSAGO=$(date +%U --date='2 weeks ago')
if [ $TWOWEEKSAGO -eq 51 ]; then
    LASTYEAR=$(date +%Y --date='1 year ago')
    rm -r /home/[my home directory]/Backups/$LASTYEAR/$TWOWEEKSAGO/
elif [ $TWOWEEKSAGO -eq 52 ]; then
    LASTYEAR=$(date +%Y --date='1 year ago')
    rm -r /home/[my home directory]/Backups/$LASTYEAR/
else
    rm -r /home/[my home directory]/Backups/$YEAR/$TWOWEEKSAGO/
fi
```[COLOR=Red](if you copy it do not forget to replace "[my home directory]")[/COLOR]

---

### Post by dino99 on 2011-04-21
[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)

---

### Post by SeijiSensei on 2011-04-21
Use this:

```
TWOWEEKSAGO=$(date +%U --date='2 weeks ago')
```

The --date parameter is very flexible.

---

### Post by LeonHuzen on 2011-04-21
Thanks a lot SeijiSensei, I didn't know that was possible.

> **SeijiSensei said:**
> Use this:

```
TWOWEEKSAGO=$(date +%U --date='2 weeks ago')
```The --date parameter is very flexible.

---

### Post by Portmanteaufu on 2011-04-21
Here you go:

```

TWOWEEKSAGO=$( expr $(date +%U) - 2 )
echo $TWOWEEKSAGO

```

Or, alternatively:

```

TWOWEEKSAGO=$( echo $(date +%U) - 2 | bc )
echo $TWOWEEKSAGO

```

---

### Post by Locke_99GS on 2011-04-21
You don't need bc when doing integer math.

```

let TWOWEEKSAGO=$(date +%U)-2
echo $TWOWEEKSAGO #returns 14

```

or 

```

TWOWEEKSAGO=$((`date +%U` - 2))
echo $TWOWEEKSAGO  #returns 14

```

bc with variable complicates things a bit. If you really wanted to use it, you could use it like so:

```

TWOWEEKSAGO=$(echo $(date +%U)-2|bc)
echo $TWOWEEKSAGO #also returns 14

```

You need to keep track of order-of-operations. Use echo to return the output of the date command with "-2" appended = "16-2". "16-2" then gets piped to bc, which of course returns "14". "14" then is the only thing standing with nothing else to evaluate, so it is set to variable.

---

### Post by DaithiF on 2011-04-21
+1 for Sensei's solution.  

but if you wanted to get your version working, something like this:
```
week=$(( $(date +%U) - 2))

```
in other words, you need to nest the date command execution $(date ...) within an arithmetic operation $(( ... ))

then to test if week is less than zero and delete a previous years archive ...
```

if [[ $week -lt 0 ]]; then
   # do stuff here
fi
```

---

