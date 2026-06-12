---
title: "how to start phpmyadmin"
date: 2009-08-20
forum: General Help
---

### Post by masoud23 on 2009-08-20
Hello
I have started apache and mysql and want to start phpmyadmin so i can open it at this adress: [http://localhost/phpmyadmin](http://localhost/phpmyadmin)
how can i do that?

---

### Post by Bachstelze on 2009-08-20
I'm not sure what you mean here. Did you install phpmyadmin?

---

### Post by credobyte on 2009-08-20
Open Apache config file:
```
sudo gedit /etc/apache2/apache2.conf

```

Add this line:
```
Include /etc/phpmyadmin/apache.conf
```

Restart Apache:
```
sudo /etc/init.d/apache2 restart
```

---

### Post by DaithiF on 2009-08-20
Have you already installed phpmyadmin ?
sudo apt-get install phpmyadmin

if so, then as long as apache is running then phpmyadmin should be accessible at that address.

---

### Post by credobyte on 2009-08-20
> **DaithiF said:**
> Have you already installed phpmyadmin ?
sudo apt-get install phpmyadmin

if so, then as long as apache is running then phpmyadmin should be accessible at that address.

No, it shouldn't ( see my previous post ).

---

### Post by DaithiF on 2009-08-20
> **credobyte said:**
> No, it shouldn't ( see my previous post ).
you're right, my bad.

---

### Post by Jwaweru on 2010-07-14
> **credobyte said:**
> Open Apache config file:
```
sudo gedit /etc/apache2/apache2.conf

```Add this line:
```
Include /etc/phpmyadmin/apache.conf
```Restart Apache:
```
sudo /etc/init.d/apache2 restart
```[Type in your browser:]("http://localhost/phpmyadmin")
[URL="http://localhost/phpmyadmin"]```
http://localhost/phpmyadmin
```
[/URL]

---

