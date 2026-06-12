---
title: "I succeed to set the ubuntu as server"
date: 2009-11-07
forum: General Help
---

### Post by jason.tan on 2009-11-07
I succeed to set the ubuntu as server.
It can be registered the account of ubuntu through the php page.

I finished it with expect script.

I share it in my website.

[http://www.godmaker.cn/?p=36](http://www.godmaker.cn/?p=36)

We can discuss it together~.thx

---

### Post by jason.tan on 2009-11-07
Here is the php file to excute system commond



<?php
$username=$_GET['username'];
$password=$_GET['password'];
 echo $username.$password;
system(”expect callregister.sh “.$username.” “.$password);
 ?>

---

