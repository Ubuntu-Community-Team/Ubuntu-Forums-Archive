---
title: "bash help"
date: 2011-09-05
forum: General Help
---

### Post by Bradburts on 2011-09-05
Hi,
Trying to decode bash files. In cron.daily I have:
[FONT=Courier New]# Email will go to the address specified in /etc/mdadm/mdadm.conf .
#
set -eu[/FONT]
[FONT=Courier New]MDADM=/sbin/mdadm
[ -x $MDADM ] || exit 0 # package may be removed but not purged[/FONT]
[FONT=Courier New]exec $MDADM --monitor --scan --oneshot
[/FONT]
[FONT=Courier New][FONT=Verdana]Which I think means launch a new shell and run the command:[/FONT][/FONT]
[FONT=Courier New]/sbin/mdadm --monitor --scan --oneshot[/FONT]
[FONT=Courier New][/FONT] 
[FONT=Courier New][FONT=Verdana]But what does:[/FONT][/FONT]
[FONT=Courier New][ -x $MDADM ] || exit 0 # package may be removed but not purged [/FONT]
[FONT=Courier New][FONT=Verdana]do?[/FONT]
[/FONT]

---

### Post by nothingspecial on 2011-09-05
[ -x means if the file exists and is executable ($MDADM)

|| means if the result of the previous command fails do the next one

So if $MDADM doesn't exist or isn't executable then exit.

---

### Post by Bradburts on 2011-09-05
Thank you very much!

---

### Post by sisco311 on 2011-09-05
I hope you don't mind if I expand upon nothingspecial's answer a bit.

[ is a built-in command, see:
```
help test
help [

```

[ EXP ] returns 0 (true) or 1 (false) depending on the evaluetion of EXP

[ -x FILE ] is true if the file is executable by you.

**command1 || command2** means: command2 is executed if and only if command1 returns a non-zero (false) exit status.

See:
```
man bash | less +/^"SHELL GRAMMAR"
```
scroll down to the *Lists* section.

**exec** replaces the shell with the given command, see:
```
help exec
```
and [http://wiki.bash-hackers.org/commands/builtin/exec](http://wiki.bash-hackers.org/commands/builtin/exec)

BTW, **set -e** means: exit immediately if a command exits with a non-zero status. I have no clue what was in the mind of the author...

The script will exit anyway if [ returns false, so why he is using || exit 0? Just to exit with 0? Then why the set -e? Arghhh...

---

### Post by nothingspecial on 2011-09-05
> **sisco311 said:**
> I hope you don't mind if I expand upon nothingspecial's answer a bit.

Well it makes a welcome change from correcting them :P


> **sisco311 said:**
>  I have no clue what was in the mind of the author...

The script will exit anyway if [ returns false, so why he is using || exit 0? Just to exit with 0? Then why the set -e? Arghhh...

At least you get to correct someone :lolflag:

---

### Post by sisco311 on 2011-09-05
> **nothingspecial said:**
> 
At least you get to correct someone :lolflag:

LOL

Unfortunately (j/k), your answer is accurate.

---

### Post by Bradburts on 2011-09-06
No he's right, clearly he needs the exit 0 as he used the ||  ](*,)
 
Seriously though, & commands not being executable aside, the script will return the result of:
[FONT=Courier New]/sbin/mdadm --monitor --scan --oneshot[/FONT]
and so may return true?

---

### Post by nothingspecial on 2011-09-06
> **Bradburts said:**
> No he's right, clearly he needs the exit 0 as he used the ||  ](*,)
 
Seriously though, & commands not being executable aside, the script will return the result of:
[FONT=Courier New]/sbin/mdadm --monitor --scan --oneshot[/FONT]
and so may return true?

Of course he's right, he's always right](*,)](*,)](*,)

I'm only usually sort of right, which means if I ever answer a thread like this you can bet your last 50p that sisco will come along later and say something like

The prefered way to do it is.....

Or doing it that way will create unnecessary processes, do it this way.....

See bash pitfalls no364 etc,etc,etc

I was expecting the usual but for once \\:D/

Seriously, you'll learn alot from sisco

Whether or not it returns true is not the issue, what he's pointing out is why set -e if your going to do || exit 0

It's the sort of thing I'd do.

---

### Post by sisco311 on 2011-09-06
Hmmm, I was thinking a little... :)

Actually, exit with 0 (true) if the command is not executable is just plain wrong.

If you don't have /sbin/mdadm, your cron log will say: everything went fine, don't worry, relax and enjoy your day. :)

I would expect something like: HEY! What's going on on your system <insert personal insult here>? You have a completely useless daily cron job <more personal insults>. :P

---

### Post by Bradburts on 2011-09-06
Yes I appreciated Sisco's help. 
I was attempting humor (O well, not a life on stage for me), thinking that adding the || makes the set -e not work(?). 
as in;
 -e   *errexit*
          Exit immediately if a simple command exits with a non-zero
          status, unless the command that fails is part of an until or
          while loop, part of an if statement, part of a && or || list,
          or if the command's return status is being inverted using !. 
 
Just tried it and the [] is not an if but as we know the || prevents the set -e.
I would have gone my whole life thinking that [] and if were the same without the post!

---

### Post by nothingspecial on 2011-09-06
[ is a test, you can use it in an if statement.

I ought shut up now. I am not posting some explanation about [ in a thread where I got something right :-$

---

### Post by CharlesA on 2011-09-06
Not to derail, but I thought [[ was superior to [ for tests?

I think I read that from [here]("http://mywiki.wooledge.org/BashPitfalls"), but I've used [[ for all my conditional tests since.

EDIT: Found [another link]("http://www.thegeekstuff.com/2010/06/bash-conditional-expression/") with some more common BASH conditional expressions.

---

### Post by nothingspecial on 2011-09-06
> **CharlesA said:**
> Not to derail, but I thought [[ was superior to [ for tests?

I think I read that from [here]("http://mywiki.wooledge.org/BashPitfalls"), but I've used [[ for all my conditional tests since.

It is, but we were talking about the script as it is.

Look here [http://mywiki.wooledge.org/BashGuide/TestsAndConditionals](http://mywiki.wooledge.org/BashGuide/TestsAndConditionals)

[[ has extra features but I suppose if [ does the job then using it is fine.

---

### Post by CharlesA on 2011-09-06
> **nothingspecial said:**
> It is, but we were talking about the script as it is.

Look here [http://mywiki.wooledge.org/BashGuide/TestsAndConditionals](http://mywiki.wooledge.org/BashGuide/TestsAndConditionals)

[[ has extra features but I suppose if [ does the job then using it is fine.

Ah, thanks!

---

### Post by sisco311 on 2011-09-06
There is nothing wrong with [, but for reasons detailed @ Greg's Wiki, in bash, as a rule of thumb, one should use [[ .. ]] to test strings or files, (( .. )) to test numbers or arithmetics and **if ..** to test commands. [ should be avoided in bash and only used in sh.

---

