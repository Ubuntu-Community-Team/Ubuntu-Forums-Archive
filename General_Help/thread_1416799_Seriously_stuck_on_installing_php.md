---
title: "Seriously stuck on installing php"
date: 2010-02-26
forum: General Help
---

### Post by boatman1 on 2010-02-26
I've been reading tutorials for the last three hours. Here's what I've done.

I've run this:

  ```

  sudo apt-get install apache2
  sudo apt-get install php5
  sudo apt-get install libapache2-mod-php5
  sudo /etc/init.d/apache2 restart
```

On that last one I got an error, but this fixed it:

  ```
echo "ServerName [servername]" | sudo tee /etc/apache2/conf.d/fqdn
```

Now I try making an actual page with the code 

  ```
<?php echo '<p>Hello World</p>'; ?>
```

I get 

 ```
Hello World

 '; ?>
```

Including those symbols. So I tried <?php phpinfo() ?> and the result page was blank. Yes the extension is .php. I've tried a load of other commands, deleting everything and reinstalling it all, but no luck.

(Sorry text editor isn't working for me I'm on Opera but whatever, I indented the code.)

(Edit: lol indentation didn't work either. What the hell is going on today?)

---

### Post by howlingmadhowie on 2010-02-26
can you place your code in a code block by adding *SQUARE_BRACKET_OPEN*CODE*SQUARE_BRACKET_CLOSE before your code and
*SQUARE_BRACKET_OPEN*/CODE*SQUARE_BRACKET_CLOSE after your code?

can you also paste the code the browser is actually receiving? (crtl-U is quite close to this, better would be to wget it)

---

### Post by boatman1 on 2010-02-26
> **howlingmadhowie said:**
> can you place your code in a code block by adding *SQUARE_BRACKET_OPEN*CODE*SQUARE_BRACKET_CLOSE before your code and
*SQUARE_BRACKET_OPEN*/CODE*SQUARE_BRACKET_CLOSE after your code?

can you also paste the code the browser is actually receiving? (crtl-U is quite close to this, better would be to wget it)

Thanks, was trying to look for that code.

The browser is receiving exactly what I copied and pasted from [http://www.php.net/manual/en/tutorial.firstpage.php](http://www.php.net/manual/en/tutorial.firstpage.php)

```

<html>
 <head>
  <title>PHP Test</title>
 </head>
 <body>
 <?php echo '<p>Hello World</p>'; ?> 
 </body>
</html>

```

---

### Post by howlingmadhowie on 2010-02-26
> **boatman1 said:**
> Thanks, was trying to look for that code.

The browser is receiving exactly what I copied and pasted from [http://www.php.net/manual/en/tutorial.firstpage.php](http://www.php.net/manual/en/tutorial.firstpage.php)


placing this code on my webserver and running 
```

wget localhost/testpage.php | less testpage.php

```
if get the following:
```

<html>
 <head>
  <title>PHP Test</title>
 </head>
 <body>
 <p>Hello World</p> 
 </body>
</html>

```

what does running this command do on your system?

---

### Post by boatman1 on 2010-02-26
> **howlingmadhowie said:**
> what does running this command do on your system?

"Unsupported scheme"

---

### Post by howlingmadhowie on 2010-02-26
> **boatman1 said:**
> "Unsupported scheme"


oh, sorry. i'm an idiot:

```

wget *PATH_TO_FILE.php* && cat *FILENAME.php*

```

---

### Post by cdenley on 2010-02-26
```

sudo a2enmod php5
sudo /etc/init.d/apache2 restart
echo -e "GET /testpage.php HTTP/1.0\n"|nc 127.0.0.1 80

```

---

### Post by boatman1 on 2010-02-26
> **cdenley said:**
> ```

sudo a2enmod php5
sudo /etc/init.d/apache2 restart
echo -e "GET /testpage.php HTTP/1.0\n"|nc 127.0.0.1 80

```

Results:

sudo a2enmod php5

```
Module php5 already enabled
```

sudo /etc/init.d/apache2 restart

```
 * Restarting web server apache2          
... waiting                                     [ OK ]
```

echo -e "GET /testpage.php HTTP/1.0\n"|nc 127.0.0.1 80

...not found.

```

HTTP/1.1 404 Not Found
Date: Fri, 26 Feb 2010 20:22:24 GMT
Server: Apache/2.2.12 (Ubuntu)
Vary: Accept-Encoding
Content-Length: 304
Connection: close
Content-Type: text/html; charset=iso-8859-1

```

---

### Post by cdenley on 2010-02-26
> **boatman1 said:**
> Results:

sudo a2enmod php5

```
Module php5 already enabled
```

sudo /etc/init.d/apache2 restart

```
 * Restarting web server apache2          
... waiting                                     [ OK ]
```

echo -e "GET /testpage.php HTTP/1.0\n"|nc 127.0.0.1 80

```

hang on

```

Well you have to substitute testpage.php with the name of the PHP file you created, since you never told us the filename.

---

### Post by boatman1 on 2010-02-26
> **cdenley said:**
> Well you have to substitute testpage.php with the name of the PHP file you created, since you never told us the filename.

Edited, didn't see that sorry.

---

### Post by cdenley on 2010-02-26
> **boatman1 said:**
> Edited, didn't see that sorry.

But you're still trying to access a file which doesn't exist.
```

ls /var/www/*.php

```

---

### Post by boatman1 on 2010-02-26
I don't really know what I'm doing to be honest. I just need to write a webpage in PHP for an assignment, I've never even used the terminal before.

---

### Post by timZZ on 2010-02-26
> **boatman1 said:**
> I don't really know what I'm doing to be honest. I just need to write a webpage in PHP for an assignment, I've never even used the terminal before.


What they are trying to determine is whether your php file is within the correct place.

Can you see your file when you use the following command

```
ls /var/www/
```

---

### Post by boatman1 on 2010-02-26
> **timZZ said:**
> What they are trying to determine is whether your php file is within the correct place.

Can you see your file when you use the following command

```
ls /var/www/
```

I can see index.html and testphp.php, but neither are mine.

---

### Post by timZZ on 2010-02-26
What if you type the command.

```
find . -name "*.php"
```

and post the results.

Basically the file should be within /var/www/

So lets find out where it is and move it.

If you are using the GUI and know where your file is you could simply move it into /var/www/

my next question is how are you trying to execute the page? Using a browser? What are you typing into the address bar?

---

### Post by howlingmadhowie on 2010-02-26
creating anything in /var/www requires root rights, because it isn't owned by the default user.  the easy way to do this is:

press alt+f2 and then enter:
```

gksudo nautilus

```

enter your password and wait for a file browser to open. this file browser is running as root. now you can go to /var/www and create a directory to store your php scripts in. i'd suggest calling it "phpscripts" or something.  right-click the directory and either change its owner to the standard user (i don't know if you can do that using the file browser) or set it so anybody can access and delete it. now you should be able to save files under /var/www/phpscripts as the standard user.

---

### Post by boatman1 on 2010-02-27
I've moved the file to /var/www/phpscripts (directory I made), I also tried moving it to /var/www/ but phpinfo() still gives a blank page. Anything else you need to check?

Thanks for the help by the way.

---

### Post by cdenley on 2010-02-27
You still haven't given us the name or full path to your PHP file, and you haven't posted the response from the server using the netcat command I posted to request a PHP script which actually exists.

---

