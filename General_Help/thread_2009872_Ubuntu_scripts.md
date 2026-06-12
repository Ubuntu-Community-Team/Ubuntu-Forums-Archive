---
title: "Ubuntu scripts"
date: 2012-06-25
forum: General Help
---

### Post by bender1 on 2012-06-25
1.How can i make so that a application stays open even after i closed putty?
2.Can someone tell me is it possible to make a script that will run all the time and check if a program is running and if not to run it?

---

### Post by deathadder on 2012-06-25
1) You want to look at nohup and background jobs: [http://www.cyberciti.biz/tips/nohup-execute-commands-after-you-exit-from-a-shell-prompt.html](http://www.cyberciti.biz/tips/nohup-execute-commands-after-you-exit-from-a-shell-prompt.html)
2) Yes it is; how you do it depends on what application you're running. The usual method would be to create a script that uses "while true" to run "for ever" which checks for the existence of a application using "ps", or checks for a PID file or lock file.

---

### Post by bender1 on 2012-06-25
One more thing.I have a folder with a program inside but when i am trying to run it ,using ./program it says no such file or directory and  the file is there .What does it mean?

---

### Post by deathadder on 2012-06-25
Does the file have execute permission? Are you trying to run a 32bit app on a 64bit system? There's quite a bit of Google for this error: [https://www.google.co.uk/search?sugexp=chrome,mod=12&sourceid=chrome&ie=UTF-8&q=linxu+executable+no+such+file+or+directory#hl=en&pwst=1&sa=X&ei=OiXoT5D5LcjP8gOp4YCoCg&ved=0CAgQvwUoAQ&q=linux+executable+no+such+file+or+directory&spell=1&bav=on.2,or.r_gc.r_pw.r_cp.r_qf.,cf.osb&fp=21405353d8475aae&biw=1357&bih=907](https://www.google.co.uk/search?sugexp=chrome,mod=12&sourceid=chrome&ie=UTF-8&q=linxu+executable+no+such+file+or+directory#hl=en&pwst=1&sa=X&ei=OiXoT5D5LcjP8gOp4YCoCg&ved=0CAgQvwUoAQ&q=linux+executable+no+such+file+or+directory&spell=1&bav=on.2,or.r_gc.r_pw.r_cp.r_qf.,cf.osb&fp=21405353d8475aae&biw=1357&bih=907)

---

### Post by codemaniac on 2012-06-25
> **bender1 said:**
> One more thing.I have a folder with a program inside but when i am trying to run it ,using ./program it says no such file or directory and  the file is there .What does it mean?

+ what already have been suggested above .

There is a feature available on bash called "bash command completion" .

when you are trying to execute "program" from commandline ,
just after partially tying the program name , hit **tab**key .

```
./prog[TAB]
``` 

That should autocomplete to "program" or list all the file names available on the current directory starting with **prog** .

---

### Post by matt_symes on 2012-06-25
Hi
 
If you are using is the command line, might i suggest screen to keep an application running after you stop putty.
 
You can start a screen session and keep it running. 
 
When you need to close putty you can detach from the screen session first. Screen will keep running along with any applications you may have started in the screen session.
 
At a later date you can reconect to the screen session from putty. 
 
It also allows you to create multiple pseudo terminals and switch between them as well.
 
It is a versitle program.
 
Check out 
 
```
man screen
```
 
for more information.
 
Kind regards

---

