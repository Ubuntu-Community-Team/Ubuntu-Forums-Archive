---
title: "SSH help"
date: 2010-09-02
forum: General Help
---

### Post by djyoung4 on 2010-09-02
I have a nokia n900 home and I would like to be able to SSH into it from my desktop running ubuntu 10.04 x64.  I haven't been able to find any beginner tutorials through google so if somebody could walk me through some basic steps that would be awesome.  thanks for all the help

---

### Post by djyoung4 on 2010-09-03
bump

---

### Post by earthpigg on 2010-09-03
could you show us what ssh tutorials you ***did*** find?

---

### Post by dulbirakan on 2010-09-03
What kind of SSH help do you require? Do you need a general SSH help or like something specific to Nokia n900?

I have found this brief guide on n900: [http://www.nokian900applications.com/openssh-on-nokia-n900/]("http://www.nokian900applications.com/openssh-on-nokia-n900/")

Seems like you should first install openssh server on n900. I dont know anything about n900 so you should figure out how to install openssh on it.  Then you will access it through 'root' user with password 'OpenSSH'. To get the device's IP adress you should run. 

```
ipconfig -a
``` on your n900

Then on the machine you want to access n900 from, run:

```
ssh root@<ip.add.re.ss>
```

Then it will prompt for a password. After that you are done.

You might want to investigate the scp command for file transfer purposes.
Hope that will help

---

### Post by djyoung4 on 2010-09-03
> **earthpigg said:**
> could you show us what ssh tutorials you ***did*** find?
[SSh Tutorial for Linux]("http://support.suso.com/supki/SSH_Tutorial_for_Linux")
[Getting started with SSH]("http://kimmo.suominen.com/docs/ssh/")
> **dulbirakan said:**
> What kind of SSH help do you require? Do you need a general SSH help or like something specific to Nokia n900?

I have found this brief guide on n900: [http://www.nokian900applications.com/openssh-on-nokia-n900/]("http://www.nokian900applications.com/openssh-on-nokia-n900/")

Seems like you should first install openssh server on n900. I dont know anything about n900 so you should figure out how to install openssh on it.  Then you will access it through 'root' user with password 'OpenSSH'. To get the device's IP adress you should run. 

```
ipconfig -a
``` on your n900

Then on the machine you want to access n900 from, run:

```
ssh root@<ip.add.re.ss>
```

Then it will prompt for a password. After that you are done.

You might want to investigate the scp command for file transfer purposes.
Hope that will help
Thanks for that.  my N900 has OpenSSH running on it.  I read that tutorial you gave me and couldn't figure out how to use the program it suggests.  Its for windows only so i was just confused.  Ill try this once I get off my schools wifi.

---

### Post by djyoung4 on 2010-09-05
i couldnt get it to work.  any suggestions

---

### Post by Intersys on 2012-08-03
I know this topic is very old, but if u still need help setting it up, its quite easy. did it with ubuntu 11.10 x64. 

U need to install these apps on N900:
OpenSSH Client
OpenSSH Client and Server (when asked for password enter and confirm a pass easy to remember)
SSH Status and Switcher (After installation you will be able to see SSH status plugin in your Status Menu. You can enable or disable it from there)

download personal IP address widget to see your n900 ip.

afterwards on your terminal from pc, type:  **ssh root@”ip address of phone written here”**

---

### Post by wildmanne39 on 2012-08-04
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

