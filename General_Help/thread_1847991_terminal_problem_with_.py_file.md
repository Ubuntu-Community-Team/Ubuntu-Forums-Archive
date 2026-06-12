---
title: "terminal problem with .py file"
date: 2011-09-21
forum: General Help
---

### Post by upupz on 2011-09-21
I am trying my hand at python programming my problem is;

I have written a hello world program. Named hello world.py

It is saved in Documents/ Python/ Basics

I cd over to Basics and then entered

```
python hello world.py
```
as the tutorial instructs. The output is 'hello world is not a file...etc

i tried

```
python hello_world.py
```
same
I tried the ls command, it lists

```
hello world.py
```


How can get the terminal to recognised and execute the file?

I am sure I am missing some rudimentary command :L

regards and thanks

upupz

---

### Post by patryk77 on 2011-09-21
Three options:

python 'hello world.py'
python "hello world.py"
python hello\ world.py

Or simply don't save filenames with spaces ;)

---

### Post by WorMzy on 2011-09-21
To elaborate on what patryk said: the shell understands spaces to mean that one argument is ending, and the next one is beginning, so by running

```
python hello world.py
```

You are telling the application (python) to run two files: hello, and world.py. Obviously, this isn't what you meant to happen.

One way around this problem is put quotes around the file name:

```
python "hello world.py"
python 'hello world.py'
```

Quotes tell the shell that everything between the two quote marks should be treated as /one/ argument, and not multiple.

Another way would be to "escape" the space, by using the escape character (\):
```
python hello\ world.py
```

The escape character tells the shell that the next character should be treated as a normal character, rather than what the shell would normally treat it as (space is a seperator, $ is a variable, ; ends a command, etc.)

The other way, as patryk said, is to not use spaces. That way the shell won't get confused.

---

### Post by upupz on 2011-09-22
Much appreciated, thanks a bunch :)

I will now be digesting "linux shell programming" in the next few days!

---

### Post by patryk77 on 2011-09-22
One more tip: use Bash auto-completion.

If you type:
python hello
and press tab, it should add the '\ world.py' for you (with the escaped space, no quotes), unless you have other files beginning with hello.

Either way, it generally takes care of the escaping for you, and pressing tab twice will give you a list of all the matching files if there is more than one.

---

### Post by upupz on 2011-09-22
Thanks again, this is all much appreciated :)

---

