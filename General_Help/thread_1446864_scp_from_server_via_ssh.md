---
title: "scp from server via ssh"
date: 2010-04-04
forum: General Help
---

### Post by spiky001 on 2010-04-04
I,m learning bits of terminal i have learnt how to move a file over ssh to server but I cant get it back via terminal

```
scp Downloads/test8 user@host:home/user/Documents
```

moves it to server now i need to transfer back, I know I can do it with nautilus but i wanna learn terminal, I have googled but cant find what i,m looking for

---

### Post by terrrorr on 2010-04-04
Hi,

Here is couple examples

Push "test.txt" file from server1's /home/user/ directory to server2's /root directory using remote servers (server2) root account:

```
user@server1:~$ scp /home/user/test.txt root@server2:/root/
```

Pull "test.txt" file from server2's /root directory to server1's /home/user/ directory using remote servers (server2) root account:
```
user@server1:~$ scp root@server2:/root/test.txt /home/user/
```

I hope this helps you

---

### Post by spiky001 on 2010-04-04
I will try that tomorrow is late now, Also I just realized I need ssh server installed on lappy opps

---

