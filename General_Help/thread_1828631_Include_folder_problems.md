---
title: "Include folder problems"
date: 2011-08-19
forum: General Help
---

### Post by benton101 on 2011-08-19
Hi,
I have just started to use Ubuntu and want to move my web development to this environment. I have successfully installed LAMP using the tasksel command.  The apache and php test pages run fine to show that the installation is successful.

My web folders have the following structure;

root folder
> inc
>img

When I run one of my pages that has include statements nothing displays in the browser.

Would anyone know what is happening?

Thank You
Ben

---

### Post by sahabcse on 2011-08-19
Did you check the error log?

Is document root folder updated?

---

### Post by Wim Sturkenboom on 2011-08-19
Check /var/log/http..../error.log or /var/log/apache..../error.log Not sure what the exact names are as I'm not behind a server.

In a terminal, run
```

tail -f /path/to/error.log

```
Next open a page and check the nlog. You can interrupt tailwith <ctrl>c

Are you migrating from Windows? If so, be aware that names in Linux are case sensitive and that the path seperator is a forward slash instead of a backslash.

---

### Post by benton101 on 2011-08-19
Hi and thank you for your responses.

I have managed to find out that I need the following syntax on my include statements ./ or a ../;

The includes below work when the hello.php is in the same folder as the calling procedure.
1. <?php require("hello.php"); ?>  
2. <?php require("./hello.php"); ?>

But when I put the hello.php file in a folder named inc none of these work;
3. <?php require("inc/hello.php"); ?> 
4. <?php require("./inc/hello.php"); ?>
5. <?php require("../inc/hello.php"); ?>

I am making my way through the emails, but I am very green with all this.

Thank You
Ben

---

### Post by Wim Sturkenboom on 2011-08-19
Wild guess is that apache does not have permissions to read the inc directory or its contents.

Not why I posted.
[LIST]
[*]. (dot) indicates the current directory and you don't need it; to my knowledge it's only when you want to execute programs on the command line that it might be necessary
[*].. (dotdot) indicated the parent directory; that one you would use if the inc directory is next to the root directory instead of in the root directory
[/LIST]

---

### Post by benton101 on 2011-08-19
Thank You for the clarification on the dots
How could i find out if Apache has permission to read the inc directory?
Ben

---

### Post by benton101 on 2011-08-19
I checked the error log as advised and this is what it says for my last attempt;

[Fri Aug 19 22:07:35 2011] [error] [client ::1] PHP Warning:  include(/home/benton/public_html../inc/hello.php): failed to open stream: No such file or directory in /home/benton/public_html/test.php on line 10
[Fri Aug 19 22:07:35 2011] [error] [client ::1] PHP Warning:  include(): Failed opening '/home/benton/public_html../inc/hello.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in /home/benton/public_html/test.php on line 10
[Fri Aug 19 22:07:35 2011] [error] [client ::1] PHP Warning:  include(/home/benton/public_html../includes/hello.php): failed to open stream: No such file or directory in /home/benton/public_html/test.php on line 12
[Fri Aug 19 22:07:35 2011] [error] [client ::1] PHP Warning:  include(): Failed opening '/home/benton/public_html../includes/hello.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in /home/benton/public_html/test.php on line 12

What is this telling me, the directories definitely exist.

This is the code that I have in my php file.
Number 1 works but 2 and 3 do not.

 1. File from the root directory
 <?php include($_SERVER['DOCUMENT_ROOT'] . '/hello.php');?> 
 2. File from a sub directory
 <?php include($_SERVER['DOCUMENT_ROOT'] . '../inc/hello.php');?> 
 3. File from a sub directory
 <?php include($_SERVER['DOCUMENT_ROOT'] . '../includes/hello.php');?>  

Ben

---

### Post by Wim Sturkenboom on 2011-08-19
```

[Fri Aug 19 22:07:35 2011] [error] [client ::1] PHP Warning: include(/home/benton/public_html../inc/hello.php): failed to open stream: No such file or directory in /home/benton/public_html/test.php on line 10
```
This tells me that you must leave the dot dot out. The dot dot at the end of 'public_html..' is part of that directory name in thisn case so you tell the system to look for something in a directory *_/path/to/public_html.._* which does not exist; it's *_/path/to/public_html_* 

Also
```

<?php echo $_SERVER['DOCUMENT_ROOT'];?>

```
It will tell you if the document root ends with a slash; I think it does based on (2) not giving errors. If it does, there is no need for dot or dot dot in your current setup.

(1) works because slash slash is the same as slash
(2) works if I'm correct with the echo statement
(3) does not work because you don't have a directory includes

PS
Start to get into the habit of placing output (and source code) between [noparse]```
 and 
```[/noparse] here on the forum. It will maintain indentations in source code and makes outputs easier to read.

---

### Post by Wim Sturkenboom on 2011-08-19
I suggest, by the way,that you place the inc directory at the same level as what you called root. In that case it's not in the document root and therefore not accessible by browsers. That way you can hide a function to login to the mysqldatabase (if you're planning to use it) that contains the username and password. Apache can theretically read from any directory (if the permissions are normal).

---

### Post by benton101 on 2011-08-19
Hello and Thank You for your response.

This is the directory structure that I have;

benton/public_html/test.php

benton/public_html/inc/hello.php

I have tried all sorts of variations of ./ ../ with no success.

When I put the file named hello.php in the structure** benton/public_html** it works, but when I put the file named hello.php in the structure **benton/public_html/inc** it fails.

I have attempted to carry out your advice, by doing the following (I am interested in the security reasons you raised with this approach);

benton/public_html/test.php
benton/inc/hello.php

But I am still not having any success, its almost as if the folder named **inc** does'nt exist.

Somebody earlier mentioned something about apache permissions on files, could this be the problem and if so how do I apply permissions on the folders?

Thank You
Ben

---

### Post by Wim Sturkenboom on 2011-08-20
//Edit  see that I swapped the files around ;)

Your include line should in that case look like
```

include("../inc/test.php");

```

Not behind a server, so can only check what I actually code on monday.

With regards to permissions; I've created your directory structure and the below is what the permissions look like.
```

fortyfourgalena@desktop-01:~$ tree -pug websites
websites
&#9500;&#9472;&#9472; [drwxr-xr-x fortyfou fortyfou]  inc
&#9474;   &#9492;&#9472;&#9472; [-rw-r--r-- fortyfou fortyfou]  test.php
&#9492;&#9472;&#9472; [drwxr-xr-x fortyfou fortyfou]  public_html
    &#9492;&#9472;&#9472; [-rw-r--r-- fortyfou fortyfou]  hello.php

2 directories, 2 files
fortyfourgalena@desktop-01:~$ 

```
This should allow apache to read (e.g. -rw-r--**[COLOR="Red"]r[/COLOR]**--).
But if it's a permission issue, I would expect apache to log it as such.

The following should allow you to modify the permissions if necessary
```

chmod -R a+rX path/to/public_html/
chmod -R a+rX path/to/inc/

```
The capital X will set the execute bit on directories but not on files; lowercase x will set it on files as well but should not be necessary.
The success of the chmod depends on the original permissions.
Alternatave is to use
```

chmod -R 755 path/to/public_html/
chmod -R 755 path/to/inc/

```
and is what I usually use; slight disadvantage is that it makes files also executable.

---

### Post by benton101 on 2011-08-20
Hello Vim,

Thank You for persisting and assisting me with this problem, it was starting to get the better of me.

The problem seems to have been solved by using the following code;

```

chmod -R a+rX path/to/public_html/
chmod -R a+rX path/to/inc/

```

As a post script the following two lines worked;

```

<?php include($_SERVER['DOCUMENT_ROOT'] . '/hello.php');?> 
<?php include($_SERVER['DOCUMENT_ROOT'] . '/inc/hello.php');?> 

```

The following two did not work;
```

<?php include($_SERVER['DOCUMENT_ROOT'] . './hello.php');?> 
<?php include($_SERVER['DOCUMENT_ROOT'] . '../inc/hello.php');?>  

```

Having worked in a windows environment for the last twenty years I have some concepts that I need to learn.

Thank You for your patience
Benton

---

### Post by Wim Sturkenboom on 2011-08-20
Still curious what 
```

<?php echo $_SERVER['DOCUMENT_ROOT'];?>

```shows ;)

If the problem is solved, please mark the thread as solved using the thread tools just above the first post on this page.

---

### Post by benton101 on 2011-08-20
The code;
```

<?php echo $_SERVER['DOCUMENT_ROOT'];?>

```Displays;
/home/benton/public_html

Cheers
Benton

How do you mark the thread as solved.

---

### Post by Wim Sturkenboom on 2011-08-20
As I said, using the thread tools just above tyhe first post on a (this) page ;)

One thing that has not been mentioned yet:
If you need apache to write files, you need to give it write permission as well. I use a dedicated directory under (in your case) public_html for that (e.g. public_html/files); that will allow e.g. file uploads via html pages as well as files (e.g. reports) generated by your 'application' to be stored in there.

You can make that directory world writable or, better, use ACL to only allow apache to write in there.

---

