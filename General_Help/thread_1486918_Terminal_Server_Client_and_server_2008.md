---
title: "Terminal Server Client and server 2008"
date: 2010-05-18
forum: General Help
---

### Post by acarter on 2010-05-18
Hey guys, ok so I love Ubuntu and last night I wiped crappy windows 7 off my laptop and installed and customised a beautiful Ubuntu 9 OS ( I tried the new 10.04 first but it had some issues for me ).

Now, up here at work we got a Domain Controller that is running windows server 2008, I need to be able to RDP into it and mess with it, I tried to use the Terminal Server Client that comes with Ubuntu, and I can see the login screen just fine, but when I try to log in it says incorrect password and wont go through.

Just to make sure it was not my account that was the issue, I went to my boss and used his computer (a MAC running OSX) and I was able to get into the same server with the same credentials, so it has something to do with my computer not my account.

Do any of you have any ideas on what the problem could be? Thanks so much, you are all the greatest!

---

### Post by Chesamo on 2010-05-18
Which Ubuntu 9.x are you using? 9.04 or 9.10? (The numbers are significant.)

---

### Post by CharlesA on 2010-05-18
I used Ubuntu 10.04 to connect to a VM running Server 2008 R2 that is a domain controller.

Here is what I had to fill out:

[IMG]http://img200.imageshack.us/img200/7466/ubuntu1004.png[/IMG]

The domain is "serv"

Testing with 9.10 now.

Works with 9.10.

---

### Post by acarter on 2010-05-18
OK wow, Im amazed at my own stupidity, I put our Fully Qualified Domian Name in the box for the domain and it works now, sorry to waste your time i thought i did that before i posted here.

Anyway your post was very helpful, thank you so much for posting! Issue resolved.

---

### Post by acarter on 2010-05-18
> **Chesamo said:**
> Which Ubuntu 9.x are you using? 9.04 or 9.10? (The numbers are significant.)

Ubuntu 9.10 and the issue was user error (lol) didnt have the domain right

---

### Post by CharlesA on 2010-05-18
Domain names can be confusing. :) Glad you got it working.

Please mark the thread as solved from the thread tools menu.

---

