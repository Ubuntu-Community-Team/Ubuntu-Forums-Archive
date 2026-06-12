---
title: "Bash - store a command in a variable, that uses a variable"
date: 2009-07-20
forum: General Help
---

### Post by Hawk__0 on 2009-07-20
How can I do this? Ex:
var1=`who | grep $user`

I can't find out how to get this to work

---

### Post by koenn on 2009-07-20
```
var1=$(who|grep $user)
```

---

### Post by decoherence on 2009-07-20
just by way of explanation...

```
var1=`who | grep $user`

```

This is the old method. It often works but, as you can see, not always.

```
var1=$(who|grep $user)
```

This is the new method. It is much more sane.

There is no reason to prefer the old method over the new one, so from now on use the $() syntax instead of backticks and you'll be fine!

---

### Post by Hawk__0 on 2009-07-20
Still doesn't work.  I am running SCO 6 (Old beast, I know..)

Now I have:
```

user=$(who | grep $user2 | cut -c 1-4)

```
When I echo the variable, it's blank :(

---

### Post by koenn on 2009-07-20
upgrade to Linux, then ?

this is going to depend on the shell you're using, actually. 
you sure you have bash on that old beast ?

---

### Post by decoherence on 2009-07-20
> **Hawk__0 said:**
> Still doesn't work.  I am running SCO 6 (Old beast, I know..)

Now I have:
```

user=$(who | grep $user2 | cut -c 1-4)

```
When I echo the variable, it's blank :(

SCO 6?? Holy carp.... okay, we assumed you were using Ubuntu.

can you please post the output of 
```

echo $SHELL
```

If it comes back saying "/bin/bash" could you please paste the output of
```

bash -version
```

Good luck finding a solution... I've never used SCO but maybe the above commands will help someone who has find you a solution?

---

### Post by slakkie on 2009-07-20
> **decoherence said:**
> just by way of explanation...

```
var1=`who | grep $user`

```

This is the old method. It often works but, as you can see, not always.

```
var1=$(who|grep $user)
```

This is the new method. It is much more sane.

There is no reason to prefer the old method over the new one, so from now on use the $() syntax instead of backticks and you'll be fine!

If you must use sh compliant code, backticks are still the way to go (since sh doesn't know the $() syntax), solaris for example still used the real sh.

@TS
The backticks start a new shell session, might be that you need to export your var before calling it with backticks.

@decoherence

ps -p $$ will give you the name of the shell which you are actually using. $SHELL only looks at shell from the passwd entry.

and echo $BASH_VERSION also works to display the version of bash.

---

### Post by Hawk__0 on 2009-07-20
shell is bash for sure (/bin/bash), and version=
```
bash -version
GNU bash, version 3.2.17(1)-release (i586-pc-sysv5)
Copyright (C) 2005 Free Software Foundation, Inc.

```

---

### Post by koenn on 2009-07-20
gnu bash, should be OK ... 


does it work  with a hard value in stead of a variable ? like 
var1=`who | grep john` or whatever name that's logged on

are you sure $user has a value ?

does the command return anything when you're not trying to capture the return in a var ?

does this work : 
```
 var=`echo $user` ; echo $var ; 
```

... just trying to get a handle

---

### Post by Hawk__0 on 2009-07-20
Okay it works now.  I wasn't aware of the way bash worked with variables... (like a script, in order).  I assigned the variable value the line below.  I just swapped the 2 lines and now it works with user=$(<code here)

Thanks for the help guys!

---

