---
title: "Dosemu Cannot Connect To Network Drive"
date: 2009-11-26
forum: General Help
---

### Post by wrgt on 2009-11-26
My computer is using Ubuntu Jaunty 9.04 and I wanted to try Karmic 9.10 so I installed Karmic on another computer, set it up and replaced the Jaunty computer. The problem is Dosemu cannot change to the network drive. When I type cd sis, it returns chdir failed for sis. Jaunty computer doesn't have this problem. 

My setup is adding this line to fstab to create a network drive in Karmic computer connecting to the server 169.254.1.101:

//169.254.1.101/sis /home/ws1/sis cifs username"",password""

IP address for Karmic computer is 169.254.1.102, subnet mask 255.255.0.0, gateway 169.254.1.1 (no internet connection, I just need to fill this field)

This enables me to access the files in the server's folder sis. 

In Jaunty computer, I can change folder to sis in Dosemu, but this is not possible in Karmic computer. Typing ls -l in terminal displayed the properties of the folder sis in Jaunty computer:

drwxrwxrwx

and in Karmic computer:

drwxr-xr-x

is this the cause of the failure of Dosemu changing folders? I tried changing the properties in Karmic computer by using chmod:

chmod go+w sis
sudo chmod go+w sis

but it won't allow me (permission denied). Logging in as root gives the same result. 

Any suggestions?

---

### Post by ocascante on 2009-12-14
Hi,

I have the same problem.
With ubuntu 9.03 all cifs mounted folders works well.
After upgrade to 9.10, i have no access to mounted folders from dosemu.
Dosemu 35 error ( network name not found )
Any help!!

---

### Post by wrgt on 2010-01-04
I tried adding umask=000 to my fstab but this didn't work.

---

### Post by samant on 2010-01-05
I have exactly the same problem after updating from Jaunty to Karmic. I have a cifs share, mounted to /I, and I'm connected to it in dosemu through lredir i: linux\fs/I. Everything worked in 9.04, but now dosemu writes: Error 35 (network name not found). Any ideas? Please...

---

### Post by wrgt on 2010-01-16
do you guys have the following options in your fstab cifs entry?

uid=1000
gid=1000
noperm
file_mode=0777
dir_mode=0777

I haven't tried any of these. Could anyone explain what to these options mean?

---

### Post by wrgt on 2010-01-23
well, I tried all of the options I mentioned, and none worked. 

does anyone has a suggestion?

---

### Post by juanJosepablos on 2010-01-25
You can find more info here:
[http://marc.info/?t=123453458800002&r=1&w=2](http://marc.info/?t=123453458800002&r=1&w=2)

Alternatively, mount the CIFS share with the option
noserverino

---

### Post by wrgt on 2010-01-27
what does noserverino do?

---

### Post by juanJosepablos on 2010-01-27
[http://linux.die.net/man/8/mount.cifs](http://linux.die.net/man/8/mount.cifs)

---

### Post by samant on 2010-01-28
My row of mounting cifs share, which doesn't work:

//10.5.96.10/share   /I   cifs   user,username=nick,password=qwerty,codepage=1251,iocharset=utf8,noperm,nobrl  0  0

noserverino has helped!!! Yahoo! Thank's, juanJosepablos.

---

### Post by wrgt on 2010-03-03
sorry it took me a long time to reply. I was playing around with some other Linux distributions. 

noserverino alone didn't work, but together with noperm, everything worked well. Here's my successful fstab entry:

//169.254.1.101/sis /home/ws1/sis cifs username"",password"",noserverino,noperm

Thank you guys for all your help.

---

### Post by Pupetier on 2010-04-29
Sorry for using this solved thread but i have the same problem and i can not solve it.

 I want to say that I am using this command to mount the shared folder (XP drive):

sudo mount -t cifs -o username=caja,password=1234,noserverino,noperm,rw //192.168.1.11/c$ /farmatronic/

 I try this with and without password, noperm and rw.

 I can access this files if i surf with cd but when a try to use this in the autoexec.bat file in dosemu, it does not work.

lredir f: linux\fs/farmatronic

and then I start dosemu, the error shows up:

Invalid drive F:

I do not know how to solve it, if someone could give me some help i will really appreciate.

Thanks in advance.

Pupetier.

---

