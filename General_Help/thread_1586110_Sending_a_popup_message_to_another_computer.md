---
title: "Sending a popup message to another computer"
date: 2010-10-01
forum: General Help
---

### Post by karthick87 on 2010-10-01
In windows we used to send a pop up message to another computer that is connected in home network using the following command,

```
Netsend [username] "message"
```

what is the equivalent command in ubuntu..?

---

### Post by Manifest on 2010-10-01
I think you'd need ssh
maybe not but Yeah, i dont know anything

---

### Post by luvshines on 2010-10-01
May you can use notify-send along with ssh if you have password

Or you can explore 'wall' command or 'write' command

---

### Post by pizza-is-good on 2010-10-01
> **getyourkarthick said:**
> In windows we used to send a pop up message to another computer that is connected in home network using the following command,

```
Netsend [username] "message"
```what is the equivalent command in ubuntu..?

I remember doing that. It was fun, and a good way to scare people :lolflag:
Good memories.
But they removed it in Vista and 7.

I don't think there is a way to do this in Ubuntu. It is definitely a security risk, imagine, someone could put a virus in the pop up...:(
So yea, you might have to SSH your way into the other computer, and even then, I wouldn't know how.

---

### Post by 2007mordor on 2011-04-07
if you have access to ssh you can try: 
ssh user@ComputerNameOrIP zenity --info --title 'some title' --text 'your message here' --display : 0

---

### Post by heatpumpcontrol on 2012-04-21
Found this to be the proper way...


[http://askubuntu.com/questions/31582/send-messages-between-2-ubuntu-pcs-net-send-style]("http://askubuntu.com/questions/31582/send-messages-between-2-ubuntu-pcs-net-send-style")

---

### Post by uRock on 2012-04-21
Necromancy = Thread Closed

---

