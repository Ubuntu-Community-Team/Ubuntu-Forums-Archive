---
title: "Bash help"
date: 2010-10-22
forum: General Help
---

### Post by gyussz on 2010-10-22
Hey everyone!

Since my touchpad disable/enable hotkey doesn't work, i'm turning it off/on with 2 different scripts, but I would like to make only one script file to assign it to the default touchpad hotkey.

My problem: I don't know how to make the condition to work...
Here's what I've got so far:
```
if [ 'gconftool -g /desktop/gnome/peripherals/touchpad/touchpad_enabled'=='true' ]; then
	gconftool -s -t bool /desktop/gnome/peripherals/touchpad/touchpad_enabled false
else
	gconftool -s -t bool /desktop/gnome/peripherals/touchpad/touchpad_enabled true
fi
```

Anyone knows how to make the condition to work? Help appreciated :)

---

### Post by Hippytaff on 2010-10-22
Out of curiosity, what to the two sripts look like?

---

### Post by DaithiF on 2010-10-22
I would do it something like:

```
status=$(gconftool -g /desktop/gnome/peripherals/touchpad/touchpad_enabled)

[[ "$status" = "true" ]] && new_status=false || new_status=true

gconftool -s -t bool /desktop/gnome/peripherals/touchpad/touchpad_enabled $new_status

```

---

### Post by sisco311 on 2010-10-22
the exit status of the true builtin is 0 and the exit status of the false builtin is 1,
0 as boolean is false and 1 as boolean is true:
```

#!/bin/bash

$(gconftool -g /desktop/gnome/peripherals/touchpad/touchpad_enabled)
gconftool -s -t bool /desktop/gnome/peripherals/touchpad/touchpad_enabled $?
```

---

### Post by gyussz on 2010-10-22
> **Hippytaff said:**
> Out of curiosity, what to the two sripts look like?

script to disable
```
gconftool -s -t bool /desktop/gnome/peripherals/touchpad/touchpad_enabled 0
```
script to enable
```
gconftool -s -t bool /desktop/gnome/peripherals/touchpad/touchpad_enabled 1
```

---

### Post by Hippytaff on 2010-10-22
> **gyussz said:**
> script to disable
```
gconftool -s -t bool /desktop/gnome/peripherals/touchpad/touchpad_enabled 0
```
script to enable
```
gconftool -s -t bool /desktop/gnome/peripherals/touchpad/touchpad_enabled 1
```
 
Thanks - I would have done the same as you - learning too :-)

---

### Post by sisco311 on 2010-10-22
> **gyussz said:**
> Hey everyone!

Since my touchpad disable/enable hotkey doesn't work, i'm turning it off/on with 2 different scripts, but I would like to make only one script file to assign it to the default touchpad hotkey.

My problem: I don't know how to make the condition to work...
Here's what I've got so far:
```
if [ 'gconftool -g /desktop/gnome/peripherals/touchpad/touchpad_enabled'=='true' ]; then
	gconftool -s -t bool /desktop/gnome/peripherals/touchpad/touchpad_enabled false
else
	gconftool -s -t bool /desktop/gnome/peripherals/touchpad/touchpad_enabled true
fi
```

Anyone knows how to make the condition to work? Help appreciated :)

You have to use command substitution:
```
if [[ $(gconftool -g /desktop/gnome/peripherals/touchpad/touchpad_enabled) == true ]]; then
```

See:
```
man bash |  less +/"Command Substitution"
```

Oh, and the double brackets do everything the single ones do and a bit more, so it's safest to use double brackets with your expressions.

> **DaithiF said:**
> I would do it something like:

```
status=$(gconftool -g /desktop/gnome/peripherals/touchpad/touchpad_enabled)

[[ "$status" = "true" ]] && new_status=false || new_status=true

gconftool -s -t bool /desktop/gnome/peripherals/touchpad/touchpad_enabled $new_status

```

+1

---

### Post by gyussz on 2010-10-22
Thanks for the replies. I think I wasn't clear enough with the first post, (and also noticed some mistakes in the posted code). So the problem is: the condition is always returns true value, so *gconftool -g /desktop/gnome/peripherals/touchpad/touchpad_enabled* could be true or false, the result of the condition will be true.

If I'm not mistaken *gconftool -g* command is basically just a function to print the value of the specified key. Putting it to a variable (already tried yesterday) doesn't really work, or I'm doing something wrong.

Here what it looks like with a variable:
```
status=$(gconftool -g /desktop/gnome/peripherals/touchpad/touchpad_enabled)
if [ "$status"="true" ]; then
	gconftool -s -t bool /desktop/gnome/peripherals/touchpad/touchpad_enabled 0
else
	gconftool -s -t bool /desktop/gnome/peripherals/touchpad/touchpad_enabled 1
fi
```

edit:
@sisco311: If I use double brackets in the way, i get: ./tpfunction.sh: 5: [[: not found

---

### Post by sisco311 on 2010-10-22
> **gyussz said:**
> Thanks for the replies. I think I wasn't clear enough with the first post, (and also noticed some mistakes in the posted code). So the problem is: the condition is always returns true value, so *gconftool -g /desktop/gnome/peripherals/touchpad/touchpad_enabled* could be true or false, the result of the condition will be true.

If I'm not mistaken *gconftool -g* command is basically just a function to print the value of the specified key. Putting it to a variable (already tried yesterday) doesn't really work, or I'm doing something wrong.

Here what it looks like with a variable:
```
status=$(gconftool -g /desktop/gnome/peripherals/touchpad/touchpad_enabled)
if [ "$status"="true" ]; then
	gconftool -s -t bool /desktop/gnome/peripherals/touchpad/touchpad_enabled 0
else
	gconftool -s -t bool /desktop/gnome/peripherals/touchpad/touchpad_enabled 1
fi
```

You need a space between the string and the = sign:
```
if [ "$status" = "true" ]; 
```

---

### Post by matt_symes on 2010-10-22
Hi

if [ "$status"="true" ]; then

=> 
if [ "$status" = "true" ]; then
Notice the spaces in the condition between = 

Sorry sisco311. I seem to have duplicated your post.

Kind regards

---

### Post by gyussz on 2010-10-22
> **DaithiF said:**
> I would do it something like:

```
status=$(gconftool -g /desktop/gnome/peripherals/touchpad/touchpad_enabled)

[[ "$status" = "true" ]] && new_status=false || new_status=true

gconftool -s -t bool /desktop/gnome/peripherals/touchpad/touchpad_enabled $new_status

```

Doesn't work either :/

---

### Post by gyussz on 2010-10-22
Ahh, the spaces... Thank you very much, now it works :D

Didn't think whitespaces would make any different after those C oriented programming languages...

Thanks again, and sorry for being a bit dumb, this was the first time I tried bash programming :)

For those who run into the same problem the final code looks like:
```
status=$(gconftool -g /desktop/gnome/peripherals/touchpad/touchpad_enabled)
if [ "$status" = "true" ]; then
	gconftool -s -t bool /desktop/gnome/peripherals/touchpad/touchpad_enabled 0
else
	gconftool -s -t bool /desktop/gnome/peripherals/touchpad/touchpad_enabled 1
fi
```

---

