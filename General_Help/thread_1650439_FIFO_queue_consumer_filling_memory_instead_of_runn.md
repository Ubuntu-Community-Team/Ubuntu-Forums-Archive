---
title: "FIFO queue: consumer filling memory instead of running"
date: 2010-12-21
forum: General Help
---

### Post by DasherDooDad on 2010-12-21
I created a FIFO file using the mkfifo command.
I passed this file name to an application to use for its output.
I wrote a PERL script that reads from the FIFO and processes the output.

The main reason is that the application generates a huge amount of output.
I should be able to quickly process it on-the-fly and collect statistics, without consuming much CPU time or memory space.

What I'm finding instead, though, is that the consumer process won't advance past the first read command until the producer process has completed or been killed.
The consumer process ends up using a huge amount of memory, and both it and the producer process can die because memory ran out.

Apparently processing is not happening on-the-fly.
Evidently the producer data is just filling up memory and the consumer waits until the FIFO is closed before it processes the input.

Is there a way to control this? I tried setting
          ulimit -v 1024
to give the consumer process a 1MB limit, but it's not making any difference.
          ulimit -a
gives me 
          pipe size            (512 bytes, -p) 8

This is on Ubuntu 10.10, 64bit.

---

### Post by DasherDooDad on 2010-12-21
Here are some snippets. To make the FIFO and invoke the consumer:

mkfifo buffer.trace
get_stats_1a buffer.trace > profile &
PID1=$!

The consumer starts off as follows:

while ( $END_TIME == 0 ) {
    open INFILE, "<", $ARGV[0];     # Loop causes it to reopen.
    foreach $line ( <INFILE> ) {

When I run this under the PERL debugger, it advances past the "open" as soon as the producer process kicks off.
However, it won't advance past the "foreach" line until the producer process ends.

---

