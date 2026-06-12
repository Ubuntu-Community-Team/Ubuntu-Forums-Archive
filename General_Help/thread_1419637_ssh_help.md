---
title: "ssh help"
date: 2010-03-02
forum: General Help
---

### Post by ooobooontooo on 2010-03-02
Hi,

I'm having a bit of trouble with my ssh sessions, and am wondering what's going on. When I connect to the server, it will authenticate me and let me in (I know this because I saw the server's logs), but it won't let me have a shell. It also freezes any old ssh connections that I might have had. I find that whenever I refresh my network connection, I am able to get back on to the server, but after a while the same problem returns. I'm not having this problem with any of the servers that I connect to. Everyone else that connects to problematic server says they're able to log in and stay on no problem. I have tried the "ServerAliveInterval" option, but it didn't do anything for me.

So, I guess I have 2 questions:
1. Is this is a ssh or a server problem?
2. How do you recommed narrowing down the field to see what kind of problem this is? I've never had this kind of problem before and my google-fu has been failing me.

Thanks in advance.

EDIT: I'm able to connect to the server in question in other ways (HTTP, SMTP).

---

### Post by 1/0 on 2010-03-02
One way is to connect to another ssh server and see if the problem repeats. If it does, then its on the client side. If not it indicates that it could be on the server side. 

It could be a lot of things causing this. For instance the *ServerAliveInterval*.

---

