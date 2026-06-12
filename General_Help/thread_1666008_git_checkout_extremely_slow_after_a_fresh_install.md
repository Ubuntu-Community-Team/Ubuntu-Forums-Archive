---
title: "git checkout extremely slow after a fresh install"
date: 2011-01-13
forum: General Help
---

### Post by halstead on 2011-01-13
I've done a fresh install of 10.10 and I've noticed the git is way slower then it has been on any other machine. I first tried switching to the git-stable ppa to see if that would help but it didn't.

Here is the output of strace from when it is really slow.
```
stat("/etc/resolv.conf", {st_mode=S_IFREG|0644, st_size=133, ...}) = 0
socket(PF_INET, SOCK_DGRAM|SOCK_NONBLOCK, IPPROTO_IP) = 5
connect(5, {sa_family=AF_INET, sin_port=htons(53), sin_addr=inet_addr("8.8.8.8")}, 16) = 0
poll([{fd=5, events=POLLOUT}], 1, 0)    = 1 ([{fd=5, revents=POLLOUT}])
sendto(5, "\342\355\1\0\0\1\0\0\0\0\0\0\10\n\t\3"..., 40, MSG_NOSIGNAL, NULL, 0) = 40
poll([{fd=5, events=POLLIN}], 1, 5000)  = 1 ([{fd=5, revents=POLLIN}])
ioctl(5, FIONREAD, [40])                = 0
recvfrom(5, "\342\355\201\202\0\1\0\0\0\0\0\0\10\n\t\3"..., 1024, 0, {sa_family=AF_INET, sin_port=htons(53), sin_addr=inet_addr("8.8.8.8")}, [16]) = 40
close(5)                                = 0
socket(PF_INET, SOCK_DGRAM|SOCK_NONBLOCK, IPPROTO_IP) = 5
connect(5, {sa_family=AF_INET, sin_port=htons(53), sin_addr=inet_addr("8.8.4.4")}, 16) = 0
poll([{fd=5, events=POLLOUT}], 1, 0)    = 1 ([{fd=5, revents=POLLOUT}])
sendto(5, "\342\355\1\0\0\1\0\0\0\0\0\0\10\n\t\3"..., 40, MSG_NOSIGNAL, NULL, 0) = 40
poll([{fd=5, events=POLLIN}], 1, 5000)  = 1 ([{fd=5, revents=POLLIN}])
ioctl(5, FIONREAD, [40])                = 0
recvfrom(5, "\342\355\201\202\0\1\0\0\0\0\0\0\10\n\t\3"..., 1024, 0, {sa_family=AF_INET, sin_port=htons(53), sin_addr=inet_addr("8.8.4.4")}, [16]) = 40
close(5)                                = 0
socket(PF_INET, SOCK_DGRAM|SOCK_NONBLOCK, IPPROTO_IP) = 5
connect(5, {sa_family=AF_INET, sin_port=htons(53), sin_addr=inet_addr("8.8.8.8")}, 16) = 0
poll([{fd=5, events=POLLOUT}], 1, 0)    = 1 ([{fd=5, revents=POLLOUT}])
sendto(5, "\342\355\1\0\0\1\0\0\0\0\0\0\10avarice\n\tincitedev\3"..., 40, MSG_NOSIGNAL, NULL, 0) = 40
poll([{fd=5, events=POLLIN}], 1, 5000)  = 1 ([{fd=5, revents=POLLIN}])
ioctl(5, FIONREAD, [40])                = 0
recvfrom(5, "\342\355\201\202\0\1\0\0\0\0\0\0\10\n\t\3"..., 1024, 0, {sa_family=AF_INET, sin_port=htons(53), sin_addr=inet_addr("8.8.8.8")}, [16]) = 40
close(5)
```
It repeats this several times for a few seconds then eventually works. So it's trying to do DNS lookups of addresses that don't exist. I suppose I'll check if I can make changes to /etc/hosts.

---

### Post by halstead on 2011-01-13
So I hadn't yet set up my name and e-mail.

Following the guide at [http://book.git-scm.com/2_setup_and_initialization.html](http://book.git-scm.com/2_setup_and_initialization.html) I ran these commands.

$ git config --global user.name "Scott Chacon"
$ git config --global user.email "schacon@gmail.com"

I normally do this right away when setting up my account on a new machine. The fresh install didn't trigger that reflex. I'm surprised that this is needed to keep git from preforming silly DNS lookups but no big deal.

---

