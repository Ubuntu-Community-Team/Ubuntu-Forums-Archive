---
title: "sudo: [command in custom PATH entry]: command not found"
date: 2011-10-29
forum: General Help
---

### Post by Techer on 2011-10-29
Hello people,

I'm doing some JFF (just for fun) web development using LAMPP (XAMPP for Linux) and I just tried to add /opt/lampp/ to $PATH by adding```
export PATH=$PATH:/opt/lampp/
``` to my ~/.bashrc so that I can use ```
$ sudo lampp start
```Instead of ```
$ sudo /opt/lampp/lampp start
``` to save an awful lot of time typing lol.

Well, the problem is that ```
asmund@Illumix:~$ echo $PATH
/home/asmund/bin:/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/asmund/bin/:/opt/lampp/
asmund@Illumix:~$ lampp start
You need to start XAMPP as root!
``` and ```
asmund@Illumix:~$ sudo echo $PATH
/home/asmund/bin:/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/asmund/bin/:/opt/lampp/
asmund@Illumix:~$ sudo lampp start
sudo: lampp: command not found
```Any idea of what I've misunderstood regarding the sudo command?

 Thanks in advance

---

### Post by mcduck on 2011-10-29
What are the ownership & permissions of the lampp executable?

(anyway, I'd actually recommend using the native LAMPP stack from Ubuntu's repositories instead. Integrates better with the rest of the OS, plus you can always use the official server guides and you'll also get better support from the community... And of course managing it is the same as with a real production server so any stuff you might have to learn with it will be more useful than things you might have to learn to make XAMPP work... ;))

---

### Post by hwttdz on 2011-10-29
When running a command as another user, perhaps the super user, it's their path that matters not your own.  Observe

whoami
sudo whoami

or even

echo $PATH
sudo echo $PATH

---

### Post by Techer on 2011-10-29
> **mcduck said:**
> What are the ownership & permissions of the lampp executable?
This:
```
asmund@Illumix:~$ ls -l /opt/lampp/lampp
-rwxr-xr-x 1 root root 15325 2011-09-02 12:41 /opt/lampp/lampp
```> (anyway, I'd actually recommend using **the native LAMPP stack from Ubuntu's repositories** instead. Integrates better with the rest of the OS, plus you can always use the official server guides and you'll also get better support from the community... And of course managing it is the same as with a real production server so any stuff you might have to learn with it will be more useful than things you might have to learn to make XAMPP work... ;))Actually a friend of mine suggested that yesterday but I can't find it :confused:. I've tried searching with synaptic but the closest i could find was [FONT=Courier New]syscp[/FONT] ("system control panel for LAMP servers"). Where do I find it?

When running a command as another user, perhaps the super user, it's their path that matters not your own.  Observe

> whoami
sudo whoami

or even

echo $PATH
sudo echo $PATH     If you had read my code quotes you might have noticed that [FONT=Courier New]echo $PATH [/FONT]and [FONT=Courier New]sudo echo $PATH [/FONT]prints the same.

---

### Post by hwttdz on 2011-10-29
Ahh, yes, that's because the replacement for $PATH happens before the command gets interpreted, so what you'd actually have to do is "sudo -i" and then "echo $PATH".

Or 

sudo bash -c "echo \$PATH"

---

### Post by mcduck on 2011-10-29
> **Techer said:**
> ]Actually a friend of mine suggested that yesterday but I can't find it :confused:. I've tried searching with synaptic but the closest i could find was [FONT=Courier New]syscp[/FONT] ("system control panel for LAMP servers"). Where do I find it?

There is no package called "lamp" or "lampp", it's simply a question of installing the components you want (Apache2, PHP5, MySQL and of course Perl if you need it).

The best way is to just follow the server guide: [https://help.ubuntu.com/11.10/serverguide/C/index.html]("https://help.ubuntu.com/11.10/serverguide/C/index.html")

[https://help.ubuntu.com/11.10/serverguide/C/httpd.html]("https://help.ubuntu.com/11.10/serverguide/C/httpd.html")
[https://help.ubuntu.com/11.10/serverguide/C/php5.html]("https://help.ubuntu.com/11.10/serverguide/C/php5.html")
[https://help.ubuntu.com/11.10/serverguide/C/mysql.html]("https://help.ubuntu.com/11.10/serverguide/C/mysql.html")

---

### Post by Techer on 2011-10-29
> **hwttdz said:**
> Ahh, yes, that's because the replacement for $PATH happens before the command gets interpreted, so what you'd actually have to do is "sudo -i" and then "echo $PATH".

Or 

sudo bash -c "echo \$PATH"
Ah that explains it: "sudo echo $PATH" actually calls sudo with parameter "echo /usr/bin/:/usr/local/sbin: ..." ](*,)
So I'll have to add /opt/lampp/ to the root .bashrc:idea:

> There is no package called "lamp" or "lampp", it's simply a question of  installing the components you want (Apache2, PHP5, MySQL and of course  Perl if you need it).

The best way is to just follow the server guide: [https://help.ubuntu.com/11.10/serverguide/C/index.html](https://help.ubuntu.com/11.10/serverguide/C/index.html)

[https://help.ubuntu.com/11.10/serverguide/C/httpd.html](https://help.ubuntu.com/11.10/serverguide/C/httpd.html)
[https://help.ubuntu.com/11.10/serverguide/C/php5.html](https://help.ubuntu.com/11.10/serverguide/C/php5.html)
[https://help.ubuntu.com/11.10/serverguide/C/mysql.html](https://help.ubuntu.com/11.10/serverguide/C/mysql.html)OK I'll give that a shot.

Thank you so much both of you :D Ju meid mai oikNd :KS

---

