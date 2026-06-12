---
title: "time vs /usr/bin/time --- getting different results..."
date: 2012-05-17
forum: General Help
---

### Post by Kdar on 2012-05-17
I am getting different results from using time and /usr/bin/time -f "%e" from two following scripts:

```
(time xz -kfc -file | ssh name@serverIP "cat > /dev/null") 2>>timelogfile.txt
```
```
(/usr/bin/time -f "%e" xz -kfc -file | ssh name@serverIP "cat > /dev/null") 2>>timelogfile.txt 
```

whats wrong? is it the way I wrote my script?

---

### Post by rai4shu2 on 2012-05-17
I'm guessing it's related to the difference between

```
help time
```

and

```
man time
```

It's basically internal BASH code versus an external app.

---

### Post by Kdar on 2012-05-17
right. I think time is the default, internal utility for the shell.

And /usr/bin/time is GNUtime, which I had to install from repository.

However, which one should I trust?

I run 10 iterations for each and I was getting different results:
Averages:
time - 6.1614
/usr/bin/time -f "%e" 4.4810 (most times were close to 4)
perf stat - 5.4821

Then I tried to put working portion of script into a file and run it as a script with time utility in front of it.
```
xz -kfc -file | ssh name@serverIP "cat > /dev/null"
```
and then run:
time ./file.sh
usr/bin/time -f "%e" ./file.sh
perf stat ./file.sh

Averages:
time - 5.6286
/usr/bin/time -f "%e" - 6.1830 (now most times are close to 6)
perf stat - 6.5933

---

### Post by rai4shu2 on 2012-05-17
I doubt there's much difference in accuracy between the two, so just use the BASH version.

---

### Post by Kdar on 2012-05-17
I tried to run 20 iterations too.. same thing.

Does anyone know if the way I wrote my script will measure both time for compression and for piping (the whole process)

---

### Post by David Andersson on 2012-05-18
> **Kdar said:**
> 
Does anyone know if the way I wrote my script will measure both time for compression and for piping (the whole process)

/usr/bin/time only measures the command in its argument. That is, the xz command in post #1 and the script (the whole thing) in post #3. Of course, when output is piped to something (or input from something), the "real" or "elapsed" time will include time waiting for the other process, if it is a bottleneck.

The time command built into Bash takes a pipeline as its argument. That is, the whole thing in both post #1 and #3. Seems you can use parenteses to restrict it to one command: ((time xz ...) | ssh ... )

---

### Post by Kdar on 2012-05-18
How can I make /usr/bin/time to measure both the compression and any delay waiting on transfer to finish?

I started to use it instead of shell's time since it gives more formatted output. (I didn't know of this problem before)

Also......
Since time is built into a shell.. Is it more efficient and accurate since it doesn't fork a new process?

---

### Post by Kdar on 2012-05-18
Can I be sure that time and time -p will give me similar results?

---

### Post by rai4shu2 on 2012-05-18
If I ever need precision in my network logging, I always take a look at Wireshark. That gets the job done. I don't know about all this fiddling with time (which, after all, uses a lot of CPU and wait()s and who knows what).

---

