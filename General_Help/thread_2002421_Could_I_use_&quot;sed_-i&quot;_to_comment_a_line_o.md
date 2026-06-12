---
title: "Could I use &quot;sed -i&quot; to comment a line of text?"
date: 2012-06-12
forum: General Help
---

### Post by kansasnoob on 2012-06-12
I'm slowly working out the intricacies of creating two scripts, one to change something, and the other to revert that change :)

Right now I'm stuck on commenting out a line I've added to .xprofile in home via:

```
echo export LIBOVERLAY_SCROLLBAR=0 >> ~/.xprofile
```

BTW that axes the overlay-scrollbars only in a specific user session :)

I'll grant you that .xprofile seldom exists unless user-created, but let's imagine I created a .xprofile to edit the resolution for only one user, eg;

```
xrandr --output VGA1 --mode 1440x900 --rate 60

```

**[COLOR="Red"]Note: that is an untested example and may blow up your hardware![/COLOR]**

But if .xprofile exists with the above text and I run "echo export LIBOVERLAY_SCROLLBAR=0 >> ~/.xprofile" it becomes:

```
xrandr --output VGA1 --mode 1440x900 --rate 60
export LIBOVERLAY_SCROLLBAR=0
```

Now, if I only want to comment out or remove "export LIBOVERLAY_SCROLLBAR=0" I can easily do so with any text editor, and since it's my home I need not even use sudo ............. but how in the world could I comment out that line or remove it using a script :confused:

I've even thought about just backing up the original, then restoring it would be easy, but what if I edited that file after adding the bit about overlay-scrollbars :confused:

I would certainly think that I could use "sed -i" to comment out that line while maintaining the integrity of the rest of .xprofile, eg;

```
xrandr --output VGA1 --mode 1440x900 --rate 60
### export LIBOVERLAY_SCROLLBAR=0
```

But I'm stuck. I've been trying for a few hours and I need help ](*,)

---

### Post by steeldriver on 2012-06-12
sure - you can use the special character '&' to represent the matched expression in a substitute command:

```
sed -i 's/regex/### &/'
```where regex is something like

```
export[ \t]\+LIBOVERLAY_SCROLLBAR
```

Try it without the '-i' until you get it doing exactly what you want ;)

---

### Post by wojox on 2012-06-12
Is it always the last line?

```
 sed -ie '$d' ~/.xprofile
```

---

### Post by papibe on 2012-06-12
Hi kansasnoob.

Here are a few ideas:

Very safe brute force:
```
sed -i 's/export LIBOVERLAY_SCROLLBAR=0/#export LIBOVERLAY_SCROLLBAR=0/'  .xprofile
```

Simpler, but taking a little riskier if you have more LIBOVERLAY patterns:
```
sed  -i 's/^#\(.*LIBOVERLAY.*\)/\1/'  .xprofile
```

Hope it hepls.
Regards.

---

### Post by kansasnoob on 2012-06-12
> **wojox said:**
> Is it always the last line?

```
 sed -ie '$d' ~/.xprofile
```

It may not be. I assume that it'd only be the last line of text if it was the last thing added to that file.

---

### Post by kansasnoob on 2012-06-12
> **papibe said:**
> Hi kansasnoob.

Here are a few ideas:

Very safe brute force:
```
sed -i 's/export LIBOVERLAY_SCROLLBAR=0/#export LIBOVERLAY_SCROLLBAR=0/'  .xprofile
```

Simpler, but taking a little riskier if you have more LIBOVERLAY patterns:
```
sed  -i 's/^#\(.*LIBOVERLAY.*\)/\1/'  .xprofile
```

Hope it hepls.
Regards.

That looks promising. Right now I'm cooked so I'm going to look at this again tomorrow.

---

### Post by kansasnoob on 2012-06-13
This works:

```
sed -i 's/export LIBOVERLAY_SCROLLBAR=0/#export LIBOVERLAY_SCROLLBAR=0/' ~/.xprofile
```

Many, many thanks :D

---

### Post by markbl on 2012-06-13
> **kansasnoob said:**
> This works:
```
sed -i 's/export LIBOVERLAY_SCROLLBAR=0/#export LIBOVERLAY_SCROLLBAR=0/' ~/.xprofile
```

Many, many thanks :D
Well you may as well improve this as steeldriver suggested above and use the match pattern. Also you should anchor the expression so you only comment it out once (if you run it again). Also, comment it regardless of the value. Thus, this is better:
```

sed -i 's/^export LIBOVERLAY_SCROLLBAR.*/#&/' ~/.xprofile

```

---

### Post by kansasnoob on 2012-06-13
> **markbl said:**
> Well you may as well improve this as steeldriver suggested above and use the match pattern. Also you should anchor the expression so you only comment it out once (if you run it again). Also, comment it regardless of the value. Thus, this is better:
```

sed -i 's/^export LIBOVERLAY_SCROLLBAR.*/#&/' ~/.xprofile

```

Thanks. I'm just writing some new test-cases so I'll add this :)

---

### Post by steeldriver on 2012-06-13
The '^export' is certainly an improvement  (match only if 'export' is at the beginning of the line) - you could also do '^[ \t]*export' in case there's whitespace ahead of the 'export'

The '.*' wildcard after LIBOVERLAY_SCROLLBAR is not really necessary imo - you don't really gain anything by matching and then exactly replacing an arbitrary sequence of characters versus just letting anything after the key text remain untouched i.e.

```
sed -i 's/^export LIBOVERLAY_SCROLLBAR.*/# &/'
```replaces 'export LIBOVERLAY_SCROLLBAR=0' with '# export LIBOVERLAY_SCROLLBAR=0'

while

```
sed -i 's/^export LIBOVERLAY_SCROLLBAR/# &/'
```replaces just 'export LIBOVERLAY_SCROLLBAR' with '# export LIBOVERLAY_SCROLLBAR' leaving the '=0' (or anything else in the remainder of the line) exactly as before

---

