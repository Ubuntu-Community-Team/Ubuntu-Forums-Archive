---
title: "need help with bash line formatting"
date: 2011-02-02
forum: General Help
---

### Post by RaginRob on 2011-02-02
Hi there,

suppose I have a line that looks like this:

```
13:47:54.830735 192.168.168.65.54487 85.214.141.246.80: 336
```and I want it to look like that:

```
13:47:54 192.168.168.65 85.214.141.246 336
```The first line is already the output of a long expression with a lot of piping and formatting with awk etc., but now I'm somehow stuck with the rest. Can you give me a clue how to achieve it? Thanks for your help!

PS: The command that outputs the lines looks like that at the moment:

```
tcpdump -n | grep 192.168.168. | grep -v "length 0" | grep length | awk '{print $1,$3,$5,$(NF)}' | grep 192.168.168 | grep -v Request
```

---

### Post by DaithiF on 2011-02-02
Hi, using sed, something like this:
```
echo "13:47:54.830735 192.168.168.65.54487 85.214.141.246.80: 336" | sed 's/\.
[0-9]\+[ :]/ /g'
13:47:54 192.168.168.65 85.214.141.246  336

```

the sed expression says find a period followed by a string of digits and terminating in either a space or a : character, and replace it all with a space

---

### Post by djeikyb on 2011-02-02
You can learn more about sed, awk, and regular expressions at this excellent website:

[http://www.grymoire.com/Unix/](http://www.grymoire.com/Unix/)

---

