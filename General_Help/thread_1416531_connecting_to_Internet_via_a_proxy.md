---
title: "connecting to Internet via a proxy"
date: 2010-02-26
forum: General Help
---

### Post by knowledgestudent on 2010-02-26
Hi there, 
I am new to ubuntu,
my network connection is using a proxy, I have edited the FireFox preferences and set the proxy connection parameters, and could connect to the Internet, 
But not via the Terminal, 
when I am using the command : wget [http://......the](http://......the) link I am trying to download....
I got an error, as the Terminal can not connect via the proxy, in another word to use the proxy parameters , 

any help regarding thins !!!!!,
am I missing something , some settings , or may be commands I can use to tell the Terminal to connect through the proxy !!!

Thanks in advance , :) 
regards.

---

### Post by steviefordi on 2010-02-26
Can't remember which but you can set up your proxy in '**System >> Administration**' or '**System >> Preferences**', after which wget should work.

---

### Post by knowledgestudent on 2010-02-27
> **steviefordi said:**
> Can't remember which but you can set up your proxy in '**System >> Administration**' or '**System >> Preferences**', after which wget should work.
Thank u very much :), for replying, appreciated, 
it is the preferences, 
my proxy asks for authentication, is there a way to set authentication information too, instead of setting them each time in the terminal by : 
> export http_proxy:[http://myproxy: portNumber]("http://myproxy:portNumber")
thanks

---

### Post by steviefordi on 2010-02-27
I'm sure there are other ways around this, but you could put the code

```
export http_proxy:http://myproxy: portNumber
```

into your .bashrc - a hidden file which you can find in your home folder. Just edit it with a text editor and add the line above somewhere that looks convenient. The line will then get run automatically when you open a terminal to start a bash session.

---

