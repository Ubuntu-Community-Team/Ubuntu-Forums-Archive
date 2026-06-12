---
title: "file transfer from shell account ???"
date: 2011-03-03
forum: General Help
---

### Post by vivek.pandey on 2011-03-03
hi everyone
   today itself i joined a shell account given to me by cjb.net.. i am able to ssh shell.cjb.net from my putty... but how can i download files or get help from the this server... i mean as far as i know these shell accounts give you files and help you know more about shell..i have bash shell
i browsed a lot for it but couldnt get a solution :-(
anybody with a solution ?
thanx in advance

---

### Post by Lars Noodén on 2011-03-03
Your file manager (e.g. konqueror) probably has built in SFTP support.  So you can use that.  There are quite a few [SFTP clients](http://en.wikibooks.org/wiki/OpenSSH/Client_Applications#GUI_Clients) to choose from.

---

### Post by vivek.pandey on 2011-03-03
> **Lars Noodén said:**
> Your file manager (e.g. konqueror) probably has built in SFTP support.  So you can use that.  There are quite a few [SFTP clients](http://en.wikibooks.org/wiki/OpenSSH/Client_Applications#GUI_Clients) to choose from.

and after installing those clients how should i proceed? i mean how will i come to know the list of files the server keeps for downloading

---

### Post by Lars Noodén on 2011-03-03
Put in the URL for the remote host, starting with **sftp://**.

---

### Post by vivek.pandey on 2011-03-03
> **Lars Noodén said:**
> Put in the URL for the remote host, starting with **sftp://**.

do you have a shell account?

---

### Post by ThaDoctor99 on 2011-03-03
And why is it you want to download a file without knowing where the file is or whether there really is a file to be downloaded.?

---

### Post by vivek.pandey on 2011-03-03
> **ThaDoctor99 said:**
> And why is it you want to download a file without knowing where the file is or whether there really is a file to be downloaded.?

i just want to know what all things i can do with my shell account and how... have heard that a linux user should have a shell account . he gets to learn a lot.. so i just wanna know what all files they have and how are they useful

---

### Post by matt_symes on 2011-03-03
Hi

```
man sftp
```

Upload some test files and then re-download then to get the basic feel.

Root around with ssh to see what you have there.

Kind regards

---

### Post by vivek.pandey on 2011-03-03
> **matt_symes said:**
> Hi

```
man sftp
```

Upload some test files and then re-download then to get the basic feel.

Kind regards

thanx for your reply and how to know what all files a server is providing me?

---

### Post by matt_symes on 2011-03-03
Hi

Logon using ssh. View directory contents using standard 

```
ssh <username>@<address> -p <port number>
ls -al
cd <dir>
```

commands. 

I expect you might be in a chrooted directory so there might not be much there or you might be in a VM. Have a root around and see. Create directories, upload files etc.

Sounds like a lot of fun.

Kind regards

---

### Post by vivek.pandey on 2011-03-03
> **matt_symes said:**
> Hi

Logon using ssh. View directory contents using standard 

```
ssh <username>@<address> -p <port number>
ls -al
cd <dir>
```

commands. 

I expect you might be in a chrooted directory so there might not be much there or you might be in a VM. Have a root around and see. Create directories, upload files etc.

Sounds like a lot of fun.

Kind regards

thanx for answering
k if i ssh in the server i get a bash shell so if i type ls -al that would be listing all the files that i have in my account or say virtual home directory i dont think it would list files available for me from server

---

### Post by jerome1232 on 2011-03-03
It looks like those shells accounts are mainly intended for use as a tunnel so you can use the web and hide your real ip address.


Usually on a shell account like that you would only have access to your users home folder, so if there are any file preloaded onto the account to give you help they would be there. Those are FreeBSD accounts so some commands are going to be different than for a Linux OS.

Use the command ls to get a list of files in your pwd (present working directory) probably your users home folder if you've just logged in.

Use cd *directoryname* to change directories.

See a text file? you can view it with cat, assuming FreeBSD has the Less program you can use less for easier viewing.

less *filename*


so an example would be like this....

```
jeremy@jeremy-Virtualbox:~$ ls
Documents
jeremy@jeremy-Virtualbox:~$ cd Documents
jeremy@jeremy-Virutalbox:~/Documents$ ls
file
jeremy@jeremy-Virutalbox:~/Docuemnts$ less file
Hey this is a text file!
file (END) _
```

---

### Post by matt_symes on 2011-03-03
Hi

> k if i ssh in the server i get a bash shell so if i type ls -al that would be listing all the files that i have in my account or say virtual home directory i dont think it would list files available for me from server

That is quite possibly all the files you may have access to.

It would be good practice to sftp some files to your home directory and then download them again.

As to what files you can down load from them, send them an e-mail and ask them.

What do you want the shell account for ? 

You should understand i don't have a shell account with an ISP but i do manage all my servers remotely using ssh and sftp etc.

EDIT: I am reading up on cjb.net now.

Kind regards

---

### Post by matt_symes on 2011-03-03
Hi

Here you go from the web site

> Software

What commands and software are available?
All shell accounts include access to the FreeBSD binaries and libraries, compilers, scripting languages (Perl/PHP/Python/Ruby/Tcl), editors (emacs/nano/pico/vi/vim), shells (bash/csh/sh/tcsh), Lynx, wget, and other utilities, and more than 10,000 software packages to install in your home directory.

How do I install a software package?
Enter the command you want to use at the prompt. If it is available in a package, installation instructions will be provided. Otherwise, you may need to compile and install from source.

A package I installed didn't work.
Packages are a quick and easy way to install basic commands. Unfortunately, some packages have hard coded system paths or other dependencies which prevents them from working when installed this way. In these cases, you may need to compile and install from source.

How do I list the packages I have installed or remove a package?
Type 'installedhome' at the prompt to list the packages you have installed and how to remove them.

What operating system do you use and what are the server specifications?
Our shell server runs the FreeBSD 8.1 amd64 operating system on an Intel quad core 3 GHz processor with 16GB of RAM and 1TB of disk space.

Get reading up on freeBSD :)

EDIT: Have a look at this.

[http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/ports-finding-applications.html](http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/ports-finding-applications.html)

and specifically this part of it

> If you do not know the name of the application you want, try using a site like FreshMeat ([http://www.freshmeat.net/](http://www.freshmeat.net/)) to find an application, then check back at the FreeBSD site to see if the application has been ported yet.

It might help with finding software names you want.

Kind regards

---

### Post by vivek.pandey on 2011-03-03
thanx everyone for your invaluable replies
i will follow all links and commands by you people
and a special thanx to matt_symes for taking pain to browse websites for me
will return soon if i cant get to find any binaries from them :-) ;-)

---

### Post by jerome1232 on 2011-03-03
Looks like they have their special system for installing software.

if you want to install a package type the name of the package and it will tell you if it's avaible or not and if it is then how to install it.

ie
```

htop

htop is not installed, but is available in the following package(s):

Package:        htop
Description:    A better top(1) - interactive process viewer

Use the following command to install a package in your home directory:

installhome <package>

Died at /usr/local/packages/bin/htop line 18.
[jerome1232@shell ~]$ installhome htop
htop has been installed in your home directory.
lsof-4.84A,5 has been installed in your home directory as a dependency.


```

---

### Post by matt_symes on 2011-03-03
Hi

I think we have all helped here. :D Sounds like it will be great fun playing around.

Was the shell account expensive ? How long did you get it for ?

Kind regards

---

### Post by vivek.pandey on 2011-03-03
> **jerome1232 said:**
> Looks like they have their special system for installing software.

if you want to install a package type the name of the package and it will tell you if it's avaible or not and if it is then how to install it.

ie
```

htop

htop is not installed, but is available in the following package(s):

Package:        htop
Description:    A better top(1) - interactive process viewer

Use the following command to install a package in your home directory:

installhome <package>

Died at /usr/local/packages/bin/htop line 18.
[jerome1232@shell ~]$ installhome htop
htop has been installed in your home directory.
lsof-4.84A,5 has been installed in your home directory as a dependency.


```

 i am really gratefu towards you for being such a great help..yeah i saw their package installing system but they mention that they would give access to some binaries and libraries .. how to know which binaries and also these binaries and libraries would consider the codes for say software nmap.. i know binaries to linux are like installation .exe files to windows...

---

### Post by vivek.pandey on 2011-03-03
> **matt_symes said:**
> Hi

I think we have all helped here. :D Sounds like it will be great fun playing around.

Was the shell account expensive ? How long did you get it for ?

Kind regards

that shell account is FREE OF COST.. plus you just need to register it in same way as tis forum . they will give you an activation link and thats it ;-) :-)....only condition is it seems we need to be an active member...

---

### Post by matt_symes on 2011-03-03
Hi

> that shell account is FREE OF COST.. plus you just need to register it in same way as tis forum . they will give you an activation link and thats it  ....only condition is it seems we need to be an active member...

Nice. I did not check that one link. I have set up an account for myself and i am going to have a play and see what it can do.

Nice find. You the man. :popcorn:

Kind regards

---

### Post by vivek.pandey on 2011-03-03
> **matt_symes said:**
> Hi



Nice. I did not check that one link. I have set up an account for myself and i am going to have a play and see what it can do.

Nice find. You the man. :popcorn:

Kind regards

hey if you get to learn something new and interesting and you feel you can share it then please let me know even i am going to try do something in there

---

### Post by matt_symes on 2011-03-03
Hi

> hey if you get to learn something new and interesting and you feel you can share it then please let me know even i am going to try do something in there

> Can I use public key authentication to log in?
Yes, public key authentication is supported.

One of the first things i will do is set up ssh keys to make it secure and require no password. I will do that tomorrow. When i have done that i will tell you how i did it so you can set it up. Then you must make a backup of your private keys.

Kind regards

---

### Post by vivek.pandey on 2011-03-03
> **matt_symes said:**
> Hi





One of the first things i will do is set up ssh keys to make it secure and require no password. I will do that tomorrow. When i have done that i will tell you how i did it so you can set it up. Then you must make a backup of your private keys.

Kind regards

what i do is i type shell.cjb.net in putty then putty terminal pops r and i am required my user name and then a password and after this authentication i am provided bash shell terminal.. if i type ls no file is displayed obviously because i dont have any... i need to download some files from them like some kernel code files if they provide...

---

