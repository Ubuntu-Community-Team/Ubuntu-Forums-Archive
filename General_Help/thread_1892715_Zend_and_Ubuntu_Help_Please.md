---
title: "Zend and Ubuntu Help Please"
date: 2011-12-08
forum: General Help
---

### Post by davidtheo on 2011-12-08
I have downloaded zend

I have added the path to my php.ini
I have add the path to zf.sh in my .bashrc

but when I type zf.sh --help I get this error message is I am not in the same folder as zf.php

> Could not open input file: ./zf.php


and if I am in the same folder as zf.php I get this

> 
***************************** ZF ERROR ********************************
In order to run the zf command, you need to ensure that Zend Framework
is inside your include_path.  There are a variety of ways that you can
ensure that this zf command line tool knows where the Zend Framework
library is on your system, but not all of them can be described here.

The easiest way to get the zf command running is to give it the include
path via an environment variable ZEND_TOOL_INCLUDE_PATH or
ZEND_TOOL_INCLUDE_PATH_PREPEND with the proper include path to use,
then run the command "zf --setup".  This command is designed to create
a storage location for your user, as well as create the zf.ini file
that the zf command will consult in order to run properly on your
system.

Example you would run:

$ ZEND_TOOL_INCLUDE_PATH=/path/to/library zf --setup

Your are encourged to read more in the link that follows.
Zend_Tool & CLI Setup Information
(available via the command line "zf --info")
   * Home directory found in environment variable HOME with value /home/david
   * Storage directory assumed in home directory at location /home/david/.zf/
   * Config file assumed in home directory at location /home/david/.zf.ini
   * Config file does not exist at /home/david/.zf.ini
   * Config file assumed in storage directory at location /home/david/.zf//zf.ini

To change the setup of this tool, run: "zf --setup"

I have tried doing
> 
ZEND_TOOL_INCLUDE_PATH=/path/to/library zf --setup

but that does not help

Please can someone help.

---

### Post by davidtheo on 2011-12-09
Can anyone help?

---

