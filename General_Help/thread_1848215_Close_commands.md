---
title: "Close commands"
date: 2011-09-22
forum: General Help
---

### Post by dryder on 2011-09-22
Hi,

I am starting evolution and thunderbird using scheduled tasks.

But what are the commands /switches that will gracefully quit them, please?

Regards,
David

---

### Post by dcstar on 2011-09-22
> **dryder said:**
> Hi,

I am starting evolution and thunderbird using scheduled tasks.

But what are the commands /switches that will gracefully quit them, please?

Regards,
David

```
man kill
```

---

### Post by dryder on 2011-09-22
Thanks, but as I understand it that requires the PID.

All I'm trying to do is start and close thunderbird and evolution while I am asleep so they can pickup business overseas mail then closedown before the system does a daily backup.

David

---

### Post by raja.genupula on 2011-09-22
Hi Dryder 
        PID->Process ID
open system monitor , there in the process TAB , you are going to have ID.

---

### Post by sisco311 on 2011-09-22
You can use pkill(1) to send the TERM signal based on process name.

---

### Post by dryder on 2011-09-23
No, I'm just not with you.

thunderbird runs as a child process and
pkill -t /usr/lib/thunderbird-3.1.13/thunderbird-bin
or
pkill -t /usr/lib/thunderbird-3.1.13/thunderbird

do not work.

Before my first post I had expected something like
thunderbird -quit
but obviously not.

Is scheduling the close of a program difficult?

David

---

### Post by Azdour on 2011-09-23
Hi,

I believe you do not need the -t parameter. I have been playing with pkill and firefox, and to stop firefox I just issued the command:

```
pkill firefox
```

So I think pkill thunderbird should hopefully work for you.

---

### Post by sisco311 on 2011-09-23
Well, *pkill -TERM thunderbird* should do the trick, but it's **insecure**. For more info, please check out: [http://mywiki.wooledge.org/ProcessManagement](http://mywiki.wooledge.org/ProcessManagement)

---

### Post by raja.genupula on 2011-09-23
I have got one more useful 

look at this also 

[http://www.howtogeek.com/howto/ubuntu/kill-a-process-by-process-name-from-ubuntu-command-line/](http://www.howtogeek.com/howto/ubuntu/kill-a-process-by-process-name-from-ubuntu-command-line/)

---

### Post by dryder on 2011-09-23
Thanks for the replies.

The simplest,
pkill thunderbird
and
pkill -TERM thunderbird
both seem to work (begs the question, what''s the '-TERM' do  to help?).

Very grateful for these. I must ask, as I am not terminating a frozen, misbehaving etc. task, do these close down the app gracefully?

David

---

### Post by sisco311 on 2011-09-23
> **dryder said:**
> 
Very grateful for these. I must ask, as I am not terminating a frozen, misbehaving etc. task, do these close down the app gracefully?


Yes, assuming that the process (thunderbird) interprets the TERM signal correctly.

[http://en.wikipedia.org/wiki/SIGTERM](http://en.wikipedia.org/wiki/SIGTERM)

---

### Post by psrdotcom on 2011-09-23
Its useful ..

Please close the thread i.e. please mark the thread as solved. so that, other people might refer your thread.

Thanks):P

---

### Post by dryder on 2011-09-23
I'm afraid
> Its useful ..
doesn't help me understand or learn anything at all. :-)

Usful for what reason?

---

