---
title: "Redirect output to a file and to the console"
date: 2011-04-11
forum: General Help
---

### Post by albox on 2011-04-11
I'd like to redirect the output to a file and to the console. I know about tee but the issue is that it waits until the first process finishes.

e.g
echo "hello world" | tee test.txt
first calls echo and then tee.

Is there a way to redirect "on the fly" ?

Thanks

---

### Post by mendhak on 2011-04-11
Hi, apologies if this is incorrect, but what about this:

echo "hello world" 1>&1>test.txt

---

### Post by deathadder on 2011-04-11
Opps, sorry misread that...removing what I put :)

---

### Post by deathadder on 2011-04-11
> **mendhak said:**
> Hi, apologies if this is incorrect, but what about this:

echo "hello world" 1>&1>test.txt
I would change that to:
```
echo "hello world" 2>&1 | tee test.txt
```
So that stderr is redirected to stdout and then to the file. 

As for doing it "on-the-fly" I don't know of anyway to do it apart from waiting for the first process.

---

### Post by vanadium on 2011-04-11
Not sure if that is what you are looking for, but "script" will record everything that happens in your console to a file. Start with "script", close with "exit".

---

### Post by albox on 2011-04-11
echo "hello world" 1>&1>test.txt  doesn't work. It only redirects the output to test.txt but nothing appears on the console.

I didn't know about script. It saves more information than what I need but that will definitely be useful. Thanks :D

---

