---
title: "Echo-ing &quot;$1&quot;"
date: 2010-11-05
forum: General Help
---

### Post by nl4m on 2010-11-05
In a script, when I enter "echo $1" the first argument is outputted. When I enter:

a=1
echo "\$$a"

The output is just "$1", not the first argument. If I enter:

a=1
b=\$$a
echo $b

The output is still "$1" and not the first argument. How can I get echo to output the first argument without use "$1" directly?

---

### Post by WorMzy on 2010-11-05
> **nl4m said:**
> a=1
b=\$$a
echo $b

Why would this echo the first argument? You're specifically telling b to be a string with "$1" as it's value, so when you perform "echo $b", that's exactly what it prints: "$1".

Why can't you use "echo $1"?

---

### Post by nl4m on 2010-11-05
> **WorMzy said:**
> Why would this echo the first argument? You're specifically telling b to be a string with "$1" as it's value, so when you perform "echo $b", that's exactly what it prints: "$1".

Why can't you use "echo $1"?

I'm trying to make a script that has an output for each argument. I want it to say "Your first argument was abcd", "Your second argument was blah2", and so forth until there is no more arguments left. If the user inputs 2, or more, arguments and in my script I enter "echo $1" all the other arguments will not be outputted. That's why I thought if I type "a=1", then type "echo \$$a", increase the value of "a" by "1", then type again "echo \$$a" I can get to all the user inputs/arguments. You know?

---

### Post by sisco311 on 2010-11-05
How about:
```

i=1
for arg in $@; do
  echo "$i: $arg"
  i=$((++i))
done

```

EDIT:
```
n=1
echo ${!n}
#or
echo ${@:$n:1}

```

---

### Post by nl4m on 2010-11-05
You are a Genius! This is exactly what I wanted. And you put it in such simple terms even I understand it. This is great. Thank you so much! 

> **sisco311 said:**
> How about:
```

i=1
for arg in $@; do
  echo "$i: $arg"
  i=$((++i))
done

```

---

