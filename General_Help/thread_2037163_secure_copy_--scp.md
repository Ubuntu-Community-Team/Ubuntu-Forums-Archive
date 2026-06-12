---
title: "secure copy --scp"
date: 2012-08-03
forum: General Help
---

### Post by micahpage on 2012-08-03
I am trying to scp from local to remote (without ssh into the remote) 

```
metulburr@ubuntu:~$ scp ops.txt -P 9969 metulburr@***.***.***.***:/home/metulburr
ssh: connect to host ***.***.***.*** port 22: Connection timed out
lost connection

```

I am not sure why it is looking for port 22 when i specified port 9969?

however in the same token, in reverse it works:
when i copy from remote to local
```
metulburr@ubuntu:~$ scp -P 9969 metulburr@***.***.***.***:/home/metulburr/rerun_hist.py /home/metulburr
Arch Linux \r (\l)
Rob Graves
metulburr@***.***.***.***'s password: 
rerun_hist.py                                 100%  534     0.5KB/s   00:00    
metulburr@ubuntu:~$ 

```

both of these are where i am NOT ssh'ed into the remote host, and doing it from my terminal
this is where i am getting the examples from
[http://www.hypexr.org/linux_scp_help.php](http://www.hypexr.org/linux_scp_help.php)

---

### Post by papibe on 2012-08-03
Hi micahpage.

It looks like a syntax problem. Put all options first, and then source and destination:
```
ssh -P 9969  ops.txt  metulburr@yourserver:/home/metulburr
```
Let us know how it goes.
Regards.

---

### Post by micahpage on 2012-08-03
that worked perfect. Thanks a lot.
[QUOTE="papibe"]Put all options first[/QUOTE]
did not  know this part

```
metulburr@ubuntu:~$ scp -P 9969 ops.txt metulburr@***.***.***.***:/home/metulburr
Arch Linux \r (\l)
Rob Graves
metulburr@***.***.***.***'s password: 
ops.txt                                       100%   10     0.0KB/s   00:00    
metulburr@ubuntu:~$ 

```

---

### Post by papibe on 2012-08-03
:D

Please mark this thread as solved (read [here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")), when you have the chance.

Regards.

---

