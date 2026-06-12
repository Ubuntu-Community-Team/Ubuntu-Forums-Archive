---
title: "bash help"
date: 2009-11-10
forum: General Help
---

### Post by prem1er on 2009-11-10
I want to see if a grep statement has returned anything. I am saving the results of a grep command to a variable. If that grep command has not returned any results i.e. the _test variable is empty I want to do something. How would I do this?  Thanks.

```
   
   _test=`grep -x "$_accountNum" visibility-accounts.dat | cut -d "|" -f 1`
   if [ _test is empty ]; then
      echo "$_accountNum"
   fi

```

---

### Post by prem1er on 2009-11-10
I found this.  Is it the correct way of doing it?

```
  
    _test=`grep -x "$_accountNum" visibility-accounts.dat | cut -d "|" -f 1`
   if [ "$_test" == "" ]; then
      echo "$_accountNum"
   fi
```

(checking for an empty string)

---

### Post by sisco311 on 2009-11-10
```
if [ ! $_test ]; then
```
or
```
if [ -z $test ]; then
```


for more info:
```
man bash | less --pattern\="CONDITIONAL EXPRESSIONS"
```

[http://tldp.org/LDP/abs/html/comparison-ops.html]("http://tldp.org/LDP/abs/html/comparison-ops.html")

---

### Post by alphaniner on 2009-11-10
If all you want is to see if grep returned something (and you don't care what it returned):

```
grep foo bar
if [ $? = 0 ]
then
     grep returned something
else
     grep returned nothing
fi
```

```

if ( `grep foo bar &>/dev/null` )
then
     grep returned something
else
     grep returned nothing
fi
```

$? is the exit status of the last command, and grep returns 0 if it finds a match.  This won't work if you pipe the output of to cut.  In fact it might be completely useless to your current predicament.

---

