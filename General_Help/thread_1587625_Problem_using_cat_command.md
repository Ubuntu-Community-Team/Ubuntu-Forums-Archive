---
title: "Problem using cat command"
date: 2010-10-03
forum: General Help
---

### Post by mashhype on 2010-10-03
Hi,

I am very new to Linux and have searched online unsuccesfully to find an answer to something that seems very simple:

I want to use the cat command to create a file and put one word in that file all from the command line...

so here is what I want to do --

cat >test.dat wow

Now that is what I am typing in the command line, then hitting CONTROL-D and then enter...

when I hit enter, I get "cat: wow: no such file or directory"

Can someone please explain what I am doing wrong???

Thanks

MS

---

### Post by WorMzy on 2010-10-03
cat reads a file and displays the output. It can write the contents of one (or more) file(s) to another file, but it doesn't work the way you're trying to use it.

You want the echo command:

```
echo "wow" > test.dat
```

---

### Post by mashhype on 2010-10-03
Hi,

Is it possible to write "wow" to a file that I create using cat from the command line?  If so, what is the correct way to do it?

---

### Post by papibe on 2010-10-03
> $ cat >test.dat wow
You're placing the word "wow" in the arguments, so cat tries to open a file called wow.

Try:
[LIST=1]
[*]$ cat > test.dat
[*]write wow, or whatever you want in the file, and then
[*]hit ctrl-d
[/LIST]

---

### Post by mashhype on 2010-10-03
So this is telling me that there is no way, in UBUNTU to actually write something in the file at the same time you create it from the command prompt??

Because there are examples in Linux that shows that you can do it...so I was assuming you could do the same in Ubuntu...

---

### Post by WorMzy on 2010-10-03
You can use ```
echo wow | cat > test.dat
``` if you really have to, but it seems rather redundant to me.

> **mashhype said:**
> So this is telling me that there is no way, in UBUNTU to actually write something in the file at the same time you create it from the command prompt??

Reread my first post.

---

### Post by mashhype on 2010-10-03
Sorry about that, just followed your instructions...I get it now...so I really needed to use the echo command...its just confusing because online it shows that you can do it the way I was originally trying...

thanks.

---

### Post by xaegis on 2010-10-03
> **mashhype said:**
> Hi,

I am very new to Linux and have searched online unsuccesfully to find an answer to something that seems very simple:

I want to use the cat command to create a file and put one word in that file all from the command line...

so here is what I want to do --

cat >[COLOR="Red"]test.dat wow[/COLOR]

Now that is what I am typing in the command line, then hitting CONTROL-D and then enter...

when I hit enter, I get "cat: wow: no such file or directory"

Can someone please explain what I am doing wrong???

Thanks

MS

Your code is correct. try this: 
```

cat > test.dat
wow

```
then Ctrl-d
press enter after after ".dat"
then enter the "wow"
and press enter

If you put them on the same line it thinks you are asking it to concatenate the two files one of which doesn't exist.

hope this helps.

:)

Oops well this has already been covered. forget I said anything

---

### Post by mashhype on 2010-10-03
OK NOW THAT is what I was missing thank you SOOO much...that clears things up alot

So I actually hit enter and type the string on the next line then hit control-D

YOU ARE AWESOME...thanks!!

---

### Post by WorMzy on 2010-10-03
> **mashhype said:**
> Sorry about that, just followed your instructions...I get it now...so I really needed to use the echo command...its just confusing because online it shows that you can do it the way I was originally trying...

thanks.

Where abouts are you reading it? Do you have a link to it?

---

### Post by papibe on 2010-10-03
> **mashhype said:**
> So this is telling me that there is no way, in UBUNTU to actually...

There are many ways to do that. Both WorMzy's posts can help you.

May be if you tell us more of what you want to accomplish, we can give you more options.

Regards.

---

### Post by mashhype on 2010-10-03
[http://www.mediacollege.com/linux/command/cat.html](http://www.mediacollege.com/linux/command/cat.html)

is one of them but after my previous post it was my error..


i have to actually type the text of the file on a new line...sorry for the confusion and thanks for all of your prompt responses!

---

### Post by WorMzy on 2010-10-03
In that tutorial, the files already contained the text that was displayed; cat just printed out the contents of each file., it wasn't being used to make either file.

---

