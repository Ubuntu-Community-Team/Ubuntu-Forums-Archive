---
title: "Mediatomb problem!"
date: 2011-05-08
forum: General Help
---

### Post by Xiah on 2011-05-08
Evening ladies and gents, i'm abit new to Ubuntu, currently running 11.04 (Natty) and having a few (Alot) of problems over the past few days it's got my HEAD DONE IN :(!

A few things i've been trying/noticing there maybe a small problem so i'll list them one by one.

When I check home folder where my mediatomb is located, it has a small padlock next to it and it won't let me edit anything, I think this is where the 2nd problem may lie!

When I attempt to run mediatomb, i get the below error. I already have a config saved in another folder ready to run, that I know will work but i can't edit anything at all and google really isn't my friend this time!

fez@fez-6150M2MA:~$ /etc/init.d/mediatomb start
 * Starting upnp media server mediatomb                                         
touch: cannot touch `/var/run/mediatomb.pid': Permission denied
chown: changing ownership of `/var/run/mediatomb.pid': Operation not permitted
touch: cannot touch `/var/log/mediatomb.log': Permission denied
chown: changing ownership of `/var/log/mediatomb.log': Operation not permitted
Could not open log file /var/log/mediatomb.log : Permission denied                      


This is the error i get when i try /ect/init.d/mediatomb start

Any help will be massively appreciated!

---

### Post by Anonymous is Incognito on 2011-05-08
[list]
[*] You should have super-user privileges, when attempting to start a service.

The command will be:

```
sudo /etc/init.d/mediatomb start
```

You can also start the service with:

```
sudo service mediatomb start
```

This is the new and preferred way.

[*] The lock next to the folder means that you don't have the correct permissions set up.

```
sudo chmod 644 /path/to/mediatomb
```

Will give you read/write access and everyone can read it.
[/list]

---

### Post by Xiah on 2011-05-08
The mediatomb folder is just in my home folder, so
```
 sudo chmod 644 /home/fez/.mediatomb
```
should work shouldn't it? Is chmod 644 the default to get rid of the permissions for any folder? 
Tried the below and now I get command not found! 
```
sudo /ect/init.d/mediatomb start
``` 
This is slightly infuriating! However once I get the hang of it I think everything else will be ok for me. Much appreciated for the help so far

---

