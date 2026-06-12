---
title: "Bash Alias for Festival"
date: 2010-11-19
forum: General Help
---

### Post by cfree220 on 2010-11-19
I've been playing around with text-to-speech on my laptop. I have festival installed and running, but I'm finding that the syntax is really cumbersome, particularly within festival's shell.

I know that I can operate festival from bash by typing something like

```
echo "Hello" | festival --tts
```

Is there any way that I could create a bash alias, perhaps "fest" which would allow me to do something like this:

```
fest Whatever I want to say
```

and have it translate into

```
echo "Whatever I want to say" | festival --tts
```

This will be very useful for times when I lock myself out of my apartment, or run out of tp.

---

### Post by Kulshrax on 2010-11-19
Add the following to your ~/.bashrc:

```
function fest {
    echo $1 | festival --tts
}
```

---

### Post by cfree220 on 2010-11-19
Thanks, that's perfect!

---

### Post by asmoore82 on 2010-11-19
Have you tried espeak?

```
espeak "hello world"
```

I've known about festival longer but I've come to assume that espeak is more mature
because I think it's used for Gnome's official accessibility features.

---

