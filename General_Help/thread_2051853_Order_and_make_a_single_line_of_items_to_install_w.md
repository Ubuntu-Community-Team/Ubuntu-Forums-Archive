---
title: "Order and make a single line of items to install with apt-get"
date: 2012-09-02
forum: General Help
---

### Post by Rytron on 2012-09-02
Hi.

If I had a large list of games to install and they were in this format:
[COLOR="Purple"]sudo apt-get install viruskiller warzone2100
pouetchess gnome-mahjongg
qmc2
trigger
zod[/COLOR]

... How would I order them like so (in a non-stop line with spaces between each game to install) and in alphabetical order with a command?
[COLOR="SeaGreen"]sudo apt-get install gnome-mahjongg pouetchess qmc2 trigger viruskiller warzone2100 zod[/COLOR]

Edit: To make things easier lets ignore the "***sudo apt-get install***" part as that can be added last.

---

### Post by Bachstelze on 2012-09-02
```
sudo apt-get install `cat list.txt | sort | tr "\n" " "`
```

The sorting part is probably unnecessary, though...

---

### Post by Rytron on 2012-09-02
> **Bachstelze said:**
> ```
sudo apt-get install `cat list.txt | sort | tr "\n" " "`
```

The sorting part is probably unnecessary, though...

Hi Bachstelze.

I want them sorted in the text file (if possible). Then I can copy the full ordered line into the terminal.

I ran just this part:
```
cat list.txt | sort | tr "\n" " "
```
And got this (all is fine bar pouetchess and gnome-mahjongg being in the wrong order):
```
pouetchess gnome-mahjongg qmc2 trigger viruskiller warzone2100 zod
```

---

### Post by Bachstelze on 2012-09-02
pouetchess and gnome-mahjongg are on the same line in the input file, so sort treats them as one word. If you want them sorted you can run another pass of tr before sort, replacing all spaces with newlines.

To get a sorted file, just redirect the output of sort:

```
cat list.txt | sort > list.sorted.txt
```

---

### Post by Rytron on 2012-09-02
```
cat list.txt | sort | tr "\n" " "
```
# Turned this
[B]viruskiller warzone2100
pouetchess gnome-mahjongg
qmc2
trigger
zod[/B]
# into this
**pouetchess gnome-mahjongg qmc2 trigger viruskiller warzone2100 zod**
# Then I copied it into list.txt and ran
```
cat list.txt | sort > list.sorted.txt
```
# Nothing changed.

-----------------------------------------------------

```
cat list.txt | sort > list.sorted.txt
```
# Turned this:
[B]viruskiller warzone2100
pouetchess gnome-mahjongg
qmc2
trigger
zod[/B]

# into this:
[B]pouetchess gnome-mahjongg
qmc2
trigger
viruskiller warzone2100
zod[/B]

---

### Post by Vaphell on 2012-09-02
try 
```
sudo apt-get install $( cat list.txt | tr " " "\n" | sort )
```
it will replace all spaces with newlines for sorting purposes, but these newlines will get flattened either way when the result is passed to apt-get ( embedded command not shielded by "" )

to illustrate:
```
$ echo $'a\nb c'
a
b c
$ echo $( echo $'a\nb c' )  # unquoted, doesn't preserve formatting, all whitespaces become spaces
a b c
$ echo "$( echo $'a\nb c' )"  # quoted, preserves formatting
a
b c
```

---

### Post by Rytron on 2012-09-02
> **Vaphell said:**
> try 
```
sudo apt-get install $( cat list.txt | tr " " "\n" | sort )
```
it will replace all spaces with newlines for sorting purposes, but these newlines will get flattened either way when the result is passed to apt-get

I just ran the part
```
( cat list.txt | tr " " "\n" | sort )
```
and copied the terminal output list into a text file (for future use with apt). Cheers to you Vaphell. ):P

---

