---
title: "Redirecting"
date: 2010-04-24
forum: General Help
---

### Post by nl4m on 2010-04-24
I have some questions about file descriptors and redirecting. How I can change the "1" file descriptor to a "5". Then use the "5" file descriptor to output the content to another file. This code does not work:

```
echo "hello" 5>&1 5> somefile
```


I read somewhere that this code can change the file descriptor, but it too does not work:

```
exec 5< file1 6> file2
```

I have tried ">&5", and "exec 5< file1" return "5> file2". Neither worked. Is there a way that I can change the file descriptors and still have the contents of a file outputted to another file.

I even tried making a file with these commands:
```
echo "This is null" 5>&1 
echo "This is Not null"
```

I would then launch the command prompt and type in "(file name) 5> /dev/null". Yet I get both lines as the output. When I replace "5>&1" with "1>&2" and type in the command prompt "(file name) 2> /dev/null" it works. The first line is sent to /dev/null and the second is outputted. I want to know how can I change the file output descriptor to "5" and send it using "5>" to null?

---

### Post by rnerwein on 2010-04-25
hi
i think that's what you want:
exec 5>bla                            # open the file descriptor 5 first
exec 1>&5                            # redirect stdout to fd 5
echo "this is going to ./bla"   # stdou is fd 5 now
echo "this will prove it ! "  5>> bla

have fun  :-)

ciao

---

### Post by nl4m on 2010-04-26
> **rnerwein said:**
> hi
i think that's what you want:
exec 5>bla                            # open the file descriptor 5 first
exec 1>&5                            # redirect stdout to fd 5
echo "this is going to ./bla"   # stdou is fd 5 now
echo "this will prove it ! "  5>> bla

have fun  :-)

ciao

You're a genius. It worked like a charm!!! Thanks.

---

