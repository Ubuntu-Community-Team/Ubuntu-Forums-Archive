---
title: "Virtual Domains on Apache2"
date: 2011-10-11
forum: General Help
---

### Post by Zidaps on 2011-10-11
Hi, 

I am running a few websites off of my physical server. They are being run virtually. So in /var/www  i have symbolic links to where the actual sites reside.

Lets say I am running 3 sites:

example1.com
example2.com 
example3.com

Now I registered these with godaddy and have them pointing to my ip address. So If i put [www.example1.com]("http://www.example1.com") it takes me to the site - [www.example2.com]("http://www.example2.com") etc etc.. will get me where I need to be. 

However, if i forget to type in the www it takes me to the /var/www folder and pulls up the usual server working index.html file thats in /var/www

So here's the question. How do I get it to route to [www.example1.com]("http://www.example1.com") when I just type in example1.com and at the same time be able to route to [www.example2.com]("http://www.example2.com") when I just type example2.com in the browser? same for example3 or course...

I tried changing the link in godaddy as well as the files in /etc/apache2/sites-available and it allows me to make the change so that if I put in example1.com it brings me to example1.com straight away. But that's no good, because it leaves out the www.

How do I get multiple virtually hosted domains to be redirected to their www. folder when the URL is typed in the browser omitting the www. part?? :confused:

Thanks...

---

### Post by SeijiSensei on 2011-10-11
1)  Make sure domain.name has an A record that points to your server just like [www.domain.name](www.domain.name) does.

2)  Add a "ServerAlias" directive to the virtual host definitions like this:

```

<VirtualHost *:80>
ServerName     www.domain.name
ServerAlias    domain.name
[etc.]
</VirtualHost>

```

---

### Post by Zidaps on 2011-10-11
Adding the line below did the trick!! Thank you !! 

> ServerAlias    domain.name

:guitar:

---

