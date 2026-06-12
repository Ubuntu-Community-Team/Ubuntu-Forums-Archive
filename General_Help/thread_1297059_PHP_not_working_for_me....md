---
title: "PHP not working for me..."
date: 2009-10-21
forum: General Help
---

### Post by erikbrannlund on 2009-10-21
I have installed PHP5
```

sudo apt-get install apache2
sudo apt-get install php5
sudo apt-get install libapache2-mod-php5
sudo /etc/init.d/apache2 restart

```
Except the first line since I had apache installed previously.
 
Now when i make an extremely simple php file
```

<html>
<body>
<H1>Any text</H1>
</body>
</html>

```
All i get when calling this page is "500 Internal server error"

---

### Post by badger_fruit on 2009-10-21
what does your apache_error.log file say?
ps, I'm not sure where that will be precisely having only really used apache and Suse ...

---

### Post by OpenGuard on 2009-10-21
Can we see your Apache configuration file ?

---

### Post by indytim on 2009-10-21
> 
<html>
<body>
<H1>Any text</H1>
</body>
</html>


Where's the PHP script start and end?  

```

<?PHP
print 'Hellow World';
?>

```

IndyTim

---

### Post by brunitto on 2009-10-21
A PHP file should work without the <?php and ?> tags, in this case, the HTML markup should be presented. Again, checkout the log files.

---

### Post by erikbrannlund on 2009-10-21
After some more trying...
changed file to 
```
 
<?php
print 'hello world';
?>

```
I also tried echo instead of print
Still then same result in error.log I see this line
..................(8) Exec format error: exec of /var/www/cgi-bin/test.php
..................Premature end of script headers

---

### Post by satish_j on 2009-10-22
Are you able to view the default Apache page??
i.e [http://localhost](http://localhost)

---

### Post by erikbrannlund on 2009-10-22
Apache works fine and the "compiled cgi-scripts" I have works fine but php doesn't. I have tried to setup logging from PHP but so far no success.
 
/Erik

---

### Post by erikbrannlund on 2009-10-29
Now it suddenly works if I have the php file in /var/www but in /var/www/cgi-bin no luck! Where is this configured in php config file or in apache config file and if so which one?

---

