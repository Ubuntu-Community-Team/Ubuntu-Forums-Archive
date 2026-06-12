---
title: "Gwibber and Facebook notifications"
date: 2012-03-02
forum: General Help
---

### Post by palimmo on 2012-03-02
Hello!
I'm experiencing some problems with Gwibber 3.3.2 in Ubuntu 11.10 64bit and my facebook account.

I don't receive any notice when I have a new notification in my account... but just the number of new friends' posts (when there are).

For example, in this moment I have a new notification in Facebook (probably a tag or an invitation) but, as you can see in the attached image, there's no sign in the Gwibber menu.

What's the problem?

---

### Post by palimmo on 2012-03-03
the image...

---

### Post by palimmo on 2012-03-03
Any idea?

---

### Post by raja.genupula on 2012-03-03
* Please dont bump so early , minimum give a time of 24 Hours for BUMP . 

ok while coming to your issue ,   you got anything after press F5 in Gwibber ?

---

### Post by palimmo on 2012-03-03
> **raja.genupula said:**
> * Please dont bump so early , minimum give a time of 24 Hours for BUMP . 

ok while coming to your issue ,   you got anything after press F5 in Gwibber ?

No.. just new friends' posts... but no that kind of notifications...(in this moment I can see in my facebook page 5 new notifications).

---

### Post by palimmo on 2012-03-03
> **raja.genupula said:**
> * Please dont bump so early , minimum give a time of 24 Hours for BUMP . 

ok. next time i'll wait at least 24 hours. :popcorn:

---

### Post by palimmo on 2012-03-04
And it doesn't notificate me new private messages, too.

---

### Post by raja.genupula on 2012-03-04
have you verified preferences ?

---

### Post by palimmo on 2012-03-04
> **raja.genupula said:**
> have you verified preferences ?
Yes.
I've tried both with "All messages" and "Mentions and Replies only".. but nothing...

---

### Post by palimmo on 2012-03-04
And this is the situation in my facebook account, regarding Gwibber access.

Is it the same for you?

---

### Post by palimmo on 2012-03-06
Can I force and try a previous version without removing the "ubuntu-desktop" package?

---

### Post by raja.genupula on 2012-03-06
is it fine with previous Gwibber versions ?

---

### Post by palimmo on 2012-03-06
> **raja.genupula said:**
> is it fine with previous Gwibber versions ?
I haven't tried.. because it asks me to remove ubuntu-desktop too... and honestly I'd like to avoid it.
How can I try it without messing up my ubuntu?

---

### Post by palimmo on 2012-03-06
Package version: 3.3.1+1234-oneiric1

---

### Post by raja.genupula on 2012-03-06
I heard Facebook gonna stop on march 15th ,  so i have stopped focus on Facebook .

---

### Post by palimmo on 2012-03-06
> **raja.genupula said:**
> I heard Facebook gonna stop on march 15th ,  so i have stopped focus on Facebook .

naaa [http://edition.cnn.com/2011/TECH/social.media/01/10/fb.shutdown.rumor.mashable/index.html](http://edition.cnn.com/2011/TECH/social.media/01/10/fb.shutdown.rumor.mashable/index.html)

---

### Post by raja.genupula on 2012-03-06
hmm ..so you're getting the same behaviour from the first time or from days (Gwibber/facebook)?

---

### Post by palimmo on 2012-03-06
> **raja.genupula said:**
> hmm ..so you're getting the same behaviour from the first time or from days (Gwibber/facebook)?

from the first time... few days ago. I haven't used Gwibber before.

---

### Post by raja.genupula on 2012-03-06
> **palimmo said:**
> And this is the situation in my facebook account, regarding Gwibber access.

Is it the same for you?

yeam all are same the only difference is App activity privacy is Public i have selected but i think thats not the reason . my gwibber with facebook working fine . its giving me all updates with update interval . 

ok try this 
```
sudo apt-get install --reinstall gwibber
```

---

### Post by palimmo on 2012-03-07
> **raja.genupula said:**
> yeam all are same the only difference is App activity privacy is Public i have selected but i think thats not the reason . my gwibber with facebook working fine . its giving me all updates with update interval . 

ok try this 
```
sudo apt-get install --reinstall gwibber
```

I did it.. but nothing.
I'm trying now with the version 3.2.1 (avoiding the other one proposed by the gwibber daily ppa)... but I haven't solved anything.

---

### Post by palimmo on 2012-03-07
> **raja.genupula said:**
> yeam all are same the only difference is App activity privacy is Public i have selected but i think thats not the reason . my gwibber with facebook working fine . its giving me all updates with update interval . 

ok try this 
```
sudo apt-get install --reinstall gwibber
```
mmh... do you have the python-facebook package installed?

---

### Post by palimmo on 2012-03-07
> **palimmo said:**
> mmh... do you have the python-facebook package installed?

I've installed it. But no success.
No new private messages are shown.

---

### Post by raja.genupula on 2012-03-07
are they showing even after some time duration ?

---

### Post by palimmo on 2012-03-07
> **raja.genupula said:**
> are they showing even after some time duration ?

Never.
Only the stream is update correctly.

---

### Post by raja.genupula on 2012-03-07
aah! this is makes me think more . 
look at the image , you also enable those things ? 

one more thing , if things are same to you also as you mentioned in the image , please remove your account and add it to Gwibber again .

---

### Post by palimmo on 2012-03-07
> **raja.genupula said:**
> aah! this is makes me think more . 
look at the image , you also enable those things ? 

one more thing , if things are same to you also as you mentioned in the image , please remove your account and add it to Gwibber again .

Yes, the options enabled are the same.
What should I do with my Twitter account? And why? (well.. my twitter account seems to work good, the problem is with the facebook one..)

---

### Post by raja.genupula on 2012-03-07
No , what i am saying is make a fresh start with facebook . I mean remove your facebook account from gwibber and from your facebook   list remove gwibber . and then again add it . this time make some focus on settings .

---

### Post by palimmo on 2012-03-08
> **raja.genupula said:**
> No , what i am saying is make a fresh start with facebook . I mean remove your facebook account from gwibber and from your facebook   list remove gwibber . and then again add it . this time make some focus on settings .

I did it. Without success.

---

