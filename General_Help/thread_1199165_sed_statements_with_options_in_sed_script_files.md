---
title: "sed statements with options in sed script files"
date: 2009-06-28
forum: General Help
---

### Post by motoperpetuo on 2009-06-28
i'm working through the excellent bash beginner's guide at [http://tldp.org/LDP/Bash-Beginners-Guide/html/](http://tldp.org/LDP/Bash-Beginners-Guide/html/), and i'm trying to figure out the exercises at the end of chapter 5, "The GNU sed stream editor."

Exercise 3 asks me to come up with a sed statement that will delete the first three lines of a text file. I came up with:
```

sed -i '1,3d' sedfile01.txt

```
Exercise 4 asks me to come up with something that will "Print to standard output only the lines containing the pattern 'an'." I came up with:
```

sed -n '/an/p' sedfile02.txt

```
These statements both work, however, the next exercise asks me to put them both in a sed script file and run them that way. i've been able to get sed script files to work for doing simple search and replace operations like this:
```

s/yyy/xxx/g
s/pig/dog/g

```
but i don't know how to include sed statements in a sed script while retaining the -i and -n options that seems absolutely necessary to get my sed statements from exercise 3 and 4 to work. can anyone help me with this?

also, does anyone know if the answers to the practice exercises in the bash beginner's guide are available anywhere? i manage to work most of them out myself, but it would be nice to have the answers to fall back on when i get really stuck like this.

---

### Post by ghostdog74 on 2009-06-28
you can practically skip learning sed. Try learning gawk/awk fully instead.  ( See my sig for link ).
```

sed '1,3d' sedfile01.txt

```
awk equivalent
```

awk 'NR>3' file

```

```

sed -n '/an/p' sedfile02.txt

```
awk equivalent
```

awk '/an/' sedfile02.txt

```

to put them together using awk
```

awk 'NR>3 && /an/' sedfile02.txt

```

awk is a little programming language by itself that does what sed does and more, therefore, learning awk instead of sed will be more relevant.

---

### Post by motoperpetuo on 2009-06-28
maybe i'll do that. in fact, an introduction to awk is the next chapter on the tutorial i'm doing. supposing for the sake of argument that you know both equally well, are there any instances where you'd want to use sed instead of awk?

---

### Post by ghostdog74 on 2009-06-28
> **motoperpetuo said:**
>  are there any instances where you'd want to use sed instead of awk?
no. In my entire script writing experience, i have never used sed once. awk does the job well enough for me. 
( Of course in the end, its entirely up to you whether you want to use them.)

---

