---
title: "This message pops up when I try to run Update Manager."
date: 2010-10-17
forum: General Help
---

### Post by TheNerdAL on 2010-10-17
[IMG]http://i.imgur.com/zHE1U.png[/IMG]
That's the message that pops up when I try to run Update Manager. I noticed that I can't open Ubuntu Software Center either.

How can I fix this? 

Thanks.

---

### Post by sohlinux on 2010-10-17
I had same problem recently just run sudo apt-get update , it should do the trick

---

### Post by TheNerdAL on 2010-10-17
> **sohlinux said:**
> I had same problem recently just run sudo apt-get update , it should do the trick

Nope. 
[IMG]http://i.imgur.com/WCaF2.png[/IMG]

---

### Post by silbak04 on 2010-10-17
Before deleting that file, read me your output for:

```

$ cat /etc/apt/sources.list.d/ronmi-wallbox-maverick.list

```If there seems that there is nothing too important, then go ahead to the next step:

Try deleting that file in that directory. I don't think you need that. So do:

```

$ sudo rm /etc/apt/sources.list.d/ronmi-wallbox-maverick.list

```then try:

```

$ sudo apt-get update 

```

---

### Post by TheNerdAL on 2010-10-17
> **silbak04 said:**
> First try deleting that file in that directory. I don't think you need that. So do:

```

$ sudo rm /etc/apt/sources.list.d/ronmi-wallbox-maverick.list

```

then try:

```

$ sudo apt-get update 

```

Thanks, it worked! :D

---

