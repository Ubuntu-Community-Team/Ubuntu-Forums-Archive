---
title: "Viewing a logfile on an html page"
date: 2009-10-25
forum: General Help
---

### Post by blazemore on 2009-10-25
Is there a way to tail -f a file in a box on a webpage, so I can see a realtime view of a log file from anywhere? I already have apache set up and working.

---

### Post by OpenGuard on 2009-10-25
[php] 
$file = $_GET['file'];
$data = exec("tail -f $file");
 
echo $data;
[/php]
 
[http://127.0.0.1/getlog.php?file=/var/log/boot.log](http://127.0.0.1/getlog.php?file=/var/log/boot.log)

---

### Post by blazemore on 2009-10-25
When I do that it just outputs
```
$file = $_GET['file']; $data = exec("tail -f $file"); echo $data;
```

---

### Post by OpenGuard on 2009-10-25
```
 
sudo apt-get install php5 libapache2-mod-php5 && sudo /etc/init.d/apache2 restart

```
 
Also, save it as a PHP file ( .php ), and enclose the code in [COLOR=blue]<?php /* code here */ ?>[/COLOR] tags

---

### Post by blazemore on 2009-10-25
Now it just hangs, doesn't display any output at all.

---

### Post by blazemore on 2009-10-25
*bump*

---

### Post by OpenGuard on 2009-10-25
> **blazemore said:**
> Now it just hangs, doesn't display any output at all.

Post the source and check if boot.log exists ( that was just an example ).

---

### Post by blazemore on 2009-10-25
Here's the source
```
root@server1:/# cat /var/www/getlog.php
<?php
$file = $_GET['file'];
$data = exec("tail -f $file");

echo $data;
?>
```


The file exists
```
root@server1:/# file /var/www/foldlog.txt
/var/www/foldlog.txt: ASCII text
```

And here's the link I use
```
root@server1:/# cat /var/www/index.php | grep getlog
<p><a href="getlog.php?file=/var/www/foldlog.txt">Folding Log</a></p>
```

I don't really know anything about php.

---

### Post by OpenGuard on 2009-10-25
[PHP]<?php

$file = "/var/log/foldlog.txt";
echo exec("tail -f $file");

?>
[/PHP]

Still nothing ?

---

### Post by blazemore on 2009-10-25
it's /var/www/foldlog.txt and still nothing
foldlog.txt is a hard link, I'm going to try tailing the "proper" file

---

### Post by blazemore on 2009-10-25
Now it's ```

<?php

$file = "/root/FAHlog.txt";
echo exec("tail -f $file");

?>

```

It doesn't hang, it finishes loading but displays a white page.

---

### Post by OpenGuard on 2009-10-25
[php]<?php

if (function_exists('exec')) {
    echo exec("tail -f /root/FAHlog.txt");
} else {
    echo "exec disabled";
}

?>
[/php]What's the output ?

---

### Post by blazemore on 2009-10-25
No output at all...

---

### Post by blazemore on 2009-10-25
No output at all... AND when I do the page source in my browser, it's blank!

---

### Post by OpenGuard on 2009-10-25
> **blazemore said:**
> No output at all...

Seems that your PHP is broken ( or not installed ). 

```
sudo apt-get reinstall php5 libapache2-mod-php5
sudo /etc/init.d/apache2 restart
```

---

### Post by blazemore on 2009-10-25
No, it's installed, and I've tried rebooting the whole server.

---

### Post by blazemore on 2009-10-25
If I substitute "tail -f" for "tail" I get the last line, and the last line only. It's just the -f option that doesn't work.

---

### Post by blazemore on 2009-10-25
OK I have this 
```

  GNU nano 2.0.9           File: /var/www/getlog.php

<?php

$handle = popen("tail foldlog.txt 2>&1", 'r');
while(!feof($handle)) {
    $buffer = fgets($handle);
    echo "$buffer<br/>\n";
    ob_flush();
    flush();
}
pclose($handle);

?>


```

But it doesn't work with -f. with -f it just stays loading.

---

### Post by blazemore on 2009-10-25
OK I hacked it with an HTML auto refresh.
[http://rory.is-a-geek.com](http://rory.is-a-geek.com)

Don't know whether to mark as solved or not...

---

