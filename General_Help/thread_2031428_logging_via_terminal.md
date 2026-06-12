---
title: "logging via terminal"
date: 2012-07-22
forum: General Help
---

### Post by riyas786tk on 2012-07-22
how to login to any website account using bash shell so that i can access the contents from the shell itself. 
for example how to login to yahoo in terminal. please guide me as i am new to the linux.

---

### Post by codemaniac on 2012-07-22
> **riyas786tk said:**
> how to login to any website account using bash shell so that i can access the contents from the shell itself. 
for example how to login to yahoo in terminal. please guide me as i am new to the linux.

There are many console based web browsers available in Ubuntu.
I had tried **elinks **a some time back .

---

### Post by riyas786tk on 2012-07-22
i need this for scripting. so how to include the login details too.

---

### Post by codemaniac on 2012-07-22
> **riyas786tk said:**
> i need this for scripting. so how to include the login details too.

Elinks is a console based text web browser only .

If what you want to do is retrieve content from a website using HTTP Basic authentication then you can achieve this from the command line using curl:

please have a look at the man page of curl .

---

### Post by riyas786tk on 2012-07-22
i can't find any option for providing the username and password for logging purpose in curl. please help with this.

---

### Post by codemaniac on 2012-07-22
> **riyas786tk said:**
> i can't find any option for providing the username and password for logging purpose in curl. please help with this.

To tell curl to use a user and password for authentication .

```
curl --user name:password http://www.example.com
```

HTTP Authentication is the ability to tell the server your username and password so that it can verify that you're allowed to do the request you're doing. The Basic authentication used in HTTP (which is the type curl uses by default) is *plain* *text* based, which means it sends username and password only slightly obfuscated, but still fully readable by anyone that sniffs on the network between you and the remote server.

---

### Post by Lars Noodén on 2012-07-22
[lynx](http://lynx.browser.org/) is another text-based web browser.  It is highly recommended and is even in the default set up of some distros.  

If you are accessing Yahoo for mail instead of web searching, then you might look to nice tools like [alpine](http://www.washington.edu/alpine/).  It is competitive with Thunderbird as far as features of the basic package go.

Both are in the repositories.

---

