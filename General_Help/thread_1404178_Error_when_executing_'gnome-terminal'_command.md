---
title: "Error when executing 'gnome-terminal' command"
date: 2010-02-11
forum: General Help
---

### Post by ubuntuv on 2010-02-11
hello,

I wrote a shell script and tried to execute it in separate terminal using command 'gnome-terminal -e <script>'. When executing first time, it went fine.  From second time, I am getting error 'There is error creating child process for this terminal' repeatedly.  Please tell me, if this way of calling is wrong.

-uv

---

### Post by patchwork on 2010-02-11
Try gnome-terminal -x /path/to/script

also, do you have any other parameters, such as geometry or profile, on the command line?   If you do, make sure that the -x <script_info> is at the end of the command.

---

### Post by ubuntuv on 2010-02-11
I tried giving -x option, still getting the same error.  There are no geometry parameters.  Can you suggest a fix?

-uv

---

### Post by patchwork on 2010-02-11
Are you calling the script the same way as you did the first time (i.e did you type the command out the first time and are now trying to call the command from a keyboard preference?)

If you are calling the command the same way as you did the the first time you called it, I don't know the answer.

---

### Post by kaibob on 2010-02-11
> **ubuntuv said:**
> hello,

I wrote a shell script and tried to execute it in separate terminal using command 'gnome-terminal -e <script>'. When executing first time, it went fine.  From second time, I am getting error 'There is error creating child process for this terminal' repeatedly.  Please tell me, if this way of calling is wrong.

-uv


The answer to your question varies, depending on the script and what you want to happen after the script is executed, but as a general rule I use the following to open a terminal window and execute a script. 

```
gnome-terminal --execute bash -c "scriptname ; bash"
```

By way of example, I created a shell script named sname that changed directories and executed the ls command. I then created a desktop launcher that contained the following command:

```
gnome-terminal --execute bash -c "/home/kaibob/bin/sname ; bash"
```

When I clicked on the launcher, a terminal window opens and lists the contents of the directory. The terminal window stays open and shows a prompt.

---

### Post by rnerwein on 2010-02-11
hi
i think the best will be: post the "gnome-terminal" call of your script. we are no clairvoynats.
ciao :-)

---

