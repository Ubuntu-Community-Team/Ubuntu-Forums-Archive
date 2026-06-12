---
title: "imap gmail not working in karmic!"
date: 2009-11-08
forum: General Help
---

### Post by Matthewthegreat on 2009-11-08
I was using my netbook the yesterday and it's running 9.10 and Thunderbird would not connect to imap. I keep getting the error: 

could not connect to mail server imap.gmail.com the connection was refused

or 

connection to server imap.gmail.com timed out

So I decided to connect to it with my desktop computer that's running 9.10 and it had the same problem. So, I try it with evolution instead, same problem. So, I was thinking it was just the servers were down but I found out that I could connect via web and with thunderbird on windows XP. then I booted the ubuntu 9.04 live cd, installed thunderbird and was able to connect fine. 

When I went back to karmic I found that it will occasionally connect but most the times I get the above errors. I've been googling for a few hours now and have found nothing that has helped.

I know it's not any of the e-mail settings in Thunderbird because it was working fine and it works fine in XP and 9.04.

I also don't think it's the firewall. I have not messed with any on the firewall settings. And if it's the firewall why does it occasionally connect? 

Please Help!!!

Thanks!

---

### Post by noSelf on 2009-12-02
i'm having the same problem on karmic-64 after the Nov. 30 kernel upgrade. In addition to Thunderbird 3.0 not being able to connect to imap.gmail.com or smtp.gmail.com, Firefox can't connect to [http://www.google.com](http://www.google.com) nor to [http://www.gmail.com](http://www.gmail.com) - it all times out.

Browsing every other website i visit regularly is fine.

i can ping google and gmail with no problem.

Connecting from Firefox in Windows 7 (via VirtualBox) on the same machine is no problem.

Connecting from the same Thunderbird and Firefox versions on my Jaunty (32-bit) machine has no problem.

i'm not using any firewall. Haven't changed my DSL modem configuration.

i'm using the ubuntu-mozilla-daily ppa ([http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu)) for Thunderbird 3 and Firefox 3.5.x. They were updated within a day of the kernel.

Googling hasn't helped much - it lead me to this thread. i have yet to try the old IPv6 trick mentioned here: [http://www.james-blogs.com/2009/11/04/have-you-upgraded-to-ubuntu-9-10-karmic-koala/](http://www.james-blogs.com/2009/11/04/have-you-upgraded-to-ubuntu-9-10-karmic-koala/)

---

### Post by nguyenjfhk09098 on 2009-12-02
this one attract my attention

---

### Post by Matthewthegreat on 2009-12-05
I never did get this fixed. I just downgraded my desktop to 9.04 and my netbook still runs 9.10. Now everything works! This is the weirdest bug I've ever seen.

---

### Post by noSelf on 2009-12-06
well, it's all working for me now. i took the machine to another (wired) network, and had no problems. Just or laughs, i disbled ipv6 in firefox & thiunderbird, brought the machine home, and all is well now. Go figure.

---

### Post by Matthewthegreat on 2010-03-29
I just upgraded to lucid beta and I had this problem again. So I disabled IPv6 and that fixes the problem.  I'm marking this as solved.

---

