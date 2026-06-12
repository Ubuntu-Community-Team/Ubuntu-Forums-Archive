---
title: "newbie command line start program with arg"
date: 2009-10-04
forum: General Help
---

### Post by TwinStinger on 2009-10-04
Hi there.

I'm a bit of a newbie and have a problem.
Sure there is a solution and hope that someone with the knowledge is willing to help me. 

I have a simple terminal application when started I have 10 options.

I start the program and then choose 1 option by typing 1-10.

I would like to be able to start the program with an option/argument so that it automatically starts with option 1, 2, 3 and so on.

So the program must be started and then have the input.

Maybe a script?

Or is there a way to do it from the command line?

If any thing is unclear (most likely, since the explanationis a bit hmmm) please ask.
 
Think it's written in python.

/ Twinned

---

### Post by unutbu on 2009-10-04
If the program is called test.py you can send a "1" to stdin by running:
```
test.py <<< 1
```

---

### Post by undecim on 2009-10-04
use: "echo 1 | application"

where 1 is the text that you would normally type by hand and application is the name you use to open your application.

---

### Post by undecim on 2009-10-04
> **unutbu said:**
> If the program is called test.py you can send a "1" to stdin by running:
```
test.py <<< 1
```
ooh, neat... Somehow, I never knew about that bash trick.

---

### Post by TwinStinger on 2009-10-04
undecim  

Marvelous!!

Exactly what I was looking for and it worked perfect.

Thank you VERY much.

And thank you unutbu. 

Amazingly swift answers from both of you.

It wasn't python, should have known since it didn't end with .py

---

