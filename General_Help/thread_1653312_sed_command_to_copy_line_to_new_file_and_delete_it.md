---
title: "sed command to copy line to new file and delete it at the same time"
date: 2010-12-26
forum: General Help
---

### Post by terminator14 on 2010-12-26
I have a file that is constantly being updated with lines. Some lines are important to me, others are not. I need to look for the lines that are important to me using a regular expression, copy them to a file, and delete them from the original file. Normally, that could easily be accomplished with

```
grep 'Important Lines: ' original_file >> /new/file
sed -i '/Important Lines: /d' original_file
```

The problem is that while sed is deleting lines in the second command, some new lines may appear that match the pattern that have not been copied to the new file by grep.

What I basically need is a single command (I imagine it would be a sed command) that would go line by line and check if the current line matches a pattern. If it does, append it to a new file, delete it, and move on. This way there would be no chance of a line being deleted without being processed (copied to the new file) first.

---

### Post by dcstar on 2010-12-26
> **terminator14 said:**
> I have a file that is constantly being updated with lines. Some lines are important to me, others are not. I need to look for the lines that are important to me using a regular expression, copy them to a file, and delete them from the original file. Normally, that could easily be accomplished with

```
grep 'Important Lines: ' original_file >> /new/file
sed -i '/Important Lines: /d' original_file
```

The problem is that while sed is deleting lines in the second command, some new lines may appear that match the pattern that have not been copied to the new file by grep.

What I basically need is a single command (I imagine it would be a sed command) that would go line by line and check if the current line matches a pattern. If it does, append it to a new file, delete it, and move on. This way there would be no chance of a line being deleted without being processed (copied to the new file) first.
See if this works:
```
tail +0 -f original_file | grep 'Important Lines: ' >> /new/file | sed -i '/Important Lines: /d' original_file
```

---

### Post by terminator14 on 2010-12-26
> **dcstar said:**
> See if this works:
```
tail +0 -f original_file | grep 'Important Lines: ' >> /new/file | sed -i '/Important Lines: /d' original_file
```

Seems amazingly simple and works great! I was going to put the thing on an infinite loop that runs every 60 seconds but this is so much better. Thanks!

Just one question: what's the +0 do? I get an error with it:

```
tail: cannot open `+0' for reading: No such file or directory
```

which shows tail trying to open +0 as if it were a file, failing, and continuing on to original_file which works great. So what's the +0 supposed to do? Make tail start from the beginning of the file?

---

### Post by dcstar on 2010-12-27
> **terminator14 said:**
> 
..........
which shows tail trying to open +0 as if it were a file, failing, and continuing on to original_file which works great. So what's the +0 supposed to do? **Make tail start from the beginning of the file?**

Yes, I may have got the syntax wrong, probably should be **-n+0**

---

### Post by terminator14 on 2010-12-28
> **dcstar said:**
> Yes, I may have got the syntax wrong, probably should be **-n+0**

You sir are a genius. I've always used tail like so:

```
tail -#
```
ex:
```
tail -20
```

to show more than the default 10 lines. With the -f option however, -# doesn't work. I've never been able to figure out how to make it do this. -n+0 works great, thanks! Very useful indeed...

---

### Post by dcstar on 2010-12-28
> **terminator14 said:**
> You sir are a genius.
......

Not really, just someone who has been using Unix/Linux for over 20 years....:

[http://www.dilbert.com/fast/2010-12-23/](http://www.dilbert.com/fast/2010-12-23/)

;)

---

### Post by terminator14 on 2010-12-28
> **dcstar said:**
> Not really, just someone who has been using Unix/Linux for over 20 years....:

Impressive.

> **dcstar said:**
> [http://www.dilbert.com/fast/2010-12-23/](http://www.dilbert.com/fast/2010-12-23/)

haha good one.

Ok so I'm testing the code you suggested above, and at first, it seemed to be working, but now, I'm not entirely sure. This is what I'm doing:

In one terminal, I'm running:

```
for (( i=1;;i++ )); do echo Test:$i >> original_file; done
```

in the other terminal, I'm running:

```
tail -n+0 -f original_file | grep 'Test' >> new_file | sed -i '/Test/d' original_file
```

In theory, it should work no matter which command starts running first, as long as the original_file already exists (or tail will complain about a non-existing file). The problem is, what it does seems to be pretty random. Sometimes it will begin filling up the new_file, but not delete anything from the original_file. Sometimes it will delete a few lines from the top of the original_file and keep filling up both the original_file and the new_file. Sometimes it will simply keep filling up the original_file and just leave the new_file empty. What's going on here? 

This may or may not be related to file descriptors changing for some reason. For example, when I try:

```
tail --follow=name
```
instead of simply
```
tail -f
```

in the command above, I get a message pretty much every time, about 10 seconds after I run the command that the original_file has been replaced and tail is now following the end of the new file called original_file. How could it have been replaced? Other than the 2 lines above, nothing is deleting the file or overwriting it. Could the problem be that despite the fact that tail realizes it's a different file (for some reason), sed doesn't? I'm not sure what's going on here...

---

### Post by terminator14 on 2010-12-29
To simplify the problem a bit, here's what I don't understand. When using the same:

```
for (( i=1;;i++ )); do echo Test:$i >> original_file; done
```

command to generate a file, and the following to show it:

```
tail -n+0 -f original_file | grep 'Test'
```

everything works ok. When I add on another pipe to grep, tee, or try to redirect it with >>, it breaks. Ex:

```
tail -n+0 -f original_file | grep 'Test' | grep .
```

no longer shows any output.

```
tail -n+0 -f original_file | grep 'Test' >> new_file
```

doesn't fill up the new_file

and 

```
tail -n+0 -f original_file | grep 'Test' | tee new_file
```

doesn't fill up the new_file either. Is this behaviour somehow expected, or is it as strange as I think it is?

Edit: the above was written for, and tried on an embedded linux system (a router). When I try the same on a regular ubuntu, it seems to work fine. Any reason there may be a difference? Like a settings somewhere on the number of pipes that is the maximum?

---

### Post by dcstar on 2010-12-30
> **terminator14 said:**
> 
..........
Edit: **the above was written for, and tried on an embedded linux system** (a router). When I try the same on a regular ubuntu, it seems to work fine. Any reason there may be a difference? Like a settings somewhere on the number of pipes that is the maximum?

Not all Linuxes are the same, there can be subtle differences in the commands and responses so what can work on one may not work on another without modification (if at all).

You just have to find out exactly what the differences are and try to work around them.

---

### Post by terminator14 on 2010-12-30
Hmmm. Removing the sed for now, the following seems to work a bit better:

```
tail -n+0 -f original_file | (while [ 1 ]; do read f; echo "$f" | grep 'Test'; done) >> new_file
```

because it copies every single line that tail reads from the file, whereas:

```
tail -n+0 -f original_file | grep 'Test' >> new_file
```

stops copying for some reason when the source stops generating lines, like when I interrupt the:

```
for (( i=1;;i++ )); do echo Test:$i >> original_file; done
```

loop.

It does seem to have trouble keeping up with the for loop, as seen when I stop the for loop and the original file has a few thousand lines, the new_file only has a few hundred, and keeps filling up about 100 lines per second until it is all caught up. Removing the grep from the while loop seems to speed it up significantly so it appears the grep is slowing it down (I guess it can only process so fast).

So with that worked out (unless someone knows of a faster way to do it?), it's time for sed. Whenever I add:

```
| sed -i '/Test/d'
```

to the command, the new_file stops filling up and the original_file keeps being written to. Basically it makes the whole command do nothing (except create an empty new_file). I even tried replacing the:

```
>> new_file
```

with another pipe:

```
| tee new_file
```

but it still results in the same thing. Is there perhaps a different way to make sed delete the lines grep finds? Or does grep have anything that can tell it to delete them?

I imagine it would look something like:

```
tail -n+0 -f original_file | (while [ 1 ]; do read f; echo "$f" | grep 'Test'; done) | tee -a new_file | sed -i "0,/`cat /dev/stdin`/d" original_file
```

but this obviously doesn't work.

---

### Post by terminator14 on 2010-12-30
I think I've got it. I may have figured out the problem too. Here's what I'm using:

```
tail -n+0 --follow=name out | (while [ 1 ]; do read f; echo "$f"; grep 'Test' >> new_file && sed -i "/$f/d" original_file; done)
```

The --follow=name was necessary in this case because "sed -i" does not edit a file directly - it runs sed on the original file and copies output to a temporary file. Then it switches the original file for the temporary one. This would normally cause tail to mess up because it follows a file descriptor by default and in this case, the file descriptor would point to a now deleted file. the --follow=name makes it work with the file name instead, which solves the problem.

I need to do a little more testing, but it seems to work pretty good. And it's based on your line of code dcstar, so thanks for that. Now the only problem is that it's crazy slow...

---

### Post by terminator14 on 2010-12-30
I think the problem with the code above that makes it slow is that 'sed -i' has to copy the file back and fourth each time. Is there a better way to delete lines from a file then sed -i? A way that doesn't involve the whole file being copied to a temp file first.

Sorry for bombaring the thread with replies but it's hard to contain the ideas in my head. I guess I'm just using this thread as a scratch pad for all of them.

---

### Post by DaithiF on 2011-01-05
With your current approach you have 2 processes writing to the original file ... whatever is creating the output, and your piped tail / grep / sed command which deletes lines from that original file.  What will happen if the first process writes a line of output while sed is doing its processing ?  You are likely to lose some data.

Better to leave the original file untouched and create two output files ... one with the matched lines and the other file a copy of the original but with those matched lines removed.

something like:

```
while read line
do
[[ $line =~ Test ]] && echo $line >> file1 || echo $line >> file2
done < <( tail -f somefile)
```

---

### Post by terminator14 on 2011-01-05
> **DaithiF said:**
> With your current approach you have 2 processes writing to the original file ... whatever is creating the output, and your piped tail / grep / sed command which deletes lines from that original file.  What will happen if the first process writes a line of output while sed is doing its processing ?  You are likely to lose some data.

Better to leave the original file untouched and create two output files ... one with the matched lines and the other file a copy of the original but with those matched lines removed.

something like:

```
while read line
do
[[ $line =~ Test ]] && echo $line >> file1 || echo $line >> file2
done < <( tail -f somefile)
```

Thanks. I'm gonna write this one down in my Linux notes folder in case I ever need it - it seems like the fastest way to go - it was able to process about a hundred thousand lines in just a few seconds.

When I started this thread, I had a log file on an embedded system that kept growing and I needed to take lines that matched a particular regular expression and save them to a different file, removing them from the original log at the same time. I know that this is the job of syslog (in the embeded system's case it was syslog-ng), but /etc/syslog-ng.conf seemed complicated and I figured it would take a while to understand so I thought I could, with your guys' help make a hack that would do the same job until I learned syslog-ng syntax. A few days ago I came across a book, Hardening Linux 2005, that explained in a few, easy to read pages exactly how to do what I needed with syslog-ng. I thought about marking this thread as solved but I was still curious if this hack could be done (in case I ever needed to do something like this again). It seems however that the hack is not as easy a thing to accomplish as I originally thought, especially since the same original_file has to be written to constantly by the source, and at the same time has to be written to again as lines from it are deleted. This slows down any attempts to do just that considerably. Maybe if I ever run into a similar problem again, and can't work around it, I'll continue my search for the answer, but for now, I'm satisfied with syslog-ng doing the job, and the techniques you guys suggested should I ever need them. I also learned a few things about bash (like the -n+0 argument), so thanks a lot guys for that.

---

