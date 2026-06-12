---
title: "Very IMP"
date: 2009-11-14
forum: General Help
---

### Post by ikon_ on 2009-11-14
Hey guys I'm having some trouble with mysql-php software.Well I get an error message when I try to include a file.

My file is

  ```
1 <?php
  2 include 'db_connect.php';
  3 ?>
  4 <html>
  5 <body>
  6 <br><h2>Can I log in to the system or not</h2>
  7 </body>
  8 </html>
```

The error when I try to view this file is :
                                                                                                                                                                                                                                                                                                                                            

```
Fatal error: Unknown: Failed opening required '/home/ikon/public_html/main_project/2_sign_in.php' (include_path=''.:/usr/share/php:/usr/share/pear'') in Unknown on line 0

```

I don't have any clue what the problem is. I downloaded the php-db package but it didn't help.
Can somebody help????

---

### Post by Monotoko on 2009-11-14
that means it cant find the 2_sign_in.php file

i would try renaming it, i believe iv read somewhere that it doesnt like a number being at the start of the filename

---

### Post by ikon_ on 2009-11-14
Well I tried renaming it but it didn't help . I got the same error message with the different file name in each case I changed it.

---

### Post by Monotoko on 2009-11-14
is the PHP file in the same folder as the file your after?

For example:

in one php file (call it test.php)

it will have the line:

```
include db_connect.php;
```

and then there should be another file called db_connect.php in the same folder?

---

### Post by ikon_ on 2009-11-14
Yes, I have both the files in the same folder.Please I need the patch quickly.
Thanks for your help.

---

