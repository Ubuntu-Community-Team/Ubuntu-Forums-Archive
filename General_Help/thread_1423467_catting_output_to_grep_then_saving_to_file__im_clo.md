---
title: "catting output to grep then saving to file ? im close but cant get it"
date: 2010-03-06
forum: General Help
---

### Post by Rizla on 2010-03-06
Hey,

I'm trying to figure out why this expression is not working as it should.

I'm trying to cat data from my usb serial port and then modifying the ouput with grep to strip the extra blank lines and lastly saving it to a file.

This is what i'm doing:

cat /dev/ttyUSB0

this works successfully and I see all the input from serial as I should.  The data coming in looks like this:

Line1

Line2

Line3

What i want the output to look like is this:

Line1
Line2
Line3

After doing a little searching i found two ways of doing it, one using grep.  Like so:

cat /dev/ttyUSB0 | grep .

Which actually produces the output I want:

Line1
Line2
Line3

Only problem is that I cant pipe that to a text file for some reason.  I tried this:

cat /dev/ttyUSB0 | grep . > log.txt

but when i look at the log file afterwards there's no data.  

If i just output the the data without going through grep, it saves it successfully in the log file..

what am i doing wrong with piping greps output to a file?

Thanks.

---

### Post by dcstar on 2010-03-06
> **Rizla said:**
> 
.......
cat /dev/ttyUSB0 | grep . > log.txt

but when i look at the log file afterwards there's no data.  

If i just output the the data without going through grep, it saves it successfully in the log file..

what am i doing wrong with piping greps output to a file?

Thanks.

Try:

```
cat /dev/ttyUSB0 | grep "." > log.txt
```

---

### Post by Rizla on 2010-03-06
> **dcstar said:**
> Try:

```
cat /dev/ttyUSB0 | grep "." > log.txt
```

no it didnt save to the file, but adding the quotes to grep still worked.  It doesnt make sense how that cant be valid.  Your taking the ouput from grep and saving it to a file.. thats like IO redirect 101.

---

### Post by flippo on 2010-03-06
I bet its not flushing the stream (there is a buffer filled with the data, and it isn't actually written until the stream is closed).  I'm not sure how to take care of this with output redirecting.  Maybe >> will have better luck? (note >> is append)

---

### Post by Rizla on 2010-03-06
> **flippo said:**
> I bet its not flushing the stream (there is a buffer filled with the data, and it isn't actually written until the stream is closed).  I'm not sure how to take care of this with output redirecting.  Maybe >> will have better luck? (note >> is append)


the append didnt work either..  hmm.. not sure what else I could try

---

### Post by patchwork on 2010-03-06
For kicks, I gave this a try with a test file, text with newline IFS.  The cat/grep/redirect combo worked smoothly, both with > and >>....   Not sure exactly what is happening with your set-up

```
kevin@crystalpepsi:~/Desktop$ cat tester
1

2

2

2

3

3

3

34

4

4

4

4

5

5

5

5
kevin@crystalpepsi:~/Desktop$ cat tester | grep .
1
2
2
2
3
3
3
34
4
4
4
4
5
5
5
5
kevin@crystalpepsi:~/Desktop$ cat tester | grep . > tester2
kevin@crystalpepsi:~/Desktop$ cat tester2
1
2
2
2
3
3
3
34
4
4
4
4
5
5
5
5
kevin@crystalpepsi:~/Desktop$ 

```

---

### Post by Rizla on 2010-03-06
> **patchwork said:**
> For kicks, I gave this a try with a test file, text with newline IFS.  The cat/grep/redirect combo worked smoothly, both with > and >>....   Not sure exactly what is happening with your set-up

```
kevin@crystalpepsi:~/Desktop$ cat tester
1

2

2

2

3

3

3

34

4

4

4

4

5

5

5

5
kevin@crystalpepsi:~/Desktop$ cat tester | grep .
1
2
2
2
3
3
3
34
4
4
4
4
5
5
5
5
kevin@crystalpepsi:~/Desktop$ cat tester | grep . > tester2
kevin@crystalpepsi:~/Desktop$ cat tester2
1
2
2
2
3
3
3
34
4
4
4
4
5
5
5
5
kevin@crystalpepsi:~/Desktop$ 

```


So i pretty much did something similar, i created a text file with the output similar to what i get from the serial port and it worked also..

cat sample.txt | grep "." > newlog.txt

but for some reason it doesnt work with the output from the serial port.. ug.

---

### Post by flippo on 2010-03-06
I am quite convinced the buffer is not flushing.  In your test cases when the program finishes the buffer flushes, but in the real case the input never finishes, so the buffer never flushes.  I have been unable to figure out how to flush the buffer (I've been googling), but I would recommend just rewriting this in C/C++ or python, it should be easy to open the stream as a file, drop empty lines, then write the result out to a file (and flush accordingly!).

---

### Post by falconindy on 2010-03-06
This is the kind of thing the 'stdbuf' program was made for. It allows you to change the functionality of a program (such as grep) which will normally buffer its output.

This should do the trick, if my hunch is right.
```
cat /dev/ttyUSB0 | stdbuf -o0 grep . > log.txt
```
That's a zero, not a capital o as an argument to the small -o option.

---

### Post by Rizla on 2010-03-06
> **flippo said:**
> I am quite convinced the buffer is not flushing.  In your test cases when the program finishes the buffer flushes, but in the real case the input never finishes, so the buffer never flushes.  I have been unable to figure out how to flush the buffer (I've been googling), but I would recommend just rewriting this in C/C++ or python, it should be easy to open the stream as a file, drop empty lines, then write the result out to a file (and flush accordingly!).

haha, doing it in C would be ideal, but i havent touched it so thats a no go.  I have a php serial library that can probably do that, but was hoping to use the OS tools rather than relying on php

---

### Post by flippo on 2010-03-06
I would try falconindy's suggestion.  That uses the terminal commands to control the buffer for you, the thing I couldn't figure out.

---

### Post by falconindy on 2010-03-06
as a last resort, just use sed to ditch the empty lines:

```
sed -i '/^$/d' file.log
```

---

### Post by dcstar on 2010-03-06
Instead of cat try:

```
tail -f
```

---

### Post by falconindy on 2010-03-06
> **dcstar said:**
> Instead of cat try:

```
tail -f
```
tail is actually buffered as well. inotail, is not.

---

### Post by Rizla on 2010-03-06
tail -f /dev/ttyUSB0 doesnt output anything..

---

### Post by jnylen on 2010-05-19
I know this thread is a couple months old but:

1) I can't figure out how to get the stdbuf command in Ubuntu Karmic or Lucid.

2) The --line-buffered option to grep should do what you want.

---

