---
title: "Finding history command with the same begining"
date: 2011-04-26
forum: General Help
---

### Post by Ivangelion.tw on 2011-04-26
Hello,

I would like to set a config in .bashrc file, that would show previous command starting with the word I've already typed when I hit up arrow. 

For example, when I type "vim" in command prompt and hit the up arrow key, the command prompt will automatically circularly show all the commands I've previously typed which begins with "vim",  e.g. "vim ~/.bashrc", from the most recent to the least recent.

I've seen this in FreeBSD, but I cannot access the FreeBSD bashrc now. Doing a lot of googling still couldn't find the answer.

Any help will be greatly appreciated.

---

### Post by idoitprone on 2011-04-26
so how about

```
history | grep ^command
```

it is built in bash

but it goes from least recent up to most recent down

btw the carrot mean the beginning

---

### Post by Ivangelion.tw on 2011-04-26
Thank you idoitprone for your swift reply!

Maybe I should state more clearly my purpose: I just want the command prompt to show only the most recent command I entered with the same beginning as what I've already typed in the command prompt, when I hit the up arrow key. 

And each time I hit the up arrow, the command prompt will show another one command I entered that is less recent, until the least recent, then the most recent again.

---

### Post by idoitprone on 2011-04-26
> **Ivangelion.tw said:**
> Thank you idoitprone for your swift reply!

Maybe I should state more clearly my purpose: I just want the command prompt to show only the most recent command I entered with the same beginning as what I've already typed in the command prompt, when I hit the up arrow key. 

And each time I hit the up arrow, the command prompt will show another one command I entered that is less recent, until the least recent, then the most recent again.


this is out of me. I might try it to do it since it is pretty useful. here a link that might help point you to the right direction [http://www.linuxquestions.org/questions/linux-software-2/change-up-arrow-behavior-with-bash-history-520242/](http://www.linuxquestions.org/questions/linux-software-2/change-up-arrow-behavior-with-bash-history-520242/)

---

### Post by wojox on 2011-04-27
Try:

```
Ctrl+R
```

Type first letter.

---

### Post by papibe on 2011-04-27
Try this:
```
$ echo !command
```
Or if you know what was called before, you just can run it again:
```
$ !command
```
Regards.

---

### Post by mc4man on 2011-04-27
I use a file in home dir. named
 .inputrc
with this, uses the page up/down keys to search history based on what you have typed   in 
```
"\e[5~": history-search-backward
"\e[6~": history-search-forward

```
I guess you could adjust to arrow keys, though I find the page keys are fine

---

### Post by Ivangelion.tw on 2011-04-27
Thank you guys for all your generous helps~~!! :D

Finally I put the following 2 lines in ~/.inputrc to achieve my needs:

```

"\x1b\x5b\x41": history-search-backward
"\x1b\x5b\x42": history-search-forward

```

Yet there is one small problem in what is otherwise perfect: the cursor will not automatically jump to the end of line after hitting up/down arrow key. I must hit ctrl+e or End key to jump to the end of line. But it is fine for me now.

---

### Post by SecretCode on 2011-04-27
> **Ivangelion.tw said:**
> Yet there is one small problem in what is otherwise perfect: the cursor will not automatically jump to the end of line after hitting up/down arrow key. I must hit ctrl+e or End key to jump to the end of line. But it is fine for me now.

That's probably by design, and certainly important the way I use it: it allows you to start matching on the first few characters, and then realise you have 100 different rsync commands in the buffer: then you type a few more characters to narrow it down.

---

### Post by Telengard C64 on 2011-04-27
> **wojox said:**
> Try:

```
Ctrl+R
```

Type first letter.

^This.

[http://www.gnu.org/software/bash/manual/html_node/Commands-For-History.html#Commands-For-History](http://www.gnu.org/software/bash/manual/html_node/Commands-For-History.html#Commands-For-History)

[quote=8.4.2 Commands For Manipulating The History - Bash Reference Manual]reverse-search-history (C-r)
    Search backward starting at the current line and moving `up' through the history as necessary. This is an incremental search.[/quote]

):P

---

