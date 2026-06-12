---
title: "Stop Shell from closing automatically"
date: 2009-11-08
forum: General Help
---

### Post by Acidianus on 2009-11-08
Hi Guys!
Noob question here: I have created a launcher in the Applications Menu (Xubuntu 9.10) with a command to execute an application in a terminal. Launching my application from the Menu now works great, the only problem is, that I would like the terminal to stay open after the application is executed. Normally it closes automatically after executing my application. Any ideas?

---

### Post by Primefalcon on 2009-11-08
> **Acidianus said:**
> Hi Guys!
Noob question here: I have created a launcher in the Applications Menu (Xubuntu 9.10) with a command to execute an application in a terminal. Launching my application from the Menu now works great, the only problem is, that I would like the terminal to stay open after the application is executed. Normally it closes automatically after executing my application. Any ideas?
run the application from the terminal

or you could ask for user input....

---

### Post by Druke on 2009-11-08
he's looking for a shortcut to display something.

I'm not sure how to help. Perhaps if you were more clear with what your are doing, we could give better suggestions.

---

### Post by Primefalcon on 2009-11-08
> **Druke said:**
> he's looking for a shortcut to display something.

I'm not sure how to help. Perhaps if you were more clear with what your are doing, we could give better suggestions.
as I said if you ask for user input through the terminal the terminal will stay open until you hit enter....

example

```
#!/bin/bash
echo "hi there"
read why

```

try it, not really what it's meant for... but..

---

### Post by Druke on 2009-11-08
A hah! I see, so make a bash script to execute the command and then do the input request.

---

### Post by Primefalcon on 2009-11-08
> **Druke said:**
> A hah! I see, so make a bash script to execute the command and then do the input request.
yup, as I said its not what it's meant for but it works, kinda like the c++ cin command I guess if you don't want the window to close

---

### Post by benj1 on 2009-11-08
i dont have xubuntu but i would have thought there would be a flag to keep the terminal open after it has finished processing, have a look at the man page

---

### Post by Druke on 2009-11-08
I looked at the man pages myself, but nothing lept at me.

---

### Post by Primefalcon on 2009-11-08
> **Druke said:**
> I looked at the man pages myself, but nothing lept at me.
I don't think there is a way, if your script creates a terminal, it closes on script completion, the only way is to pause the script so to speak by asking for user input, sleep could work as well too, or you could do an infinite loop, asking for user input would probably be the easiest though since you could close it just by hitting enter

---

### Post by benj1 on 2009-11-08
sorry i thought there would be a -H (hold flag) or something

i suppose you could do: 

```
xfce-terminal -e "cal; read"
```

assuming -e is the execute flag.

---

### Post by Acidianus on 2009-11-09
> **Primefalcon said:**
> as I said if you ask for user input through the terminal the terminal will stay open until you hit enter....

example

```
#!/bin/bash
echo "hi there"
read why

```

try it, not really what it's meant for... but..

Worked like a charm! Many thanks:D

---

