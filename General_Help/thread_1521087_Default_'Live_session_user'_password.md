---
title: "Default 'Live session user' password"
date: 2010-06-30
forum: General Help
---

### Post by Oven Glove on 2010-06-30
I'm using 10.04 lucid lynx on a usb stick and it automatically logs in with that account. I wanted to change the account's settings, name ans password so that I can use it at login, but I don't know what the original password is to change it.

Any help is appreciated.
Thanks in advance, Owen.

---

### Post by yeleek on 2010-06-30
isn't the pw blank by default?

---

### Post by C.S.Cameron on 2010-06-30
I recall that you used to be able to add accounts to a persistent disc image install but I haven't been able to do it lately.
You can do a full install to flash drive which will take care of the problem.

---

### Post by octaedro7 on 2010-09-06
> **yeleek said:**
> isn't the pw blank by default?

That's the actual live user password!

Thanks for that one

---

### Post by octaedro7 on 2010-09-09
Problem now is that the system doesn't allow to either change the live user password or delete the live user once you have created your own one.
I haven't found info on how to accomplish either of them.

Any one here?

Thanks in advance

---

### Post by tg3793 on 2010-09-09
Be careful what you do here :-) ... I did change the password successfully and thought I had changed the username successfully. 

But what I didn't realize is that the username that I had changed was some sort of pseudo username and I had inadvertently locked myself out of my USB stick until I figured out the default username is "ubuntu" LOL

_Ok I'm not booted into my Lucid USB stick right now so I have to go by memory. _There is a **drop down menu under the administration options** at the top and one of those features will allow you to add an "ask for password" option when it boots up. It is there that it will ask you to enter a password. And yes I think the previous password will be empty.

I'll tell you more once I boot up to my Ubuntu USB again. Might be a couple of days though so I hope someone else might flesh out my answer here. ... I'm currently trying to figure out another problem I'm having where I want to transfer everything from my one gig persistent image to a new four gig persistent image.

---

### Post by viralmeme on 2010-09-09
> **Oven Glove said:**
> I'm using 10.04 lucid lynx on a usb stick and it automatically logs in with that account. I wanted to change the account's settings, name ans password
That account is hardwired into the CD image, the simplest solution is to add a new user and set that to [auto Login]("http://www.killertechtips.com/2008/04/09/how-to-auto-login-to-ubuntu/")

---

### Post by tg3793 on 2010-09-15
> **viralmeme said:**
> That account is hardwired into the CD image, the simplest solution is to add a new user and set that to [auto Login]("http://www.killertechtips.com/2008/04/09/how-to-auto-login-to-ubuntu/")

That sounds pretty good, thank I'll try it.

---

