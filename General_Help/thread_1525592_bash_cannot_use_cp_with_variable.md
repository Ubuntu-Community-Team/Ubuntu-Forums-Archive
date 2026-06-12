---
title: "bash: cannot use cp with variable?"
date: 2010-07-06
forum: General Help
---

### Post by d3v1150m471c on 2010-07-06
```

cp "$var" ~/`basename "$var" `
cp: cannot stat `~/Videos/psycho.mp4': No such file or directory

```

...okay what am I doing wrong here?

---

### Post by StuartN on 2010-07-07
> **d3v1150m471c said:**
> ...okay what am I doing wrong here?

A guess, but did you by any chance create the bash script with an unusual editor? This error does occur if you have Windows-type line breaks - which you can replace by choosing "Line ending" in the Save As dialogue of gedit.

---

### Post by HankB on 2010-07-07
> **d3v1150m471c said:**
> ```

cp "$var" ~/`basename "$var" `
cp: cannot stat `~/Videos/psycho.mp4': No such file or directory

```

...okay what am I doing wrong here?
I can't say without knowing what $var expands to.

Faced with such a situation, I usually prepend the command line with 'echo' to see what the command expands to. e.g.

```
echo cp "$var" ~/`basename "$var" `
```

I presume ~/Videos/psycho.mp4 does exist.

---

### Post by d3v1150m471c on 2010-07-07
solved:
after much trial and error i've found cp will accept the variable if the variable contains the full path with no aliases or variables.

```

var="/home/d3v11/folder/video"
cp "$var" ~/`basename "$var"`

```...works like a charm. thanks for all the help btw.

---

### Post by kaibob on 2010-07-07
Deleted by kaibob.

---

