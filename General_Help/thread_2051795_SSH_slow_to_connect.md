---
title: "SSH slow to connect"
date: 2012-09-02
forum: General Help
---

### Post by prkos on 2012-09-02
I recently switched ISP provider on the machine I want to connect to, there were no problems with the old ISP but as soon as I switched connecting through ssh (scp too) became very slow, even up to several minutes to get the authentication query to appear. 

After the connection is established it all works fast. 

What could be the problem? Is it some SSH configuration I can tweak to speed it up? Or is it my new ISP configuration I should look at?

---

### Post by spiky001 on 2012-09-02
Hi

I added a line in /etc/hosts ```
ip    name of server
```127.0.0.1    localhost
127.0.1.1    spiky-laptop

[COLOR=Red]10.42.43.1      spiky-server[COLOR=Black] <<<<<

I also done it on the server file as well   ip   then client name , not sure if this part help but all in all connected quicker, I would try the 1st part 1st.
[/COLOR][/COLOR]

---

### Post by Lars Noodén on 2012-09-02
Is it just as slow whether you connect via IP address or hostname?

---

### Post by Bachstelze on 2012-09-02
[http://openssh.org/faq.html#3.3](http://openssh.org/faq.html#3.3)

---

### Post by prkos on 2012-09-02
Thank you for all the comments! 

It turned out that DNS lookup wasn't the problem. 

The problem was with authentications, and the solution was to skip various authentication types and land right onto password authentication: 

I created the ```
~/.ssh/config
``` file and put 

```
PreferredAuthentications password,keyboard-interactive
```

in it. It's still not super fast like it had been before but it's much better and perfectly acceptable at around 10 seconds wait. 

Here's the article that helped: 
[http://www.toptip.ca/2010/03/slow-ssh-connection-to-remote-server.html](http://www.toptip.ca/2010/03/slow-ssh-connection-to-remote-server.html)

---

