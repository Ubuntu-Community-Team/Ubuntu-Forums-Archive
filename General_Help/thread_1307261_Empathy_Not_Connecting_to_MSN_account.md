---
title: "Empathy Not Connecting to MSN account"
date: 2009-10-31
forum: General Help
---

### Post by AlexJudoka51 on 2009-10-31
Hi, I have just installed 9.10 and I love it, except for that problem, I can't log in into my @hotmail.com account. Something that I'm missing?

---

### Post by odinbaal on 2009-10-31
Same here...

---

### Post by scouser73 on 2009-10-31
I don't use Empathy, but looking at Pidgin now for the server details:

Server: messenger.hotmail.com

Port: 1863

HTTP Method Server: gateway.messenger.hotmail.com


I hope that helps.

---

### Post by AlexJudoka51 on 2009-10-31
Weird, now is working, but thanks anyway for the replies :) I will leave this thread as is for anyone who has the same problem.

---

### Post by jtpoole99 on 2010-06-19
The settings below match my settings in Empathy on Ubuntu 10.04, but I'm still not able to connect to my MSN account.  Each time I try to connect, I get a Network Error.  So is there another reason why Empathy isn't connecting?

:confused:

> **scouser73 said:**
> I don't use Empathy, but looking at Pidgin now for the server details:

Server: messenger.hotmail.com

Port: 1863

HTTP Method Server: gateway.messenger.hotmail.com


I hope that helps.

---

### Post by Linuxforall on 2010-06-19
Empathy is working fine here with MSN, gotta be local network issue, I am currently in India.

---

### Post by jtpoole99 on 2010-06-19
Well I don't feel it's a local network issue since I can log into other messaging platforms without any problem.  My MSN log-in information is correct and yet there still isn't a connection to the messaging protocol. I don't know about the others, but for me, it's not a local network issue.  So let's try again.

:mad:

---

### Post by rrebel on 2010-08-18
Solution (worked for me..):

[http://www.ubun2.com/question/283/network_error_connecting_msn_using_empathy_http_method_karmic_910](http://www.ubun2.com/question/283/network_error_connecting_msn_using_empathy_http_method_karmic_910)

---

### Post by zerek on 2010-10-20
pidgin with direct and private proxy worked. 
Might be some problems with a buildt-in proxy setting for empathy.

(location: norway, trondheim)

---

### Post by frogotronic on 2010-10-21
> **AlexJudoka51 said:**
> Hi, I have just installed 9.10 and I love it, except for that problem, I can't log in into my @hotmail.com account. Something that I'm missing?

```
sudo apt-get remove telepathy-butterfly
```

Restart Empathy & re-create your MSN account

- CH

---

### Post by koleoptero on 2010-10-21
> **cement_head said:**
> ```
sudo apt-get remove telepathy-butterfly
```

Restart Empathy & re-create your MSN account

- CH

A gazillion of thanks for this. I had the same problem and it worked. :KS

---

### Post by abdulmajid on 2010-10-21
Thanks, It worked for me. :)

---

### Post by pcm_man on 2010-10-21
Thank you so much.  This easy removal of a single piece of software totally worked!!!

Can anyone explain WHY this works?  After all this is a Ubuntu supported and standard installation component!

---

### Post by prince_niceguy on 2010-10-21
> **cement_head said:**
> ```
sudo apt-get remove telepathy-butterfly
```

Restart Empathy & re-create your MSN account

- CH

thanks so much... it did the trick for me and it worked...

---

### Post by allandk78 on 2010-10-22
This helped me on ubuntu 10.10 as well.

Major issue.

Thanks.

---

### Post by irvingswiftj86 on 2010-10-22
Cheers mate, that did work. I can't believe this bug has slipped through testing!

---

### Post by gabbace on 2010-10-22
Thanks,
it works also on Ubuntu 9.10

---

### Post by rocktorrentz on 2010-10-22
Thanks very much. :)

---

### Post by Segofam on 2010-10-22
> **cement_head said:**
> ```
sudo apt-get remove telepathy-butterfly
```Restart Empathy & re-create your MSN account

- CH

I did this an now it doesn't even try to connect!!!

:(

Do you think I need to re-install it?

Gone and back again...

I did a restart on the computer as a last resort, and it now works fine :)

---

### Post by AXe Naqvi on 2010-10-22
Great... was searching for the solution.. works like a charm..
Cheers mate..

---

### Post by frogotronic on 2010-10-22
> **pcm_man said:**
> Thank you so much.  This easy removal of a single piece of software totally worked!!!

Can anyone explain WHY this works?  After all this is a Ubuntu supported and standard installation component!

telepathy-butterfly has a bug in it - or rather MSN changed/changes their protocol from time to time and for some people its an issue.  In fact, it so happens that its the order in which the empathy components are installed that make the difference.  You might find that re-installing (i.e. installing telepathy-butterfly last) now will not crash empathy with MSN.

- CH    :guitar:

---

### Post by emilywind on 2010-10-23
An update was recently added to fix this issue, at least for Maverick. It's an update for a python MSN client, which I imagine is used by telepathy-butterfly.

No sort of reinstallation was required, I just ran the update manager. Cheers. :)

---

