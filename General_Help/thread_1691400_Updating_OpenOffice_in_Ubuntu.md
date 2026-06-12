---
title: "Updating OpenOffice in Ubuntu"
date: 2011-02-19
forum: General Help
---

### Post by Wuxin on 2011-02-19
[FONT=Times New Roman][SIZE=4]I presently have OpenOffice 3.2 and I want to upgrade to 3.3.  Is there a way to do that without having to create an entirely new program?  Can you do an update that will simply modify or replace the existing version?  What is the simplest way to do this?  I am using Ubuntu 10.10.  Thank you in advance for assistance.


[/SIZE][/FONT]

---

### Post by tekkidd on 2011-02-19
This is really quite simple. 

First download the latest OpenOffice from: [http://www.openoffice.org/](http://www.openoffice.org/). Download the one respective to your system (32bit or 64bit) and language. 

After it has downloaded extract the thing somewhere.

After you have extracted it. Execute these commands:

```
cd /path/to/folder/DEBS
```

```
sudo dpkg -i *deb
```

Now go into the "Desktop Integration" folder and install that deb file. 

Thats all their is to it. 

You might also want to consider LibreOffice. Much better .docx support

If you have any issues installing just email me (my support email): [email]thetekkidd@gmail.com[/email] 

I usually respond the same day

---

### Post by Krytarik on 2011-02-19
Ohoh, the OOo people are loosing ground fastly, not even isn't it the choice for future releases of Ubuntu anymore, but they also don't manage to update the official PPA even after a month of the release.

So, I recommend replacing OOo by LibreOffice.

OOo PPA:
[https://launchpad.net/~openoffice-pkgs/+archive/ppa]("https://launchpad.net/%7Eopenoffice-pkgs/+archive/ppa")

Guide to install LibreOffice, definetely read it!:
[https://wiki.ubuntu.com/LibreOffice](https://wiki.ubuntu.com/LibreOffice)

LibreOffice PPA:
[https://launchpad.net/~libreoffice/+archive/ppa]("https://launchpad.net/%7Elibreoffice/+archive/ppa")

Greetings.

---

