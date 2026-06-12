---
title: "Anybody any good on mgetty?"
date: 2010-03-25
forum: General Help
---

### Post by Fitch on 2010-03-25
After a week of trying to find out how to set up mgetty-voice,
I've finally managed to get something.
--
03/25 22:19:20 yS0  WARNING: parent process not init(pid=1), but pid=4831 (bash)
03/25 22:19:20 yS0  reading program vgetty configuration from config file /etc/mgetty/voice.conf
03/25 22:19:20 yS0  reading port ttyS0 configuration from config file /etc/mgetty/voice.conf
03/25 22:19:20 yS0  check for lockfiles
03/25 22:19:20 yS0  locking the line
03/25 22:19:21 yS0  lowering DTR to reset Modem
03/25 22:19:21 yS0  send: \dATQ0V1H0[0d]
03/25 22:19:22 yS0  waiting for ``OK''
03/25 22:19:42 yS0  timeout in chat script, waiting for `OK'
03/25 22:19:42 yS0  init chat timed out, trying force-init-chat
03/25 22:19:42 yS0  send: \d[10][03]\d\d\d+++\d\d\d[0d]\dATQ0V1H0[0d]
03/25 22:19:46 yS0  waiting for ``OK''
03/25 22:20:06 yS0  timeout in chat script, waiting for `OK'
03/25 22:20:06 yS0  init chat failed, exiting...: Interrupted system call
03/25 22:20:06 ##### failed in mg_init_data, dev=ttyS0, pid=6625

I presume I have to set the "chat" correctly, but where is the file that does this?
I have a US Robotics message modem, which uses AT+MCA=1=MCS=1 etc
What is this "\d[10][03]\d\d\d" all about?

---

### Post by Fitch on 2010-03-25
Found mgetty.config had the same string, but remmed out in directory /etc/mgetty.
Have altered it to
init-chat "" \d\d\d+++\d\d\dAT+MCS=1+MCR=3+MCA=1+MCF=1+MCL=1 OK

Will see what happens.

---

### Post by Fitch on 2010-03-25
Not much difference.

--
03/25 22:56:46 yS0  WARNING: parent process not init(pid=1), but pid=4831 (bash)
03/25 22:56:46 yS0  reading program vgetty configuration from config file /etc/mgetty/voice.conf
03/25 22:56:46 yS0  reading port ttyS0 configuration from config file /etc/mgetty/voice.conf
03/25 22:56:46 yS0  check for lockfiles
03/25 22:56:46 yS0  locking the line
03/25 22:56:47 yS0  lowering DTR to reset Modem
03/25 22:56:48 yS0  send: \d\d\d+++\d\d\dAT+MCS=1+MCR=3+MCA=1+MCF=1+MCL=1[0d]
03/25 22:56:51 yS0  waiting for ``OK''
03/25 22:57:11 yS0  timeout in chat script, waiting for `OK'
03/25 22:57:11 yS0  init chat timed out, trying force-init-chat
03/25 22:57:11 yS0  send: \d[10][03]\d\d\d+++\d\d\d[0d]\dATQ0V1H0[0d]
03/25 22:57:15 yS0  waiting for ``OK''
03/25 22:57:35 yS0  timeout in chat script, waiting for `OK'
03/25 22:57:35 yS0  init chat failed, exiting...: Interrupted system call
03/25 22:57:35 ##### failed in mg_init_data, dev=ttyS0, pid=6939

---

### Post by Fitch on 2010-04-09
Solved it! Got rid of mgetty.

---

### Post by aazevedo1984 on 2012-04-03
how do u solved it?

---

### Post by Fitch on 2012-04-03
I'm surprised I am still a member here as I asked to be removed quite some time ago...
Not your fault, but even a direct mail to the moderators gets ignored.

Sorry to disappoint you., but the problem was critical to my business, and as there were no replies, I removed Linux and re-insalled Windows.
I no longer use Linux as the support was just not there.
Sorry!

I will have to unsuscribe  myself from the post and find out how to get out of this forum.

All the best in your search.

---

### Post by jerome1232 on 2012-04-03
I think you misunderstand, this is a forum for community, volunteer based help. If you want professional support for critical aspects of your business, it costs money.

[http://www.canonical.com/enterprise-services/ubuntu-advantage/support](http://www.canonical.com/enterprise-services/ubuntu-advantage/support)

Here, we just try and help each other out the best we can.

Good luck, with, whatever it is your doing.

Whoops, necro!

---

