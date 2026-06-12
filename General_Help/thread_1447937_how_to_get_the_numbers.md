---
title: "how to get the numbers?"
date: 2010-04-06
forum: General Help
---

### Post by luofeiyu on 2010-04-06
i can get : 0 1 2 3 4 5 6 7 8 9 10  with command
echo  -n  {0..10}

how can i  get  : 0 2 4 6 8 10?
and : 0  3 6  9??

---

### Post by iMisspell on 2010-04-06
One way would be to do a check in side your loop:

```

# even (=)
if [ $((${i} % 2)) = 0 ]; then
echo ${i}
fi

#odd (!=)
if [ $((${i} % 2)) != 0 ]; then
echo ${i}
fi


```

---

### Post by kaibob on 2010-04-06
> **luofeiyu said:**
> 
how can i  get  : 0 2 4 6 8 10?
and : 0  3 6  9??

Bash 4 in Karmic allows you to specify an increment:

```
$ echo {1..10..2}
1 3 5 7 9
$ echo {10..1..2}
10 8 6 4 2
```

Although frowned upon, you can also use the seq command:

```
$ echo $(seq 0 2 10)
0 2 4 6 8 10
```

And, a third option:

```
for ((i=0 ; i<=10 ; i=i+2)); do printf "$i " ; done ; echo
0 2 4 6 8 10
```

---

### Post by dcstar on 2010-04-06
> **luofeiyu said:**
> i can get : 0 1 2 3 4 5 6 7 8 9 10  with command
echo  -n  {0..10}

how can i  get  : 0 2 4 6 8 10?
and : 0  3 6  9??

Assignment time already?

---

### Post by bluefrog on 2010-04-06
seq 0 2 10
seq 0 3 9

man seq

---

