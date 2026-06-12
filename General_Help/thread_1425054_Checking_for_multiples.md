---
title: "Checking for multiples"
date: 2010-03-08
forum: General Help
---

### Post by nathand28 on 2010-03-08
In a Bash script how do you check for multiples? 
IE, check for multiples of 3, and echo a word.
[Here]("http://www.unixforum.co.uk/topic/9174-checking-multiples/") it says use the modulus operator %, and, in my script, I have it set up as 
```
if test $n%3 == 1
```
Obviously, I'm trying to test for multiples of 3. What would the right code be?

---

### Post by LoneWolfJack on 2010-03-08
I'm not that much into bash programming and maybe I misunderstand what you are trying to do, but you can try something like this

```
if test $n%3 > 0
```

this is true if modulo returns something greater than 0 and if it does so, the number is not a multiple

---

### Post by richardjh on 2010-03-08
[There is a famous test question]("http://en.wikipedia.org/wiki/FizzBuzz"), this is my (probably quite crappy) solution which should help you on your way.

For each number from 1 to 100, print the number unless it is a multiple of 3, then print Fizz, if it is a multiple of 5 print Buzz, and if it is a multiple of 3 and 5 print FizzBuzz.

```
for i in `seq 1 100`
do
if [[ `expr $i % 3` -eq 0 ]];then
 echo -n "Fizz"
  if [[ `expr $i % 5` -eq 0 ]];then
   echo -n "Buzz"
  fi
elif [[ `expr $i % 5` -eq 0 ]];then
 echo -n "Buzz"
else
 echo -n $i
fi

echo

done
```

I hope it clarifies how to use modulo in bash.

---

### Post by nathand28 on 2010-03-09
That helped a lot.
Many thanks.

---

