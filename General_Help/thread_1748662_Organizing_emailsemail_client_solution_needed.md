---
title: "Organizing emails/email client solution needed"
date: 2011-05-03
forum: General Help
---

### Post by jonathonblake on 2011-05-03
All:

Currently using Thunderbird. on xubuntu 11.4

Today I spent more than four hours trying to find, unsuccessfully, some emails. Last Friday I spent at least four hours, trying to find a different set of emails. That search was equally unsuccessful.

a) I get emails on roughly a dozen different accounts;
b) Currently I have roughly half a TB of email stored;
c) I get roughly 50 MB of email per day;

Does anybody have any suggestions for:
* email storage that can easily, and rapidly be searched;
* email client that doesn't give up and die, under that volume of email;

jonathon

---

### Post by tprice99 on 2011-05-03
Hi Jonathon!

I would personally recommend using "Claws Mail" it is fully customizable with themes, plugins, and tools. Take a look at it. [http://www.claws-mail.org](http://www.claws-mail.org)

Please let me know what you think!

---

### Post by bergfly on 2011-05-03
I'd suggest that email is not the best method of organising the data you are trying to access. I work in a very active email driven environment and we keep try to keep the mail stores for around 50 users under 1GB each. Half a TB of email is enough to make a seriously powerful and configured mail server struggle. You would need multiple machines load balancing to get any sort of acceptable mail performance with that much email. I'm only assuming that the mail you are getting comes with large attachments, otherwise you are looking at simply unreadable volumes. This sort of volume scream database as the solution. Sorry not to be helpful from a mail client perspective, but if you have more details, maybe suggestions around other ways to organise the data would be useful.

---

### Post by jonathonblake on 2011-05-04
> **tprice99 said:**
> 
I would personally recommend using "Claws Mail"

Can it handle half a terrabyte of emails?

I don't know how many emails that is, but here are some guestimates:

mean character length - 3150 : 158 730 159 emails
median character length - 1304 : 383 435 583 emails
Size: 80kb (size of "long" email in 2004):6 250 000 emails
Size: 59Kb (IDC 2006 estimate): 8 474 577 emails
Size: 20kb (size of "short" email in 2004): 25 000 000 emails
Size: 18.5kb (average size in 2001): 27 027 027 emails
Size: 14kb (average size of a webpage in 2000): 35 714 286 emails
Size: 6kb (size of spam in 2007): 83 333 334 emails

Guestimate based on AT&T data: 250 000 000 emails

>  it is fully customizable with themes, plugins, and tools.

In looking at that website, I didn't see anything about its ability to search the content of email.

Can one do boolean searches of the body of messages?
Can one do a regex search of the body of messages?

If so:
* how fast are the searches;
* what is the scope of the searches;

I did see that procmail can be used as a front end filter. To me that is a virtue, because procmail is the only email filtering client I've come across that can do literally anything and everything.

> Please let me know what you think!

None of the reviews I read delved into how well it scales, how much inbound/outbound email it can handle, or any other metrics that relate to performance functionality.

They either talk about it being a pretty picture, or being lightweight.
Neither of those inspire confidence in its ability to handle more than one email per second.

jonathon

---

### Post by jonathonblake on 2011-05-04
> **bergfly said:**
> I'd suggest that email is not the best method of organising the data you are trying to access.

It doesn't matter how the data is stored, or archived.
What matters is that it can be found when I need it.

> I'm only assuming that the mail you are getting comes with large attachments,
Maybe one 10MB attachment a week, and a 100MB attachment once a month.

Otherwise you are looking at maybe 100kb per email, if html, and much less if plain text.

> otherwise you are looking at simply unreadable volumes.

It is an unreadable volume.

Most of the time, the only time I read an email, is when I search the body for specific words, or phrases.

I'd be surprised if I opened 5% of the email I received.

>  This sort of volume scream database as the solution.

Suggestion?  

>  Sorry not to be helpful from a mail client perspective, 

I didn't think that changing email clients would help. OTOH, I don't know what will help.

> but if you have more details, maybe suggestions around other ways to organise the data would be useful.

I have no idea how many emails there are. Several of the "dump piles" contain more than 250K emails.  Things land up in them, because they don't fit the filters I have set up.   

The last time I counted, I had just over 5000 filter rules in thunderbird.

jonathon

---

### Post by dragonfly41 on 2011-05-04
> 
The last time I counted, I had just over 5000 filter rules in thunderbird.Perhaps you could benefit from a bayesian proxy .. a "learning" algorithm to drop email into appropriate boxes?

[EDIT]

[https://help.ubuntu.com/community/Privoxy](https://help.ubuntu.com/community/Privoxy)

---

### Post by jonathonblake on 2011-05-04
> **dragonfly41 said:**
> Perhaps you could benefit from a bayesian proxy .. a "learning" algorithm to drop email into appropriate boxes?

I was doing that with procmail a decade and a half ago. 


jonathon

---

### Post by bergfly on 2011-05-06
Jonathan

I'm simply intrigued why you are getting so much email, and if you are only reading 5% of it, why you are even keeping 95% of it?

Inbox zero perhaps?
[http://www.youtube.com/watch?v=z9UjeTMb3Yk]("http://www.youtube.com/watch?v=z9UjeTMb3Yk")

---

### Post by jonathonblake on 2011-05-06
> **bergfly said:**
> why you are even keeping 95% of it?

Call it industry tracking.

jonathon

---

### Post by keithpeter on 2011-05-08
Hello All

I'm amazed that Thunderbird or any desktop mail client can even scan that much e-mail.

I have no expertise with this at all, but I'd imagine a server side archive of some kind would be needed.

A quick Google came up with...

[http://www.enkive.org/](http://www.enkive.org/)

...which is open source and aimed at companies who need to search e-mail archives for evidential purposes. It looks like it backends off a mail server.

Let us know if you find a solution... fascinating problem.

---

### Post by jonathonblake on 2011-05-09
> **keithpeter said:**
> http://www.enkive.org/
...which is open source and aimed at companies who need to search e-mail archives for evidential purposes. It looks like it backends off a mail server.

I'll test it out later this month. I need to see how well it plays with Tryton. (And yes, these are both for my private, individual usage.)

jonathon

---

