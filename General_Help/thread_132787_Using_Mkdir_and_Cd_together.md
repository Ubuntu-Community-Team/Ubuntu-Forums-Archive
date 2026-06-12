---
title: "Using Mkdir and Cd together"
date: 2006-02-18
forum: General Help
---

### Post by capi on 2006-02-18
I couldn't find a command line specific forum so I figured this are is fairly general. I'll give you an example of what I mean by working together.

I find myself making and moving to a directory quite a bit, normally I use something like this...

mkdir ~/dir && cd ~/dir

...however is there any quick and easy way to combine the tasks so I don't need to repeat the dir(with longer paths it becomes a serious pain). I tried piping but it seems cd doesn't respond to that. I realize I could write a bash script or alias, but I don't want to do that if their a simple CLI-only option.

Any thoughts are welcome,
~ capiCrimm

---

### Post by heimo on 2006-02-19
Maybe this is what you're looking for:
```
mkdir -p create/new/dir && cd !$
```
Two tips: When creating directory structures, you can create parent directories at the same time (no repeating of mkdir dir; cd dir; mkdir 2dir; cd 2dir) using flag -p. And you can refer to last parameter of latest command using !$

---

### Post by ximok on 2006-02-19
Or you could just use the ;  It is actually designed to execute one command AFTER the other.
```

mkdir ~/blah; cd ~/blah

```

---

### Post by heimo on 2006-02-19
[quote=ximok]Or you could just use the ;  It is actually designed to execute one command AFTER the other.
```

mkdir ~/blah; cd ~/blah

```[/quote] 
&& is *and. ***If the first command doesn't execute successfully, the latter is not executed at all. Examples, let's assume directory /ne doesn't exist.
```
cd /ne && echo "success"
``` gives error message for unsuccessul *cd* but doesn't output "success"
```
cd /ne || echo "failed"
``` gives error message and output "failed"

---

