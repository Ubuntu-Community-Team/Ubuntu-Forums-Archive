---
title: "New to Linux, Questions regarding Terminal and Commands"
date: 2011-07-21
forum: General Help
---

### Post by Lestathim on 2011-07-21
I am new to Linux and have already been helped tremendously by the forums.  I don't exactly know how to ask this question but I'm going to do the best that I can.  To better understand Linux I am read a book called "Linux for Dummies".  The book is very informative has has provided a large bit of information thus far.  With that said I have reached a part that I can't seem to get past, on the technical end that is at least.  If you so happen to have the book or want to torrent it quickly the part I'm getting stuck on is on page 112.  Anyway her is where I run into some problems.  It begins by saying access the Terminal program which I have figured out how to do.  After saying that it says for example if I typed /etc and typed ls I should see what is shown on this page but I do not.  Basically what he has open is a window that says rich@testbox: /etc and he typed in ls somewhere and there are all these files with different names and different colors signifying their specific functions and what they are used for.  What I'm asking is basically how do I view these files or how do I enter the command to view these files in this folder?  It says if I type ls -a that I should be able to view hidden ones as well but I can't seem to figure that out either.  Basically I am just trying to figure out what to do here next and whatever help anyone would like to give is greatly appreciated!  Thanks!

---

### Post by howefield on 2011-07-21
Try typing 

```
cd /etc
``` 

then ls -a

---

### Post by Lestathim on 2011-07-21
Wow that worked perfectly thanks a lot!  Has there been changes to the terminal that have made just typing the /etc invalid?  I know the book is a few years old so I'm basically just wondering out of curiosity of commands change or just how that works exactly.

---

### Post by bobnutfield on 2011-07-21
You could also type in the terminal without changing to the /etc directory:

> ls -la /etc

If you haven't already noticed, the "ls" command is very similar to the "dir" command on the Windows command prompt.  It simply lists the contents of a directory.

---

### Post by haqking on 2011-07-21
not directly relevant to your question.

However as you are learning and new to terminal i feel it would help you to know 2 very important and usefull commands.

man = manual pages for all commands so you know how to use them and what parameteres they accept.

example:

man copy

apropos = helps you find a command when you dont know what command or what it is called but you know what you want to do.

example:

apropos delete

remembering both of these when you are at a console should help you achieve or carry out any task you need to.

good luck

---

### Post by WorMzy on 2011-07-21
> **Lestathim said:**
> Wow that worked perfectly thanks a lot!  Has there been changes to the terminal that have made just typing the /etc invalid?  I know the book is a few years old so I'm basically just wondering out of curiosity of commands change or just how that works exactly.

He could be using a different shell. zsh, with the autocd option set, allows you to omit the cd, so "/etc" will work the same way as "cd /etc". By default, Ubuntu uses the bash shell.

---

### Post by TeoBigusGeekus on 2011-07-21
Try [this]("http://sourceforge.net/projects/linuxcommand/files/TLCL/09.12/TLCL-09.12.pdf/download") for a starter's book.

---

### Post by sisco311 on 2011-07-21
> **WorMzy said:**
> He could be using a different shell. zsh, with the autocd option set, allows you to omit the cd, so "/etc" will work the same way as "cd /etc". By default, Ubuntu uses the bash shell.

bash 4 also supports the autocd option.

---

### Post by Lestathim on 2011-07-21
Thanks so so much for the help everyone!  This is the first time I'm engaging in entering any type of code so all info you all have given me GREATLY helps!  Also for the Starter Book that was recommended above, I have already downloaded it and have dug in.  It seems like an excellent starter guide!  Thanks so much everyone!

---

