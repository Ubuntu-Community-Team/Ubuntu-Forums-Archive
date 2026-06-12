---
title: "Stupid e-mail problem"
date: 2012-04-20
forum: General Help
---

### Post by Barney-R on 2012-04-20
Hello,

Ubuntu 10.10 (64-bit). Thunderbird 11.0.1.

I've got a problem with e-mail that should be simple enough, but I'm stuck, and so is my ISP.

I reinstalled Ubuntu yesterday following a hard drive replacement, and now I can neither send nor receive e-mails. The e-mail addresses and passwords are correct, as are the pop3 and smtp settings.

I'm with BT, and both pop3 and smtp are mail.btinternet.com, port 110 for pop3 and 25 for smtp.

I set a new sub-address up in the hope of getting through, but still no luck.

I can log on to my ISP account, where I can access webmail, though only on the main address.

It's got to be something simple, but I can't work out what it is. I rang my ISP today, and they were unable to advise me.

Can anyone help?

---

### Post by Dngrsone on 2012-04-20
You got SSL/TLS set?

---

### Post by jadtech on 2012-04-20
I had this problem long ago, I know this is going to sound odd but try unplugging your modem and if it has battery back up remove the battery leave it completely off  for a min the same with the router and then replace the battery plug the modem and router back in let it reset ...

this is what worked for me after several hours of battling this with the tech support we had discovered, there system wasnt recognizing the computer connection and blocked the mail port on the ip the system set for me..

not sure this will work for you cant hurt to give it a shot

---

### Post by Barney-R on 2012-04-20
Thank you both for your prompt replies.

Yes Dngrsone. I've got SSL set, not that I really understand all that stuff, which may well be why I'm having this problem.

jadtech, I'll try what you suggested, but I don't think it's going to work because I always switch the power off at night, and this has been going on since yesterday. Anything's worth a try though.

Update. I've now set Evolution up, so far only for the main account, and it's working. I'd much rather get Thunderbird working though because I don't like Evolution.

At least now we know I CAN get my mail. I don't know whether that narrows things down.

I'm still hoping to solve this problem, and welcome any suggestions.

---

### Post by jadtech on 2012-04-20
well I would say if you can get your mail with one program and not another then its a set up issue ..

the fact that you say you unplug your modem every nite tell me the issue I  described not  the trouble, if you had a cable modem with digital phone and back up battery you most likely would not be unplugging t for that long ..

 the mail issue would only effect your providers mail not other accounts

---

### Post by Barney-R on 2012-04-20
Sorry to have wasted your time. I do appreciate your efforts to help, but I've solved the problem at last.

I deleted all accounts from Thunderbird, apart from a Gmail account I use for emergencies and which was working properly, and after a few failed attempts, during which Thunderbird kept changing the POP3, SMTP and port settings, I finally managed to get it to work.

The port numbers kept reverting to the defaults, rather than the ones supplied by my ISP (110 and 25 respectively), and it kept changing the POP3 and SMTP settings to pop.mail.yahoo.com and smtp.mail.yahoo.com when what they _should_ have been was mail.btinternet.com for both, with nothing before the word "mail".

That's

mail.btinternet.com

NOT

pop.mail.btinternet.com

and exactly the same for the SMTP.

Thanks again for at least trying to help. Perhaps others will benefit from my experience. I hope so.

---

### Post by Dngrsone on 2012-04-20
Thanks for letting us know how you fixed your problem.

---

