---
title: "GUI program launcher open terminal as well"
date: 2012-06-04
forum: General Help
---

### Post by Steven D on 2012-06-04
Hi everyone!
i have a very minor issue, I have a barcode / QRcode scanning program (zbarcam in Ubuntu SC) which obviously reads QR & bar codes.

My issue is the scanned material outputs to the terminal, but i have made a quick launcher (.desktop) which launches the scanner itself, but because there is no accompanying terminal I cannot see the output.

is there a way I can have the terminal launch with the .desktop launcher?

It does work now if i just open a terminal and type "zbarcam" but i would prefer an icon on the dock.

Thanks in advance!

---

### Post by idoitprone on 2012-06-04
> **Steven D said:**
> Hi everyone!
i have a very minor issue, I have a barcode / QRcode scanning program (zbarcam in Ubuntu SC) which obviously reads QR & bar codes.

My issue is the scanned material outputs to the terminal, but i have made a quick launcher (.desktop) which launches the scanner itself, but because there is no accompanying terminal I cannot see the output.

is there a way I can have the terminal launch with the .desktop launcher?

It does work now if i just open a terminal and type "zbarcam" but i would prefer an icon on the dock.

Thanks in advance!

why dont you output the result to a file with the file redirect operator '>'

echo "characters can go to a file" > "RESULTS.txt"

---

### Post by Steven D on 2012-06-04
Would i add this to the end of the .desktop file?

I'm not too sure what to add there, I tried
echo ~/Desktop/result.txt

---

### Post by idoitprone on 2012-06-04
> **Steven D said:**
> Would i add this to the end of the .desktop file?

I'm not too sure what to add there, I tried
echo ~/Desktop/result.txt

you have two ways

you can pipe the resulting script to a file which allow you scan the items and read it later

or you can pipe it to a program to and read it as a popup which i do not know the command

If you have to ask about an echo command then you do not use bash often huh

[http://en.wikipedia.org/wiki/Redirection_%28computing%29]("http://en.wikipedia.org/wiki/Redirection_%28computing%29")
here a decent explanation on piping and redirects

---

### Post by mcduck on 2012-06-04
Easy thing to fix, you just need to change your launcher to launch Gnome-Terminal, and at the same time tell that terminal to run your program:

```
gnome-terminal -e "zbarcam"
```

---

### Post by idoitprone on 2012-06-04
> **mcduck said:**
> Easy thing to fix, you just need to change your launcher to launch Gnome-Terminal, and at the same time tell that terminal to run your program:

```
gnome-terminal -e "zbarcam"
```

i wished they at least list it when i type

gnome-terminal -h

gui have way too many hidden parameters

---

### Post by mcduck on 2012-06-04
> **idoitprone said:**
> i wished they at least list it when i type

gnome-terminal -h

gui have way too many hidden parameters

"man gnome-terminal" would probably have told you that. The "-h" option in programs usually only gives a simplified list of most common options instead of a complete manual.

---

### Post by idoitprone on 2012-06-04
nvm

---

### Post by Steven D on 2012-06-05
> **mcduck said:**
> Easy thing to fix, you just need to change your launcher to launch Gnome-Terminal, and at the same time tell that terminal to run your program:

```
gnome-terminal -e "zbarcam"
```

Sorry for the late reply, 12 hour shift at work.

This works amazing! can't thank you enough.

---

