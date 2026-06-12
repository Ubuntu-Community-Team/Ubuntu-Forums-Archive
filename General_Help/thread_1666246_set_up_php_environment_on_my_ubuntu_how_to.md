---
title: "set up php environment on my ubuntu how to ?"
date: 2011-01-13
forum: General Help
---

### Post by capt_nemo777 on 2011-01-13
been developing on windows os eversince I learned my hello world thing..
can someone please tell me "step by step" how to set up
PHP, Mysql, Apache in my newly setup ubuntu 10.10  ?

---

### Post by Primefalcon on 2011-01-13
```
sudo apt-get install apache2 php5 mysql-server; sudo /etc/init.d/apache2 restart
```

your web files then then be in /var/www and you can point your browser at [http://localhost](http://localhost) to see how it goes

---

### Post by Smart Viking on 2011-01-13
> **capt_nemo777 said:**
> been developing on windows os eversince I learned my hello world thing..
can someone please tell me "step by step" how to set up
PHP, Mysql, Apache in my newly setup ubuntu 10.10  ?

```
sudo apt-get install mysql-server apache2 php5
```
Something like dat should get you goin'.

Apache root directory will be /var/www/ where you can create an index.html.

I don't know much about mysql i just have it running for some certain things for my webserver. You could install phpmyadmin to administer mysql.
```
sudo apt-get install phpmyadmin
```
cheers

---

### Post by capt_nemo777 on 2011-01-13
> **Primefalcon said:**
> ```
sudo apt-get install apache2 php5 mysql-server; sudo /etc/init.d/apache2 restart
```

your web files then then be in /var/www and you can point your browser at [http://localhost](http://localhost) to see how it goes

if on windows there's this file called "hosts" where in I can edit

127.0.0.1 localhost and etc., 
and is found under C:\Windows\System32\drivers\etc\

how bout in ubuntu? is there such file ?,
where can i locate that ?

---

### Post by Primefalcon on 2011-01-13
> **Smart Viking said:**
> You could install phpmyadmin to administer mysql.
phpmyadmin is very good I use that myself all the time

---

### Post by Primefalcon on 2011-01-13
> **capt_nemo777 said:**
> if on windows there's this file called "hosts" where in I can edit

127.0.0.1 localhost and etc., 
and is found under C:\Windows\System32\drivers\etc\

how bout in ubuntu? is there such file ?,
where can i locate that ?
/etc/hosts

you'll need admin privs though to edit, just open a terminal and type in

```
gksudo gedit /etc/hosts
```

---

### Post by Smart Viking on 2011-01-13
> **capt_nemo777 said:**
> if on windows there's this file called "hosts" where in I can edit

127.0.0.1 localhost and etc., 
and is found under C:\Windows\System32\drivers\etc\

how bout in ubuntu? is there such file ?,
where can i locate that ?

Yep. I would be careful when editing that file.

```
(smartviking)-(jobs:0)-(~/tem)
(! 558)-> locate hosts | grep "hosts$"
/etc/hosts
/etc/avahi/hosts
/etc/exim4/conf.d/router/150_exim4-config_hubbed_hosts
/etc/vlc/http/.hosts
/etc/vlc/lua/http/.hosts
/home/smartviking/.ssh/known_hosts
/usr/share/vlc/http/.hosts
/usr/share/vlc/http/dialogs/.hosts
/usr/share/vlc/lua/http/.hosts
/usr/share/vlc/lua/http/dialogs/.hosts
(smartviking)-(jobs:0)-(~/tem)
(! 559)-> cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	1001px-laptop
# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
(smartviking)-(jobs:0)-(~/tem)
(! 560)-> 

```

---

### Post by capt_nemo777 on 2011-01-13
```

sudo /etc/init.d/apache2 restart

```

command not found, why?

---

### Post by Primefalcon on 2011-01-13
> **capt_nemo777 said:**
> ```

sudo /etc/init.d/apache2 restart

```

command not found, why?
do that after apache2 has been installed, it just restarts the webserver the valid commands are restart stop and start

---

### Post by Smart Viking on 2011-01-13
> **capt_nemo777 said:**
> ```

sudo /etc/init.d/apache2 restart

```

command not found, why?

Try to reboot the system will probably fix it self, or something.

---

### Post by capt_nemo777 on 2011-01-13
i did
```

sudo apt-get install php5 apache2 mysql-server

```
and I supposed it was installed,and also I installed the phpmyadmin too..but 
is there a command to know if those 3 things were really installed ?

---

### Post by Primefalcon on 2011-01-13
> **capt_nemo777 said:**
> i did
```

sudo apt-get install php5 apache2 mysql-server

```
and I supposed it was installed,and also I installed the phpmyadmin too..but 
is there a command to know if those 3 things were really installed ?
do as smart viking said if it continues to refuse that command and as for checking if it works easy..... point your browser at [http://localhost](http://localhost)

---

### Post by capt_nemo777 on 2011-01-13
I did
```

sudo reboot

```
it rebooted the machine, now I pointed my browser to [http://localhost](http://localhost)
"unable to connect"

then I tried
```

sudo /etc/init.d/apache2 start

```
still command not found..why?

---

### Post by capt_nemo777 on 2011-01-13
found out why it didn't work, i tried installing the apache2 alone 
```

sudo apt-get install apache2

```
and it worked

---

### Post by Primefalcon on 2011-01-13
> **capt_nemo777 said:**
> found out why it didn't work, i tried installing the apache2 alone 
```

sudo apt-get install apache2

```
and it worked
weird oh well for whatever reason it must not have installed... oh well fixed now :)

---

### Post by capt_nemo777 on 2011-01-13
new problem, I did
```

sudo apt-get install phpmyadmin

```
i believe it got installed coz there are alot of lines in my screen,
then i pointed to 
```

http://locahost/phpmyadmin

```
it says not found , why?

---

### Post by capt_nemo777 on 2011-01-13
new problem, I did
```

sudo apt-get install phpmyadmin

```
i believe it got installed coz there are alot of lines in my screen,
then i pointed to 
```

http://locahost/phpmyadmin

```
it says not found , why?

---

### Post by capt_nemo777 on 2011-01-13
new problem, I did
```

sudo apt-get install phpmyadmin

```
i believe it got installed coz there are alot of lines in my screen,
then i pointed to 
```

http://locahost/phpmyadmin

```
it says not found , why?

---

### Post by capt_nemo777 on 2011-01-13
new problem, I did
```

sudo apt-get install phpmyadmin

```
i believe it got installed coz there are alot of lines in my screen,
then i pointed to 
```

http://locahost/phpmyadmin

```
it says not found , why?

---

### Post by capt_nemo777 on 2011-01-13
new problem, I did
```

sudo apt-get install phpmyadmin

```
i believe it got installed coz there are alot of lines in my screen,
then i pointed to 
```

http://locahost/phpmyadmin

```
it says not found , why?

---

### Post by weedeater64 on 2011-01-13
> **capt_nemo777 said:**
> 
is there a command to know if those 3 things were really installed ?

```
dpkg --get-selections
```

will give all installed packages, pipe it through less, cause its gonna run off the buffer

```
dpkg --get-selections | less
```

you can scroll up and down with arrows, or pgup/dwn

```
q
```

to get out.

---

### Post by capt_nemo777 on 2011-01-13
new problem, I did
```

sudo apt-get install phpmyadmin

```
i believe it got installed coz there are alot of lines in my screen,
then i pointed to 
```

http://locahost/phpmyadmin

```
it says not found , why?

---

### Post by weedeater64 on 2011-01-13
> **capt_nemo777 said:**
> 
is there a command to know if those 3 things were really installed ?

```
dpkg --get-selections
```

will give all installed packages, pipe it through less, cause its gonna run off the buffer

```
dpkg --get-selections | less
```

you can scroll up and down with arrows, or pgup/dwn

```
q
```

to get out.

Alternatively,

```
dpkg --get-selections | grep apache
```

for a keyword search for "apache" in the installed packages.

---

### Post by capt_nemo777 on 2011-01-13
Sorry, for those dupe posts, my internet connection is going crazy, i didn't know it was posted several times

---

### Post by weedeater64 on 2011-01-13
> **capt_nemo777 said:**
> 
is there a command to know if those 3 things were really installed ?

```
dpkg --get-selections
```

will give all installed packages, pipe it through less, cause its gonna run off the buffer

```
dpkg --get-selections | less
```

you can scroll up and down with arrows, or pgup/dwn

```
q
```

to get out.

Alternatively,

```
dpkg --get-selections | grep apache
```

for a keyword search for "apache" in the installed packages.

---

### Post by weedeater64 on 2011-01-13
> **capt_nemo777 said:**
> Sorry, for those dupe posts, my internet connection is going crazy, i didn't know it was posted several times

I don't think it was on your end. haha.:popcorn:

---

### Post by capt_nemo777 on 2011-01-13
but still am not able to see phpmyadmin
```

http://localhost/phpmyadmin

```

---

### Post by Primefalcon on 2011-01-13
> **capt_nemo777 said:**
> but still am not able to see phpmyadmin
```

http://localhost/phpmyadmin

```
an easy fix I found is this
```
sudo ln -s /usr/share/phpmyadmin /var/www/phpmyadmin
```

---

### Post by Primefalcon on 2011-01-13
double posted myself lol....

---

### Post by weedeater64 on 2011-01-13
> **capt_nemo777 said:**
> but still am not able to see phpmyadmin
```

http://localhost/phpmyadmin

```


I don't know, but are you aware of the docs?

```
cd /usr/share/doc
```

or

```
w3m /usr/share/doc
```

and the man pages?

```
man man
```

---

