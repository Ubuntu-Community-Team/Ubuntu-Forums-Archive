---
title: "setting environment variables"
date: 2006-05-31
forum: General Help
---

### Post by ShendZ on 2006-05-31
how to set multiple values to a environment variables?
in windows, i know that u just simply go to my computer->advance->environment variable-> edit a variable
for multiple value, simply just add ; <bla bla bla>;

ex:
CLASSPATH=c:\java\bin;
if i want to add a new value c:\test\bin, it becomes
CLASSPATH=c:\java\bin;c:\test\bin;

thank you in advance

---

### Post by kaamos on 2006-05-31
```
export CLASSPATH="/opt/java/bin:/home/username/bin/"
```
or to add something to a variable:
```
export CLASSPATH="$CLASSPATH:/opt/java/bin"
```
If you want to make these permanent, add the lines to ~/.bashrc and ~/.bash_profile (files start with a dot so they are hidden, press ctrl+h)

---

### Post by tribaal on 2006-05-31
Well... you pretty much do the same thing in linux:

Open a terminal, and type

```
export TESTVAR='Hi there'
```

To access the value of a variable you use the $ symbol.
So to print the TESTVAR value type

```
echo $TESTVAR
```

The you can add stuff to your variable by adding itself. Example:

```
export TESTVAR=$TESTVAR', how are you?'
echo $TESTVAR
```

So to change your PATH variable to include /yourhome/bin:

```
export PATH=$PATH:~/bin
```


How this helps :)

- trib'

**EDIT:** Man I should really learn to refresh before I post :)

---

