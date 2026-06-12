---
title: "Gnome Terminal's stupid &quot;clear&quot; command"
date: 2009-07-14
forum: General Help
---

### Post by Intrepid Ibex on 2009-07-14
Gnome Terminal's "clear" command acts really stupidly for my requirements as it doesn't actually CLEAR the terminal "log".

So can I change Gnome Terminal to clear the terminal "log" instead of just jumping to a new line? Or is there some terminal that has all Gnome Terminal's functions but still does the clearing the way I want?

I attached a screenie of what Gnome Terminal's clear command does to clarify.
[ATTACH]121080[/ATTACH]

---

### Post by swisstone198 on 2009-07-14
what is the output of

echo $TERM

---

### Post by Intrepid Ibex on 2009-07-14
uh, well:
```
[det@myhost ~]$ echo $TERM
xterm
```

---

### Post by lukeiamyourfather on 2009-07-14
The clear command is simply a visual thing, to remove whatever is on the screen above the clear command, but not modify the command history. Why would you want to remove the history of the terminal? Its useful information.

---

### Post by swisstone198 on 2009-07-14
Oh, I didn't understand what your problem was, I thought it wasn't clearing your screen.

---

### Post by DirtDawg on 2009-07-14
If you want to delete the the command history from your terminal, delete the .bash_history file from your home folder. 

If you want to remove one or a few lines from your history, use the 'history' command in your terminal, take note of the number of the command you would like to delete, and use 'history -d <number>' to delete that line. Or simply edit the aforementioned .bash_history file.

---

### Post by .nedberg on 2009-07-14
```

history -c

```
will clear your history. I am sure xterm can be set to not log anything if that is what you want.

---

### Post by Intrepid Ibex on 2009-07-14
> **lukeiamyourfather said:**
> The clear command is simply a visual thing, to remove whatever is on the screen above the clear command, but not modify the command history. Why would you want to remove the history of the terminal? Its useful information.
Dudes, you are getting me wrong.

What I want the clear command to do is exactly what you said: "The clear command is simply a visual thing, to remove whatever is on the screen above the clear command" - that is not what Gnome Terminal does.

I don't want to delete any command histories, I just want to clear the texts above so that I don't need to open a whole new tab in order to do so.

---

### Post by mcduck on 2009-07-14
how about a simple Ctrl-L? Although the "clear" should work just as fine regardless of what terminal you are using (as the commands are executed by the shell, not the terminal).

edit: If you mean that you want to clear the terminal's output so that even if you scroll up there's nothing visible, then that's not what "clear" does. For that purpose use "reset".

---

### Post by Intrepid Ibex on 2009-07-14
Still, "Ctrl + L" (clear) doesn't **clear** the texts above, it just jumps to a new line.


**edit:**
> edit: If you mean that you want to clear the terminal's output so that even if you scroll up there's nothing visible, then that's not what "clear" does. For that purpose use "reset".**This** is what I was looking for, thanks! :)

---

### Post by ddrichardson on 2009-07-14
That's a little odd. Does it do it from other profiles?

Clear actually checks the $TERM variable to see what its run on then checks terminfo for how to clear the screen, which either clears the screen, clears the line or does both.

I'm not sure why this isn't doing what it should but would need to have a good look in man to find out.

---

### Post by doas777 on 2009-07-14
I think the op's problem is that if you run some commands and then run clear, you can still scroll the window back up (buffer) to see the previous commands. clear just scrolls the window down so that the current prompt is at the top of the screen. it doesn't really clear the window, just scrolls it down.

---

### Post by ddrichardson on 2009-07-14
/etc/terminfo should be empty other than a README - is it?

---

### Post by ddrichardson on 2009-07-14
> **doas777 said:**
> I think the op's problem is that if you run some commands and then run clear, you can still scroll the window back up (buffer) to see the previous commands. clear just scrolls the window down so that the current prompt is at the top of the screen. it doesn't really clear the window, just scrolls it down.
Is it?  I can't really tell from the screenshot.

---

### Post by mcduck on 2009-07-14
> **ddrichardson said:**
> Is it?  I can't really tell from the screenshot.

If you look at the scrollbar of the terminal window you'll notice that the OP has scrolled up. Which is what made me think that he's talking about the output buffer and not actually that "clear" wouldn't empty the terminal window like it should..

---

### Post by Intrepid Ibex on 2009-07-14
> **ddrichardson said:**
> Is it?  I can't really tell from the screenshot.
Yeah, sorry. Anyways this is solved already..

---

### Post by doas777 on 2009-07-14
> **mcduck said:**
> If you look at the scrollbar of the terminal window you'll notice that the OP has scrolled up. Which is what made me think that he's talking about the output buffer and not actually that "clear" wouldn't empty the terminal window like it should..

ahh gotcha. mea culpa

---

