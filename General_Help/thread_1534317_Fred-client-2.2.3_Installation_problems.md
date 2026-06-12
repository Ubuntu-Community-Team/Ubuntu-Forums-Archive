---
title: "Fred-client-2.2.3: Installation problems"
date: 2010-07-19
forum: General Help
---

### Post by hasins on 2010-07-19
Dear All

I apologize in advance if the following problems I am facing seem 'basic'.
I am a newbie to Unix systems and trying to learn and adapt.

I am trying to install fred-client-2.2.3 on Ubuntu 8.04 - the Hardy Heron.

So I first downloaded the .tar.gz file from
[http://fred.nic.cz/sources/fred-client-2.2.3.tar.gz](http://fred.nic.cz/sources/fred-client-2.2.3.tar.gz)

Then using the terminal I entered:

[I]$ tar -xf Fred-Client-2.2.3.tar.gz

$ cd Fred-Client-2.2.3

$ sudo ./install.sh[/I]

the last command gave me an error:

**sudo: ./install.sh: command not found**

Using the instructions from
[http://fred.nic.cz/attachment/wiki/documentation/notasfred-en.odt](http://fred.nic.cz/attachment/wiki/documentation/notasfred-en.odt), i tried:

*$ python ./setup.py install*

This started working but then gave me an error:
[B]
creating /usr/lib/python2.5/site-packages/fred
error: could not create '/usr/lib/python2.5/site-packages/fred':
Permission denied[/B]

I have no idea what I should do. Would really appreciate some help.

I need to run the client to communicate with the EPP server of our local
registrar so as to be able to register domains.

Currently if i try running ./fred-client it returns an error:

[B]FredClient 2.2.3
Type "help", "license" or "credits" for more information.

Using configuration from conf/fred-client.conf
Connecting to localhost, port 700 ...

ERROR: I cannot connect to the server localhost.

Connection socket.error: (111, 'Connection refused') (localhost:700)[/B]

Many thanks for your kind assistance in advance

regards

Hasin




Many thanks for your kind assistance

regards

Hasin

---

### Post by hasins on 2010-07-19
Oh, I did a search before posting. Seems there are no posts on fred-client.

Fred-client documentation is available at [http://fred.nic.cz/wiki/documentation](http://fred.nic.cz/wiki/documentation)

---

### Post by hasins on 2010-07-19
> creating /usr/lib/python2.5/site-packages/fred
error: could not create '/usr/lib/python2.5/site-packages/fred':
Permission denied

i am wondering why permission to create the above is being denied! 

Any ideas?

---

