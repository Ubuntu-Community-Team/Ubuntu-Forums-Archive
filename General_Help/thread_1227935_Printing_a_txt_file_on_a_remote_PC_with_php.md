---
title: "Printing a txt file on a remote PC with php"
date: 2009-07-31
forum: General Help
---

### Post by unavenged on 2009-07-31
Hi, Im trying to print a txt file on a remote PC using php... I have got this to work with a windows machine using xampp and then using the following php file and a batch file:

test.php
[PHP]
<?php
passthru('test.bat');
?>
[/PHP]

test.bat
```

start /min notepad /p print.txt

```

Can i do the same thing in ubuntu using xampp?? I know i can print using the "lpr print.txt" command but i doesn't work when i put it directly into the php file or in a sh script because i can't seem to get php to run the scritp

Thanks in advance

PS: I don't know anything about php or shell scripting... I'm just winging it:D

---

### Post by nikhilk on 2009-07-31
Any special reason for doing this? You can share the file/folder on the remote machine using Samba and then print it.
Why run a web server and use PHP scripts?

---

### Post by unavenged on 2009-07-31
I am looking for a way to print on a remote PC through a browser... We have a kiosk system that prints vouchers and we need to be able to tell the kiosk to reprint a voucher without having to ssh in.

---

### Post by nikhilk on 2009-07-31
> **unavenged said:**
> I am looking for a way to print on a remote PC through a browser... We have a kiosk system that prints vouchers and we need to be able to tell the kiosk to reprint a voucher without having to ssh in.

OK, see if you can execute simple commands using exec instead of passthrough. e.g.
```
exec('touch /tmp/tmp');
```

If you cannot execute any commands, it could be some PHP/xampp configuration issue.

---

### Post by unavenged on 2009-08-03
Cool thanks... I managed to get it to print by doing the following and it works great :D

[PHP]
<?php

exec('lpr test.txt');

?>
[/PHP]

---

### Post by nikhilk on 2009-08-03
> **unavenged said:**
> Cool thanks... I managed to get it to print by doing the following and it works great :D

[PHP]
<?php

exec('lpr test.txt');

?>
[/PHP]

You are welcome. I am glad that it worked for you.

---

