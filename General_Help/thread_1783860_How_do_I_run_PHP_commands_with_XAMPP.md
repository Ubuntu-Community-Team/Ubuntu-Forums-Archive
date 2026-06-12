---
title: "How do I run PHP commands with XAMPP"
date: 2011-06-16
forum: General Help
---

### Post by Chris Psycho on 2011-06-16
I'm not quite sure where I should post this but here goes..

I installed XAMPP, and got it running but I'm not too sure on how I should be able to run PHP commands? As in the command line?

I did google for it but didn't really find anything.

Cheers!

---

### Post by dragonfly41 on 2011-06-16
[http://www.php-cli.com/php-cli-tutorial.shtml](http://www.php-cli.com/php-cli-tutorial.shtml)

---

### Post by Chris Psycho on 2011-06-16
the 'php' command wasn't recognised as far as I remember...

Am I looking for a specific directory?
Eg. /opt/lampp/phpcli php phpinfo


I'm trying to install a PEAR package if that helps, and hence why I need the php CLI.

---

### Post by Chris Psycho on 2011-06-17
bump

---

### Post by Chris Psycho on 2011-06-24
Bump..... =/

---

### Post by dragonfly41 on 2011-06-24
Not sure why the above link to php cli didn't help ...

anyway ... perhaps try this ...

sudo man php

/etc/php5/cli/php.ini
The configuration file for the CLI version of PHP.

e.g.

php -r 'echo "Hello World\n";'
This command simply writes the text "Hello World" to standard out.

---

### Post by Chris Psycho on 2011-06-24
=) thanks ill try that

---

### Post by Chris Psycho on 2011-06-24
I tried sudo man php I get this:
**No manual entry for php**

And this:[B] chris@chris-desktop:~$ php -r 'echo "Hello World\n"';
The program 'php' is currently not installed.  You can install it by typing:
sudo apt-get install php5-cli
[/B]
Also going to /opt/lampp/etc there is no php5 directory?
Neither in /etc/

---

### Post by Dave_L on 2011-06-24
I don't have XAMPP installed on this computer.  I think the path is /opt/lampp/bin/php.  "whereis php" might show that.

There's also an [XAMPP forum](http://www.apachefriends.org/f/), which might be more helpful for this kind of question.

---

### Post by Chris Psycho on 2011-06-24
> **Dave_L said:**
> I don't have XAMPP installed on this computer.  I think the path is /opt/lampp/bin/php.  "whereis php" might show that.

There's also an [XAMPP forum]("http://www.apachefriends.org/f/"), which might be more helpful for this kind of question.
THANK YOU! :D FALCON PUNCH! YES! It was that dam -r !

For anyone else: 
```

chris@chris-desktop:~$ /opt/lampp/bin/php -r 'phpinfo();'

```

---

