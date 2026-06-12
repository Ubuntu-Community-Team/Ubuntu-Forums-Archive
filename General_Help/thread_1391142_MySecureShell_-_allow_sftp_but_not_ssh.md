---
title: "MySecureShell - allow sftp but not ssh"
date: 2010-01-26
forum: General Help
---

### Post by KayakJim on 2010-01-26
I have Ubuntu 8.04 64-bit server and use MySecureShell to jail certain users to their home directories.

Does anyone know if it is possible to allow those users to only connect via sftp but not allow ssh?

If so, any guidance on the proper configuration for the above would be greatly appreciated.

---

### Post by bluefrog on 2010-01-27
don't know about mysecureshell.

otherwise to do what you want you can use the sshd functionnality.

edit /etc/ssh/sshd_config
#Subsystem sftp /usr/lib/openssh/sftp-server
Subsystem sftp internal-sftp
UsePAM yes
Match User user  (can use Group group-name if you wish)
 ChrootDirectory %h
 ForceCommand internal-sftp

Users listed there will be able to sftp only

---

### Post by KayakJim on 2010-01-27
> **bluefrog said:**
> don't know about mysecureshell.

otherwise to do what you want you can use the sshd functionnality.

edit /etc/ssh/sshd_config
#Subsystem sftp /usr/lib/openssh/sftp-server
Subsystem sftp internal-sftp
UsePAM yes
Match User user  (can use Group group-name if you wish)
 ChrootDirectory %h
 ForceCommand internal-sftp

Users listed there will be able to sftp only

It was my understanding that the ChrootDirectory directive did not become available until OpenSSH v4.9 while Ubuntu 8.04 Hardy only has OpenSSh v4.7 available to it.

Am I mistaken or is there a way to upgrade to OpenSSH v4.9 in Hardy?

---

### Post by bluefrog on 2010-01-27
sorry missed hardy.

using 9.04 and onward. can't tell about old versions. but indeed it has been implemented lately in openssh.

---

### Post by Lars Noodén on 2010-01-27
> **KayakJim said:**
> 
Am I mistaken or is there a way to upgrade to OpenSSH v4.9 in Hardy?

Hardy is a Long Term Release so it should be supported on the server for 5 years.  That means that the versions for the applications stay the same, but there is an extra repository for new versions that are 'backported'.

[openssh-server 5.3 is not yet backported to hardy](http://packages.ubuntu.com/search?keywords=openssh-server&searchon=names&suite=hardy-backports&section=all).  If you post a request on launchpad for it and post the link here, I am sure that others will back your request.

---

### Post by KayakJim on 2010-01-28
> **Lars Noodén said:**
> Hardy is a Long Term Release so it should be supported on the server for 5 years.  That means that the versions for the applications stay the same, but there is an extra repository for new versions that are 'backported'.

[openssh-server 5.3 is not yet backported to hardy](http://packages.ubuntu.com/search?keywords=openssh-server&searchon=names&suite=hardy-backports&section=all).  If you post a request on launchpad for it and post the link here, I am sure that others will back your request.

Thank you for the info Lars and I will follow your advice on that issue.

Any ideas on how I can accomplish my goals with what I currently have?

---

### Post by Lars Noodén on 2010-01-28
> **KayakJim said:**
> 
Any ideas on how I can accomplish my goals with what I currently have?

Start with posting the link to the request for the backport.  

As for retrofitting 4.7, if you are very comfortable with building your own packages then you could apply a patch to the source code for 4.7, but it would be easier then to build your own package for 5.3.

---

### Post by KayakJim on 2010-01-28
> **Lars Noodén said:**
> Start with posting the link to the request for the backport.  

As for retrofitting 4.7, if you are very comfortable with building your own packages then you could apply a patch to the source code for 4.7, but it would be easier then to build your own package for 5.3.

Thanks again Lars but my statement was referring to my current environment of using MySecureShell. ;)

---

### Post by Lars Noodén on 2010-01-29
Ok.  My response was for your current environment, which is Hardy Heron.  

Where did you find MySecureShell?  I'm not finding any [packages with that name](http://packages.ubuntu.com/search?keywords=+MySecureShell+&searchon=names&suite=all&section=all) or any packages [originating from projects with that name](http://packages.ubuntu.com/search?keywords=+MySecureShell+&searchon=sourcenames&suite=all&section=all).

---

### Post by KayakJim on 2010-01-29
I found MySecureShell after reading a number of posts here on the forums that provided a jailed shell to users. It works great so far. I am just wondering if it is possible to further restrict users to only sftp connections.

[http://mysecureshell.sourceforge.net/]("http://mysecureshell.sourceforge.net/")

---

### Post by Lars Noodén on 2010-01-29
> **KayakJim said:**
> I found MySecureShell after reading a number of posts here on the forums that provided a jailed shell to users. It works great so far. I am just wondering if it is possible to further restrict users to only sftp connections.

[http://mysecureshell.sourceforge.net/]("http://mysecureshell.sourceforge.net/")

Ok.  There's not much in English for it.  It is a derivative of OpenSSH and recent versions of OpenSSH do exactly what you want.

However, the English version of description for the [shell](http://mysecureshell.sourceforge.net/en/Shell.html) directive in the configuration implies that sftp-only is the default.  [http://mysecureshell.sourceforge.net/fr/Shell.html](http://mysecureshell.sourceforge.net/fr/Shell.html)

Try and see if you can connect with the shell.  If not, then it's already set.  If you can then use the Shell directive to explicitly set the shell to something like the path to the sftp-subsystem.  Don't lock yourself out during the experimenting, though.

---

### Post by KayakJim on 2010-01-29
Unfortunately for English you have to rely on Google translation, which leaves much to be desired.

I am able to connect via SSH and SFTP, which is what prompted me to ask my question here on the forums. I will try out the sftp-subsystem as you suggested.

Thanks for the guidance!  :)

---

### Post by Lars Noodén on 2010-01-31
> **KayakJim said:**
>  I will try out the sftp-subsystem as you suggested

It might need a bit of fiddling to get all the pieces into the chroot jail.

Another deriviative of OpenSSH like MySecureShell is Dropbear.  I haven't played with that but you are able to pick and choose more easily the components to use.  

However, it still might be easiest to get OpenSSH 5.3 ...

---

