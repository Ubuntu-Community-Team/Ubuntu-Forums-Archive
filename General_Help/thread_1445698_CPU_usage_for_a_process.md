---
title: "CPU usage for a process"
date: 2010-04-02
forum: General Help
---

### Post by uuser10 on 2010-04-02
Hi,

How can I maximum the CPU usage for a process? And also use both cores if possible.


Thanks.

---

### Post by jobix on 2010-04-02
man nice

---

### Post by pbrane on 2010-04-03
Generally speaking the application itself has to be written to use multiple CPUs. Libraries such as openMP can be used to do concurent processing. As jobix pointed out *nice* can be used to change the priority of the application.

---

### Post by uuser10 on 2010-04-04
@jobix.
I checked out "nice" but I can't figure out how to get it to work properly.

Could you give me an example?

@pbrane.
Thanks. But its more a simple script I want to run to do some math.
I looked at MPopen but I didn't get very far.
Isn't there a way to tell it to use 2 cpus simple alike in windows in tastmanager for example?

Its a simple math calculation script I execute by running ./mathprogram. Its barely a page long. :)

But I calculated how long it would take a do the job I wanna do with it. But that would be at full speed of course.
So far it ran at 16%cpu usage. You see what I mean?!


Also if you happen to know. I found out that I can pipe the script so it would output the math stuff into a file. But I don't know how. Now when I run it it does everything in the terminal itself which is also very short. So I don't get much. :)
But do you know how I "pipe" it into an output file perhaps?


Thanks.

---

### Post by pbrane on 2010-04-06
I really don't know how to run a script concurrently on multiple processors. If the script doesn't use multiple processors in itself I'm not sure how to do it. I don't think you can run a program concurrently in two processors in Windows using just the taskmanager settings unless the program itself is SMP aware. Basically you are just telling the OS that this application can run on either core. Sometimes a program will "core hop" from one core to the other depending on how the OS runs the program. But what you want is concurrent processing. That is not trivial. If one part of the program relies on the output of a part before it then those two parts generally don't run concurrently.

An application/script has access to all cores by default. It depends on how the OS schedules the process. Thats why you have "core hopping". As I said concurrent processing is very different and non-trivial to code.

You wouldn't use openMP in a bash script. I have used it in DSP applications I have written in C/C++. But even then I really didn't *need* to use it. One application does all processing in about 140ms without openMP, ~90ms with it. So the gain wasn't substantial. If I were doing more long term processing it would be beneficial.

How long does your script take to complete? If it is only using 16% CPU then I don't see that as needing to run on multiple cores. If your script uses 100% CPU on one core for several minutes or hours then you may want to try concurrent processing.

You can redirect your script output like so:
```

./mathprogram > output.txt

```

---

### Post by uuser10 on 2010-04-16
You see, the thing is. I clocked my dual core to 20 gigaflops.

And to complete the math calculation it would take about 8 days.

That is running two cores at max/100% and 20 gigaflops.

So if it would only use one core than 10 gigaflops goes right out the window.

You see what I mean. This is kinda the problem and what its about.


And I also figured out how to use "nice" and run it as max. But that aside.

I was really hoping for a program to simple tell it to use both or multiple/x amount of cores. Suppose I'd have more available I would want it to use everything. Max max total.
Alike the taskmanager you described only something quite better and more linux of course. :D

---

