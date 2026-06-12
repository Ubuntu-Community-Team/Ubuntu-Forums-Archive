---
title: "Question about a bash file"
date: 2009-07-31
forum: General Help
---

### Post by amitalon on 2009-07-31
Hi,

I'm new to linux/ubuntu. 
My general question is:
I've written a bash file--

#!/bin/bash
meep /home/amit/webflux.ctl >& webflux.out

meep webflux.ctl | tee webflux.out
h5topng -S 3 webflux-eps-000000.00.h5 -c /usr/share/h5utils/colormaps/gray
h5topng -S3 -ZC webflux-eps-000000.00.h5 -c /usr/share/h5utils/colormaps/dkbluered webflux-hz-slice.h5


meep N=0 webflux.ctl | tee webflux.out0
grep flux1: webflux.out > flux.dat
grep flux1: webflux.out0 > flux0.dat

Now, is bash file executes every command with out waiting for it to complete? More specifically, the the first command takes a few minutes, and the other commands that follow it depend on its output. Is the file going to work was written now, or do I need to modify it?

Thank you,

Amit

---

### Post by Brandon Williams on 2009-08-02
Unless you background a process (you haven't) or the process backgrounds itself (you'll have to check whether that's true), it will stay in the foreground and execute to completion before the command is executed. Is it possible that the command you're counting on is moving itself to the background? What happens if you run that same command at a command prompt?

---

### Post by kingjere on 2009-08-02
I have never seen an "&" after a output redirect i.e. >& in the first line of the script. Doesn't that background the meep?

---

### Post by Brandon Williams on 2009-08-03
In bash, '>& file' is used to redirect both stdout and stderr to the named file. The bash reference says that '&> file' is preferred, but doesn't say why.

---

