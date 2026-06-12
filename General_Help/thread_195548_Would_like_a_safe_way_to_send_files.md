---
title: "Would like a safe way to send files"
date: 2006-06-13
forum: General Help
---

### Post by JohanSwe on 2006-06-13
I found it very handy and easy to mount ftp-servers on the Places meny.

But since ftp is not very safe I'd like to use something else where my password and the files sent are not visible for other computers.

Also I like to mount the directory on my places meny. I got two computers with Ubuntu Dapper. I have read a couple of threads about ssh but since this is new to me I found it difficult to understand those threads.

It's important that the other computer get stucked in the directory so it's not possible to browse all the directorys on the computer. 

I hope someone are willing to help me with this any way. That would be much approciated. :D

---

### Post by simonn on 2006-06-13
ssh is the direction you want to go in.

I have heard that you can use ssh in nautilus, like so:

ssh://[username]@[computer name]:/[directory]

ssh gives access to the whole file system though, so you have to set up an ssh chroot (see [http://chrootssh.sourceforge.net/](http://chrootssh.sourceforge.net/)) if you want to limit what the users are exposed too. This requries patching openssh and installing from source. Read the documentation on the link above.

I have done this for sftp and it works great. You need to understand building from source, patching, ssh and chroots, so if you are going to stick with "I found it difficult to understand" it is probably best to use ftp or non chrooted ssh.

EDIT: Just reread the above and it sounds a bit harsh, sorry! What I am trying to convey is that if you are concerned enough about security to want to use ssh, you NEED to learn about chroots, building from source etc. There ain't no shortcuts.

sshd is probably installed and running on your machine anyway, you can use the following to check if it is running:

```

$ ps -A | grep sshd

```

If it is not running, to start it:

```

$ sudo /etc/init.d/ssh start

```

If it is not installed... synaptic it.

Once you have it up and running, try ssh, sftp and scp (man [command] is your friend) and see how it works. Once you are used to how it works, then you can start playing with it.

Try disabling root logins and allowing access from only certain users.

Also, ssh runs on port 22 by default, so you need that port open on firewalls on computers that are running sshd.

---

### Post by JohanSwe on 2006-06-13
What is sshd and what do you mean by trying ssh, sftp and scp? How do I do that? I'm not familiar whith these words but I'd like to learn..

> I have heard that you can use ssh in nautilus, like so:

ssh://[username]@[computer name]:/[directory]
Ok, but is it also possible to use the connect to server feature under the Spaces meny?

---

### Post by eth on 2006-06-13
well they're just easier from a console:
for a secure connection to a server (secured with restricted access, as Universities servers) try 
ssh <username>@<servername>
to move files you want to use
sftp <username>@<servername>
and once inside you can move file using scp.
For detailed use of scp, there's a man section, try 
man scp

---

### Post by JohanSwe on 2006-06-13
[QUOTE=eth]well they're just easier from a console:
for a secure connection to a server (secured with restricted access, as Universities servers) try 
ssh <username>@<servername>
to move files you want to use
sftp <username>@<servername>
and once inside you can move file using scp.
For detailed use of scp, there's a man section, try 
man scp[/QUOTE]
Ok, but I'd like to use nautilus to browse files. Can I do it from the *Spaces* menu. In the *connect to server* dialog I can choose ssh as the type of service.

I can't found *sshd* in synaptic? 
Maybe this is what simonn wanted me to install? :
[I]openssh-server
Secure shell server, an rshd replacement[/I]

---

### Post by JohanSwe on 2006-06-13
[QUOTE=eth]well they're just easier from a console:
for a secure connection to a server (secured with restricted access, as Universities servers) try 
ssh <username>@<servername>
to move files you want to use
sftp <username>@<servername>
and once inside you can move file using scp.
For detailed use of scp, there's a man section, try 
man scp[/QUOTE]
I can't find sshd in synaptic. Maybe this is what simonn wants me to install:
[I]openssh-server
Secure shell server, an rshd replacement[/I]

Is to start ssh all I have to do to get it to work? What is the *ssh <username>@<servername>* command for? Logging in?

And how do I disable root logins and allowing access from only certain users.

Thank you for your help. Btw I just set up a apache server. Basically all I had to do was to install the package and put files in the www directory. Very simple :D

---

### Post by simonn on 2006-06-13
[QUOTE=JohanSwe]I can't find sshd in synaptic. Maybe this is what simonn wants me to install:
[I]openssh-server
Secure shell server, an rshd replacement[/I]
[/quote]

Yes.

BTW, YOU want to install it, not me :)

> 
Is to start ssh all I have to do to get it to work? What is the *ssh <username>@<servername>* command for? Logging in?


**sshd** is the ssh daemon (daemon = server or service in *nix nomenclature). 

You need to run this (and have the port it uses - usually 22, open on the firewall) on any computer that you want to access with ssh.

With the ssh packages in Ubuntu to start sshd you should only need to:

```

$ sudo /etc/init.d/ssh start

```

To have it started automatically on boot:

```

$ sudo update-rc.d ssh defaults

```

**ssh** is the command line client software you can use to connect to a computer running sshd. If you connect to a computer using it you will get a shell, just like terminal. You can even run X windows sessions through it... but whoa there lesley... slow down... stick to the command line for now.

**sftp** and **scp** are speciailised ssh clients. 

**scp** copies files to and from computers running sshd.

**sftp** provides an interactive ftp-like interface to ssh, i.e. you can list, put and get files, but not run anything.

> 
And how do I disable root logins and allowing access from only certain users.


Install ssh then read...

```

$ man sshd_config

```

> 
Thank you for your help. Btw I just set up a apache server. Basically all I had to do was to install the package and put files in the www directory. Very simple :D

ssh is pretty much the same... unless...

> 
It's important that the other computer get stucked in the directory so it's not possible to browse all the directorys on the computer.


You have to remember that unlike a webserver (most of the time), with ssh anyone who has access to it (or breaks into it) will probably have write access to at least some part of the system. This means that they can cause damage. IOW, it is much more important that you know why you are doing something.

BTW: if you are opening the sshd port to the internet, have a look at denyhosts - it is not in any of the repositories for Ubuntu so you have to build from source. This will help keep the script kiddies at bay.

---

### Post by JohanSwe on 2006-06-14
[QUOTE=simonn]

With the ssh packages in Ubuntu to start sshd you should only need to:
[/quote]
Thank you for your explaination :)

Well, I installed openssh-server from synaptic but the command "sudo /etc/init.d/ssh start" is not working. I get the message that there is no such command.

I searched for "ssh" and this is what was found. I thougth it might help.
```
/var/lib/dpkg/alternatives/ssh-askpass
/var/lib/dpkg/info/openssh-client.conffiles
/var/lib/dpkg/info/openssh-client.config
/var/lib/dpkg/info/openssh-client.list
/var/lib/dpkg/info/openssh-client.md5sums
/var/lib/dpkg/info/openssh-client.postinst
/var/lib/dpkg/info/openssh-client.postrm
/var/lib/dpkg/info/openssh-client.prerm
/var/lib/dpkg/info/ssh-askpass-gnome.list
/var/lib/dpkg/info/ssh-askpass-gnome.md5sums
/var/lib/dpkg/info/ssh-askpass-gnome.postinst
/var/lib/dpkg/info/ssh-askpass-gnome.prerm
/etc/X11/Xsession.d/90xorg-common_ssh-agent
/etc/alternatives/ssh-askpass
/etc/alternatives/ssh-askpass.1.gz
/etc/ssh
/etc/ssh/ssh_config
/usr/bin/ssh
/usr/bin/ssh-add
/usr/bin/ssh-agent
/usr/bin/ssh-argv0
/usr/bin/ssh-askpass
/usr/bin/ssh-copy-id
/usr/bin/ssh-keygen
/usr/bin/ssh-keyscan
/usr/lib/apt/methods/ssh
/usr/lib/firefox/libgfxpsshar.so
/usr/lib/openoffice/program/syssh.uno.so
/usr/lib/openoffice/share/Scripts/beanshell/Highlight/ButtonPressHandler.bsh
/usr/lib/openoffice/share/Scripts/javascript/Highlight/ButtonPressHandler.js
/usr/lib/openssh
/usr/lib/openssh/gnome-ssh-askpass
/usr/lib/openssh/ssh-keysign
/usr/lib/codecs/vssh264core.dll
/usr/lib/codecs/vssh264dec.dll
/usr/lib/codecs/vssh264.dll
/usr/share/doc/openssh-client
/usr/share/doc/ppp/examples/scripts/options-ssh-loc
/usr/share/doc/ppp/examples/scripts/options-ssh-rem
/usr/share/doc/ppp/examples/scripts/ppp-on-ssh
/usr/share/doc/ssh-askpass-gnome
/usr/share/doc/ssh-askpass-gnome/examples/ssh-askpass-gnome.desktop
/usr/share/gimp/2.0/gimpressionist/Presets/Crosshatch
/usr/share/gnome-mag/1_32/crosshair.xpm
/usr/share/icons/HighContrastLargePrint/48x48/filesystems/gnome-fs-ssh.png
/usr/share/icons/HighContrastLargePrintInverse/48x48/filesystems/gnome-fs-ssh.png
/usr/share/icons/Human/16x16/places/folder-remote-ssh.png
/usr/share/icons/Human/16x16/places/gnome-fs-ssh.png
/usr/share/icons/Human/24x24/places/folder-remote-ssh.png
/usr/share/icons/Human/24x24/places/gnome-fs-ssh.png
/usr/share/icons/Human/48x48/places/folder-remote-ssh.png
/usr/share/icons/Human/48x48/places/gnome-fs-ssh.png
/usr/share/icons/Human/scalable/filesystems/gnome-fs-ssh.svg
/usr/share/icons/Tangerine/16x16/places/gnome-fs-ssh.png
/usr/share/icons/Tangerine/22x22/places/gnome-fs-ssh.png
/usr/share/icons/Tangerine/24x24/places/gnome-fs-ssh.png
/usr/share/icons/Tangerine/scalable/places/folder-remote-ssh.svg
/usr/share/icons/Tangerine/scalable/places/gnome-fs-ssh.svg
/usr/share/icons/Tango/16x16/places/gnome-fs-ssh.png
/usr/share/icons/Tango/22x22/places/gnome-fs-ssh.png
/usr/share/icons/Tango/24x24/places/gnome-fs-ssh.png
/usr/share/icons/Tango/scalable/places/gnome-fs-ssh.svg
/usr/share/icons/gnome/16x16/filesystems/gnome-fs-ssh.png
/usr/share/icons/gnome/48x48/filesystems/gnome-fs-ssh.png
/usr/share/lintian/overrides/openssh-client
/usr/share/man/man1/gnome-ssh-askpass.1.gz
/usr/share/man/man1/ssh-add.1.gz
/usr/share/man/man1/ssh-agent.1.gz
/usr/share/man/man1/ssh-argv0.1.gz
/usr/share/man/man1/ssh-askpass.1.gz
/usr/share/man/man1/ssh-copy-id.1.gz
/usr/share/man/man1/ssh-keygen.1.gz
/usr/share/man/man1/ssh-keyscan.1.gz
/usr/share/man/man1/ssh.1.gz
/usr/share/man/man5/ssh_config.5.gz
/usr/share/man/man8/ssh-keysign.8.gz
/usr/share/pixmaps/ssh-askpass-gnome.png
/usr/share/vim/vim64/syntax/sshconfig.vim
/usr/share/vim/vim64/syntax/sshdconfig.vim

```

---

### Post by az on 2006-06-14
Just install ssh.  That package will install the ssh server on the box you want listening.


Yes, nautilus can connect to your ssh boxes.  Yes, it will create a nice little shortcut for you on your desktop if you use the connect to servers thing.  Yes, it is safe.

All ubuntu installs include the ssh client so that you can ssh inot another box, but you have to install the ssh server (to make your box listen for connections) yourself.  That's the security policy.

---

### Post by mlind on 2006-06-14
scp is very neat tool for doing secure file management. Just try it out after you've
installed ssh package

```

scp -r /path/to/source/ otherhost.com:/tmp

```

will copy source folder's contents to otherhost.com /tmp directory. You can even
test it locally by replacing otherhost with l*ocalhost*.

---

### Post by JohanSwe on 2006-06-15
Thank you for all you help :)

Now I have installed the package ssh. But I cant start the server?

```
chefen@chefen-desktop:~$ sudo /etc/init.d/ssh start
 * Starting OpenBSD Secure Shell server...                               [fail]

```
How can I found out what's wrong?

---

### Post by mlind on 2006-06-15
[QUOTE=JohanSwe]Thank you for all you help :)

Now I have installed the package ssh. But I cant start the server?

```
chefen@chefen-desktop:~$ sudo /etc/init.d/ssh start
 * Starting OpenBSD Secure Shell server...                               [fail]

```
How can I found out what's wrong?[/QUOTE]

ssh daemon should be already automatically started. 
/var/log/damon.log or /var/log/messages should contain information about failure

does this work?
```

sudo /etc/init.d/ssh [B]restart
[/B]
```

/edit
seems like default logging facility is auth,
so look in /var/log/auth.log

---

### Post by JohanSwe on 2006-06-15
Yes, my ssh server is up running :D

Thank you all of you.. :)

---

### Post by JohanSwe on 2006-06-15
[QUOTE=simonn]
Install ssh then read...

```

$ man sshd_config

```
[/QUOTE]

I have read man sshd_config and I have opened /etc/ssh/sshd.config

but I need help

I read about "AllowUsers"  and "PasswordAuthentication" but I don't know which users they mean and what password?

I don't want anyone without the right password for the right user to get access to my computer.

Also I'd like to know how to make identification by a key (instead of or togheter with password?) and then don't get access if they don't have a key and also if not the right key. I got Seahorse were I can export keys.

I would be happy if you could give me some examples.. :D

---

### Post by mlind on 2006-06-15
[QUOTE=JohanSwe]I have read man sshd_config and I have opened /etc/ssh/sshd.config

but I need help

I read about "AllowUsers"  and "PasswordAuthentication" but I don't know which users they mean and what password?

I don't want anyone without the right password for the right user to get access to my computer.

Also I'd like to know how to make identification by a key (instead of or togheter with password?) and then don't get access if they don't have a key and also if not the right key. I got Seahorse were I can export keys.

I would be happy if you could give me some examples.. :D[/QUOTE]

Try reading OpenSSH documentation, it should explain those parameters.

I'm not sure if this is what you're looking for, but OpenSSH supports public
key authentication [http://cfm.gs.washington.edu/security/ssh/client-pkauth/](http://cfm.gs.washington.edu/security/ssh/client-pkauth/)

---

### Post by steve.horsley on 2006-06-15
Using keys and disabling access by username/password is a good idea. I gather there are a lot of ssh worms out there that just constantly try different user/password combinations for days on end.

---

### Post by JohanSwe on 2006-06-16
[QUOTE=mlind]Try reading OpenSSH documentation, it should explain those parameters.[/QUOTE]
I have read [http://www.openbsd.org/cgi-bin/man.cgi?query=ssh_config](http://www.openbsd.org/cgi-bin/man.cgi?query=ssh_config) and [http://www.openbsd.org/cgi-bin/man.cgi?query=ssh](http://www.openbsd.org/cgi-bin/man.cgi?query=ssh) but I can't find out how to create users and passwords? 

[QUOTE=mlind]
I'm not sure if this is what you're looking for, but OpenSSH supports public
key authentication [http://cfm.gs.washington.edu/security/ssh/client-pkauth/](http://cfm.gs.washington.edu/security/ssh/client-pkauth/)[/QUOTE]
That's what I meant. Thank you

---

### Post by graigsmith on 2006-06-16
you can mount ssh just like you can mount ftp in the places menu.  just click connect to server, and select service type ssh.

---

### Post by stimpsonjcat on 2006-06-16
[QUOTE=JohanSwe]I can't find out how to create users and passwords? [/QUOTE]
you don't need to create additional users and passwords. ssh will work with your existing ubuntu user names and passwords.

just type this in a terminal:
ssh user@hostname or
ssh user@ip-address
and you will be prompted for your password on that machine.

if you add
```
AllowUsers JohanSwe stimpsonjcat
```
to your sshd.config only JohanSwe and stimpsonjcat will be allowed to log in through ssh (assuming that JohanSwe and stimpsonjcat have a user account on that host)

once you got password login working you can read the manpage for
ssh-keygen to get passwordless login working.
good luck

---

### Post by JohanSwe on 2006-06-17
I will try this! Thank you :D

---

### Post by JohanSwe on 2006-06-18
I have not yet tried to log in, but I have found out that the ssh server is automatically started when I log in to my session, even if I stopped the server before shutting down the computer.

How come? And how can I change this?

---

