---
title: "Where does evolution store certificate information?"
date: 2011-06-07
forum: General Help
---

### Post by Irihapeti on 2011-06-07
I was troubleshooting an error with my email and in the course of it chose to ignore a faulty SSL certificate. (I've reported it to the ISP in question.)

Now that I want to remove that override command, I can't work out how to do it.

Can someone tell me where Evolution stores this setting so that I can remove it?

---

### Post by ubudog on 2011-06-07
Not sure, but check out the .evolution directory.

---

### Post by Irihapeti on 2011-06-07
I've had a look in the .evolution directory and tried removing 

secmod.db
key3.db
cert8.db
camel-cert.db

but when I try to send, it still goes straight to asking for the password without displaying the bad certificate message.

I suspect that evolution may cache things in a way that survives rebooting. Don't ask me to explain that - I just know that I was dealing yesterday with a caldav calendar that had been deleted but still loaded after reboot. :confused:

---

### Post by ubudog on 2011-06-07
I guess your best bet would be remove the configuration and starting over. 

Check out post 8 here:
[http://ubuntuforums.org/showthread.php?t=159407](http://ubuntuforums.org/showthread.php?t=159407)

---

### Post by Irihapeti on 2011-06-07
That will explain what happened with the calendar, I think.

However, I did it and it's still not showing the certificate error when I re-create the email account.

It's not hugely important for me, since evolution isn't my default email client. (I use thunderbird.) But it's still annoying me a bit, and it would be critical for some people.

---

### Post by ubudog on 2011-06-08
Hmm... try doing the previous post again, and then do this: (remove Evolution and reinstall it)

```
sudo apt-get purge evolution && sudo apt-get install evolution
```

---

### Post by Irihapeti on 2011-06-08
Thanks for the recommendation. However, the ISP has fixed the problem at its end now, and this means that I could do all that and not know whether it had worked or not.

If I do come across a solution to this, I'll come back and post it here. I did find that someone else had asked the same question elsewhere (can't remember where) and had got no reply.

---

### Post by ubudog on 2011-06-08
Well glad you got it working.  A bunch of people have asked the same thing on many forums.  Seems really hard to get rid of Evolution's config.

---

