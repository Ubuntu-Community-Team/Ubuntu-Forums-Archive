---
title: "How do I sort with ubuntu"
date: 2012-07-13
forum: General Help
---

### Post by klosdo on 2012-07-13
I can not figure out how to do ascending sort and descending sort with ubuntu. It is for my unix class and the teacher only has the commands for putty. Those commands do not work with ubuntu. Any help would be greatly appreciated

---

### Post by steeldriver on 2012-07-13
I don't really understand what you mean by "commands for putty" - putty is just an ssh client, any commands you type in the putty session are actually running in a shell on the remote host so they *are* the ubuntu commands (if the host is running ubuntu)

```
sort
```
```
sort -r
```

---

### Post by klosdo on 2012-07-14
Our teacher has the class set up with the putty server. At school the wireless sucks so some of us just use ubuntu. So we do not need to use the wireless. For the file he wants us to sort just the gpa in ascending and descending order. I can get it to sort the whole file but not just the Gpa.

---

### Post by Dave_L on 2012-07-14
Is it possible the teacher wants you to do your own research, for example by reading the man page, rather than having someone give you the answer on a forum? ;)

---

### Post by Vaphell on 2012-07-14
*sort --help* and look for **-k**

---

### Post by klosdo on 2012-07-14
He told us to go to a forum and see what we could find out. He dose not know how to do it with ubuntu. The command is different than what is on putty. I can get it to sort the whole file but he wants just the GPA I can not figure out how to do just the GPA

---

### Post by Pilot6 on 2012-07-15
As I got you (maybe I am wrong).
1. Your techer set up a UNIX server.
2. People connect to it using puty from windows.
3. You want to do the same from Ubuntu.

If mentioned above is correct, you just neet to use Ubuntu terminal. Login to the server using ssh command.

e.g ssh 192.168.1.1
where 192.168.1.1 is server ip address.

ALL commands will work same way as in putty, since they run on the server.

---

### Post by sisco311 on 2012-07-15
You don't sort with Ubuntu or PuTTY.

Ubuntu is an operating system and PuttY is a terminal emulator which can act as a SSH, Telnet... client.

sort is a CLI utility.

In Ubuntu you have the GNU sort command installed (by default).

Most likely, the sort utility installed on the Unix server conforms to not the most recent version of POSIX.

See:
[http://www.gnu.org/software/coreutils/manual/html_node/Standards-conformance.html](http://www.gnu.org/software/coreutils/manual/html_node/Standards-conformance.html)

If you have any questions, ask your teacher :evil:, or please feel free to ask them here. :)

---

