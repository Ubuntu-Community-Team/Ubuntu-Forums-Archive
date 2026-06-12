---
title: "Startup services not starting (mysql,apache2)"
date: 2011-02-20
forum: General Help
---

### Post by reevery on 2011-02-20
Hello all, and sorry for what may be a trivial question, but it's been doing my nut in for the last week. I've tried to search for the answer and found so many possible solutions, none of which work.

I had a hard drive failure and have recovered (rsync) my backup root filesystem onto a new drive. This all seems to be fine, except that at least two services no longer start: mysql and apache2.

I can start successfully both through
```
sudo /etc/init.d/mysql start
sudo /etc/init.d/apache2 start
```
although mysql throws a warning about Upstart. Neither start automatically.

My system is Ubuntu 10.04.1 LTS x86_64. Part of my reolution actions has involved a kernel update to 2.6.32-27-generic.

I have tried to resolve the mysql issue first:

```
sudo update-rc.d -f mysql remove
sudo update-rc.d mysql defaults
```

```
sudo apt-get remove --purge mysql-server
sudo apt-get install mysql-server
```

adding them /etc/init.d/... start commands to /etc/init.d/rc.local script and to a session startup script

checking the services are in rcX.d (using bum and sysv-rc-conf)

Ensuring there's a .conf file in /etc/init (which there is).

I can't see anything in syslog which would suggest if the system has tried to start these but failed, but then I may be looking in the wrong place. I think they're not starting at all. I wonder if it's something to do with the restore, perhaps symlinks?

Does anyone have any suggestions as to what else to check, sort of having to create a fresh installation?

---

### Post by Habitual on 2011-02-20
are they e**X**ecutable in /etc/init.d/ ?

---

### Post by reevery on 2011-02-20
Yes, both 755 there.

---

### Post by tredegar on 2011-02-20
I'm running ```
tred@vaio2:~$ lsb_release -a
LSB Version:	core-2.0-ia32:core-2.0-noarch:core-3.0-ia32:core-3.0-noarch:core-3.1-ia32:core-3.1-noarch:core-3.2-ia32:core-3.2-noarch:core-4.0-ia32:core-4.0-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04.2 LTS
Release:	10.04
Codename:	lucid

```

[[COLOR="Red"]Warning[/COLOR], Rant starts here]
Ubuntu, in their eagerness for upstart (what's wrong with systemd if you want to change how linux boots?) seem to have turned this all into a complete shambles. 

Neither **upstart** nor the traditional SysV **/etc/init.d/*service* stop | start |restart** nor the new **service *service* stop | start |restart**  are working reliably or in a consistent way. Some (like **gdm**) apparently need one method to start them and the other to stop them. This is ridiculous.

I have to try one, then the other, and then remember which works for each  service. 

Ubuntu seem to have lost the plot.

[[COLOR="SeaGreen"]Here endeth the Rant[/COLOR]]

All I can suggest is an ugly hack. If```
sudo /etc/init.d/mysql start
sudo /etc/init.d/apache2 start
```
currently work for you then you could put those lines in **/etc/rc.local** (without the **sudo** of course)

Hope this helps you.

---

### Post by reevery on 2011-02-21
That didn't work either.

---

