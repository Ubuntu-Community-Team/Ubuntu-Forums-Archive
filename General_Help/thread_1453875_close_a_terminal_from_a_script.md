---
title: "close a terminal from a script"
date: 2010-04-13
forum: General Help
---

### Post by kumoshk on 2010-04-13
If I want to open a terminal, run a script in it and have that script close that specific terminal wherein I ran the script, how do I do that? The exit command doesn't work.

---

### Post by v1ad on 2010-04-13
a lot easier if you know the name it is running in. maybe screen or something. 
have you tried ps -ef | grep program name (or pid number)

kill programname

since you are running in open shell ill recommend you to use screen and close shell after u hide screen. screen gets closed itself when completed.

---

### Post by kumoshk on 2010-04-13
> **v1ad said:**
> a lot easier if you know the name it is running in. maybe screen or something. 
have you tried ps -ef | grep program name (or pid number)

kill programname

since you are running in open shell ill recommend you to use screen and close shell after u hide screen. screen gets closed itself when completed.

Hmm. I'm not sure how to get the name without the user of the script having to know it and type it in every time. I don't want to close other terminals besides the one where the user runs the script.

However, I don't know that screen will work either as it needs to work with a terminal that I open manually via nautilus-open-terminal. Could that still work somehow?

Anyway, it's not a huge deal if I can't get this to work, but if there is a solution that wouldn't take too much effort, then I'd love to hear about it.

---

### Post by azzamite on 2010-04-13
How about this:

```
xfce4-terminal -x ls -R /etc/
```

This will open the terminal emulator from xfce, execute ls
and close the terminal as soon as the command finishes.

---

### Post by kumoshk on 2010-04-13
> **azzamite said:**
> How about this:

```
xfce4-terminal -x ls -R /etc/
```

This will open the terminal emulator from xfce, execute ls
and close the terminal as soon as the command finishes.

Hmm, that wouldn't work because in my case I can't give the terminal arguments. However, it gives me a simple idea that isn't perfect, per se, but it's a lot better than nothing:
• Instead of putting exit in the script, just put it in on the command-line: e.g. "scriptName; exit"—I guess it's not too much typing.

---

### Post by v1ad on 2010-04-13
the program name is always the same if you named the program1 kill program1 in the code. 

if you have a terminal and screen install you won't have no issues. if i was home i would give you an example of how its set but im not :[ till then.

a small bit of typing will have your code search your porgram and kill itself.

---

### Post by kumoshk on 2010-04-13
> **v1ad said:**
> the program name is always the same if you named the program1 kill program1 in the code.
I'm not sure what you mean by naming my program. Doesn't the OS or the programmer of the program handle that, instead of me?

Gnome-terminal is the program. By the name, do you mean gnome-terminal or something else? If so, how do I handle killing the right instance?

---

### Post by d3vi1dog562 on 2010-08-03
I believe the post was referring to something like this:


```

Sudo pkill -9 ./myscript.sh

```

Use that inside the script at the end and it should terminate the program. Also note that if you use terminal to execute the program it returns to a blank terminal in gnome, however if you double click the program and click run the exit command should suffice. ( just had this issue :). )


Just seen how old last post is... Hope it helps someone tho:)

---

