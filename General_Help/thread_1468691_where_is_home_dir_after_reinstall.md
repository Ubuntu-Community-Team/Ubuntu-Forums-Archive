---
title: "where is home dir after reinstall"
date: 2010-05-01
forum: General Help
---

### Post by rcayea on 2010-05-01
I have found my home directory after I reinstalled Lucid today. The thing is, is I click on my home directory in nautilus and it only has the standard startup folders. I clicked on my hard drive where the home partition is and everything is there. How do I move or substitute the home partition to when I click on my home partition it shows up?

Thanks,
Randy

---

### Post by Kilz on 2010-05-01
[Let me google that for you]("http://lmgtfy.com/?q=ubuntu+mount+home+partition")

---

### Post by oldfred on 2010-05-01
During the install when you already have a /home you have to set up your partitions for root & swap in advance and use manual install so you can choose the mount points. When you choose /home partition you make sure not to check the format box.

It may be easier to reinstall as that is very quick. You can follow the directions for moving home, you just have done all the first part of copying to a new partition and only have to complete the rest.

I used this to move home:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
Sometimes there are dmrc errors or permission errors and this has how to correct them:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

---

### Post by rcayea on 2010-05-01
Thank you, oldfred. I am assuming that the letmegooglethatforyou was not sarcasm seeing as how this is where people go to get help. So, thank you.

---

### Post by Kilz on 2010-05-04
> **rcayea said:**
> Thank you, oldfred. I am assuming that the letmegooglethatforyou was not sarcasm seeing as how this is where people go to get help. So, thank you.

Not sarcasm at all, just pointing you to a common source most people answering questions, and long time Linux users use, Google.

---

