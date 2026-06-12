---
title: "adduser access"
date: 2009-10-19
forum: General Help
---

### Post by habuchas on 2009-10-19
I am an old (75) Newbee having a challenge accessing an added user through the [http://URL/~username](http://URL/~username) route. I have Ubuntu 9.04 server and desktop installed on an additional computer on my home network and can get to the /home/username/public_html using WinSCP or Putty from my Windows computer. I can get to the /var/www directory through the [http://URL](http://URL) path but none of the added users using the ~(tilde) route. I am attempting to try my hand at some html for individual user. Is there some switch I have to turn on to enable access to users using the url method?
Any assistance would be appreciated.
habuchas....

---

### Post by spiderbatdad on 2009-10-19
file:///home/user
is this what you're looking for?

---

### Post by habuchas on 2009-10-19
> **spiderbatdad said:**
> file:///home/user
is this what you're looking for?
In each  /home/user directory I have put a public_html directory and a small index.html file to show I have located the correct user. If I can access it through the [http://URL/~username](http://URL/~username) from my Windows machine browser it should show "your are in username".  I can get the the /var/www/index.html just using the URL alone.
habuchas........

---

### Post by spiderbatdad on 2009-10-19
It sounds like you need apache to point to each directory in individual vhost sections.

---

### Post by habuchas on 2009-10-19
And that is done How?
habuchas.....

---

### Post by spiderbatdad on 2009-10-19
that is done in apache's virtual host file called, /etc/apache2/sites-available.

There is an old tutorial I wrote for myself a couple of years ago here: [http://spiderbatdad.wordpress.com/basic-apache2-how-to/](http://spiderbatdad.wordpress.com/basic-apache2-how-to/)
There are many others and better ones available on the web.

---

### Post by habuchas on 2009-10-19
Thank you!  I am presently looking at the link. I hope to have the problem solved.  If not I will re-post.
habuchas........

---

