---
title: "LAMP problem"
date: 2010-12-29
forum: General Help
---

### Post by nsathees on 2010-12-29
Hello,

I am developing Wordpress Templates and having trouble in Ubuntu.
I have developed partly in windows machine using XAMPP. There I can view the development via WordPress. But the same setup does not show up in Ubuntu.

I have read a lot how to manage php.ini and made alterations. But the theme doesn't even show up under WP appearance!

There are other php files works fine in windows+XAMPP but not even showing anything in ubuntu 10.10

I have enabled display_errors = On and so on.

What is wrong here!

Any help appreciated!

Happy New Year!

Thanks.

---

### Post by James78 on 2010-12-29
Have you restarted or reloaded apache after your edits? Either one should suffice.
```
sudo service apache2 restart
```
```
sudo service apache2 reload
```

---

### Post by nsathees on 2010-12-29
Yes I did.

---

### Post by James78 on 2010-12-29
Well, I don't know what to say. It could be a theme problem, or a completely different problem. Check your Apache error log (/var/log/apache2/error.log), it may help shed some light on this. Let me know if you find anything.

---

### Post by pqwoerituytrueiwoq on 2010-12-29
Did you install it correctly?
You should be able to get something from [http://127.0.0.1](http://127.0.0.1) if it is running
let me look up the command on my laptop for the app's for its gui
edit:
gksu /opt/lampp/lampp panel

---

### Post by nsathees on 2010-12-29
gksu /opt/lampp/lampp panel

nothing shows up.
I checked the folder and nothing in it!

---

### Post by nsathees on 2010-12-29
> **James78 said:**
> Well, I don't know what to say. It could be a theme problem, or a completely different problem. Check your Apache error log (/var/log/apache2/error.log), it may help shed some light on this. Let me know if you find anything.

I found nothing major problem. Only the favicon.ico missing error

---

### Post by pqwoerituytrueiwoq on 2010-12-30
> **nsathees said:**
> gksu /opt/lampp/lampp panel

nothing shows up.
I checked the folder and nothing in it!
where did you install lampp to?

---

