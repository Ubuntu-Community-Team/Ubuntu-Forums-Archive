---
title: "make bash script run like batch with echo on, possible?"
date: 2012-03-21
forum: General Help
---

### Post by Dreamer Fithp Apprentice on 2012-03-21
Is there any way to make a bash script run in a terminal like a dos batch with echo on? That is to say, every line in the script appears in the terminal just as it would if you typed it in by hand, followed by the system's response just as it would appear if you had entered the command by hand, line by line, until the script finishes, and then return a prompt from which you can scroll up and study how it went or just go on typing in more commands?

I've seen people advise the -x switch in the shebang, like #!/bin/bash -x and also seen the trick of invoking the script with something like "gnome-terminal -e scriptname.sh" but neither one of those really do the same thing. If not bash is there some other linux scripting language that supports a mode like this? Right about now I'm really missing 4dos.

---

### Post by wallaroo on 2012-03-21
You could turn on 'debug' in your script which will echo each of the commands as they are executed.
i.e. add the command 'set -x' as line 1 in your script, and 'set +x' as the last line in the script.

You can then use the gnome-terminal command to run it, with added 'bash' commands to keep the terminal open.

e.g.
```
gnome-terminal -e "bash -c \"yourscriptfilename; exec bash\""
```

---

### Post by Dave_L on 2012-03-21
You can also specify the -x option when invoking the script:

```
bash -x script.sh
```

For more information, see: [http://tldp.org/LDP/abs/html/debugging.html](http://tldp.org/LDP/abs/html/debugging.html)

---

### Post by Habitual on 2012-03-21
+1 for inline -x ...

Also...

```
#!/bin/bash
set -x
...
```

---

### Post by Dreamer Fithp Apprentice on 2012-03-21
Wallaroo;  Dave_L;  Habitual --

Thanks, guys!

I'm kicking myself for not having asked this question a lot sooner. Debugging, of course, is one of the two main reasons I wanted this -- the other being to facilitate clearer understanding what the commands I was running blind are actually doing. 

I've been hanging out here a bit for quite a while now. I used to be LewRockwellFAN before I lost my password to an inadequately backed up Seagate hard drive. What I've learned here, not just from responses to my own queries but even moreso perhaps in the past from lurking in other people's threads, along with a heap of googling, has gotten me sufficiently up to speed that I can do useful scripting and I appreciate everyone who takes the trouble to post answers and I try to pay it forward when I can by answering some of the ones I think I might have a useful answer to.

But I have to say that your answers here in this thread, have been the most extremely useful ones I've been lucky enough to receive.  This will make every scripting project tons easier. Thanks again.

---

