---
title: "Give me a clue....probably a php silly error"
date: 2010-09-15
forum: General Help
---

### Post by old_dog on 2010-09-15
After writing something more complicated that gave me a blank screen ended up using this as a test:-
<html>
<head>
<title>test PHP Page</title>
</head>
<body>
<?php
echo "Hello World!";
?>
</body>
</html>

Shock horror a blank screen????
changing the echo line to this:- 
echo "<p>"Hello World!";
gives me this result in the browser:-
"Hello World!"; ?> 
changing the echo line to this:-
echo "<p>Hello World!";
in the browser produces this:-
Hello World!"; ?> 
I cannot see for the life of me where I am going wrong!!!!!
Cheers

---

### Post by 3Miro on 2010-09-15
What happens if you properly close the tag:

```
 echo "<p> Hello Cruel World </p>" 
```

---

### Post by Peter09 on 2010-09-15
What is the extension of your document (HTML or PHP) many webservers have to be told to process PHP within pages - normally by defining which extensions contain embedded code.
 
I think the output you are seeing is just that you are breaking the echo line and so doing a straight text output.

---

### Post by old_dog on 2010-09-15
Tried this
echo "<p>Hello World!</p>";

gives me.....
Hello World!

"; ?> 

that is the result, you don't close paragraph tags do you?

---

### Post by realruntime on 2010-09-15
Your webserver simply does not execute the PHP code. It delivers the file as plain HTML. And the browser renders it. It ignores everything between <? and p> because it is an unknown HTML-Tag.

You must teach your webserver to execute PHP.

---

### Post by old_dog on 2010-09-15
If I change the file extension to php then firefox just wants to download it or asks me what to use to open it.
Opera just downloads it.

I can't believe I am having such difficulty with something so simple?

---

### Post by old_dog on 2010-09-15
Point me in the right direction how do I teach my webserver recognise php

---

### Post by Peter09 on 2010-09-15
What is the Webserver software? Apache?

---

### Post by TheStroj on 2010-09-15
You just can't run PHP code this way. Make a server first (I recommend using XAMPP as it's rly simple to setup).

After you put your something.php to a directory that XAMPP reads from you can access it on 'localhost' (now the code will be executed properly).

---

### Post by 3Miro on 2010-09-15
You need to install a web server (most people use Apache), then you need to install PHP and the you need to load the web-page form your web-server. Here is the official Ubuntu HowTo:

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

If you don't need MySQL you can ignore that part, but Apache and PHP is something that you do need.

---

### Post by old_dog on 2010-09-15
What a silly billy..........
haven't set apache to recognise php!

On that note thanks for all your help
cheers old_dog

---

