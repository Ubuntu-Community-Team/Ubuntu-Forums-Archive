---
title: "IP address detection script"
date: 2010-10-24
forum: General Help
---

### Post by karthick87 on 2010-10-24
Do anyone have IP address detection script like the one you see in this [webpage]("http://aruljohn.com/info/howtofindipaddress/")

---

### Post by Ahava591 on 2010-10-24
> **getyourkarthick said:**
> Do anyone have IP address detection script like the one you see in this [webpage]("http://aruljohn.com/info/howtofindipaddress/")
I'm not sure what you're asking for.
What is it exactly that you're trying to do?

---

### Post by karthick87 on 2010-10-24
Just i want to know the actual ip from where the mail has been sent.

---

### Post by HermanAB on 2010-10-24
Just look at the headers of the email.  It will have all the IP addresses of all the servers that the message bounced through. Any email client can show the headers, but they are not normally shown since they are only useful for debugging mail problems.

---

### Post by karthick87 on 2010-10-24
Do anyone have perl script for that..?It will make the work  easier like the one you see in the website..

---

### Post by Ahava591 on 2010-10-24
Why don't you just use the website, then?

---

### Post by amauk on 2010-10-24
Extremely rough, but this just outputs the last "Received: from" line from an email

```
cat my_email | grep '^Received: from' | tail -n 1
```

---

