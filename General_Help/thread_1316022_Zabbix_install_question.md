---
title: "Zabbix install question"
date: 2009-11-05
forum: General Help
---

### Post by mindwip on 2009-11-05
I am trying to install Zabbix 1.6.6 on Ubuntu 9.10 Desktop and am running in to a problem at the bold underlined font part. The error tells me the directory does is not there? any help would be great.
Thanks!



[http://www.ubuntugeek.com/how-to-setup-zabbix-monitoring-application-in-ubuntu-9-04-jaunty-server.html](http://www.ubuntugeek.com/how-to-setup-zabbix-monitoring-application-in-ubuntu-9-04-jaunty-server.html)

Preparing your server

Install the required packages

    sudo apt-get install build-essential gnustep-make

    sudo apt-get install linux-headers-$(uname -r)

    sudo apt install ntp ntp-simple ntpdate

Now you need to edit /etc/ntp.conf file and change your NTP servers after that restart ntp using the following comamnd

    sudo /etc/init.d/ntp restart

Now you need to create zabbix user with the following comamnd

    sudo adduser zabbix

enter your password

Now you need to login as zabbix user

sudo su zabbix

Install the following packages

    sudo apt-get install apache2

    sudo apt-get install postgresql-8.3 postgresql-server-dev-8.3

    sudo apt-get install php5 php5-gd php5-pgsql snmp libsnmp-dev snmpd libcurl4-openssl-dev fping libiksemel3 libiksemel-dev

Install postgresql web GUI admin application using the following command

    sudo apt-get install phppgadmin

Now you need to login as root

sudo su -

    sudo -u postgres psql postgres
    \password postgres
    password123
    \q; ubuntu and Postgres Usernames (both = zabbix) are the same so they can work in unison

    sudo -u postgres createuser –superuser zabbix

    sudo -u postgres createdb zabbix

Now you can login to psql without sudo

Now you need to login as zabbix user

    sudo su zabbix

    cd /home/zabbix

Download zabbix latest version from here (At the time of writing this article version 1.6.6)

    tar zxvpf zabbix-1.6.6.tar.gz

    cd zabbix-1.6.6/create/schema

    cat postgresql.sql | psql zabbix

    cd ../data

    cat data.sql | psql zabbix

    cat images_pgsql.sql | psql zabbix

    cd ..

    cd ..

    sudo ./configure --enable-server --enable-agent --with-pgsql --with-net-snmp --with-jabber=/usr/ --with-libcurl

    sudo make install

Now you need to add the following ports to services file

    sudo nano /etc/services

Add at the following ports

    zabbix_agent 10050/tcp
    zabbix_trap 10051/tcp

Save and exit the file

    sudo mkdir /etc/zabbix

    sudo chown -R zabbix.zabbix /etc/zabbix/

    cp misc/conf/zabbix_* /etc/zabbix/

Now we need to edit the agent config file

    nano /etc/zabbix/zabbix_agentd.conf

Make sure that the Server parameter points to the server ip address, for the agent that runs on the

server it is like this: Server=127.0.0.1 change to xxx.xxx.xxx.xxx

AND REMOVE # from ListenIP=127.0.0.1 AND CHANGE IT to ListenIP=xxx.xxx.xxx.xxx

Save and exit the file

Now we need to edit the server config file

    nano /etc/zabbix/zabbix_server.conf

For small sites this default file will do, however if you are into tweaking your config for your 10+ hosts site,

this is the place.

Change this:

# Database user

DBUser=zabbix

# Database password

# Comment this line if no password used

DBPassword=password123

AND REMOVE # from ListenIP=127.0.0.1 AND CHANGE IT to ListenIP=X.X.X.X (your server ip)

Save and exit the file

[COLOR="Black"][B][U]Now copy the zabbix server,agent startup scripts for  to /etc/init.d location

    sudo cp misc/init.d/debian/zabbix-server /etc/init.d

    sudo cp misc/init.d/debian/zabbix-agent /etc/init.d
[/COLOR][/U][/B]
Now we need to change of destination path in server and agent configuration files

For zabbix server config file

    sudo nano /etc/init.d/zabbix-server

Look for the following line:

    DAEMON=/home/zabbix/bin/${NAME}

and replace it with:

    DAEMON=/usr/sbin/${NAME}

For zabbix server config file

    sudo nano /etc/init.d/zabbix-agent

Look for the following line:

    DAEMON=/home/zabbix/bin/${NAME}

and replace it with:

    DAEMON=/usr/sbin/${NAME}

Save and exit the file

Add the zabbix server and agent config files to startup

    sudo chmod 755 /etc/init.d/zabbix-server

    sudo update-rc.d zabbix-server defaults

    sudo chmod 755 /etc/init.d/zabbix-agent

    sudo update-rc.d zabbix-agent defaults

Now you can start zabbix server and agent using the following command

    sudo /etc/init.d/zabbix-server start

    sudo /etc/init.d/zabbix-agent start

You can check the processes using the following command

    ps -aux | grep zabbix

    cd /home/zabbix/zabbix-1.6.6/

    mkdir /home/zabbix/public_html

    cp -R frontends/php/* /home/zabbix/public_html/

Now we need to edit the default apache configuration file

    sudo nano /etc/apache2/sites-enabled/000-default

Change the following section

---

### Post by P4man on 2009-11-05
should work if you are in the right folder. It assumes you are in  /whereever you downloaded the tarball to/zabbix-1.6.6/
Just check if you have a "misc" subfolder there, and browse the rest of the path. Looking at the tarball it should be there.

Can you copy/paste the terminal command as you are entering it, including the prompt and its output?

---

### Post by mindwip on 2009-11-05
Reading your reply i think i see the problem. I did not run the command from the right folder. I think i have to add "/home/zabbix/zabbix-1.6.6/" in front of "misc/init.d" correct?




Output of the command

> zabbix@SLC-Zabbix:~$ sudo cp misc/init.d/debian/zabbix-server /etc/init.d
[sudo] password for zabbix: 
cp: cannot stat `misc/init.d/debian/zabbix-server': No such file or directory
zabbix@SLC-Zabbix:~$ ^C


Location of the file they are talking about

> /home/zabbix/zabbix-1.6.6/misc/init.d/debian

---

### Post by P4man on 2009-11-05
this here, the red tilde:

```
zabbix@SLC-Zabbix:[COLOR="Red"]**~**[/COLOR]$ 
```

shows you are in your homefolder. Its the same as 

/home/[COLOR="red"]zabbix[/COLOR]

([COLOR="red"]zabbix[/COLOR] being your username)

this here:

misc/init.d/debian/zabbix-server

starts with a subfolder "misc" which is not in your home folder. It is a subfolder of 

/home/[COLOR="red"]zabbix[/COLOR]/zabbix-1.6.6/

also known as

~/zabbix-1.6.6/

So either you cd there first:

```
cd zabbix-1.6.6/
```

and try again. Or you complete the path in the copy command using a relative path (relative to where you are now, your home folder):

```
sudo cp zabbix-1.6.6/misc/init.d/debian/zabbix-server /etc/init.d
```

or absolute path which works from anywhere:

```
sudo cp ~/zabbix-1.6.6/misc/init.d/debian/zabbix-server /etc/init.d
```

which is the same as

```
sudo cp /home/[COLOR="red"]zabbix[/COLOR]/zabbix-1.6.6/misc/init.d/debian/zabbix-server /etc/init.d
```

heh. Well any of them will do. This concludes our initiation lesson in to absolute and relative file paths :)

---

### Post by mindwip on 2009-11-05
Thanks! had no idea about the "~". Moving on along now!

---

