---
title: "Constant wifi connection drops"
date: 2011-10-30
forum: General Help
---

### Post by Ertai87 on 2011-10-30
Hey all!  I've been having a bit of a problem with my wifi connection.  It seems that when I'm using it, it drops very frequently.  Unfortunately my router is messed up (it's in a different language and I can't get the character set to display properly) so I'm unable to check the logs to determine outside access, although it is WPA-PSK2 encrypted and my password is strong, so I doubt it's that.  Has anyone else had a problem with connections frequently dropping, and if so, what can I do?

My computer is a Dell Inspiron 6400.  I don't know if you need more information than that, but if you do, let me know.

Thanks.

---

### Post by coldraven on 2011-10-30
If you can find the correct screen in your router you could try and change the wi-fi channel, maybe your neighbour is using the same one.

Don't do this via wi-fi, use a network cable.

---

### Post by Ertai87 on 2011-10-30
Unfortunately the settings page for my router does not display in any discernable language, and the manual is in Korean.  Is there another way?

EDIT: Nevermind, I think I found it (luckily the Korean word for "Channel" is phonetically equivalent to the English word).  I changed the channel, we'll see if it helps.  If you don't hear back from me again, assume the problem is solved.

---

### Post by coldraven on 2011-10-31
I just found the command that I had saved the last time this topic appeared.
```
sudo iwlist scan
```  
Will scan wi-fi for reception details, then you should see what channels your neighbours are using. Obviously, set your router to use one that is free.
Please mark this tread as solved if that did the job.

---

### Post by Ertai87 on 2011-10-31
> **coldraven said:**
> I just found the command that I had saved the last time this topic appeared.
```
sudo iwlist scan
```  
Will scan wi-fi for reception details, then you should see what channels your neighbours are using. Obviously, set your router to use one that is free.
Please mark this tread as solved if that did the job.

Hm.  Apparently nobody was using the channel I was on before, but now I have a channel conflict and the problem seems to be solved.  Strange, but it seems to be working now anyway.

---

