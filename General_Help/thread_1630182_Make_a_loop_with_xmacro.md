---
title: "Make a loop with xmacro"
date: 2010-11-24
forum: General Help
---

### Post by ilcontegis on 2010-11-24
Hey guys i need to repeat a sequence of buttons in an infinite loop.
I can't find the command to do that on xmacro.
Can somebody help me pls.

Thank you

---

### Post by ilcontegis on 2010-11-25
up pls i need it.

---

### Post by searchfgold6789 on 2010-11-25
There is rumor of people who would create a bash script that makes the thing run in a bash loop. I am not quite sure how to do this though, being a bash script novice.

---

### Post by ilcontegis on 2010-11-25
> **searchfgold6789 said:**
> There is rumor of people who would create a bash script that makes the thing run in a bash loop. I am not quite sure how to do this though, being a bash script novice.

Thank you.
Can somebody explain me how can I do a bash script?
Thank you

---

### Post by ilcontegis on 2010-11-26
Found it!

I just run in the terminal the following
```
for ((;;)) do cat ~/quote | xmacroplay ":0.0"; done
```

where quote is my macro previously recorded.

---

### Post by Jakeirs on 2011-01-18
Could somebody write that commend to repeat xmacro sequences. Give me this in example.

---

### Post by Xanko on 2011-02-11
```
for ((;;)) do xmacroplay :0 < macro.txt; done
```

This runs the command xmacroplay on screen :0 with standard input (macro.txt). Inside the .txt file is the commands for running the macro. (you can experiment using the command xmacrorec :0 >> macro.txt to record your macro)

---

### Post by ikester8 on 2011-05-28
Thanks for this. I know this is a simple mistake, but I tried it on a simple "MouseButtonDown 1" program and it caught me in a loop I couldn't get out of without rebooting. Is there any way to specify it to run only a certain number of times?

---

### Post by prodigy_ on 2011-05-28
Of course. Example (bash, the loop will be executed 100 times):
```
for (( i=0; i<100; i++ ))
do
  <put your commands here>
done
```

---

### Post by layr on 2011-09-14
How about creating a finite loop, which limit is defined by other arguments than running count?

Eg. script that checks whether a process is running; if it is, sleeps for say 5 sec, then checks again etc, until the program isn't running and completes the task.

Would be easy if there was a bash command that went to specified line, eg. "goto line 23" or so. Can't find such command tho;D

---

