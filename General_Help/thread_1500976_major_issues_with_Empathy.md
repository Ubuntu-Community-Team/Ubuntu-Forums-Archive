---
title: "major issues with Empathy"
date: 2010-06-03
forum: General Help
---

### Post by thelenko on 2010-06-03
Ever since Empathy was made the default IM client of Ubuntu I have had major issues with it.

It is a complete disaster.  It sometimes does not receive messages, sometime it does not send.  Sometimes messages appear twice, sometimes they appear out of order.  Sometimes sending a message causes the chat window to close, sometimes the entire program crashes.  I have also had some pretty bizarre GUI mishaps.  Such as the client list duplicating itself into a message window, or the message window going blank after doing highlighting text.

Does anyone else experience all or a subset of these problems?  Considering it is the default Im client, you would think it would be very polished (or at least functional).  At first I thought maybe it was my computer, but I have experienced the same issue with ubuntu running on my desktop, and in a virtual machine (parallels) on my laptop.

Any help/insight would be appreciated!  I would much like to get Empathy working as the gnome integration and adium theme support sounds awesome!

Thanks :)

---

### Post by Serpher on 2010-06-03
I've had all those problems too, and I guess it's just terrible coding. I fixed it using these commands:

```
sudo apt-get remove empathy
sudo apt-get install pidgin
```

---

### Post by kiddykoff on 2010-06-03
> **Serpher said:**
> I've had all those problems too, and I guess it's just terrible coding. I fixed it using these commands:

```
sudo apt-get remove empathy
sudo apt-get install pidgin
```

lol, but seriously does Empathy have any good things about it?

---

