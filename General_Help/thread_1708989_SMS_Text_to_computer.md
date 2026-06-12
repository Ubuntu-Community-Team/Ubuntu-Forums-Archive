---
title: "SMS Text to computer?"
date: 2011-03-17
forum: General Help
---

### Post by zjmichen on 2011-03-17
Hello, currently I have conky set up to show the contents of a file todo.txt, which I use for my todo list.  However I don't usually get new things to do around my computer.  It would be nice to be able to text something (like Google Voice or Dropbox) and have it automatically added to todo.txt.

Is there any way to do this or am I crazy?

---

### Post by pricetech on 2011-03-17
If you're crazy, you're not alone.

I recently searched to see what I could find and came up empty handed.  I found plenty that would send SMS, but nothing that would receive it.

You could use web access on your phone to edit a simple text file which is saved to your dropbox account and the changed would be replicated to your computer.  Is that an option for you ??

You might check around and see if someone offers a service to suit your needs.

Also, at one point you could send a text using your email account by using the ten digit phone number as the username with something like "txt.att.net" or "vtext.com" for att and Verizon, respectively, and presumably other major carriers had that as well.  Then the phone's user would simply reply to the text and it would go as an email back to your inbox.  Maybe that would give you a workaround.

Just some thoughts.

Good luck with it and have fun.

---

### Post by An Sanct on 2011-03-17
The way I saw computer receiving text messages from mobiles was always hardware related. A nokia with a nokia communications cable and piece of software monitoring changes, for instance ... thats the way TV shows make it :), cheap and efficient.

---

### Post by zjmichen on 2011-03-17
Yeah I saw something called gnokii, which afaik uses bluetooth with a phone near the computer.

Unfortunately I don't have a data plan, only text :/

Oh well, hopefully someone with time will invent something like this someday.

---

### Post by pricetech on 2011-03-18
By the way, I checked and both Verizon and att still allow you to exchange text messages via email using the ten digit number as a username.

<ten_digit_number>@txt.att.net
<ten_digit_number>@vtext.com

Other carriers do the same as I understand it.

Would that be an option for you as a workaround ???

---

### Post by aeiah on 2011-03-18
> **zjmichen said:**
> Yeah I saw something called gnokii, which afaik uses bluetooth with a phone near the computer.

Unfortunately I don't have a data plan, only text :/

Oh well, hopefully someone with time will invent something like this someday.

text is enough, isnt it? i used to do it by permanently tethering an old phone to my pc via bluetooth, and the messages would pop up when i sent an SMS to this phone. it just used the standard gnome tool for the job (gnome-phone-manager?). there are probably others. OP would ideally want a cli one that is scriptable i guess.

---

### Post by new_tolinux on 2011-03-18
> **zjmichen said:**
> Yeah I saw something called gnokii, which afaik uses bluetooth with a phone near the computer.

Unfortunately I don't have a data plan, only text :/

Oh well, hopefully someone with time will invent something like this someday.
As for bluetooth, you don't need any data plan....
The phone next to the computer can even be a prepaid phone, since it does not send anything.
Only the "sending" phone (your phone, which you use to send a text-message to your computer) needs to be able to send text-messages.

---

### Post by zjmichen on 2011-03-19
> text is enough, isnt it? i used to do it by permanently tethering an old phone to my pc via bluetooth, and the messages would pop up when i sent an SMS to this phone. it just used the standard gnome tool for the job (gnome-phone-manager?). there are probably others. OP would ideally want a cli one that is scriptable i guess.

True, but that would mean both that I have an old phone (which I usually recycle) and that the phone could receive texts, which I'm guessing would cost more money. (Well maybe not for like a family plan, idk)

I was kinda looking for something more web-based, without the need of extra hardware.

---

### Post by lykeion on 2011-03-19
Maybe you could lookup [premium sms services]("http://en.wikipedia.org/wiki/SMS#Premium-rated_short_messages").
I don't know about availability of such services for operators in US (Asheville, NC is in US right?). 
But I know that in Sweden (for operators like Telia, Tele2, etc) there are services like this: 
[https://www.multimobil.se/web/guest/solutions](https://www.multimobil.se/web/guest/solutions) 
That will let you create a premium service thet "Let your customers send an SMS or MMS which is published directly on a web page"

---

### Post by zjmichen on 2011-03-19
> **lykeion said:**
> Maybe you could lookup [premium sms services]("http://en.wikipedia.org/wiki/SMS#Premium-rated_short_messages").
I don't know about availability of such services for operators in US (Asheville, NC is in US right?). 
But I know that in Sweden (for operators like Telia, Tele2, etc) there are services like this: 
[https://www.multimobil.se/web/guest/solutions](https://www.multimobil.se/web/guest/solutions) 
That will let you create a premium service thet "Let your customers send an SMS or MMS which is published directly on a web page"

That looks right up my alley.. perhaps if there were a free US solution?

---

### Post by lykeion on 2011-03-19
Yes, exactly what I was thinking. But I'll pass the google searching on to you ;)

---

### Post by new_tolinux on 2011-03-19
> **zjmichen said:**
> True, but that would mean both that I have an old phone (which I usually recycle) and that the phone could receive texts, which I'm guessing would cost more money. (Well maybe not for like a family plan, idk)

I was kinda looking for something more web-based, without the need of extra hardware.
As I said, for the receiving phone, you can even use a prepaid one, since receiving text messages won't cost you anything (here in europe).
That means that the only "costs" you have are these:
* Once in a while upgrading your prepaid phone, so it doesn't expire
* Charge the battery

Since I don't know the costs of electricity, I won't guess that part ;)
Upgrading your mobile phone differs from provider to provider, but usually is about €10 per 6 months/1 year around here (which you can use to call, since receiving text messages is free).

---

### Post by pricetech on 2011-04-12
Something else I've learned;

When you text to a Verizon phone, or at least to my EnV3, it shows up as from the email address rather than a string of numbers like att uses.

I can send a text message to my email address and it's counted as an SMS message, not an email.

Just wanted to pass that along.

---

### Post by earthmeLon on 2011-04-12
You could use Twilio or similar service.  Depending on how many texts you would be sending/receiving, you may be able to fall under a development (free) plan.

---

### Post by imblack on 2011-07-29
You could also install kannel and configure it then you can send and receive SMS in ubuntu. Also look for gammu.

The main problem is that your phone doesn't behave as a good, compatible GSM modem. I had that problem, did some research and bought SonyEricsson w200i which is so far the best one I found for the task at hand.

I have used kannel for my own hobby project [LoOp - Free SMS service]("http://loop.pk")

---

