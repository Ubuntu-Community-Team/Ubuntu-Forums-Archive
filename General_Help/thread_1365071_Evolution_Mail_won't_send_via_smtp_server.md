---
title: "Evolution Mail won't send via smtp server"
date: 2009-12-26
forum: General Help
---

### Post by oldtraveler on 2009-12-26
I can receive mail OK on 4 different email accounts, but when I configure the smtp servers for those accounts, evolution will not send.  For my two hotmail accounts I used these directions: [http://wiki.answers.com/Q/What_is_the_POP_server_for_hotmail](http://wiki.answers.com/Q/What_is_the_POP_server_for_hotmail).  For my pop accounts I used the standard smtp servers and settings that I use on Windows Live Mail except I can't find a way to set the port numbers. 

I tried Sendmail, but I got a message about a broken pipe.

Solved:
Hotmail pop will work with a smtp server if the encryption is set to TSL. and authorization to "login".

My other pop mail works with no encryption and autorization to "login".

---

### Post by dcstar on 2009-12-27
> **oldtraveler said:**
> I can receive mail OK on 4 different email accounts, but when I configure the smtp servers for those accounts, evolution will not send.  For my two hotmail accounts I used these directions: [http://wiki.answers.com/Q/What_is_the_POP_server_for_hotmail](http://wiki.answers.com/Q/What_is_the_POP_server_for_hotmail).  For my pop accounts I used the standard smtp servers and settings that I use on Windows Live Mail except I can't find a way to set the port numbers. 

I tried Sendmail, but I got a message about a broken pipe.
[B]
Solved:[/B]
Hotmail pop will work with a smtp server if the encryption is set to TSL. and authorization to "login".

My other pop mail works with no encryption and autorization to "login".

See below.

---

### Post by zaphod777 on 2009-12-27
Also a lot of ISP's will not allow you to use a different smtp server on port 25. So you may need to call them and ask them for their SMTP server and a username and pw to use on it(usually the free email account they give you). 

The poster above me's solution should work too if that is the case for hotmail then it is not using port 25 and you are in the clear.

---

