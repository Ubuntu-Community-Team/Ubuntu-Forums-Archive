---
title: "running PHP scripts on localhost"
date: 2012-02-22
forum: General Help
---

### Post by steveredshaw on 2012-02-22
I am learning how to create and use php scripts on my Ubuntu laptop, but have come up against a brick wall - my web browser will not run a .php file, it asks what should be done with it - ie open it with gedit or save it

I have installed LAMP, which I understand is the Apache and MySql package which will run php scripts

the localhost directory is /var/www/ inside of which is index.html and 2 simple php scripts

if I enter [http://localhost](http://localhost) in my browser the index.html file opens telling me the web server software is running, but [http://localhost/hello.php](http://localhost/hello.php) (you can guess what that is meant to do!) will not run

having done a bit of roooting around on the web I have gleaned that I may have to edit the httd.conf file which is in /etc/apache2/ - this file has no content as yet, but I am not sure what to put in it - the information I have found seems to be relevant to a different version of PHP and possibly a different installation location

if anyone can lead me on from here, with particular reference to Ubuntu, I would very grateful...

*(incidentally the hello.php file will run when I upload it to my web host, as of course it should do, but i would like to learn to create and test out PHP scripts on my own computer)*

---

### Post by roelforg on 2012-02-22
Try running:
```

sudo a2enable php5

```

---

### Post by gsgleason on 2012-02-22
I also find running the script with the php cli useful.

php file.php

---

### Post by steveredshaw on 2012-02-22
thanks but...

```
sudo: a2enable: command not found
```

---

### Post by steveredshaw on 2012-02-22
> I also find running the script with the php cli useful.

php file.php

sorry not sure what this means exactly!!

---

### Post by scwizard on 2012-02-22
Run this:
```
sudo a2enmod php5
```

Unrelated note:
Please test things a bit before you post roelforg. You're making the rest of us look bad.

---

### Post by roelforg on 2012-02-22
```

apt-get install apache2-utils php5 php5-cgi php5-cli

```try your php file again afterwards.

---

### Post by steveredshaw on 2012-02-22
this> sudo a2enmod php5
provokes
```
Module php5 already enabled
```

---

### Post by roelforg on 2012-02-22
> **steveredshaw said:**
> this
provokes
```
Module php5 already enabled
```
Tried the install command from my last post?

EDIT: Also, you might want to check up on launching CGI progs as that is how apache will detect them.

---

### Post by scwizard on 2012-02-22
> **steveredshaw said:**
> this
provokes
```
Module php5 already enabled
```
```
sudo /etc/init.d/apache2 restart
```

Try it after that. Is it working?

---

### Post by scwizard on 2012-02-22
> **roelforg said:**
> EDIT: Also, you might want to check up on launching CGI progs as that is how apache will detect them.
Jesus he's not trying to use CGI, he's trying to run php with modphp. That's why the php5 module is enabled.

Please stop confusing this poor guy. If you don't know what you're talking about post in another thread.

---

### Post by steveredshaw on 2012-02-22
:D
but this
> apt-get install apache2-utils php5 php5-cgi php5-cli
has done the job, my first php script works - now onwards and upwards

thank you folks - always there when I need you...

---

### Post by roelforg on 2012-02-22
> **scwizard said:**
> Jesus he's not trying to use CGI, he's trying to run php with modphp. That's why the php5 module is enabled.

Please stop confusing this poor guy. If you don't know what you're talking about post in another thread.
My apache won't run php progs without cgiexec enabled.
Otherwise i get 403 errors (yes, permissions are set correctly).
But it could also be the mix of the environment settings.
I don't know.
I just posted what i needed to do to get it running on my system.
It may or may not be the right way, i just worked though.

---

### Post by scwizard on 2012-02-22
> **roelforg said:**
> My apache won't run php progs without cgiexec enabled.
Proof that you're not qualified to give apache related advice.

---

### Post by roelforg on 2012-02-22
> **steveredshaw said:**
> :D
but this

has done the job, my first php script works - now onwards and upwards

thank you folks - always there when I need you...
See ya!

---

### Post by roelforg on 2012-02-22
> **scwizard said:**
> Proof that you're not qualified to give apache related advice.
See remainder of post.

---

