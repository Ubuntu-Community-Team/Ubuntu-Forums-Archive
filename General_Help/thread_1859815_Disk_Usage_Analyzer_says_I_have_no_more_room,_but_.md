---
title: "Disk Usage Analyzer says I have no more room, but I have plenty..."
date: 2011-10-14
forum: General Help
---

### Post by carrie.kandira on 2011-10-14
So the disk usage analyzer keeps telling me total file system capacity is at 100% I don't have any more room, but I do. And I've seen suggestions about putting the livecd back in and making the repositories bigger or something like that, but I did it off a USB and it was an 8. something version. It let me upgrade online to ubuntu 10.04 so I don't have a disc for ubuntu 10.04. I also have no other OS on my computer except for ubuntu.


@ CATKILLER Oh so it's suppose to say 100%. I get it, but just in case....
FOR OLLE WIKLUND

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             36843208   3998756  30972884  12% /
none                    508144       316    507828   1% /dev
none                    512384       188    512196   1% /dev/shm
none                    512384       284    512100   1% /var/run
none                    512384         0    512384   0% /var/lock
none                    512384         0    512384   0% /lib/init/rw
/dev/sdb1               250496     69808    180688  28% /media/3B69-1AFD
carriekanidra@carriekanidra-desktop:~$ 


FOR WORMZY it tells me it's an invalid optioN

---

### Post by WasMeHere on 2011-10-14
Hi carrie.kandira,

I have 10.04 too. If you post the output of some commands, I may be able to help you. Let us start with a simple one from a terminal window
```
df
```

Have fun finding out about Ubuntu :-)
Olle

---

### Post by WorMzy on 2011-10-14
As well as the above command, could you please post the output if this one:
```
sudo du -hx --max-depth=1 / | sort -h
```

Give it time to finish executing.

---

### Post by CatKiller on 2011-10-14
You're misinterpreting what baobab is telling you. It shows proportions of total usage for different parts of the filesystem. It necessarily always adds up to 100%.

---

### Post by WasMeHere on 2011-10-15
> **carrie.kandira said:**
> ...
@ CATKILLER Oh so it's suppose to say 100%. I get it, but just in case....
FOR OLLE WIKLUND

```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             36843208   3998756  30972884  12% /
none                    508144       316    507828   1% /dev
none                    512384       188    512196   1% /dev/shm
none                    512384       284    512100   1% /var/run
none                    512384         0    512384   0% /var/lock
none                    512384         0    512384   0% /lib/init/rw
/dev/sdb1               250496     69808    180688  28% /media/3B69-1AFD
```
carriekanidra@carriekanidra-desktop:~$ 

FOR WORMZY it tells me it's an invalid optioN
***df*** shows that you have plenty of space left. On the system partition '/' you have used only 12% and on the '/media/3B69-1AFD' partition you have used only 28% of the available space (I guess a 256 MB flash card or stick).

I think the problem with WorMzy's command is that sort has no -h option. Try this one to discover which directories fill the most space.
```
sudo du -x --max-depth=1 / | sort -n
```

Please add answers to our questions as a ***reply*** (new reply) or (quote)! Otherwise we may not discover that you have written.

When you feel that your problem is solved, please mark this thread SOLVED and enjoy life :-)
Olle

---

### Post by dcstar on 2011-10-15
> **carrie.kandira said:**
> So the disk usage analyzer keeps telling me total file system capacity is at 100% I don't have any more room, but I do.
........

"Disk analyzer" is run with user rights only and will only show what that **user** has accessible, if it is run like this it shows the whole system:

```
gksudo baobab
```

---

### Post by WorMzy on 2011-10-15
> **Olle Wiklund said:**
> I think the problem with WorMzy's command is that sort has no -h option.
Yeah, that was my mistake; -h should sort by human readable numbers, but it only made its way into the Ubuntu version of sort in 10.10. The version after the one OP is using. Oops.

---

### Post by carrie.kandira on 2011-10-15
Ah. lol. Sorry. Um, how exactly do I mark it as solved? I don't see that as an option.

---

### Post by carrie.kandira on 2011-10-15
Never mind, found it. lol. Thank you.

---

