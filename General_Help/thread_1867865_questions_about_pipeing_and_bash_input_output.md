---
title: "questions about pipeing and bash input output"
date: 2011-10-23
forum: General Help
---

### Post by runny6play on 2011-10-23
I want to understand how these functions of bash work better and i would really like to know how to take the results of one command or a files contents and be able to input them into the command.
ive been trying with pkill.
```
#as root.
ps -e | grep chrome >a.txt

``` which works.
what ive tried (none of them work)
```
pkill <a.txt
``` 
```
cat a.txt >>pkill
```
and a couple other variations...
how can i use the txt files contents as an input for the command?
and can i do this without writing to a txt file...
inputing the results of one command directly into another?
thanks in advance

---

### Post by TeoBigusGeekus on 2011-10-23
> **runny6play said:**
> 
what ive tried (none of them work)
```
pkill <a.txt
``` 
```
cat a.txt >>pkill
```
and a couple other variations...
how can i use the txt files contents as an input for the command?
and can i do this without writing to a txt file...
inputing the results of one command directly into another?
thanks in advance

Both your examples are wrong.
pkill accepts an argument which is the pidof a procedure and sends it a signal. So, you can't divert output from a txt file to pkill.
To use a txt file for the input of a command  you use the syntax you posted
```
command < name.txt
```
To use the commands of one command into another you'd use something like this:
```
kill $(pidof opera)
```
The command 
```
pidof opera
```
finds the pid of opera (surprise, surprise)
and the command
```
kill
```
which accepts a pid as its argument, will take this pid and kill opera.

---

### Post by haqking on 2011-10-23
> **TeoBigusGeekus said:**
> Both your examples are wrong.
pkill accepts an argument which is the pidof a procedure and sends it a signal. So, you can't divert output from a txt file to pkill.
To use a txt file for the input of a command  you use the syntax you posted
```
command < name.txt
```
To use the commands of one command into another you'd use something like this:
```
kill $(pidof opera)
```
The command 
```
pidof opera
```
finds the pid of opera (surprise, surprise)
and the command
```
kill
```
which accepts a pid as its argument, will take this pid and kill opera.

+1

@ the OP, be careful what you do as root ;-)

---

### Post by runny6play on 2011-10-23
thanks. That makes sense.

---

### Post by Lars Noodén on 2011-10-23
There is also pkill:

```

pkill -x chrome

```

---

