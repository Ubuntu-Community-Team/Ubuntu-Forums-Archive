---
title: "Hotmail: hotway+inetd+proxy =&gt; not working"
date: 2006-03-23
forum: General Help
---

### Post by jofre on 2006-03-23
Ok, here is another of my problems, sorry challanges;) .

I am trying to setup thunderbird to check my hotmail account :rolleyes: . Thanks to google, I found:
[http://www.wlug.org.nz/UbuntuBreezyNotes](http://www.wlug.org.nz/UbuntuBreezyNotes)

were basically tell you to install hotway and inetd. And make the hotmail server be 127.0.0.1 listening to port 110. At home this work perfectly, but in the office I am having problems. And the problem is called proxy. I did "man hotwayd" (note the last extra "d", it took me a while to find ouT!!! and then "hotwayd -h" which give me:
jofre@edoras:~$ hotwayd -h
Usage: hotwayd [options and arguments]
  -a <accesslist> specify a file listing permitted HTTPMail accounts
  -h print usage page
  -l <loglevel> specify the logging level (0-2)
  -p [proxy:port] specify proxy
  -r set messages as read after downloading
  -u <username> specify proxy username
  -q <password> specify proxy password
  -v display version information
Example: hotwayd -p [http://proxy:8080](http://proxy:8080) -u dave -q proxypass
Note: proxy can be specified without a username or password
jofre@edoras:~$

My proxy is at [http://proxy.dcu.ie](http://proxy.dcu.ie) and if I type this in my webbroser, it tells me that the POP3, is in port 1080, so I typed:

jofre@edoras:~$ hotwayd -p [http://proxy.dcu.ie:1080](http://proxy.dcu.ie:1080)
+OK POP3 hotwayd v0.8.2 -> The POP3-HTTPMail Gateway. Server on edoras active.
quit
+OK see you later!
jofre@edoras:

but still not luck.:-k  The funny thing is that it seems to work, in the sense that when i try to get my email in thunderbird, it ask me for my password in my hotmail account, and i see the message:

Connect: Host contacted, sending login information...


but after a while the message dissapears, and there is nothing in my inbox. But i don't get any error message neither! :-| 

Any ideas?:-k 


Thanks in advance, Jofre.

---

### Post by frodon on 2006-03-23
There's also an other way to get hotmail messages, i use [gotmail]("http://sourceforge.net/projects/gotmail") in my case and it's all i need.
I tried at the time to get hotway working without success but i know that some peoples here use it.

---

### Post by GeneralZod on 2006-03-23
This started happening out of the blue to my mum (who is on dialup) one day, and it turned out that she had received sufficiently many messages that the slightly bloated WebDav protocol used by MSN wasn't able to process them all before Thunderbird's 45 second time-out was reached :)

Google for Thunderbird POP3 timeout and see if you can find instructions for increasing it - that solved the problem for her :)

---

### Post by jofre on 2006-03-23
Thanks lads, 

I install Gotmail, but looks more like a console base program. I don't have anything against the console but I rather have it working with thunderbird. (I am sure there is a way to make it work with thunderbird, but after 5 minutes with google, I did not find anything about it).

About the second possible solution: I found a script to get to hidden variables in thunderbird, which allow me to modify the pop3 timeout variable (default=45) to 300. 

Now, at least I get an error message:

Sending of password did not succeed. Mail server 127.0.0.1 responded: Fatal connection error: Connection timed out

I changed the value to 600 and to 900, always the same error message.](*,) 

I now that the proxy setup does not need an user name and pasword, because in order to check my hotmail with firefox i had to setup the proxy settings manually, and have the 1080 port.

Damn proxy!!!

Thanks both of you anyway.

---

### Post by frodon on 2006-03-23
Gotmail is something you would use in a cronjob, check mails every 30 min for example. It create a file containing all the mails then you just have to set your mail client to look in this file for new mails, it's how gotmail works.
In my case i have msn always opened therefore i have an info box each time i have new mails then i created a script i called getmail and all i have to do to get the mails is to type "getmail" in a terminal then open my mail client (evolution).

Hope you will get hotway working since it seems to fit your needs. Anyway if you want to use gotmail tell and i will provide you my script.

---

