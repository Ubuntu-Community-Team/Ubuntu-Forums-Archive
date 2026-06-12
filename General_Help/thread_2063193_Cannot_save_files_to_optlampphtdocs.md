---
title: "Cannot save files to /opt/lampp/htdocs"
date: 2012-09-26
forum: General Help
---

### Post by thePHPdev on 2012-09-26
I have even done:

```

$ chmod -R 777 /opt/lampp/htdocs

```Multiple times, I have also tried re-installing XAMPP (LAMPP). But to no avail.

I have also tried many other permissions work arounds, but again, to no avail.

However I can save files with gedit with:

```

$ sudo gedit

```But I do not want to sudo an editor every time. It's just silly.

I have been trying for days. And I can't do it. Please can I have a solution?

PS: I have attached the error I get.

---

### Post by thePHPdev on 2012-09-26
Sorry to bump so soon, But I really need an answer, I have projects to work on.

---

### Post by Lars Noodén on 2012-09-26
XAMPP seems it might be a possibly useful crutch to bring functionality to Windows.  LAMPP (from the same project) appears intended to round up those who strayed from the herd and ensure that they have a difficult and unpleasant time.  

LAMP on the other hand is the normal way to set things up in the Linux world.  Nothing should have ended up in /opt at all.  Your configuration files should be in /etc/apache2/ and you data (initially) in /var/www

See:

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

You can install the normal LAMP server in the normal places with a pair of lines:

```

sudo apt-get update
sudo apt-get install lamp-server^

```

If you do it right, nothing ends up in /opt

If it is just you by yourself on the machine, it is enough that you take ownership of the web directory /var/www when you have it set up.

```

sudo chown -R thephpdev /var/www

```

If you are going to share it with other devs or wish to learn how, then you'll have to use groups instead.  That's easy too.

---

### Post by thePHPdev on 2012-09-26
Wow, If I had done that in the first place, thanks man. That solved it!

---

