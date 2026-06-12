---
title: "F-spot send by mail to thunderbird results in no attachment"
date: 2009-10-23
forum: General Help
---

### Post by paul1080 on 2009-10-23
Hi all,

I'm very new but ran a search on this and could not find a solution.

I'm using Jaunty with F-spot 0.5.0.3 and Thunderbird 2.0.0.23. 

When I use the "send by mail" feature in F-spot, it generates a new message in thunderbird subject "my+photos", but does not attach my photo to the email.

Is there a way to remedy this? 

Paul

---

### Post by cscj01 on 2009-11-25
I am having the same problem under [ubuntu] Karmic with F-Spot 0.6.1.5 and Thunderbird 2.0.0.23.

---

### Post by cscj01 on 2009-11-25
I just found my problem.  The preferred application for e-mail was set to Mozilla Thunderbird.  I changed that to Thunderbird, and it now works as it should.

---

### Post by el cameleon on 2010-01-02
I have a similar problem, F-Spot create a message in Thunderbird with invalid attachment path, which result in an error when trying to save or send the message.
I assume that I have correctly configured Thunderbird in my preferred application, because it works if I use "Send to" in nautilus...

---

### Post by el cameleon on 2010-01-02
I have found why: [https://bugs.edge.launchpad.net/ubuntu/+source/f-spot/+bug/112684](https://bugs.edge.launchpad.net/ubuntu/+source/f-spot/+bug/112684)

Unfortunately, no workaround for the moment... I will maybe consider to give picasa a try...

---

### Post by mr_bijae on 2010-03-06
> **cscj01 said:**
> I just found my problem.  The preferred application for e-mail was set to Mozilla Thunderbird.  I changed that to Thunderbird, and it now works as it should.
 
Thank you for this post, it was very helpful. A note to others this change is made at System / Preferences / Preferred Applications

---

### Post by el cameleon on 2010-03-07
Sorry but it doesn't work for me: I stll got an error message when the mail is send: > impossible to open the temporary file xxx\xxx.jpg. Look at your temp folder parameters.

---

