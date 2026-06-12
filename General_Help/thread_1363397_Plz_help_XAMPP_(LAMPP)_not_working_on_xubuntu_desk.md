---
title: "Plz help XAMPP (LAMPP) not working on xubuntu desktop"
date: 2009-12-24
forum: General Help
---

### Post by shanali4 on 2009-12-24
Today, I have installed XAMPP on my Xubuntu desktop according to method explained here, [http://ubuntuforums.org/showthread.php?t=223410](http://ubuntuforums.org/showthread.php?t=223410). Everything went fine but when i opened xampp control panel and clicked start button MySQL started working but Apache is not working. i have clicked it several time but nothing happened. I also restarted my PC but still their is problem. I also tried to start by following command but it's still not working. Plz help me
```
sudo /opt/lampp/lampp start
```

---

### Post by bjk03 on 2009-12-24
Try ```
sudo service apache2 start 
```

---

### Post by back2arie on 2009-12-24
> **shanali4 said:**
> Today, I have installed XAMPP on my Xubuntu desktop according to method explained here, [http://ubuntuforums.org/showthread.php?t=223410](http://ubuntuforums.org/showthread.php?t=223410). Everything went fine but when i opened xampp control panel and clicked start button MySQL started working but Apache is not working. i have clicked it several time but nothing happened. I also restarted my PC but still their is problem. I also tried to start by following command but it's still not working. Plz help me
```
sudo /opt/lampp/lampp start
```

What's the output says?

---

### Post by shanali4 on 2009-12-25
> **bjk03 said:**
> Try ```
sudo service apache2 start 
```

I have used this command it says
```
apache2: unrecognized service

```

---

### Post by shanali4 on 2009-12-25
> **back2arie said:**
> What's the output says?

Terminal says this
```
Starting XAMPP for Linux 1.5.3a...
XAMPP: Starting Apache with SSL (and PHP5)...
/opt/lampp/bin/mysql.server: 84: source: not found
XAMPP: Starting MySQL...
XAMPP for Linux started.
shanali4@shanali4-desktop:~$ /opt/lampp/bin/mysql.server: 334: log_success_msg: not found

```

But when i visited [http://localhost](http://localhost) it shows Web Page not found error. i had also put index.html files in my htdocs dir

---

### Post by back2arie on 2009-12-25
> **shanali4 said:**
> Terminal says this
```
Starting XAMPP for Linux 1.5.3a...
XAMPP: Starting Apache with SSL (and PHP5)...
/opt/lampp/bin/mysql.server: 84: source: not found
XAMPP: Starting MySQL...
XAMPP for Linux started.
shanali4@shanali4-desktop:~$ /opt/lampp/bin/mysql.server: 334: log_success_msg: not found

```But when i visited [http://localhost](http://localhost) it shows Web Page not found error. i had also put index.html files in my htdocs dir

So apache is running now?
Also check the log in [FONT=monospace][/FONT]/opt/lampp/logs/error_log

PS: You might want to use the latest version of XAMPP for linux (1.7.3).

---

### Post by nickcollie on 2010-03-08
I am struggling with an identical error message. 
> /opt/lampp/bin/mysql.server: 334: log_success_msg: not found

Error logs say this:

> [Mon Mar 08 09:45:09 2010] [notice] suEXEC mechanism enabled (wrapper: /opt/lampp/bin/suexec)
[Mon Mar 08 09:45:09 2010] [warn] RSA server certificate is a CA certificate (BasicConstraints: CA == TRUE !?)
[Mon Mar 08 09:45:09 2010] [warn] RSA server certificate CommonName (CN) `localhost' does NOT match server name!?

Any help would be hugely appreciated.

---

### Post by menryan on 2010-05-29
Hi!

Try this:

sudo gedit /opt/lampp/bin/mysql.server

change
#!/bin/sh

to
#!/bin/bash

i got this from - [http://www.apachefriends.org/f/viewtopic.php?f=17&t=21104](http://www.apachefriends.org/f/viewtopic.php?f=17&t=21104)

---

