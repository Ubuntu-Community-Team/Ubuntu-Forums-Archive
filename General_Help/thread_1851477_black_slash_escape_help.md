---
title: "black slash escape help"
date: 2011-09-28
forum: General Help
---

### Post by Diametric on 2011-09-28
Hi,

In my script, I set a variable:

```
var="10.1.5.3 10.2.5.3 10.100.1.10 10.100.1.11"
```

That is then fed to a text file exactly as it appears - as one long sting of text.  I can't seem to figure out how to include hard returns on my variable.  What I would like to do is have the text file read like this:

10.1.5.3
10.2.5.3
10.100.1.10
10.100.1.11

How do a quote or escape to get eh proper results?

Thank you.

---

### Post by dave01945 on 2011-09-28
if you are echo'ing the output you can do it like this

```
var="10.1.5.3\n10.2.5.3\n10.100.1.10\n10.100.1.11"

echo -e $var

```

then that will output like this

```
10.1.5.3
10.2.5.3
10.100.1.10
10.100.1.11
```

hope that helps

---

### Post by ofnuts on 2011-09-28
> **Diametric said:**
> Hi,

In my script, I set a variable:

```
var="10.1.5.3 10.2.5.3 10.100.1.10 10.100.1.11"
```That is then fed to a text file exactly as it appears - as one long sting of text.  I can't seem to figure out how to include hard returns on my variable.  What I would like to do is have the text file read like this:

10.1.5.3
10.2.5.3
10.100.1.10
10.100.1.11

How do a quote or escape to get eh proper results?

Thank you.
Depends a bit what you want to do. "echo -e" interprets some backslash sequences:
```

->var="x\ny\nz"
->echo $var
***x\ny\nz***
->echo -e $var
[I][B]x
y
z
[/B][/I]->echo -e $var >out
->cat out
[I][B]x
y
z
[/B][/I]
```

---

### Post by dave01945 on 2011-09-28
if i remember correctly i think the OP was using echo to add these lines to resolve.conf

---

### Post by ofnuts on 2011-09-28
> **dave01945 said:**
> if i remember correctly i think the OP was using echo to add these lines to resolve.confThen the OP is in trouble because only the first 3 addresses of resolv.conf are used, IIRC.

---

### Post by dave01945 on 2011-09-28
are you because i was reading up about networking the other day and the person explaining said you could have a hundred if you wanted

--edit--

i correct myself the documentation i was reading was wrong it is only 3

---

### Post by Diametric on 2011-09-28
It's not that I need all four, I just want them in column format instead of a single line

---

### Post by Diametric on 2011-09-28
> **dave01945 said:**
> if you are echo'ing the output you can do it like this

```
var="10.1.5.3\n10.2.5.3\n10.100.1.10\n10.100.1.11"

echo -e $var

```then that will output like this

```
10.1.5.3
10.2.5.3
10.100.1.10
10.100.1.11
```hope that helps

That was exactly what I was looking for; thank you so much for your help.  I'm going to look into the backslash n and echo -e option

Cheers!

---

### Post by sisco311 on 2011-09-29
I'd use an array & printf:
```
[sisco@acme xtmp]$ nameservers=(10.1.5.3 10.2.5.3 10.100.1.10)
[sisco@acme xtmp]$ printf 'nameserver %s\n' "${nameservers[@]}"
nameserver 10.1.5.3
nameserver 10.2.5.3
nameserver 10.100.1.10

```

---

