---
title: "Unable to access local web server with web browser"
date: 2012-05-09
forum: General Help
---

### Post by rensell on 2012-05-09
Hi all, I just recently (as in last night) built my new system and installed Ubuntu 12.04 on it. Today I'm working on migrating from my old, dying laptop running Win7 Enterprise to my desktop running Ubuntu. Most things are going good, except this and it's a HUGE issue and hopefully an easy fix.

I have a Ubuntu 10.04 server running on my LAN and I have Apache installed. On my laptop, or any windows machine, I can open Chrome and go to servername/ and it loads the webpage or I can goto 192.168.1.190 and it loads the appropriate page. Please note, that servername/ and 192.168.1.190 are the same server but DIFFERENT host/webpages.

Now, on ubuntu I've tried going to servername/ and get an error that it can't be reached, by both firefox and Chrome. However, I can access the IP based page and I can access the server shared files in Nautilus. 

Anyone have any ideas what I need to do. I thought this was a Chrome issue, but tried in F.Fox before posting to be sure.

TYIA

---

### Post by rensell on 2012-05-10
bump... Anyone?

---

### Post by strask on 2012-05-10
Try servername.local and see if that works.

Edit: Or just add the server to /etc/hosts on your new system.

---

### Post by rensell on 2012-05-11
when I server.local it loads the IP based page (which is just a landing page). I use the server for various development things and going to the IP address needs to be different from [http://server/](http://server/).

Not sure how to add it to host file, I added just the server name and it still times out, added IP Address <TAB> server Name and it just hangs.

I looked at my hosts file on windows 7 and there are no entries. So, I'm not sure what setting(s) in Ubuntu are causing it to not load.

---

### Post by rensell on 2012-05-11
Just tried to SSH to the server using server name from the terminal and got a "host could not be resolved" error. Did some googling and found this post about netbios, winbind and hosts lookup(s).

[http://ubuntuforums.org/showthread.php?t=88206]("http://ubuntuforums.org/showthread.php?t=88206")

That fixed my issues.

---

### Post by IHeequ5i on 2012-05-11
Ok, so [http://server](http://server)  and [http://192.168.1.190](http://192.168.1.190) are the same box, right? And the latter is just a "landing page".

Look at the complete URLs for both of these from one of the computers that's working. They're obviously resolving to two different files. Something like:

[http://server/index.htm](http://server/index.htm) OR [http://server/directory/index.htm](http://server/directory/index.htm)

and 

[http://192.168.1.190/index.html](http://192.168.1.190/index.html)


Try putting the complete URLs in your browser and see if you get the desired results.

---

### Post by strask on 2012-05-11
> **rensell said:**
> Just tried to SSH to the server using server name from the terminal and got a "host could not be resolved" error. Did some googling and found this post about netbios, winbind and hosts lookup(s).

[http://ubuntuforums.org/showthread.php?t=88206](http://ubuntuforums.org/showthread.php?t=88206)

That fixed my issues.

Thanks for the pointer! I was wishing there were a good way to resolve WINS addresses, and I guess there is. :)

Glad your problem is resolved.

---

