---
title: "how do I use  use 'at' command"
date: 2011-04-11
forum: General Help
---

### Post by kaykav on 2011-04-11
Hi
    Before I decided to use this forum, I tried all possible ways to use the 'at' command ,with little success. I do not have an /etc/at.allow file,and I am not mentioned in /etc/at.deny.
I make an entry:
 $ at 8:04 < ~/bin/tknotepad.sh 
warning: commands will be executed using /bin/sh
job 20 at Tue Apr 12 08:04:00 2011
       when the time arrives tknotepad does not appear.
  If I just run  'tknotepad' it runs fine. It's a good script.
I make another entry:
 at 8:32
warning: commands will be executed using /bin/sh
at> echo 'hello again'> file#1
at> <EOT>
job 22 at Mon Apr 11 08:32:00 2011
        when the time arrives it works fine.

   What is it I am doing ,or not doing, for the first command?
                            Thanks....

---

### Post by KegHead on 2011-04-11
Hi!

Try:

lower case letters

sudo apt-get update

sudo apt-get upgrade

Please advise.

KegHead

---

### Post by kaykav on 2011-04-11
Hi keghead,
            I'm not sure what you mean  'lower case'. All my commands were
entered in 'lower case'. I updated and upgraded, and tried again. Did not work.  I can't seem to get this 'at' command to activate.

---

### Post by KegHead on 2011-04-11
Hi!

Are you trying to schedule something?

Try this or other Ubuntu docs!

KegHead

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by kaykav on 2011-04-11
I'm try ing to schedule an activation of a script,or a command.
  example(script)    at -f ~/bin/ups.sh  now + 3 min
   example(command)   at -f ~/bin/tknotepad now + 3 min 
   ~/bin is in my PATH.
     If I redirect the output  of 'at' to a file, it works,but to fully actuate the command (open editor tknotepad),it doesn't.

---

### Post by KegHead on 2011-04-11
Hi!

Look here:

---

### Post by KegHead on 2011-04-11
Hi!

It might be quicker to goto Ubuntu docs via google search and then type in "at" as a search parameter.

It will kick out numerous articles and examples.

Enjoy!

KegHead

---

### Post by gruebait on 2011-04-11
kaykav, you are actually making more progress than me. I have tried every combination I could with at.deny/at.allow files,(empty, edited, chowned root:daemon, none, etc). The only way I had it working was with sudo. The one common thing with all the failures was the warning about running with /bin/sh. 
(I was running Unix from 1984 'til the late 90's, when my employer switched everything to Windoz. I used to run Red Hat at home, and I have never had a difficulty with at.)

I am running a new install (not an upgrade) of 10.10, and /etc/at.deny had 10-20 entries, including 'bin' and 'daemon' when I started. Cron jobs work fine. With no .allow/.deny, at works fine (using sudo). 

Google suggests that this is an awfully common difficulty.

---

### Post by KegHead on 2011-04-11
Hi!

Have you folks reviewed the Ubuntu docs?

That's how I learned!

KegHead

---

### Post by yetiman64 on 2011-04-11
> **kaykav said:**
> I'm try ing to schedule an activation of a script,or a command.
  example(script)    at -f ~/bin/ups.sh  now + 3 min
   example(command)   at -f ~/bin/tknotepad now + 3 min 
   ~/bin is in my PATH.
     If I redirect the output  of 'at' to a file, it works,but to fully actuate the command (open editor tknotepad),it doesn't.

I suspect it may be a syntax problem you are experiencing,

try the command ```
at -f ~/bin/<yourscriptname> now + 3 minutes
```from ```
man at
```>  ...You can  also  give times like now + count time-units, where the time-units
       can be **minutes**, hours, days, or weeks... I just activated a script called tknotepad in ~/bin here using the above command to give a 3 minute delay before getting an effect from the script.

---

### Post by kaykav on 2011-04-11
OK guys
            I'll play around with this some more. Either way I'll get back with  (hopefully) good results.    Thanks

---

### Post by KegHead on 2011-04-12
Hi!

Keep us updated and please close your thread if you solve!

KegHead

---

