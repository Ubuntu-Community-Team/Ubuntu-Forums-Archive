---
title: "Bash set aliases not staying. please help"
date: 2010-02-23
forum: General Help
---

### Post by d3v1150m471c on 2010-02-23
If I set an alias in the terminal it stays.
```

alias echo="echo whoaoaaoaoaoaoaoa"

```
But...if I write a bash script with the identical command and execute it...
```

./setalias
echo


```
I get nothing... How do I fix this?

---

### Post by slakkie on 2010-02-23
aliases do not work in scripts.

See also: [http://linux.derkeiler.com/Mailing-Lists/Debian/2008-01/msg02294.html](http://linux.derkeiler.com/Mailing-Lists/Debian/2008-01/msg02294.html)

---

### Post by d3v1150m471c on 2010-02-23
well is there an alternative? That link doesn't work btw

---

### Post by slakkie on 2010-02-23
Link works here :)

Anyhows, bottom line is, create a function:

```

some_function() {
   echo "whoahahhaa"
}

some_function

with_params() {
   echo ALL: $@
   echo first: $1
   echo second: $2
   shift;shift;
   echo third: $1
}

with_params Hello world, how you doing

```

---

### Post by d3v1150m471c on 2010-02-23
thanks but that doesn't land me what I need as far as I know. I need to be able to type in a typical command like read or echo and have it follow through with something like:
```

read
Enter your name:

```

I tried the alias because i can undo it later

---

### Post by bodhi.zazen on 2010-02-23
alises are used for shells. For bash scripts use variables.

foo="whoahahhaa"

[http://www.bash-hackers.org/wiki/doku.php/commands/builtin/printf](http://www.bash-hackers.org/wiki/doku.php/commands/builtin/printf)

For bash scripts use echo or printf and read.

[http://floppix.ccai.com/scripts1.html](http://floppix.ccai.com/scripts1.html)

---

### Post by dnairb on 2010-02-23
IIRC an alias can call a script. The script needs to be in /usr/bin/ and is called in .bashrc with: alias custom_command="script_name"

For an example see this: [http://www.webupd8.org/2010/02/make-rm-move-files-to-trash-instead-of.html](http://www.webupd8.org/2010/02/make-rm-move-files-to-trash-instead-of.html)

---

### Post by paxxus on 2010-02-23
You need to source your script:

```
source ./setalias
```or just:

```
. ./setalias
```

---

### Post by d3v1150m471c on 2010-02-23
I'm familiar with variables. Thing is, I'd like to have a script that can apply there variables. I can tell one to set variables but as soon as I execute them they're null and void.

---

### Post by d3v1150m471c on 2010-02-23
> **paxxus said:**
> You need to source your script:

```
source ./setalias
```or just:

```
. ./setalias
```

Bloody brilliant :popcorn::KS:D thanks mate!

paxxus +1

---

