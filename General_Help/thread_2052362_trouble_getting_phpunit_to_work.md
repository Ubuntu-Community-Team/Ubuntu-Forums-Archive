---
title: "trouble getting phpunit to work"
date: 2012-09-03
forum: General Help
---

### Post by gvanto on 2012-09-03
I have just installed phpunit using PEAR on our Ubuntu/Linux server ( Linux mccoy 2.6.28-11-server #42-Ubuntu SMP Fri Apr 17 02:45:36 UTC 2009 x86_64 GNU/Linux )

when I try to run a unit test I get the error:

    "Fatal error: Call to undefined method PHPUnit_Util_Filter::addfiletofilter() in /usr/bin/phpunit on line 48"

I have googled this and came across a few threads on it however none of these seem to fix my issue.

I have added the following line to my /etc/php5/cli/php.ini:

include_path = ".:/usr/share/php/PHPUnit"

(I've also tried it without the "/PHPUnit" folder included)

But I still get this error.

Any help would be greatly appreciated

gvanto

edit: this is what is in start of file /user/bin/phpunit:

> 


    // ...just comments prior to this

    if (extension_loaded('xdebug')) { xdebug_disable(); }

    if (strpos('/usr/bin/php', '@php_bin') === 0) { set_include_path(dirname(FILE) . PATH_SEPARATOR . get_include_path()); }

    require_once 'PHPUnit/Util/Filter.php';

    PHPUnit_Util_Filter::addFileToFilter(FILE, 'PHPUNIT'); //line 48

    require 'PHPUnit/TextUI/Command.php';

    define('PHPUnit_MAIN_METHOD', 'PHPUnit_TextUI_Command::main');



---

