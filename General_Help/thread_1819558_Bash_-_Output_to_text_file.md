---
title: "Bash - Output to text file"
date: 2011-08-06
forum: General Help
---

### Post by zero2xiii on 2011-08-06
Hay all,

I have a question to simple to return results in google it seems:

How can you direct output of a command (lets say echo) to be added to the BEGINING of a text file instead of the end?

I know:

```
echo some text here >> sometextfile.txt
```

adds the line "some text here" to the END of the file "sometextfile.txt",
but i need it to be added to the very begin of the file (make this line one) and still keep all the previous content.

Is this possible? or is a [SED command]("http://www.linuxquestions.org/questions/programming-9/bash-read-or-write-to-specific-line-in-text-file-664654/") the only way?

---

### Post by pasu11 on 2011-08-06
Sure, there are many ways to do the same thing. Here is a simple one:

syntext: sed '<Line Number you want to insert>i <text you want to insert>' <File Name you are outputting>

example: sed -i '1i some text here' sometextfile.txt

Description: the 1i means you want to insert the text to the 1st line. 

example 2: If you insert 'A' to the 3rd line of the file test.txt
1
2
3
4

You can do this:
sed -i '3i A' test.txt

then it will look like:
1
2
A
3
4

Hope it helps

source: [http://www.unix.com/302133610-post3.html](http://www.unix.com/302133610-post3.html)

---

### Post by zero2xiii on 2011-08-06
Ah awesome!

The final syntax I used was:

```

read input

sed -i "1i$input" fileout.txt
```

this wont generate the text file "fileout.txt", but a simple if ! -z fileout.txt statement in the begining of the routine sorted that out.

Thanks alot!

I just cant seem to find a decent SED guide or manual, I've read numerous documents on sed, but I havent come across this usage before. Thanks for pointing it out :D

---

### Post by pasu11 on 2011-08-06
That's a good idea too. Glad to hear it helps :)

---

