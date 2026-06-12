---
title: "Running python script in background"
date: 2010-09-12
forum: General Help
---

### Post by pmulgaonkar on 2010-09-12
I am trying to run a python script that works as a functional server automatically in the background under Ubuntu 10.04 (I think this used to work in 9.10, but I can't be sure).

Here is the simplest way I have found to show the problem. I can open a terminal window, cd to the right directory, and run "python servername.py &"

In the System Monitor, I see the python process being created and running. Everything runs just fine. The terminal window goes back to its usual prompt, etc. The process remains stable for days without crashing.

But, if I close the terminal window, the background process dies. I have tried redirecting its stdout, and stderr to a file, but there is nothing in the log file. 

Does anyone have any ideas why this happens? Shouldn't the background process continue independent of the terminal window which spawned it? What am I missing. 

And is this behaviour different from that under 9.10? Or am I misremembering how it worked there.

Any pointers will be much appreciated.

---

### Post by pmulgaonkar on 2010-09-12
OK. Solved my own problem :) 

I realised I was spending too much time debugging it as a Python issue, and not reading my unix manuals. The solution is to run the script using nohup, as in

```

nohup python servername.py &

```

--prasanna

---

### Post by Lukas666 on 2010-09-12
How about creating a shell script with your python command and backgrounding that script?

---

