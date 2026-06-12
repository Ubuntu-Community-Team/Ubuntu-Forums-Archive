---
title: "PHP Cli - How to run a page periodically?"
date: 2010-04-20
forum: General Help
---

### Post by imblack on 2010-04-20
Hello,
I have to run this page: [http://localhost/loop/cp/feeds?d=y&u=y](http://localhost/loop/cp/feeds?d=y&u=y) periodically, because it fetches the content of some feeds(RSS) and then inserts into Database and then sends SMS texts to subscribed users.

when i run it with php-cli in bash like this: php feeds.php?u=y&d=y
I only get:
[4] 11719

but nothing happens, running it like this: 
black@loopserver:/var/www/loop/cp$ php 'feeds.php?u=y&d=y'
Could not open input file: feeds.php?u=y&d=y

gives that ^^^

Can any one please tell me what to do? I think the problem is coming by passing get parameters, if i just run feeds.php everything goes fine, but I need to pass in those.

Any help would be appreciated.

---

### Post by Untitled_No4 on 2010-04-20
You should run it as 
```
php feeds.php -u y -d y
```
and then in your code you should use getopt:
```
$args = getopt("u:d:")
$u = $args['u']
$d = $args['d']
```

---

### Post by imblack on 2010-04-20
Ah, okay, but I also want to run it through browser sometimes, means i have to use both $_GET and $args and check which one has values in it?
no common way?

---

### Post by Untitled_No4 on 2010-04-20
Not that I know of.

---

### Post by imblack on 2010-04-20
Well thanks it solved the problem :)

---

### Post by imblack on 2010-04-21
One last problem is that I want to use it from web and cli both.
But when i use this getopt() function the webbrowser doesnt let me view the page, instead downloads the php file. CLI is workign fine now, how to solve this? The code is given below:

/[PHP]/ If get is supplied use it
if ( isset($_GET['d']) )
    $dispatch = $_GET['d'];
if ( isset($_GET['u']) )
    $update = $_GET['u'];
    
// if no values provided in get use cli args
if ( $update != 'u' && $dispatch != 'u' )
{
    //$args = getopt("u:d:");

    if ( isset($args['u']) )
        $update = $args['u'];

    if ( isset($args['d']) )
        $dispatch = $args['d'];
}[/PHP]

---

