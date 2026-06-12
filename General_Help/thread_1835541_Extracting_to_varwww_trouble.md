---
title: "Extracting to /var/www trouble"
date: 2011-08-29
forum: General Help
---

### Post by Timster4life on 2011-08-29
Hello all!

Sorry if this seams a bit trivial, still new to Linux and on a crash learning course..
Are company has decided to run WordPress off  some virtualized LAMP servers and I am in charge of getting the first machine up and running. I install lamp with full GUI to make it easier on the editors and other sys-admins etc (as well as myself)... Now  I downloaded the latest WordPress, open with archive manager.. when I go to extract it, it states I am not the owner of the folder so this is not possible. I want to make sure I do this the correct way and keep security in tact. Any help is greatly appreciated!!

11.04 Ubuntu LAMP server W/GUI No unity
Virtual machine

---

### Post by kartabosh on 2011-08-29
> **Timster4life said:**
> Hello all!

Sorry if this seams a bit trivial, still new to Linux and on a crash learning course..
Are company has decided to run WordPress off  some virtualized LAMP servers and I am in charge of getting the first machine up and running. I install lamp with full GUI to make it easier on the editors and other sys-admins etc (as well as myself)... Now  I downloaded the latest WordPress, open with archive manager.. when I go to extract it, it states I am not the owner of the folder so this is not possible. I want to make sure I do this the correct way and keep security in tact. Any help is greatly appreciated!!

11.04 Ubuntu LAMP server W/GUI No unity
Virtual machine

well, the root user is the owner of everything that's outside of your home folder 
i suggest you create a folder inside your home folder and create a symbolic link to /var/www
that's what i did 

i have a .www folder in /home/ali/.www 
to create a symbolic link first remove the old /var/www 
```
sudo rm -rf /var/www

```then create the symbolic link with 
```
sudo ln -s /home/ali/.www /var/www 

```(replace my path with your path) 
then place the files in your .www folder 

if you don't want to do this and would prefer to use /var/www just 
```
sudo chown -R ali:ali /var/www 

```and that folder should be yours (needless to say, replace ali:ali with your-user-name:your-user-name

---

### Post by bodhi.zazen on 2011-08-29
Sorry, but that is horrible advice.

/var/www is owned by root, so you have to use sudo to copy the files or gksu nautilus

The files must be readable by the apache user, www-data .

See :

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

The problems with the above solution are:

1. It does not explain permissions to you.

2. It compromises security, which is a horrible idea when using apache.

---

### Post by Timster4life on 2011-08-29
> **bodhi.zazen said:**
> Sorry, but that is horrible advice.

/var/www is owned by root, so you have to use sudo to copy the files or gksu nautilus

The files must be readable by the apache user, www-data .

See :

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

The problems with the above solution are:

1. It does not explain permissions to you.

2. It compromises security, which is a horrible idea when using apache.

Thank you so much for your help and prompt reply!
I'm learning more and more every day and this is a big help!
I havent read through all the material you provided yet, one quick question is... on a walkthrough I read for installing wordpress.. it states to just use archive manager and extract it to /www using the GUI. Not one person had mention of the problem in the comments.. so I wasn't sure if I was overlooking a simple step, or possibly some type of setting not involving terminal considering none of the other steps involved it. 

Any-who,Thank you again!

---

### Post by bodhi.zazen on 2011-08-29
Wordpress is in the ubuntu repositories.

```
sudo apt-get install wordpress
```

---

### Post by Timster4life on 2011-08-29
> **bodhi.zazen said:**
> Wordpress is in the ubuntu repositories.

```
sudo apt-get install wordpress
```


I was thrilled to find that out! Once "installed" however.. I didn't find it under www, or if I went to 127.0.0.1/wordpress nothing appeared..

I finally just decided.. why not extract it to desktop than use sudo mv to move it to /var/www and Voila! 

```
Sudo mv wordpress /var/www
```

 Thanks for the responses and the step in the right direction, much appreciated!

---

### Post by bodhi.zazen on 2011-08-29
For further information on wordpress, see :

[https://help.ubuntu.com/community/WordPress](https://help.ubuntu.com/community/WordPress)

---

### Post by kartabosh on 2011-08-29
> **bodhi.zazen said:**
> Sorry, but that is horrible advice.

/var/www is owned by root, so you have to use sudo to copy the files or gksu nautilus

The files must be readable by the apache user, www-data .

See :

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

The problems with the above solution are:

1. It does not explain permissions to you.

2. It compromises security, which is a horrible idea when using apache.

that's what i do, but i do guess i don't really care about permissions and security, my sudo never asks for password and i find myself running as root most of the time
so in my case my solution doesn't matter, if he's into that whole security thing my solution is not recommended

---

