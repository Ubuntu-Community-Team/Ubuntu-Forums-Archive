---
title: "trouble with Zend Debugger"
date: 2010-12-14
forum: General Help
---

### Post by ubscott on 2010-12-14
hi,

i have been going in circles trying to get Eclipse + php  debugging for Drupal working.  i have installed Eclipse a couple of  times from different sources.  then i decided to delete them and pick up  the 'all-in-one' version of Eclipse from the Zend site:
[http://www.zend.com/en/community/pdt](http://www.zend.com/en/community/pdt)

(I got the 32 bit for Linux.  this is not the Zend Studio upgrade.)

with Eclipse Helios up and running, i installed the XTend Drupal plugin:
[http://xtend.us/downloads/eclipse](http://xtend.us/downloads/eclipse)

I also downloaded the Zend Server-Debugger from this page:
[http://downloads.zend.com/pdt/server-debugger/](http://downloads.zend.com/pdt/server-debugger/)
[http://downloads.zend.com/pdt/server-debugger/ZendDebugger-5.2.14-linux-glibc23-i386.tar.gz](http://downloads.zend.com/pdt/server-debugger/ZendDebugger-5.2.14-linux-glibc23-i386.tar.gz)

i have some reservations about where I put Eclipse and the Zend Debugger.  I put them both in my Drupal root; i.e.,
[http://localhost/Drupal](http://localhost/Drupal)

then  i modified the PHP.ini.  (I know we're not supposed to do this.   however, every time i try to create an INI in the /etc/apache2/conf.d  folder, I get an error.  i don't know how to make a custom INI.)

i changed the PHP to add these lines:

zend_extension="/usr/lib/php5/20090626+lfs/xdebug.so"
zend_extension_manager.debug_server=/var/www/Drupal/ZendDebugger-5.2.14-linux-glibc23-i386/5_2_x_comp
zend_debugger.allow_hosts=127.0.0.1
zend_debugger.expose_remotely=always

(I'm  not sure at the moment where i got these commands from. it seems odd  that the first line references xdebug.so .  it makes sense if Zend  builds on xdebug, though.)

I have closely looked over the paths given for zend_extension and zend_extension_manager.debug_server.  The paths are correct.

when i run phpinfo.php, among the many lines of output I see this:
This program makes use of the Zend Scripting Language Engine:
Zend Engine v2.3.0, Copyright (c) 1998-2010 Zend Technologies

(I don't see a message indicating the Zend Debugger is working.)

from  Eclipse, i have created a project that points to the folder of my  Drupal installation.  I have created a Debug Configuration that points  to the index.php for the particular installation of Drupal i am  attempting to debug.

when i try to test the debug configuration i get this familiar error:
"A  timeout has occurred on [http://localhost/foobar](http://localhost/foobar) . Please verify the  Zend Debugger is properly installed on the server and that the  'dummy.php' is located in your Web Server's document root."

i don't think the problem is the dummy.php, as i copied it into /var/www .

does anyone have any ideas?  

thanks in advance.

---

### Post by afroyd on 2010-12-16
For start, try loading only the zend debugger (uncomment the other) with:
zend_extension= and full path to the .so file name (including the file name).

A side note, for using zend_extension_manager.debug_server you need to load zend extension manager first. You don't realy need it if you just want to load the debugger.

---

### Post by ubscott on 2010-12-16
hi afroyd,

thanks for the reply.  i commented out the line in php.ini that refers to the Zend_extension_manager.  the php.ini looks like:
zend_extension="/usr/lib/php5/20090626+lfs/xdebug.so"
zend_debugger.allow_hosts=127.0.0.1
zend_debugger.expose_remotely=always

i restarted Apache.  i also verified (again) that the zend_extension path is correct.

unfortunately, nothing has changed. phpInfo shows the same message; it doesn't indicate the Zend Debugger is working.  

also, when i start Eclipse Helios, click 'debug configurations' and then try to test the index.php for my Drupal installation, i get the same error about Zend Debugger and/or the dummy.php.

thanks for the advice.  do you have any other ideas?

---

### Post by afroyd on 2010-12-20
Do you have error messages in your php error log?
Did you also try loading zend debugger with zend_extension= full path?

---

