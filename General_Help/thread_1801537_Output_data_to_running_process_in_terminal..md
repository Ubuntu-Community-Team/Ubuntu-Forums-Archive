---
title: "Output data to running process in terminal."
date: 2011-07-10
forum: General Help
---

### Post by Erik1984 on 2011-07-10
This title might sound a bit vague but don't know how to describe it otherwise.

There is text based game in the Ubuntu repos called** gomoku** (just 5 in a row) it comes with the package **bsdgames**. The manual page ([http://manpages.ubuntu.com/manpages/hardy/man6/gomoku.6.html](http://manpages.ubuntu.com/manpages/hardy/man6/gomoku.6.html)) lists an option (-b) to run it in the background. I want to try that and if I know how it works create a simple graphical front-end. When I start the program with:

```
gomoku -b
```it starts and remains active, the terminal does not return to prompt which is OK as the command is not finished. The manual says the program reads from stdin, and this might sound stupid but how to get anything there?

I've tried to pipe an echo command to gomoku which works but ends the program after is receives input.

```
echo "black" | gomoku -b
```just finishes. After that when you type another command like:

```
echo "justsometext" | gomoku -b
``` gomoku tells it expects either black or white as input. So it forgot the previous "black" because it is a new instance.

So my question: How do I pass text to an already running gomoku?

---

### Post by Erik1984 on 2011-07-11
I noticed now that when I execute ```
gomoku -b
```It picks up the commands when typed in the same terminal (it quits when invalid input is given so interaction takes place in the background) but I can't see the output nowhere, only when giving the wrong opening command. Any ideas on this?

Is General Help the proper place for this kind of question anyway?

---

### Post by OldBoy44 on 2011-07-11
> **Euroman said:**
> Is General Help the proper place for this kind of question anyway?

Gaming and Leisure maybe ?  :)

---

