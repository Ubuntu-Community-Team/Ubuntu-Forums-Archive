---
title: "Configure computer to automatically send IP by mail"
date: 2011-12-17
forum: General Help
---

### Post by JunCTionS on 2011-12-17
ok, I've been trying to figure this out and googling on different occasions is been fruitless, so I'm hoping someone can point me in the right direction here.

I have a netbook that I like to leave online behind a router that gets a dynamic WAN IP address.

I have already set up the router to give this computer a static port and to forward ports 22 and 5900 so I can ssh and vnc to it (vnc closed and can activated thru ssh).

So, what I want is to set up the built-in mail (aka xmail or mailx) to send me an email if the IP changes (or send me the current WAN IP every 6 hours or something), also it'd be awesome if it would send me the battery state.

Is there a way to do this?

---

### Post by Tkissinger on 2011-12-17
Just add a job to cron to run a script with:

wget -O - [www.whatismyip.org](www.whatismyip.org) | tail | mail [email]whatever@whatever.com[/email]

You can pipe that into any send mail program that you have setup.

---

### Post by JunCTionS on 2011-12-17
thanks! that will probably work, but I guess I forgot to add that I don't know which command to use to configure the smtp server of mail. Or can I just configure the default mail client graphically and will it take the same configuration? (although I'd prefer to do it by bash).

---

### Post by Tkissinger on 2011-12-18
Not a problem.  You can install sendemail from apt-get (sudo apt-get install sendemail).

Then just setup your script to run:

```
wget -O - www.whatismyip.org | tail | sendemail -f from@address.com -t to@address.com -s smtp.server.address
```

No other configuration needed.

---

### Post by The Cog on 2011-12-18
I would prefer
> GET [www.whatismyip.org](www.whatismyip.org) | sendmail
GET doesn't produce the progress dialogue that you're stripping again.

---

