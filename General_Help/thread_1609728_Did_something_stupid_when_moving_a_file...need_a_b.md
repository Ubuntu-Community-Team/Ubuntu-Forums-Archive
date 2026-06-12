---
title: "Did something stupid when moving a file...need a bit of help."
date: 2010-10-30
forum: General Help
---

### Post by dolphy on 2010-10-30
I ran the command: 

```

sudo mv filename /~

```

I meant to move it to my home directory but realize that I was running as sudo.  Now I can't find the file.  Any help on this one?  

I know I acted without thinking first.

---

### Post by Rocket2DMn on 2010-10-30
There is no such thing as /~.  If you were using sudo with -i or -s it may be in the /root folder. Otherwise your environment variables should remain intact and the file should be in your home directory.  Is it a hidden file?

---

### Post by xjesse on 2010-10-30
Use the:

```
locate ***FILENAME***
```

to search for it. Hope you find it!

---

### Post by dolphy on 2010-10-30
I had it in /var/www and I wanted to move it to my home directory.  After I executed the command:

```

sudo filename /~

```

It moved it from /var/www and now I'm not sure where it went.  I tried to search using Nautilus with no luck.

---

### Post by dolphy on 2010-10-30
> **xjesse said:**
> Use the:

```
locate ***FILENAME***
```

to search for it. Hope you find it!


Tried that already and nothing.  Not a huge deal.  Just a pain in the *** to grab a backup.

---

### Post by cgroza on 2010-10-30
I think it took it at the root of the FS and gave it the name of ~. Try locate /~.

---

### Post by Rocket2DMn on 2010-10-30
The commands that you are showing us don't make any sense, it should be complain when you try to run them.  Please show us the exact command that you executed (you can scroll up in the terminal to see previous commands or open and look in ~/.bash_history). Again, /~ is not a valid directory so the file should not have moved at all.

---

### Post by cgroza on 2010-10-30
> **Rocket2DMn said:**
> The commands that you are showing us don't make any sense, it should be complain when you try to run them.  Please show us the exact command that you executed (you can scroll up in the terminal to see previous commands or open and look in ~/.bash_history). Again, /~ is not a valid directory so the file should not have moved at all.


It executes here when run with sudo. I just moved a file like that just to test.

EDIT: I can't find the file either. It is not at the / nor in the ~.

---

### Post by dolphy on 2010-10-30
> **Rocket2DMn said:**
> The commands that you are showing us don't make any sense, it should be complain when you try to run them.  Please show us the exact command that you executed (you can scroll up in the terminal to see previous commands or open and look in ~/.bash_history). Again, /~ is not a valid directory so the file should not have moved at all.

I did display the exact command except the file name is different.

```

sudo mv filename /~

```

---

### Post by Rocket2DMn on 2010-10-30
You're right, that is odd that it runs the command even though it's not a valid directory.  I tried it and it moved my file to /root, please check there like I specified in my first response and let us know if it's there.

---

### Post by dolphy on 2010-10-30
I found it!  It is in the '/' directory and the file changed name to '~' .

Hope this make sense to you all.

---

### Post by Rocket2DMn on 2010-10-30
> **dolphy said:**
> I found it!  It is in the '/' directory and the file changed name to '~' .

Hope this make sense to you all.

I see that as well, do you also see the file with its original name in /root ?

---

### Post by dolphy on 2010-10-30
I marked the thread as SOLVED.  Thanks guys.  Next time I'll try not to be so dumb!  Need to shed my terminal commands more!

---

### Post by dolphy on 2010-10-30
> **Rocket2DMn said:**
> I see that as well, do you also see the file with its original name in /root ?

The original name is not there.

---

