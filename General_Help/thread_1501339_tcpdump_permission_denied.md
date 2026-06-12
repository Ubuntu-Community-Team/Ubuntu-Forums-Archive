---
title: "tcpdump permission denied"
date: 2010-06-04
forum: General Help
---

### Post by el_fiqs on 2010-06-04
[FONT=Courier New][SIZE=2]when i type this command : "tcpdump -r 12072006.tcpdump.log" 

this output appear : "tcpdump: 12072006.tcpdump.log: Permission denied"

i access the 12072006.tcpdump.log file from another hard disk which installed with windows os.

please help..[/SIZE][/FONT]

---

### Post by splater on 2010-06-04
I think you need to have root privileges ...

so: sudo tcpdump ...

++

---

### Post by el_fiqs on 2010-06-04
[FONT=Comic Sans MS][FONT=Courier New][SIZE=2]i'm in root user, but still got the permission denied.
please help[/SIZE][/FONT]
[/FONT]

---

### Post by samemiki on 2010-06-18
Do you have a solution for this ? Can you please post the solution ? 
I have exactly the same problem, doing "sudo tcpdump -r fileName" gives me "Permission denied" error, the file is in an external harddisk.

Thanks.

---

### Post by redyaky on 2010-08-05
I happened to find a fix here:

[http://thecomputergroup.net/how-to-fix-tcpdump-in-ubuntu-904-server](http://thecomputergroup.net/how-to-fix-tcpdump-in-ubuntu-904-server)

I'm not sure about the security risks of doing this however.

---

### Post by noahspurrier on 2010-11-02
This is probably caused by [AppArmor]("https://apparmor.wiki.kernel.org/index.php/Main_Page"). You need to switch from 'enforcement' mode to 'complain' mode on 'tcpdump'. Run the following command as root:

[INDENT]```
aa-complain /usr/sbin/tcpdump
```[/INDENT]

You can check by running the following command as root:

[INDENT]```
grep tcpdump /sys/kernel/security/apparmor/profiles
```[/INDENT]

You should see **(enforce)** or **(complain)**. You want it to say **(complain)**.

---

### Post by gsgleason on 2010-11-02
show the output of:
ls -l 12072006.tcpdump.log

---

### Post by jbowen7 on 2010-12-17
el_fiqs,

Was this problem solved for you? I too am experiencing this problem as root user. 

```
tcpdump -i eth0 -Xnnvv -w tcpdump.file port 53
```

produces:

tcpdump: tcpdump.file: Permission denied

I'm in /etc when it fails.

the command works in /root though.

I'm sure noahspurrier is right, it's probably an apparmor issue.

But did you solve it, and what did you do to solve it?

---

### Post by peely on 2011-02-28
noahspurrier is correct, "aa-complain /usr/sbin/tcpdump" definitely fixed the issue for me, thanks.

You still ened root priviledges though, but this command is useful if you need to write pcaps to a folder which is not owned by root e.g. when it needs to be accessible to other users and groups.

---

