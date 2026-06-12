---
title: "SSH Question"
date: 2010-11-14
forum: General Help
---

### Post by Lucrin on 2010-11-14
Ok so I just recently installed ubuntu on my computer because I use it in my classes (computer science major) Previously I had been using putty on windows to connect to the school server and edit my files but I know linux has built in SSH. So my question is how do I go about using it? I know how to enter my server and login info into putty but I don't know what to type or where in ubuntu. I also use WinSCP to keep my files synced with the server. Thanks!

---

### Post by issih on 2010-11-14
Open a terminal and type:

```
man ssh
```

that will give you the manual

the very simplest basics are:

```
ssh me@mymachine
```

and enter your password when prompted.

*Edit*
For something more akin to winSCP functionality go to places->connect to server.
In that dialog select ssh as the service type and enter the other details (N.B. the default ssh port is 22)
*End Edit*

Hope that helps

---

