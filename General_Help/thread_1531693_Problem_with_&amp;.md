---
title: "Problem with &amp;"
date: 2010-07-15
forum: General Help
---

### Post by nord_ua on 2010-07-15
I've made a simple script:

[code=nocolor]
php -r 'sleep(2); echo "Done...\n\n";' &
[/code]
It shoud go to background for 2 sec when echo "Done..." and finish.

But instead on my machine (Ubuntu 9.X & 10.04 on other) it stops (like i press Ctrl+Z). "jobs" print this: (same for other scripts):
[code=nocolor]
nord@nord-laptop:~/projects/transactions$ jobs 
[1]   Stopped                 ./symfony task:b 
[2]   Stopped                 ./symfony task:b 
[3]   Stopped                 ./symfony task:b 
[4]   Stopped                 php symfony task:b
[5]   Stopped                 ./run.sh          
[6]   Stopped                 ./run.sh          
[7]   Stopped                 ./run.sh          
[8]-  Stopped                 ./symfony         
[9]+  Stopped                 ./run.sh > /tmp/symfony.log
[/code]

Wo why & is doing in so wierd way?

---

### Post by mcduck on 2010-07-15
Well, you actually setting the command to run in the background, so that's what's happening. ;)

If the command runs in the background, it's output will also happen in the background. And as you run the command in background the script itself finishes immediately after *executing* the command instead of waiting it to actually *finish* that command..

---

### Post by nord_ua on 2010-07-15
You have explained me how it must work. I'm telling you how it happens in a wrong way on my machine: after i put "&" in the end of line task stops _LIKE IF I PRESS Ctrl+Z_ and run again only when i execute "fg". On debian machine and SuSE it works fine. 
BTW: if i run: 
sleep 2 && echo "12312312" &
It works fine. php wan't work fine.

---

### Post by mcduck on 2010-07-15
> **nord_ua said:**
> You have explained me how it must work. I'm telling you how it happens in a wrong way on my machine: after i put "&" in the end of line task stops _LIKE IF I PRESS Ctrl+Z_ and run again only when i execute "fg". On debian machine and SuSE it works fine. 
BTW: if i run: 
sleep 2 && echo "12312312" &
It works fine. php wan't work fine.

Can't say anything about Debian or Suse, but what comes to non-php command in your post that's a different thing. The command in your first post runs the whole PHP command in background, while the one in your above post only runs the echo command in the background...

---

### Post by AlphaLexman on 2010-07-15
I personally haven't tried using '&' in my scripts (still learning), but I have noticed from the CLI that '&' is more consistent with a trailing 'space' after the '&'.

---

### Post by nord_ua on 2010-07-16
> **mcduck said:**
> Can't say anything about Debian or Suse, but what comes to non-php command in your post that's a different thing. The command in your first post runs the whole PHP command in background, while the one in your above post only runs the echo command in the background...

You are wrong. sleep are else goes to bg. And any script should go to bg with "&". And php scripts goes to bg on some machines (and i know it right way) but not on my. Thanks you for explaining my  scripts, but can you give the answer: why & works in a different ways on different machines? This is the only question. Thanks.

upd: May be i miss something in your answer, just becouse English is a foreign language. If so, please rephrase your post.

---

### Post by mcduck on 2010-07-16
Yes, scripts run in background when you add a & to the end of the command you use to start the script. But the "&" only applies to the command you add it to. And the example in your later post doesn't have a script, it has two separate commands that follow each other.

You are not running a script, you are running a sleep command and after that finishes you run echo command. The "&" only applies to the echo command.

What you do in your first post is different because it only has a single command (from the shell's point of view the PHP script is just a parameter given to the php command.)

This is one command, from shell's point of view. The command contains php script, but that's something for PHP, not for the shell. Because this is just one command, you of course need just one "&" to execute it in the background.
```
php -r 'sleep(2); echo "Done...\n\n";' &
```

..and this is two separate commands following each other. The last command is sent to background because only the last command is told to do so.
```
sleep 2 && echo "12312312" &
```

---

### Post by nord_ua on 2010-07-16
Hm... I can see a point in your post, but running:
nord@nord-laptop:~$ sleep 2 && echo "12312312" &
[1] 7097
nord@nord-laptop:~$
nord@nord-laptop:~$ 12312312

script goes to bg immediatelly. And then, in 2 secs, it echoes. But this is not important. 
Even if i put php script to bash script (named run.sh), running run.sh & stops in bg. 
Once again: it doing like i run script run.sh and then press Ctrl+Z (try it on any script). And even more: when i use "bg" command it wont work.

---

