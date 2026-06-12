---
title: "zend farmeworks with ubuntu"
date: 2010-02-04
forum: General Help
---

### Post by sathyashrayan on 2010-02-04
Dear group,
  I am not sure if this forum is a suitable place for this question. If not please guide a correct place.

I have installed php/mysql with apache2 as per the instruction of installing php. And i am able to install Drupal,osc and other open source without any errors. 

But I am unable to make a zend frame work working. I have used zf tools to create the project. The project folder with MVC is getting created. But when I code the following simple code, it showing me error.

```

require_once 'library/Zend/Application.php';

$application = new Zend_Application(
    APPLICATION_ENV, 
    APPLICATION_PATH . '/configs/application.ini'
);

$application->bootstrap()->run();

```

Warning: require_once(Zend/Loader/Autoloader.php) [function.require-once]: failed to open stream: No such file or directory in /var/www/works/zend/social/testbox/library/Zend/Application.php on line 80

Fatal error: require_once() [function.require]: Failed opening required 'Zend/Loader/Autoloader.php' (include_path='.:/usr/share/php5:/usr/share/pear:/usr/share/php/libzend-framework-php/zend') in /var/www/works/zend/social/testbox/library/Zend/Application.php on line 80

I have changed /usr/share/php5/.ini and also usr/share/php/ with include_path. But yet I can not run a hello world with zend. Can some one help me?

---

