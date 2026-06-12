---
title: "fetchyahoo to gmail?"
date: 2006-03-22
forum: General Help
---

### Post by buzst on 2006-03-22
Has anyone sucessfully setup fetchyahoo to forward yahoo emails directly to gmail? How? Currently it will log into yahoo, count the message headers then hang. I'm thinking that maybe it cannot deal with an external smtp server (gmails or my isp) but would like more feedback prior to setting one up on my system.
Thanks in advance...

---

### Post by astronerd on 2006-03-22
I tried to set this up a while ago and got the same results you were getting.  Its very annoying because I would like to use Evolution to get my yahoo mail, but I dont want to pay for the POP service from yahoo.  So if anyone has it working now can you please explain how?

---

### Post by NoNo_231 on 2006-03-22
Did you activate the POP3 service? You have to go to settings of your e-mail account, and then to the paragraph saying about POP. There you will find instructions. You can either have POP3 access(say evolution, or thunderbird - it has instructions how to set up the client) or to sychronize (if I am not mistaking with other e-mail server). The same way goes for g-mail too.

Both don't use the default settings for e-mail clients so you have to spent some time to see how the clients must be configured.

---

### Post by astronerd on 2006-03-22
Thanks, but thats not exactly the problem.  I already have gmail working with POP and evolution.  The thing is that yahoo makes you pay for POP acess from them(at least in the US) so I cant just turn on POP access for yahoo and have it go to evolution.  I think that fetchyahoo goes around this and can access it/send it to another email account, ie gmail, so that I Could get my "forwarded" yahoo mail through my free POP gmail account.  So the OP and I are trying to set up fetchyahoo to do this, which is a problem.....

---

### Post by NoNo_231 on 2006-03-22
Don't know that. Yahoo didn't ask me to pay for POP3 access, it just forced me to check some advertisement messages that I will like to accept. I selected one or two, but never had one in my inbox. I am not in the US however. I don't know if it is different there.

---

### Post by buzst on 2006-03-22
everybody, thanks for the quick reply - I got it to work.  The issue was that the version of fetchyahoo in the repo was not compatable with the current version of yahoo mail. To make it  work I downloaded the current version from the fetchmail website, extracted it into a new directory, then replaced the old fetchyahoo that synaptic had placed in /usr/bin with the new one.
fetchmail does allow me to use the google smtp server as the out going server (I used gsmtp57.google.com but there are many others). my yahoo mail is now in gmail -way cool...

---

