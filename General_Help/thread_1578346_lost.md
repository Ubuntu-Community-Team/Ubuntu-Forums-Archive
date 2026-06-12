---
title: "lost"
date: 2010-09-20
forum: General Help
---

### Post by xdweaver on 2010-09-20
Okay so I have been trying to install a program called piano booster and I am almost there, however i keep getting this error. So I went to the Synaptic package manager and I get this error

E: Type 'n' is not known on line 2 in source list /etc/apt/sources.list.d/racb-extra-lucid.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

I have no idea how to even fix this or where to go to get this corrected???? I AM LOST

---

### Post by Bizurke on 2010-09-20
There is something wrong with an entry in your sources list at /etc/apt/sources.list.d/racb-extra-lucid.list. If you can copy the file and post it here we will be able to help you better. 

```
cat /etc/apt/sources.list.d/racb-extra-lucid.list
``` in a terminal, then copy and paste it here.

---

### Post by xdweaver on 2010-09-20
wendy@ubuntu:~$ cat /etc/apt/sources.list.d/racb-extra-lucid.list
deb [http://ppa.launchpad.net/racb/extra/ubuntu](http://ppa.launchpad.net/racb/extra/ubuntu) lucid main
n
wendy@ubuntu:~$ 

 thank you for helping

---

### Post by xdweaver on 2010-09-20
> **Bizurke said:**
> There is something wrong with an entry in your sources list at /etc/apt/sources.list.d/racb-extra-lucid.list. If you can copy the file and post it here we will be able to help you better. 

```
cat /etc/apt/sources.list.d/racb-extra-lucid.list
``` in a terminal, then copy and paste it here.

wendy@ubuntu:~$ cat /etc/apt/sources.list.d/racb-extra-lucid.list
deb [http://ppa.launchpad.net/racb/extra/ubuntu](http://ppa.launchpad.net/racb/extra/ubuntu) lucid main
n
wendy@ubuntu:~$ 

 thank you for helping

---

### Post by scottuss on 2010-09-20
> **xdweaver said:**
> wendy@ubuntu:~$ cat /etc/apt/sources.list.d/racb-extra-lucid.list
deb [http://ppa.launchpad.net/racb/extra/ubuntu](http://ppa.launchpad.net/racb/extra/ubuntu) lucid main
n
wendy@ubuntu:~$ 

 thank you for helping

The line that says "n" should not be there. Remove it, save the file and try again.

---

### Post by Bizurke on 2010-09-20
Remove the "n" at the end of that line and you should be good. You can edit it in nano or gedit pretty simply. 

```
sudo nano /etc/apt/sources.list.d/racb-extra-lucid.list
``` 

remove the "n" at the end of that line and then push ctrl+o to save and ctrl+x to close nano. 

alternatively you can do this as root in gedit by pressing alt+f2 then ```
gksu gedit /etc/apt/sources.list.d/racb-extra-lucid.list
``` and saving the file.

Once this is done update your sources. ```
sudo apt-get update
```. Then try to continue where you left off with the program.

---

### Post by xdweaver on 2010-09-20
> **scottuss said:**
> The line that says "n" should not be there. Remove it, save the file and try again.

yea that is where i am stuck, i go to remove it  but not sure i am going to the right place?

---

### Post by lykeion on 2010-09-20
Try this:
[LIST]
[*]Close Synaptic
[*]Start a terminal (Applications > Accessories > Terminal) and enter this:```
gksu gedit /etc/apt/sources.list.d/racb-extra-lucid.list
```
[*]Delete the second line with the 'n'
[*]Save and exit
[*]Start Synaptic, click Reload and try again
[/LIST]

---

### Post by scottuss on 2010-09-20
I'm confused. If you've posted the contents of the file, how did you see them? Use nano (run it as root by using sudo)

In terminal:

sudo nano /etc/apt/sources.list.d/racb-extra-lucid.list

Then delete the "n" that is on it's own. Then use Ctrl+X to exit, then when it says save? say yes.

Then attempt installation again.

Perhaps do sudo apt-get update first...

---

### Post by xdweaver on 2010-09-20
> **Bizurke said:**
> Remove the "n" at the end of that line and you should be good. You can edit it in nano or gedit pretty simply. 

```
sudo nano /etc/apt/sources.list.d/racb-extra-lucid.list
```remove the "n" at the end of that line and then push ctrl+o to save and ctrl+x to close nano. 

alternatively you can do this as root in gedit by pressing alt+f2 then ```
gksu gedit /etc/apt/sources.list.d/racb-extra-lucid.list
``` and saving the file.

Once this is done update your sources. ```
sudo apt-get update
```. Then try to continue where you left off with the program.

 Okay so all that done did an update the tried again to install and get this:
wendy@ubuntu:~$ sudo apt-repository ppa:racb/extra
[sudo] password for wendy: 
sudo: apt-repository: command not found
wendy@ubuntu:~$ sudo apt-get install pianobooster
E: Type 'n' is not known on line 2 in source list /etc/apt/sources.list.d/racb-extra-lucid.list
E: The list of sources could not be read.
wendy@ubuntu:~$ cat /etc/apt/sources.list.d/racb-extra-lucid.list
deb [http://ppa.launchpad.net/racb/extra/ubuntu](http://ppa.launchpad.net/racb/extra/ubuntu) lucid main
n
wendy@ubuntu:~$ ~sudo apt-get update
No command '~sudo' found, did you mean:
 Command 'sudo' from package 'sudo' (main)
 Command 'sudo' from package 'sudo-ldap' (universe)
~sudo: command not found
wendy@ubuntu:~$ sudo apt-get update
[sudo] password for wendy: 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg
Ign [http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/](http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/) jaunty/main Translation-en_US
Ign [http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/](http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/) jaunty/deb-src Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg [198B]
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Ign [http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/](http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/) jaunty/http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu Translation-en_US
Ign [http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/](http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/) jaunty/jaunty Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg 
Ign [http://ppa.launchpad.net/racb/extra/ubuntu/](http://ppa.launchpad.net/racb/extra/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                          
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release [44.7kB]              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages [297kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages [3,252B]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages [118kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages [3,771B]
Fetched 467kB in 3s (148kB/s)                           
W: Failed to fetch [http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/dists/jaunty/Release](http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/dists/jaunty/Release)  Unable to find expected entry  deb-src/binary-i386/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
wendy@ubuntu:~$ sudo apt-get install pianobooster
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
wendy@ubuntu:~$

---

### Post by lykeion on 2010-09-20
Close Synaptic and try again

You'll get problems using two package managers at the same time (i.e Synaptic and dpkg from the command-line)

EDIT
The thread-killer strikes again it seems :-)

---

