---
title: "ssh into two systems"
date: 2010-03-20
forum: General Help
---

### Post by kngofbuntu on 2010-03-20
My home computer is under a network which has allowtcpforwording off
i can ssh into my system as root but to do that i have to ssh first into his server in a temporary account (created while we were given internet.)
how can i use my internet at my house as a "stocks proxy through ssh"

---

### Post by kngofbuntu on 2010-03-20
As such I use putty to do the ssh tunnelling 
but it doesn't seem to be working
as the firefox window says 
"Connection Reset "
P.s. I am able to w3m and wget on my home system

---

### Post by jsriz on 2010-03-21
try using the openssh-client

---

### Post by kngofbuntu on 2010-03-21
> **jsriz said:**
> try using the openssh-client
how do i do that

---

### Post by SlugSlug on 2010-03-21
[http://thinkhole.org/wp/2006/05/10/howto-secure-firefox-and-im-with-putty/](http://thinkhole.org/wp/2006/05/10/howto-secure-firefox-and-im-with-putty/)

---

### Post by kngofbuntu on 2010-03-21
> **SlugSlug said:**
> [http://thinkhole.org/wp/2006/05/10/howto-secure-firefox-and-im-with-putty/](http://thinkhole.org/wp/2006/05/10/howto-secure-firefox-and-im-with-putty/)

yes i know how to connect to a server directly but 
i cannot do that for my system as it is under a network server to which i dont have root access just a temporary account.
now to have a putty connection i first open the terminal a login the server then i ssh into my system...........

---

### Post by SlugSlug on 2010-03-21
right I see so ssh > server ssh > your pc and you want firefox using your pc internet

so you'd have to config firefox like in that website

and then tunnel that port from server to pc with ssh -D

lets use port 9999

Putty and firefox setup like the webpage says using port 9999
Putty to server and then ssh -D 9999 to your pc

that may work?

---

### Post by kngofbuntu on 2010-03-21
nope doesn't work firefox still returns 
"The connection was reset"
i have checked /etc/ssh/sshd_config the ALLOWTCPFORWARDING is set to NO on the server 
but nothing of that sort in my system....
does that make any difference

---

### Post by kngofbuntu on 2010-03-26
bump

---

