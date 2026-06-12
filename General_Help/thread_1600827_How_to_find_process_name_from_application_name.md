---
title: "How to find process name from application name"
date: 2010-10-19
forum: General Help
---

### Post by pooyaplus on 2010-10-19
Hi,

I have searched for the solution with no luck and still wondering if there is a way to find out what's an application process name is from the name of the application itself. And then pkill the process from the terminal.

I tried using 

```
ps -e | grep ....
``` 

but it says

```
Warning: bad ps syntax, perhaps a bogus '-'? See http://procps.sf.net/faq.html
```

Any ideas?

Thanks

---

### Post by Rubi1200 on 2010-10-19
Try this:

```
ps -C <name_of_program> -o pid=

```You can also work this the other way round; find the process name from the PID:

```
 ps -p <PID> -o comm=
```

---

### Post by pooyaplus on 2010-10-20
Thanks, but what value should the pid get form the first code?

---

### Post by Rubi1200 on 2010-10-20
> **pooyaplus said:**
> Thanks, but what value should the pid get form the first code?
I am not sure I understand what you mean by value?

Example, I am currently running Firefox:

```
ps -C firefox -o pid=
```return this```
2189
```2189 is the PID for Firefox.

Or did I misunderstand your original post concerning what you want to do?

---

### Post by pooyaplus on 2010-10-20
Right... but how do I get the process name? In case that I want to kill the same process frequently as the pid does change when you start it over again?

Here is an example: how do you get the process name of the "Hardware Drivers" application from the system> advanced menu?

Cheers

P.

---

### Post by cariboo on 2010-10-20
In the case of **Hardware Drivers** or any other, you can always check System->Preferences->Main Menu, select the menu item and click properties, you will see that the name of the application is jockey-gtk. You can then open a terminal and type:

```
ps ax | grep jockey-gtk
```

the result of the above command, should look like this:

```
ps ax | grep jockey-gtk
 2481 ?        Sl     0:00 /usr/bin/python /usr/bin/jockey-gtk
 2529 pts/4    S+     0:00 grep --color=auto jockey-gtk
```

the first line in the result gives you the full path of the application and it's pid.

---

### Post by pooyaplus on 2010-10-21
Hi,

Thanks so much for the insights, but is there a way to get all that info regarding the process name from the terminal instead of checking the properties of the app?

Cheers 

P.

---

