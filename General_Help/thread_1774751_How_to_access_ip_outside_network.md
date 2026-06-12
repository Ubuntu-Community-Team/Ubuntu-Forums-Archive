---
title: "How to access ip outside network"
date: 2011-06-03
forum: General Help
---

### Post by baligena on 2011-06-03
How can I access my ip address of my server on the internet outside my network

---

### Post by lmarmisa on 2011-06-03
> **baligena said:**
> How can I access my ip address of my server on the internet outside my network

Do you know the IP address of your server? What kind of service do you wish to use?.

---

### Post by baligena on 2011-06-03
yes i have a static ip address.  i have a godaddy domain name

---

### Post by Habitual on 2011-06-04
Open a terminal and type 
```
host domain.com
```

Result:
domain.com has address 66.150.120.145

Substitute your domain name for domain.com

---

### Post by mbeach on 2011-06-12
You are likely behind a router of some sort at your place, so I suspect you need to tell that router to redirect or forward requests on your ip address, port 80 to your server which likely has an local ip address.

The method to do this varies depending on your router but typically under port forward, or port redirect or something along those lines. Which brand and model router do you have?

You mentioned in your pm that you are using GoDaddy; be sure to have an ANAME record there in their control panel pointing to your static ip.


edit:
grabbing from [http://www.google.com/support/a/bin/answer.py?hl=en&answer=47610](http://www.google.com/support/a/bin/answer.py?hl=en&answer=47610), the steps to find that ANAME record may be in the area of (but you want to point to an ip, not an alias):
# Log in to your account at [www.godaddy.com](www.godaddy.com) by clicking the My Account tab.
# Under the Domains header, find the domain you're using. Click (Advanced Details) to the right of this domain.
# Under the DNS Manager header, click Launch.

---

