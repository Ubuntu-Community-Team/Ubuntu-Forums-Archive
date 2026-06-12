---
title: "apache2 and php5 woes"
date: 2006-03-19
forum: General Help
---

### Post by c-2501 on 2006-03-19
ok here goes, 

i installed apache2 and php5 through Synaptic package manager, apache seems to run ok however when i try to run a simple php test file:

```

<?php phpinfo() ?>

```

rather than displaying the php output it tries to download the file?

other people i have talked to say its just a matter of dl'ing the right packages and you should be ready to go (also several tutorials say this, including the 'official' ones) however this doesnt seem to be the case for me

---

### Post by Wallakoala on 2006-03-19
you have to put the php script into wherever the apache server is. I know mine is located at /var/www , but yours might be different. Then, in a web browser type "localhost" into the address bar. Now you should be in the apache directory, and if you put your php script in, you should be able to run it.

---

### Post by c-2501 on 2006-03-19
i know that, the file location is

[http://localhost/index.php](http://localhost/index.php)

i just dont get whats gone wrong :cry:

---

### Post by theneb on 2006-03-23
i am having a similar problem. When i go check the php script in the browser it works if i just check localhost/index but not when i use localhost/index.php it tries to download it if i put the extension.  anyone have any ideas?

---

### Post by wannabelinuxconvert on 2006-03-23
Have you added the .php extension to apache2.conf !?

```
DirectoryIndex index.html index.cgi index.pl index.php index.xhtml
```

Check that the library libapache2-mod-php5 is installed and loaded ... you can enable the php5 mod by using the command 

```
sudo a2enmod php5
```

Then restart apache2

```
sudo /etc/init.d/apache2 force-reload
```

And then empty the cache from your browser (t*his took me ages to figure out but it was the solution in my case, and it seems so simple now* :mrgreen: )

Then try navigating to [http://localhost/index.php]("http://localhost/index.php") and see if that's fixed your problem.

Let me know how you get on.

Mic

---

### Post by theneb on 2006-03-23
Thanks for the input. I got it working

---

### Post by JurB on 2006-03-27
Thank you!

---

### Post by linuxswords on 2006-09-06
Hi there, i've got the same problem, but this
solution don't seem to work for me. I installed with

apt-get install apache2 php5 libapache2-mod-php5

At first my php-files on '/var/www/' didn't execute.
I enabled the module, cleared the cache of my browser and went
to [http://localhost/testphp.php](http://localhost/testphp.php) but i got an '500 Internal Server Error'.

The Error log says 'Premature End of Script' so i thought of a typo,
but no: here is my testphp.php file:

~~~~~~~~~~~~~~~~~~~~~start~~~~~~~~~~~~~~~~~~~~
<html>
    <head>
    </head>
    <body>
    <h2>PHP Test</h2>
    <?php
        phpinfo();
    ?>
    </body>
</html>
~~~~~~~~~~~~~~~~~~~~~end~~~~~~~~~~~~~~~~~~~~

any suggestions?

---

