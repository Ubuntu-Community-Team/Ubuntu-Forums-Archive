---
title: "Closing a background SSH connection"
date: 2011-06-01
forum: General Help
---

### Post by satman-ga on 2011-06-01
I have an open ssh connection used for port forwarding using the following command:
```
ssh -fN -L "port:server:port" server
```

It worked properly, but I'd now like to close that connection. How do I close a background SSH connection?

---

### Post by seawolf167 on 2011-06-01
You can find the process ID with

```
ps -ef | grep ssh
```then kill it with

```
kill -9 *pid*
```

you can see current ssh connections with 

```
who
```You may want to take a look at [*screen*]("http://www.rackaid.com/resources/linux-screen-tutorial-and-how-to/"), it is very nice for ssh sessions (especially if something disconnects the session)

```
man screen
```

---

### Post by satman-ga on 2011-06-01
Thanks for the help seawolf.:D

---

### Post by seawolf167 on 2011-06-01
No problem, glad you got it working!

---

