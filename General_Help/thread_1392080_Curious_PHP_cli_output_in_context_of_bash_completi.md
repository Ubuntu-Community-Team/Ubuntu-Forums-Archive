---
title: "Curious PHP cli output in context of bash completion ?"
date: 2010-01-27
forum: General Help
---

### Post by lexsimon on 2010-01-27
Hello,

I'm not sure that this is the right forum but I give a try and please forgive me for English mistakes...

Why Ubuntu Forum and not a PHP or bash forum ?
Because for now, my problem only occured on Ubuntu 8.04 and Ubuntu 9.10. It worked fine under Ubuntu Dapper and works actually fine too under MAC OS X, using PHP-5.3.1 and bash-3.2.48 from macport.
I firstly searched for PHP options but could not find anything and I'm not able to understand what could be the problem source.

Here's the thing :
I have a PHP script that is "bash completed" using the output of a PHP script. When asking bash for completion, I have some curious extra newline characters that seems to be not captured by bash and completion fails.

Please find bellow the source of files to reproduce the problem :

[LIST]
[*]"completion.sh" : a bash script that declares the completion for "myscript.php", using "echoscript.php" or "echoscript.sh", depending of what you comment in the source code. (in real case, "myscript.php" is used for self-completion)
[*]"myscript.php" : a PHP script that echo "Hello World"
[*]"echoscript.php" : a simple PHP script that outputs "a b c d", without new line
[*]"echoscript.sh" : the bash version of echoscript.php
[/LIST]
Using echoscript.sh for completion, it works. Using echoscript.php, it makes "something" ... :( :

Type : "./myscript.php<TAB><TAB><TAB><ENTER>" and see :

```

alex@sd-7354:~/completion$ ./myscript.php         

a  b  c  d  
alex@sd-7354:~/completion$ ./myscript.php 
a  b  c  d  
alex@sd-7354:~/completion$ ./myscript.php 
Hello world
alex@sd-7354:~/completion$ 

```Can anybody understand what is the problem ?! I would great appreciate any help.

Thank you.


N.B. : do not forget the permissions (chmod +x myscript.php echoscript.php echoscript.sh) and the PATH (PATH=.:${PATH}) to run the example.

== Source of completion.sh ==

```
#!/bin/bash

_completemyscript()
{
        local cur cmds cmdOpts
        cur="${COMP_WORDS[COMP_CWORD]}"
        
        # This does not work...
        #COMPREPLY=( $( compgen -W "$(echoscript.php)" -- "${cur}" ) )
        # This works
        COMPREPLY=( $( compgen -W "$(echoscript.sh)" -- "${cur}" ) )
        return 0
}

complete -F _completemyscript -o "default" myscript.php
```== Source of echoscript.sh ==

```
#!/bin/bash
echo -n "a b c d"
```== Source of echoscript.php ==

```
#!/usr/bin/php
<?php
echo "a b c d";
```== Source of myscript.php ==

```
#!/usr/bin/php
<?php
echo "Hello World\n";
```-- 
Alex

---

### Post by lexsimon on 2010-01-28
OK. I just did a recompilation of PHP-5.2.4 from source ([http://museum.php.net/php5/php-5.2.4.tar.bz2](http://museum.php.net/php5/php-5.2.4.tar.bz2)) under Ubuntu-8.04, used the PHP cli that I obtained and it works.

Here's the configure I used :
```
./configure --with-mysql --with-mysql-sock=/var/run/mysqld/mysqld.sock --with-gd --with-curl --with-curlwrappers --enable-exif --with-xsl --with-zlib --without-pear --enable-mbstring --enable-pcntl --prefix=/usr/local/php
```

I didn't applied the same patchs or did not used the same compilation options than the distribution did ; I'm not a Guru of compilation and especially PHP compilation ...

Does somebody have an idea what part is the source of the problem ? Should I submit a bug ?

Thank you.

---

### Post by lexsimon on 2010-01-30
I just filled a bug now : [https://bugs.launchpad.net/ubuntu/+source/php5/+bug/514989](https://bugs.launchpad.net/ubuntu/+source/php5/+bug/514989)

---

