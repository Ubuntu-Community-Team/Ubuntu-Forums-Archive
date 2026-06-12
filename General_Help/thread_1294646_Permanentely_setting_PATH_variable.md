---
title: "Permanentely setting PATH variable"
date: 2009-10-18
forum: General Help
---

### Post by king0 on 2009-10-18
How does one on ubuntu **permanently **change the PATH variable? 

I know that one could:
```

PATH=$PATH:/usr/share/tomcat
export $PATH

```

But the above only lasts the duration of the shell; can anyone explain how to permanently change the path variable?

---

### Post by StuartN on 2009-10-18
> **king0 said:**
> But the above only lasts the duration of the shell; can anyone explain how to permanently change the path variable?

You can do the same in the hidden .profile file in your home directory.

---

### Post by king0 on 2009-10-19
> **StuartN said:**
> You can do the same in the hidden .profile file in your home directory.

I added the code below to the .profile file. Unfortunately, on server restart I get a session error. Anyone know why?

```

Path=$PATH:/usr/share/tomcat
export $PATH

```

---

### Post by uncle-c on 2009-10-19
Should be **export PATH** and not *** export $PATH***

---

### Post by mcduck on 2009-10-19
> **uncle-c said:**
> Should be **export PATH** and not *** export $PATH***

True. Also it's case sensitive, so "Path" and "PATH" are not the same thing.

---

### Post by nateperson on 2009-10-19
And it can all be added in one line:

```
export PATH=/usr/share/tomcat:$PATH
```

should you wish...

---

### Post by king0 on 2009-10-19
> **mcduck said:**
> True. Also it's case sensitive, so "Path" and "PATH" are not the same thing.

The issue was the dollar sign ($). In my second post, I incorrectly typed "Path" rather than "PATH." 

Additionally, I found that I can add files to the profile.d directory and those files are appended to the .profile file. 

However, I am curious, is there are way from the bash shell to permanently change the PATH variable or to add environment variables?

---

### Post by -Zeus- on 2009-10-19
From *within* the shell, you can't change environment variables (permanently), but you can set them to be autoset when a shell is opened.

---

### Post by Yannick Le Saint kyncani on 2009-10-19
A process (bash here) cannot change the environment variables of other running processes, there are memory protections for that.

---

### Post by king0 on 2009-10-19
> **-Zeus- said:**
> From *within* the shell, you can't change environment variables (permanently), but you can set them to be autoset when a shell is opened.

> **Yannick Le Saint kyncani said:**
> A process (bash here) cannot change the environment variables of other running processes, there are memory protections for that.

Got it; thanks for the clarification.

---

### Post by Delinquentme on 2011-12-09
Hey all I'm _completely_ new to this and trying to make sense of it...

I've edited both these files:

/etc/environments
```

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/lib/postgresql/8.4/bin"

```

and

~/.profile
```

Path=$PATH:/usr/lib/postgresql/8.4/bin
export PATH

```

for the user who I'd like to run 'pg_ctl' from

I've verified that this is the file containing the pg_ctl program I'd like to run:

```
/usr/lib/postgresql/8.4/bin
```


I've saved it and exited out ... and i STILL get 

"pg_ctl: command not found"


... the [manpage on this]("https://help.ubuntu.com/community/EnvironmentVariables") is totally useless.

---

### Post by Synoc on 2011-12-09
> **Delinquentme said:**
> Hey all I'm _completely_ new to this and trying to make sense of it...

I've edited both these files:

/etc/environments
```

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/lib/postgresql/8.4/bin"

```

and

~/.profile
```

Path=$PATH:/usr/lib/postgresql/8.4/bin
export PATH

```

for the user who I'd like to run 'pg_ctl' from

I've verified that this is the file containing the pg_ctl program I'd like to run:

```
/usr/lib/postgresql/8.4/bin
```


I've saved it and exited out ... and i STILL get 

"pg_ctl: command not found"


... the [manpage on this]("https://help.ubuntu.com/community/EnvironmentVariables") is totally useless.

we can and will get you through this, no worries. if you put in
```

Path=$PATH:/usr/lib/postgresql/8.4/bin
export PATH

```
you did it not make PATH = to PATH + your new directory.
you made a new variable called "Path" = to PATH + your new directory

in Linux, everything is case sensitive, you must make it
```

PATH=$PATH:/usr/lib/postgresql/8.4/bin

```
Path does not mean PATH and the $ in the code tells the computer the next text is a variable so $PATH is not the variable, PATH is. 

if you set VAR="Hello," and Var="World" 
then type ```
echo $VAR $Var
``` you will get "Hello, World"
for that matter typing 
```
 echo $VAR $Var $var var 
```
will yield "Hello, World var" because $var is not set to anything and "var" is simply a word.

---

