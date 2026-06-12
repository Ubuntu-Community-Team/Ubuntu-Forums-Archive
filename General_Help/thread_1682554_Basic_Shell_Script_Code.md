---
title: "Basic Shell Script Code"
date: 2011-02-06
forum: General Help
---

### Post by acwest on 2011-02-06
Hi, im new to linux and im am trying to output a list of running processes via a shell script. At the moment i got this which outputs the processes to a text file called out.

echo $(ps aux) >>out
 
The problem is though, the processes are all just one big block of text which makes it hard to read.

Does anyone know how to sort the output to a text file so that it prints  to the text file at 1 proccess per line? I know its probably simple but  im very new to linux.

Thanks.

---

### Post by hakermania on 2011-02-06
```
ps aux > out
```

---

### Post by acwest on 2011-02-06
USER PID %CPU %MEM VSZ RSS TTY STAT START TIME COMMAND root 1 0.0 0.3 2868 1596 ? Ss 10:42 0:01 /sbin/init root 2 0.0 0.0 0 0 ? S 10:42 0:00 [kthreadd] root 3 0.0 0.0 0 0 ? S 10:42 0:00 [ksoftirqd/0] root 4 0.0 0.0 0 0 ? S 10:42 0:00 [migration/0] root 5 0.0 0.0 0 0 ? S 10:42 0:00 [watchdog/0] root 6 0.0 0.0 0 0 ? S 10:42 0:00 [events/0] root 7 0.0 0.0 0 0 ? S 10:42 0:00 [cpuset] root 8 0.0 0.0 0 0 ? S 10:42 0:00 [khelper] root 9 0.0 0.0 0 0 ? S 10:42 0:00 [netns] root 10 0.0 0.0 0 0 ? S 10:42 0:00 [async/mgr] root 11 0.0 0.0 0 0 ? S 10:42 0:00 [pm] root 12 0.0 0.0 0 0 ? S 10:42 0:00 [sync_supers] root 13 0.0 0.0 0 0 ? S 10:42 0:00 [bdi-default] root 14 0.0 0.0 0 0 ? S 10:42 0:00 [kintegrityd/0] root 15 0.0 0.0 0 0 ? R 10:42 0:00 [kblockd/0] root 16 0.0 0.0 0 0 ? S 10:42 0:00 [kacpid] root 17 0.0 0.0 0 0 ? S 10:42 0:00 [kacpi_notify]........

This is what it prints out at the moment. How do i sort it line by line so its like: ? or is it not possible?

USER PID %CPU %MEM VSZ RSS TTY STAT START TIME COMMAND 
root 1 0.0 0.3 2868 1596 ? Ss 10:42 0:01 /sbin/init 
root 2 0.0 0.0 0 0 ? S 10:42 0:00 [kthreadd] 
root 3 0.0 0.0 0 0 ? S 10:42 0:00 [ksoftirqd/0] 
root 4 0.0 0.0 0 0 ? S 10:42 0:00 [migration/0] 
root 5 0.0 0.0 0 0 ? S 10:42 0:00 [watchdog/0] 
root 6 0.0 0.0 0 0 ? S 10:42 0:00 [events/0] 
root 7 0.0 0.0 0 0 ? S 10:42 0:00 [cpuset] 
root 8 0.0 0.0 0 0 ? S 10:42 0:00 [khelper] 
root 9 0.0 0.0 0 0 ? S 10:42 0:00 [netns] 
root 10 0.0 0.0 0 0 ? S 10:42 0:00 [async/mgr]

---

### Post by acwest on 2011-02-06
Anyone?

---

### Post by Spiritof76 on 2011-02-06
Have you tried another editor or  Text reader. 
```
# ps aux >> out.txt
``` works just fine for me.

---

### Post by Vaphell on 2011-02-06
#2 gave you the answer already, so what's the problem?
```
ps aux > out
```
execute ps aux and redirect output to out


or if you really want to do this hard way (yours)
```
echo "$(ps aux)" > out
```
execute ps, capture its output, print the captured output but redirect to out. As you can see echo is an unnecessary step that brings nothing to the table. But if you really want to do that, use "".
""  preserve formatting, without quotes all whitespaces (tab, newline - you name it) degrade to space (or should i say to default separator of shell)

---

