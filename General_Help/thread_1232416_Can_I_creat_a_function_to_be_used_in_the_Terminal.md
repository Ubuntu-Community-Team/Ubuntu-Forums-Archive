---
title: "Can I creat a function to be used in the Terminal?"
date: 2009-08-05
forum: General Help
---

### Post by Elexius on 2009-08-05
Basically what I want to do is to create a function that can be used in the terminal, that receives an argument and returns a value or executes a command. 

so if the terminal used C I would like to implement something like

```
int getfiles (directory)
{
ls directory;
return 1;
}
```

so I could type in the terminal 
```
getfiles(home)
```

and make the function run

---

### Post by credobyte on 2009-08-05
Why to bother creating a function if you already can do it ?

```
ls /usr/share

```

Regarding other *functions* - C/C++ app in /usr/bin would do the job !

---

### Post by benj1 on 2009-08-05
what specifically are you wanting to do?

the easiest way would be to add a function or alias or function in your ~/.bashrc

---

### Post by Elexius on 2009-08-05
> **benj1 said:**
> what specifically are you wanting to do?

the easiest way would be to add a function or alias or function in your ~/.bashrc

Well, the thing is that what I want to do is a bit too complicated to create an alias and it needs to be more flexible than a script. Besides, I think I can only use one alias at a time

for example lets say I want to create the function irun(command)

it would be written like 

```
int irun(a_command)
{
nohup "a_command" > /dev/null & ;
return 0;
}

```
so I would type in the terminal
```
irun(firefox)

```
and firefox would run, no verbose, and if I close the terminal, FF does not quit.

---

### Post by trwww on 2009-08-05
It looks like you're trying to start an external program in C?

Try this: [http://www.google.com/search?q=run+external+program+c](http://www.google.com/search?q=run+external+program+c)

---

### Post by mcduck on 2009-08-05
> **Elexius said:**
> Basically what I want to do is to create a function that can be used in the terminal, that receives an argument and returns a value or executes a command. 

so if the terminal used C I would like to implement something like

```
int getfiles (directory)
{
ls directory;
return 1;
}
```

so I could type in the terminal 
```
getfiles(home)
```

and make the function run

So you want to make this with C, or with shell scripting?

Shell scripts can take arguments (and you can create functions in them, but that might or might not be useful depending on what you are doing.

This would be the same as your code, $1 is the first argument given when executing the script. ($2 would be second argument etc)
```

#! /bin/sh
ls $1
```

---

### Post by benj1 on 2009-08-05
well if you want to do in c you can 

if you want to write a script heres a [bash guide]("http://www.tldp.org/LDP/abs/html/index.html")

i get the impression from your last post youre trying to run something without tying up the terminal?

if its a graphical application you can use the '&' suffix ie 'firefox&' but you wouldn't be able to exit the terminal

---

### Post by Elexius on 2009-08-05
> **mcduck said:**
> So you want to make this with C, or with shell scripting?

Shell scripts can take arguments (and you can create functions in them, but that might or might not be useful depending on what you are doing.

This would be the same as your code, $1 is the first argument given when executing the script. ($2 would be second argument etc)
```

#! /bin/sh
ls $1
```

Thank you!:KS
I was told that scripts could not take any arguments, and yet, your recommendation works! any other juicy tips when creating scripts?

I also thank the other posters for their willingness to help.

---

