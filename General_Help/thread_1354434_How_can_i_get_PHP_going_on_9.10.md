---
title: "How can i get PHP going on 9.10"
date: 2009-12-13
forum: General Help
---

### Post by JoeyF on 2009-12-13
I am going to learn PHP and i want to be able to test php files. How can i do that?


Thanks.

---

### Post by baddog144 on 2009-12-13
If you want to test them from the command line, the package php5-cli is probably the one you're looking for. The package php5 is a more general package, but I'm not sure if it includes a command-line interpreter

---

### Post by JoeyF on 2009-12-13
How do i install the PHP CLI?

Thanks.

---

### Post by baddog144 on 2009-12-13
> **JoeyF said:**
> How do i install the PHP CLI?

Thanks.

```

sudo apt-get install php5-cli

```

;)

---

### Post by JoeyF on 2009-12-13
One last thing, How would i open a PHP file with it? i know about the <path> but do i leave the arrows? Thanks.

---

### Post by baddog144 on 2009-12-13
> **JoeyF said:**
> One last thing, How would i open a PHP file with it? i know about the <path> but do i leave the arrows? Thanks.

No, no arrows ;)

---

### Post by JoeyF on 2009-12-13
What would i enter though?

like php file path.

---

### Post by baddog144 on 2009-12-13
Something like
```

php /home/yourname/source/foo.php

```
If my memory serves me correctly

---

### Post by JoeyF on 2009-12-14
I made a test PHP and opened it in the Terminal, But it gives me this:
[IMG]http://img121.imageshack.us/img121/8733/screenshotpc.png[/IMG]

How can i get it to display the content? Like in a Browser or whatever?


Thanks.

---

### Post by baddog144 on 2009-12-14
> **JoeyF said:**
> I made a test PHP and opened it in the Terminal, But it gives me this:
[IMG]http://img121.imageshack.us/img121/8733/screenshotpc.png[/IMG]

How can i get it to display the content? Like in a Browser or whatever?


Thanks.

In firefox (or whatever web browser you use), type the full path of the file into the address bar. For your example, it would be /home/joey/Desktop/helloworld.php
:)

---

### Post by JoeyF on 2009-12-14
I'm getting a box that says "What should Firefox do with this file, Save or open" but when i hit open with it goes to my files to find a program. How can i get it to open it with Firefox?

---

### Post by Leppie on 2009-12-14
open a filemanager (like thunar or nautilus) and go to the folder with your php script, right click the script and select to open with ff.

your script looks like html with a line of php in the middle.

---

### Post by baddog144 on 2009-12-14
> **JoeyF said:**
> I'm getting a box that says "What should Firefox do with this file, Save or open" but when i hit open with it goes to my files to find a program. How can i get it to open it with Firefox?

Ick, really? I think you'll need to set up a web server to use this, and I'm sorry to say I don't have any real experience with it :(
Google will be a great help though, I'm sure ;)

---

### Post by JoeyF on 2009-12-14
I installed PHP and have Localhost, In /var/www . But when i try to move my PHP into it a get a permissions error. So i read the permissions on the WWW folder and it said i'm not the owner.

How can i move it? and would that get it to run in the web browser?

---

### Post by JoeyF on 2009-12-14
And do i need to secure localhost like with XAMPP in Windows?

---

### Post by baddog144 on 2009-12-14
You need to move it with sudo, so 
```

sudo mv helloworld.php /var/www/

```
If you then go to localhost/helloworld.php with your webserver running, you **should** see your web page :)

---

### Post by JoeyF on 2009-12-14
One last thing and then i'm good.

How would i delete the default page in the www folder? index.html. It won't let me do it from the file browser.

---

### Post by bodhi.zazen on 2009-12-14
sudo rm /var/www/index.html

---

### Post by JoeyF on 2009-12-14
Now im getting:
[IMG]http://img687.imageshack.us/img687/2844/screenshot1re.png[/IMG]

ANd when i click on it it gives me the open screen. :(

---

### Post by baddog144 on 2009-12-14
> **JoeyF said:**
> Now im getting:
[IMG]http://img687.imageshack.us/img687/2844/screenshot1re.png[/IMG]

ANd when i click on it it gives me the open screen. :(
Try adding a basic .html page with a link to helloworld.php, and saving it as index.html (you'll need sudo) in /var/www
That file list may be doing something strange and telling firefox to download it

---

### Post by JoeyF on 2009-12-14
Should i just install LAMP? what about my current Localhost?


I downloaded PHP5 and Php5 cli but i don't know what i need to do with them


NVM above, I'll try that

---

### Post by centered effect on 2009-12-14
nevermind... can't delete posts...

---

### Post by JoeyF on 2009-12-14
> **baddog144 said:**
> Try adding a basic .html page with a link to helloworld.php, and saving it as index.html (you'll need sudo) in /var/www
That file list may be doing something strange and telling firefox to download it


What do you mean by add the link? A basic HTML link?

---

### Post by JoeyF on 2009-12-14
> **centered effect said:**
> oops saw you have everything installed

Huh?

---

### Post by baddog144 on 2009-12-14
> **JoeyF said:**
> What do you mean by add the link? A basic HTML link?
Yeah, just a basic html page:
```

<html>
<body>
<a href="helloworld.php">PHP Page.</a>
</body>
</html>

```
Save that as index.html in /var/www

---

### Post by bjk03 on 2009-12-14
I would install Apache at least.

---

### Post by JoeyF on 2009-12-14
Ok, So i tried:
```

<html>

<head>
<title>TEST</title>

</head>

<body>

<?php
Echo "Hello, World!";
?> 
</body>

</html>

```


Saved it as helloworld.html
Went to:

[http://localhost/helloworld.html](http://localhost/helloworld.html) and i get a blank white page, But the title shows up.

Any idea?

I just want to be able to test PHP in Firefox, If i try LAMP what would i have to do with my current Localhost?

Thanks,

---

### Post by JoeyF on 2009-12-14
> **bjk03 said:**
> I would install Apache at least.
I
 tried sudo apt-get install apache but i get E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

---

### Post by baddog144 on 2009-12-14
I think you need to rename helloworld.html to helloworld.php

---

### Post by bjk03 on 2009-12-14
> **JoeyF said:**
> Ok, So i tried:
```

<html>

<head>
<title>TEST</title>

</head>

<body>

<?php
Echo "Hello, World!";
?> 
</body>

</html>

```


Saved it as helloworld.html
Went to:

[http://localhost/helloworld.html](http://localhost/helloworld.html) and i get a blank white page, But the title shows up.

Any idea?

I just want to be able to test PHP in Firefox, If i try LAMP what would i have to do with my current Localhost?

Thanks,

Since you saved it in /var/www, you don't have anything to do just install LAMP.

---

### Post by JoeyF on 2009-12-14
> **baddog144 said:**
> I think you need to rename helloworld.html to helloworld.php


I tried it, It goes to a directory and if i click on it it wants me to open it again.


Is there any way i can remove PHP and just install LAMP?

---

### Post by JoeyF on 2009-12-14
> **bjk03 said:**
> Since you saved it in /var/www, you don't have anything to do just install LAMP.

LAMP would just take over my current Localhost?

---

### Post by bjk03 on 2009-12-14
> **JoeyF said:**
> LAMP would just take over my current Localhost?

Yes.

---

### Post by JoeyF on 2009-12-14
> **bjk03 said:**
> Yes.

I am following [http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies) but when i type sudo apt-get install apache2 i get E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.


Could not having Apache be the problem? I tried the tut at [http://www.howtogeek.com/howto/ubuntu/installing-php5-and-apache-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/installing-php5-and-apache-on-ubuntu/) and everytime i try to install one of those i get the error message.  Do i already have them?

And should i just try XAMPP on Vista? Would there be any things i have to do to get that working? 

Thanks

---

### Post by bjk03 on 2009-12-14
> **JoeyF said:**
> I am following [http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies) but when i type sudo apt-get install apache2 i get E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.


Could not having Apache be the problem?

Yes I believe that not having Apache is the problem. Did you run the command it suggested ```
sudo dpkg --configure -a
``` run that then try ```
sudo apt-get install apache2
``` again

---

### Post by JoeyF on 2009-12-14
It works!!! Thanks guys.


This is why Ubuntu is the best, The community!

---

