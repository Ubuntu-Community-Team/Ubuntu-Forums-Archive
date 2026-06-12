---
title: "SFTP is not working"
date: 2011-02-20
forum: General Help
---

### Post by Alex1331 on 2011-02-20
Hi,

I have a problem, when I go to Places -> Connect to server... it will not show FTP or SSH as an option. The only option is custom.

I bookmarked some SFTP locations earlier, and now when I try to open them an error shows up saying that the specified location is not supported.

What is wrong? Did I remove a package?

---

### Post by tredegar on 2011-02-20
> What is wrong? Did I remove a package?
How are we to know from the information you have given us?

For **sftp** to work you need

[B]openssh-client
openssh-server
ftp[/B]

to be installed in addition to your basic installation.

---

### Post by Alex1331 on 2011-02-21
tredegar: Thank you for trying to help, what information may I provide?

I got ftp and ssh working in the terminal.

The error message:
[IMG]http://ubuntuone.com/p/eJs/[/IMG]

Connect to server(Custom Location is the only option available):
[IMG]http://ubuntuone.com/p/eJt/[/IMG]

---

### Post by tredegar on 2011-02-21
You have obscured the address of the server you are trying to connect to, so I cannot tell you if it is mal-formed in some way.

I connect to my local server simply by using **nautilus** and putting this into the address bar:
**sftp://server.home.net**

I have ssh and ftp installed and running on the server.

---

### Post by matt_symes on 2011-02-21
Hi

Open up a terminal and type

```
dpkg -l | grep -i ssh
```

That is a small L after dpkg.

Same for the below.

```
dpkg -l | grep -i ftp
```

Post the results back here.

Here is a basic sftp tutorial for the command line.

[http://www.computerhope.com/unix/sftp.htm](http://www.computerhope.com/unix/sftp.htm)

Kind regards

---

### Post by Alex1331 on 2011-02-21
```
$ dpkg -l | grep -i ssh
ii  openssh-client                       1:5.5p1-4ubuntu5                                  secure shell (SSH) client, for secure access to remote machines
rc  openssh-server                       1:5.5p1-4ubuntu5                                  secure shell (SSH) server, for secure access from remote machines
ii  python-paramiko                      1.7.6-2                                           Make ssh v2 connections with Python
ii  ssh-askpass-gnome                    1:5.5p1-4ubuntu5                                  interactive X program to prompt users for a passphrase for ssh-add

```

```
$ dpkg -l | grep -i ftp
ii  dnsmasq-base                         2.55-1                                            A small caching DNS proxy and DHCP/TFTP server
ii  ftp                                  0.17-23                                           The FTP client
ii  lftp                                 4.0.6-1                                           Sophisticated command-line FTP/HTTP client programs

```

---

### Post by bluefrog on 2011-02-21
ftp has nothing to do in here.

sftp is only using ssh.

so in the first place is open-ssh server installed on the remote machines?

---

### Post by Alex1331 on 2011-02-21
SSH server is installed.
It is fully functional in the terminal.

As shown in the pictures, I can no longer connect to my bookmarked FTP/SFTP locations.(Picture number 1) And, the only "Service Type" available in "Connect to server" is Custom Location.(Picture number 2)

When I try to open a FTP or SFTP location in Nautilus I get an error:Nautilus can not handle SFTP/ FTP locations.

I may have removed a package, but I do not know which.:confused:

---

### Post by Alex1331 on 2011-02-21
Solved the problem. :)

I removed Nautilus and installed ubuntu-desktop again.

```
sudo apt-get remove --purge nautilus
sudo apt-get install ubuntu-desktop
```

*Happy*

Thanks for helping.

---

