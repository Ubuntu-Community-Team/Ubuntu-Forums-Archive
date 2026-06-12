---
title: "Too many password notifications"
date: 2010-01-08
forum: General Help
---

### Post by varunmagical on 2010-01-08
[SIZE="6"]How to stop Ubuntu from asking root password??[/SIZE]
Hello,
I am using ubuntu karmic & It is asking me for root password too many times.
I have been ubuntu user for 2 years now.
In earlier versions of ubuntu, there was an option "remember password" when I mounted any drive. Now I have to provide password again & again.
I dont feel its safe to type my password hundreds of times in one session when my friends are around.
And it is very annoying to type password for doing small changes.
Thank you.

---

### Post by wojox on 2010-01-08
[http://www.addictivetips.com/ubuntu-linux-tips/avoid-password-prompt-when-executing-the-sudo-command/](http://www.addictivetips.com/ubuntu-linux-tips/avoid-password-prompt-when-executing-the-sudo-command/)

---

### Post by mc4man on 2010-01-08
As far as the need for the admin. user to authenticate mounting other internal drives partitions I'm quite surprised that it hasn't yet been 'fixed' in karmic.
(in a bit of irony the bug report on that was marked 'fix released', but the fix was to apply only in lucid.

The cleanest method is[ here]("http://ubuntuforums.org/showthread.php?p=8542850#post8542850"), based on the lucid commit

(I see no need to force people to auto mount other partitions at boot

As far as some of the other times, they can be adjusted though if done improperly or without prudence will lead to unexpected results, best left alone atm.

---

### Post by HiImTye on 2010-01-08
open a terminal and type
```
export EDITOR=nano && sudo -E visudo
```add to the end of the file
```
Defaults:<user>  timestamp_timeout=-1
```
substitute <user> with your username

while you're at it find the line that starts with defaults near the top of the file and change it to read
```
Defaults        env_reset,insults
```press ctrl+O then delete the '.tmp' and hit enter to save
press ctrl+X to exit

much more secure than enabling free access to admin tasks, although you will still have free access to admin tasks once you enter your password once

---

### Post by varunmagical on 2010-01-08
> **wojox said:**
> [http://www.addictivetips.com/ubuntu-linux-tips/avoid-password-prompt-when-executing-the-sudo-command/](http://www.addictivetips.com/ubuntu-linux-tips/avoid-password-prompt-when-executing-the-sudo-command/)

Thank you for your reply but this guide helps only when I am doing command line stuff.

---

### Post by varunmagical on 2010-01-08
Thank you for your reply to all you guys but this only helps only when I am doing command line stuff.
In nautilus, its asking me for password again.
Is there any way to login as a root like centos?

---

### Post by Project PWNED on 2010-01-08
Well if its just mounting drives, couldn't the poster just make an entry in /etc/fstab?

---

### Post by varunmagical on 2010-01-08
I know it is not a good idea to login as a root but it will solve all my troubles. Nobody touches my computer other than myself.

---

### Post by varunmagical on 2010-01-08
> **Project PWNED said:**
> Well if its just mounting drives, couldn't the poster just make an entry in /etc/fstab?

No. It's not just about mounting drives. I was just using an example.

---

### Post by HiImTye on 2010-01-08
> **Project PWNED said:**
> Well if its just mounting drives, couldn't the poster just make an entry in /etc/fstab?
good question, skimmed over that part

---

### Post by HiImTye on 2010-01-08
> **varunmagical said:**
> I know it is not a good idea to login as a root but it will solve all my troubles. Nobody touches my computer other than myself.
it's not just about physical access, it's about programmable access as well which is why admin tasks have the authentication level. the sudo command gives explicit access to ring 1 and all files while all other processes have only access to ring 4 and files with permissions explicitly set

---

