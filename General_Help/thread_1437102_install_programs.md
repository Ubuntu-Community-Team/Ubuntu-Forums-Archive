---
title: "install programs"
date: 2010-03-23
forum: General Help
---

### Post by rebel ahmed on 2010-03-23
[FONT=Arial Black][SIZE=5]please i have some questions[/SIZE][/FONT]

[FONT=Arial Narrow][SIZE=3]1- when i install a new program where it is installed?
2- what to do to change this directory?
3-how to log as a root from the gnome?
4- how to access  the internet from the terminal?
thanks:popcorn:
[/SIZE][/FONT]

---

### Post by darolu on 2010-03-23
1.- Open a terminal and do:
```
$ whereis <applicationname>
```
It's possible it will print more than one directory, that's normal as binaries are written in different directories than other type of files (i.e. images or sounds the app may use).

2.- You shouldn't change it, you can simply move the files to wherever you want but symlinks will need to be edited as well; don't fix something that is working though. When installing from source code, some apps allow you to choose installation location using a configuration file; always read the documentation either via README/INSTALL file or online.

3.- It is possible but is discouraged as it is dangerous, if you were aware of the risks you wouldn't be asking how to do it. Anyways System-Admin-Users and Groups sounds like a logical place to start.

4.- There are several Command Line applications that use internet, if you want to browse in text mode I recommend using "links", install with:
```
$ sudo apt-get install links
```
To go to ubuntu.com you run:
```
$ links http://www.ubuntu.com
```
If you type "**g**" while browsing you can change the URL, "**q**" to quit, you follow a link by pushing the right arrow key; full documentation with:
```
$ man links
```

Other popular cli browsers are lynx and elinks. There are command line IRC clients, e-mail applications, etc., too.

---

### Post by prodigy_ on 2010-03-23
> **rebel ahmed said:**
> 1 - when i install a new program where it is installed?
2- what to do to change this directory?
3-how to log as a root from the gnome?
4- how to access  the internet from the terminal?

1. This depends on the program. Binary executables (or symlinks) you can usually find in /usr/bin but libraries and other resources might be harder to locate.

2. If you mean changing installation paths, you'll probably have to edit source files.

3. You shouldn't login to Gnome as root. Instead, you need to use sudo command to start applications with root privileges. If you need an interactive root shell: Alt+F2, type "gnome-terminal" to start Terminal, and use "sudo -i" command.

4. If you want to check connectivity, use ```
ping <host_name_or_IP_address>
``` if you want to download a file via http: ```
wget http:://<URL>
``` if you want to use ftp ```
ftp <username>@<DNS_name_or_IP_address>
```

---

### Post by darolu on 2010-03-23
> **prodigy_ said:**
> 4. If you want to check connectivity, use ```
ping <host_name_or_IP_address>
```
Don't forget to include how many packages you want to transfers with **-c** option, or it will keep transfering packages untill you end the process, for example:
```
$ ping -c 4 www.ubuntu.com
```

---

### Post by bodhi.zazen on 2010-03-23
> **rebel ahmed said:**
> [FONT=Arial Black][SIZE=5]please i have some questions[/SIZE][/FONT]

[FONT=Arial Narrow][SIZE=3]1- when i install a new program where it is installed?[/SIZE][/FONT][FONT=Arial Narrow][SIZE=3]

Linux is not windows, so parts of the application will be installed in various locations.

See :

[http://www.freeos.com/articles/3102/](http://www.freeos.com/articles/3102/)

There are many ways to list this information, 

command line :

```
dpkg --listfiles foo
```where foo is the name of the package in question.

synaptic will do this :

[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

Seledt a package -> properties -> select the "installed files" box.

> 2- what to do to change this directory?do not change this unless you understand what you are doing.

To change you will need to install from source  code, and use 

```
./configure --prefix=/directory
```To list the options, use

./configure --help
> 3-how to log as a root from the gnome?Logging into gnome as root is not encouraged or supported here.
> 4- how to access  the internet from the terminal?
thanks:popcorn:What do you mean "Access the internet from the terminal", what do you want to do ? Configure your network card ? ping ? email ? surf the web ?[/SIZE][/FONT]

---

### Post by Serpher on 2010-03-23
1) Why do you want to know where it's installed? If it's system wide it's in /bin/, and if not it's in your home folder and a hidden file.

3) This is like the worst thing you can do. The reason why Windows is so vunurable is because you're doing something like that and you probably know how annoying viruses are on it. If you really want to do it go into terminal and type in "[b]sudo passwd[/b[". This will activate the root account for login after you change the password. From there go to the login screen and go to Other User, type in 'root' for user then your password.

4)
```
sudo apt-get install lynx
lynx http://www.google.ca/
```

Not sure exactly what you mean but I think that's what you want

---

