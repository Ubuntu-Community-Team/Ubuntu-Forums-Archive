---
title: "iptables remove record by hostname"
date: 2011-04-20
forum: General Help
---

### Post by ItsAsh on 2011-04-20
Hey Guys,

I am trying to delete a host rule from my iptables to allow access to the server (i accidentally got banned).

I use sudo iptables -L. However this exceeds the putty character limit, plus if i have say over 100, 000 records? and this rule is like 99, 500. Do i need to count all those rows?

Basically wondering if i can delte by hostname, for instance

sudo iptables -D -S my.hostname.com.or.ip.here

Cheers :)

---

### Post by Lars Noodén on 2011-04-20
How about piping the output through **less** or **grep**? 

```
sudo iptables -L | less
```

You can search forward and backward through  **less** output with regular expressions, accessible with a slash **/**

---

### Post by ItsAsh on 2011-04-20
Hi there, I'm rather new to using linux and out of curiosity wondered if you'd mind explaining what the piping does/allows?

Perhaps if it's not to much trouble explain what the command is doing.

Thanks,
Ash.

---

### Post by Lars Noodén on 2011-04-20
Piping takes output from one program (iptables) and provides it as input for another program (less).  

```

iptables -L | less

```

**less** is a pager that queues up text and allows you to roll forward or backwards through it a page or a line at a time.  Or you can search forwards or backwards with regular expressions using / or ? respectively.

piping is one of the reasons why the shell is so powerful.

---

### Post by ItsAsh on 2011-04-20
Thank you for your information.

Finally, how could i correctly construct a command to remove a row from iptables using the specification? When the line number is not known.

Thanks,
Ash

---

### Post by SeijiSensei on 2011-04-20
If you want to remove a line with the text "badhost.example.com" use this:

```
grep -v 'badhost.example.com' oldfile > newfile
```

grep reads each line of oldfile and outputs any line that doesn't match  (the -v switch) 'badhost.example.com'.  It then directs the output to newfile.  If you omit the "> newfile" part of the command it will display the text on the screen, or you can use "| less" as described above.

In principle the regular expression badhost.example.com would match any string like badhostXexampleYcom, since the dot is a placeholder that represents any character.  You can force it to recognize the dot as a literal character rather than a placeholder by using 'badhost\.example\.com' instead.  In practice, though, it's likely only to match the actual host name.

If you want to see what lines will be removed in advance, first run

```
grep 'badhost.example.com' oldfile
```

which will print all matching lines to the terminal.

---

### Post by ItsAsh on 2011-04-20
Thanks for your help, I understand regular expressions (although it was nice for your clear explanation nonetheless, appreciated).

As for the the command above, if I executed...

```
sudo iptables -D 'my.hostname.com'
```

Or, does the -D require a regex value? Also do I need to pipe grep to remove the row containing 'my.hostname.com'.

Basically I have accidentally been banned from the server for several days and i've had to ssh through a server at work, now i'm trying to manually remove the row in the iptables to unban my host from the blocked list.

And I was looking for the best/fastest way to achieve this.

Thanks,
Ash.

---

### Post by SeijiSensei on 2011-04-20
I was assuming the blocks were all stored in a file, so that you just needed to delete the line that includes your host name, then restart iptables.  

If you want to find the line in the current ruleset that includes your host name do:

```
sudo iptables -L -v --line-numbers | grep badhost.example.com
```

to find the appropriate line numbers, then

```
sudo iptables -D INPUT|OUTPUT|FORWARD [number]
```

to remove line [number] from the appropriate chain.

---

### Post by ItsAsh on 2011-04-20
Thank you for your help, i'm currently about to execute the command.

I appreciate your help :) Thanks.

---

### Post by ItsAsh on 2011-04-20
What if the response is...

```
iptables: Index of deletion too big.
```

---

### Post by SeijiSensei on 2011-04-20
Are you sure you specified the right chain?  Each chain (INPUT, FORWARD, OUTPUT) has its own set of line numbers starting from one.  So if your hostname is on line 435 of the INPUT chain you'd need to use

```
sudo iptables -D INPUT 435
```

If you can't figure this out, show us the results of 

```
sudo iptables -L -v --line-numbers | grep badhost.example.com
```

---

### Post by Lars Noodén on 2011-04-21
Another way to do it would be to use **iptables-save** and **iptables-restore**

```


iptables-save >/tmp/somefile
nano /tmp/somefile
iptables-restore < /tmp/somefile
```

---

### Post by ItsAsh on 2011-04-21
I very much, appreciate your help. I executed..

```
ameadows@kiwi:~$ sudo iptables -L -v --line-numbers | grep my.badhost.com
98       2   104 DROP       all  --  !lo    any     my.badhost.com     anywhere    
98       0     0 DROP       all  --  any    !lo     anywhere             my.badhost.com
ameadows@kiwi:~$
```

I then execute...

```
ameadows@kiwi:~$ sudo iptables -D INPUT 98
iptables: Index of deletion too big.
ameadows@kiwi:~$
```

---

### Post by ItsAsh on 2011-04-21
> **Lars Noodén said:**
> Another way to do it would be to use **iptables-save** and **iptables-restore**

```


iptables-save >/tmp/somefile
nano /tmp/somefile
iptables-restore < /tmp/somefile
```


I tried this method, it worked perfectly. So thanks for your help, i did need the IP address rather than the hostname, then delete all occurrences, nonetheless it's fixed. Thank-You.

However it would be really interesting from a learning perspective to my previous post if I have done something wrong?

---

### Post by SeijiSensei on 2011-04-22
Run "iptables -L -v" and see which chain has that rule. It will appear at the top of each list of rules. Maybe it's in FORWARD rather than INPUT.  

You can test each chain separately with "iptables -L CHAIN -v".

It's also possible that there are custom chains defined.  On RedHat, for instance, the INPUT chain just jumps to a custom chain called "RH-Firewall-1-INPUT". "iptables -L -v" will list all chains.

---

### Post by ItsAsh on 2011-04-28
> **SeijiSensei said:**
> Run "iptables -L -v" and see which chain has that rule. It will appear at the top of each list of rules. Maybe it's in FORWARD rather than INPUT.  

You can test each chain separately with "iptables -L CHAIN -v".

It's also possible that there are custom chains defined.  On RedHat, for instance, the INPUT chain just jumps to a custom chain called "RH-Firewall-1-INPUT". "iptables -L -v" will list all chains.

Ohh, that's where I think i've been going wrong. Thank you very much for your help. it's very appreciated!

---

