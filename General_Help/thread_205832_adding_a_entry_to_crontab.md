---
title: "adding a entry to crontab"
date: 2006-06-29
forum: General Help
---

### Post by lex1 on 2006-06-29
how do i add this entry to crontab?



*/44   *     *     *     *     suck news.aioe.org -A -bp -hl localhost -c -i 200 -M -n -Q


lex1

---

### Post by scxtt on 2006-06-29
"crontab -e" (personal)  from a terminal or add it to /etc/crontab (system wide) - at least for the default anacron ...

---

### Post by lex1 on 2006-06-29
This is what /etc/crontab looks like where do i add the line from my first post.?

lex1

                                                                                         

# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file.
# This file also has a username field, that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user  command
17 *    * * *   root    run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.daily
47 6    * * 7   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.weekly
52 6    1 * *   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.monthly
#

---

### Post by xtacocorex on 2006-06-29
I wouldn't add it to the system cron unless it's really important.

To allow your user to run cron jobs, you need to create a file in /etc/ called cron.allow and in it type the following (as root):
```

root
<username>

```

From there, you can as your user, type 
```

export EDITOR=gedit
contab -e
```
This will change your editor to gedit so you won't have to mess with vi and then open up gedit to modify your crontab.

Then just paste the line from the OP and save/exit.

---

### Post by lex1 on 2006-06-29
Thanks for post.
#
think I follow but only have nano editior so put that instead of gedit
and the file cron.allow.

root

username but like so <lex1>?

lex1

---

### Post by xtacocorex on 2006-06-29
Nano is fine.

Replace <username> with lex1, there should be no brakets around it. I just do that to denote something to wholly replace. Sorry for not clarifying that.

So your cron.allow file will have the following:
root
lex1

---

### Post by lex1 on 2006-06-29
sorry a little braindead today

so have a file called cron.allow

with
root
lex1

where do i type export EDITOR=nano
crontab -e ?

on command line

save and exit from where?

lex1

---

### Post by xtacocorex on 2006-06-29
>>where do i type export EDITOR=nano
>>crontab -e ?

Yes, from the command line, once you add the line to the file, you'll need to save it in nano (don't remember the command since I don't use it)

To check if it was correctly saved, you can type 
```
crontab -l
``` from the command line to list the contents of the file.

---

### Post by lex1 on 2006-06-29
this look ok?

lex1@xstation:~$ export EDITOR=nano
lex1@xstation:~$ crontab -e
no crontab for lex1 - using an empty one
crontab: installing new crontab
lex1@xstation:~$ crontab -l
# m h  dom mon dow   command
*/44 * * * * suck news.aioe.org -A -bp -hl localhost -c -i 200 -M -n -Q
lex1@xstation:~$ 

lex1

---

### Post by xtacocorex on 2006-06-29
It looks good to me. 

Are you trying to have it open a GUI program? I've never seen the suck command before.

I guess you'll know if it works or not when it's 44 minutes into the hour.

---

### Post by lex1 on 2006-06-29
sent a pm

lex1

ps what i realy need is a good news news reader client very light if possible

---

