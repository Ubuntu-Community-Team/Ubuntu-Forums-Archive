---
title: "Bash script to log into website"
date: 2009-09-02
forum: General Help
---

### Post by paal on 2009-09-02
I'm trying to make a bash script that's supposed to log in to a web page and download some information. However I keep getting a html-file telling me that my browser doesn't support cookies. The wget-line I'm trying to use is 
```
wget --save-cookies cookies.txt --keep-session-cookies --post-data="username=foo&password=bar" "http://form-action-url/
```
I've tried similar things with cURL too, but without any luck. What should I do to fix the cookies-problem?

---

### Post by metalx1000 on 2009-09-06
Try cURL.

This is how I login to facebook

```
curl -A "Mozilla/4.73 [en] (X11; U; Linux 2.2.15 i686)" \
--cookie cjar --cookie-jar cjar \
--data "email=myemail@mail.com" \
--data "pass=mypassword" \
--data "login=Login" \
--location "https://login.facebook.com/login.php?login_attempt=1">/tmp/tmp.html


```

The "-A" switch changes the user agent and makes the website think you're using firefox.  You may not need it for your site, but it doesn't hurt to have it in there.  

The output files is sent to "/tmp/tmp.html"
but you can change that.

---

### Post by bear24rw on 2009-09-06
> **metalx1000 said:**
> Try cURL.

This is how I login to facebook

```
curl -A "Mozilla/4.73 [en] (X11; U; Linux 2.2.15 i686)" \
--cookie cjar --cookie-jar cjar \
--data "email=myemail@mail.com" \
--data "pass=mypassword" \
--data "login=Login" \
--location "https://login.facebook.com/login.php?login_attempt=1">/tmp/tmp.html


```

The "-A" switch changes the user agent and makes the website think you're using firefox.  You may not need it for your site, but it doesn't hurt to have it in there.  

The output files is sent to "/tmp/tmp.html"
but you can change that.

What do you use that for?

---

### Post by paal on 2009-09-07
> **metalx1000 said:**
> 
The "-A" switch changes the user agent and makes the website think you're using firefox.  You may not need it for your site, but it doesn't hurt to have it in there. 
Works like a charm. Thank you so much!

---

### Post by metalx1000 on 2009-09-07
> **bear24rw said:**
> What do you use that for?

That's just part of a script I created to grab some info from my Facebook and display it on my Neo FreeRunner.  I just displayed the part of the script that would help paal out.

[http://www.bashscripts.info/]("http://www.bashscripts.info/")

---

