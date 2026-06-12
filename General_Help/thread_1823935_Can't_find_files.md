---
title: "Can't find files"
date: 2011-08-12
forum: General Help
---

### Post by PizzaLover101 on 2011-08-12
I dual boot windows and ubuntu 11.04. On my HD is windows and ubuntu part on my HD part external 500 gb Segate HD. I have files on the external hard drive that I would like to use in ubuntu, problem though that I can't find the files. I can find my windows files though. Any help?

---

### Post by raja.genupula on 2011-08-12
was it mounting and showing its used storage and all the details,

---

### Post by PizzaLover101 on 2011-08-13
Yes it was. It said it was mounted  and it said the total 500gb space.

---

### Post by varunendra on 2011-08-14
> **PizzaLover101 said:**
> I dual boot windows and ubuntu 11.04. On my HD is windows and ubuntu part on my HD part external 500 gb Segate HD. I have files on the external hard drive that I would like to use in ubuntu, problem though that I can't find the files. I can find my windows files though. Any help?
You mean you have installed Ubuntu on some partition of the external hard drive? If so, can you confirm whether the files and Ubuntu itself are on seperate partitions or on the same one?

If they are on the same partition, the files should be in root (/) and will have read-only permission for user.

If they are on different partitions and you still can't find the files, you should provide more info on your partitions like how and where you installed Ubuntu, where were the files before, etc.

[COLOR=DarkRed][B]
**Off-Topic**[/B][/COLOR]
Great avatar raja.genupula! My heartiest greetings for our 65th Indepence Day in one day advance:)
[IMG]http://i621.photobucket.com/albums/tt292/varunjnp/Flag.gif[/IMG]

---

### Post by PizzaLover101 on 2011-08-14
Not sure, I used the wubi installer, and I have part of the files on my HD, part on the external. I tried root but I didn't find anything.

---

### Post by bcbc on 2011-08-14
Alt-F2  /host
Ctrl+D to bookmark

---

### Post by PizzaLover101 on 2011-08-14
That worked! Thanks!!!!!

---

