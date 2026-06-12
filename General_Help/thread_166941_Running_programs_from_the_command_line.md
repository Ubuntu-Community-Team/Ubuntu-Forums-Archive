---
title: "Running programs from the command line"
date: 2006-04-27
forum: General Help
---

### Post by WebDrake on 2006-04-27
Not really a specifically Ubuntu question, but here goes...

... suppose I'm running a program from the command line.  Now, using Ctrl-z I can suspend it; typing bg will send it into the background.  If the program prints output, it will continue to print in the relevant shell.

Is there any way to make the program print its output instead to a file?  If I was running the file from scratch, obviously I could use ./command > outputfile, but suppose I only want it to print to file after I send it to the background?

---

### Post by cgjones on 2006-04-27
I'm not quite sure I understand what you are asking, but you could try this:
```

*command* > *filename* &

```
This will start the program in the background, so you won't need to suspend it first.

---

### Post by WebDrake on 2006-04-27
[QUOTE=cgjones]I'm not quite sure I understand what you are asking, but you could try this:
```

*command* > *filename* &

```
This will start the program in the background, so you won't need to suspend it first.[/QUOTE]
Thanks for the suggestion, but no, that won't work.

It's vital that initially the program print to the shell, because it asks for various bits of input to be typed in.  Then I suspend and send it to the background.  It will continue to print info to the screen (it's written in C and uses printf).  I want to be able to send that info to a file so that I can exit that shell, but still be able to check the progress of the program at a later stage.

I realise this is an unusual thing to ask (especially on this forum:rolleyes:) so no worries if no one knows how to do this.

---

### Post by echo $USER on 2006-04-27
[QUOTE=WebDrake]Thanks for the suggestion, but no, that won't work.

It's vital that initially the program print to the shell, because it asks for various bits of input to be typed in.  Then I suspend and send it to the background.  It will continue to print info to the screen (it's written in C and uses printf).  I want to be able to send that info to a file so that I can exit that shell, but still be able to check the progress of the program at a later stage.

I realise this is an unusual thing to ask (especially on this forum:rolleyes:) so no worries if no one knows how to do this.[/QUOTE]

You need to check out the tee command.
> man tee
It allows you to simotanously display standard output to the terminal and also redirect it to a file.  I dont know how to use it personally, but it sounds like what you are after.

---

### Post by PriceChild on 2006-04-27
from flashtux.org, it tells you to use use ```
eciadsl-start | tee log.txt
``` to start the program... I think you should just be able to replace eciadsl-start with your program name, and log.txt with whatever you want to save it to.

Try it out, can't harm anything :)

---

### Post by WebDrake on 2006-04-27
echo, Pricechild---thanks very much!  That works wonderfully.

I had to make one small modification to the  program---I needed to insert fflush(stdout) commands in some places to ensure that some stuff was printed "in real time".  tee obviously doesn't flush the output buffer when a scanf() query is made...

---

