---
title: "How do I install DB Main in Ubuntu (tar.gz package)"
date: 2012-03-28
forum: General Help
---

### Post by flordelis7 on 2012-03-28
I am beginner in Linux, and use Ubuntu 11.10. I will do a job for university, and I have to install a program for modeling database called DB Main. In the program's website,  downloaded the package for Linux and is called dbm-915-linux-setup.tar.gz. I do not know to install it and would like to help. I entered inside it and it has a file called readme.html, with some installation instructions, but I could not do. Below the file:


Linux

Two kings of installation are possible:

Installation for single user
Extract the dbm-9xx-linux-setup.tar.gz or dbm-deasy-9xx-linux-setup.tar.gz (with the DEASY plug-in) archive in the directory of your choice:
cd ~/db-main
tar -xf dbm-9xx-linux-setup.tar.gz (or tar -xf dbm-deasy-9xx-linux-setup.tar.gz)

Edit the .bashrc file (.profile in some environment) in the home directory and add the following lines (adapt the ~/db-main/bin directory to the one chosen previously):

export DB_MAIN_BIN=~/db-main/bin
export PATH=$DB_MAIN_BIN:$PATH
export LD_LIBRARY_PATH=$DB_MAIN_BIN:$DB_MAIN_BIN/../java/jre/lib/i386/client:$LD_LIBRARY_PATH
#CLASSPATH modification only for dbm-deasy-9xx-linux-setup.tar.gz
export CLASSPATH=.:$DB_MAIN_BIN/../plugins/deasy/lib/jidbmjava.jar:$DB_MAIN_BIN/../plugins/deasy/lib/sqlite-jdbc-3.6.20.1.jar:$CLASSPATH


Installation for all users
Extract the dbm-9xx-linux-setup.tar.gz archive in /usr/local/db-main (or any other directory of your choice):
cd /usr/local/db-main
sudo tar -xf dbm-9xx-linux-setup.tar.gz (or sudo tar -xf dbm-deasy-9xx-linux-setup.tar.gz)

Change the permissions so that any user can execute db_main:

sudo chmod a+x /usr/local/db-main/bin/db_main

Edit the global bash profile for all users (something like /etc/bash.bashrc) and add the following lines (adapt the /usr/local/db-main/bin directory to the one chosen previously):
export DB_MAIN_BIN=/usr/local/db-main/bin
export PATH=$DB_MAIN_BIN:$PATH
export LD_LIBRARY_PATH=$DB_MAIN_BIN:$DB_MAIN_BIN/../java/jre/lib/i386/client:$LD_LIBRARY_PATH
#CLASSPATH modification only for dbm-deasy-9xx-linux-setup.tar.gz
export CLASSPATH=.:$DB_MAIN_BIN/../plugins/deasy/lib/jidbmjava.jar:$DB_MAIN_BIN/../plugins/deasy/lib/sqlite-jdbc-3.6.20.1.jar:$CLASSPATH

To run DB-MAIN, there are also two approaches:

Execute the file db_main as a normal user from the command prompt.

Create a shortcut in your desktop that calls a shell file that contains something like this:

#!/bin/sh
export DB_MAIN_BIN=/the-path-to-the-db-main-bin-directory
export PATH=$DB_MAIN_BIN:$PATH
export LD_LIBRARY_PATH=$DB_MAIN_BIN:$DB_MAIN_BIN/../java/jre/lib/i386/client:$LD_LIBRARY_PATH
#CLASSPATH modification only for dbm-deasy-9xx-linux-setup.tar.gz
export CLASSPATH=.:$DB_MAIN_BIN/../plugins/deasy/lib/jidbmjava.jar:$DB_MAIN_BIN/../plugins/deasy/lib/sqlite-jdbc-3.6.20.1.jar:$CLASSPATH
cd /the-path-to-the-db-main-bin-directory/
db_main


Adapt the-path-to-the-db-main-bin-directory to your environment, save the shell file in the DB-MAIN bin directory (called db_main.sh for example) and give the execute permissions for all users.

Finally, put the following command in the shortcut:

/bin/sh /the-path-to-the-db-main-bin-directory/db_main.sh

A file db_main.ini is created in the .db_main directory of the user's home directory when DB-MAIN is run for the first time.



Thanks!

---

