---
title: "unable to access shared folder from Windows"
date: 2012-02-25
forum: General Help
---

### Post by Ewe Loon on 2012-02-25
I have recently got a pc running Ubuntu 11.10 
My knowledge of linux is very small

I have setup a shared folder, this folder is visible from computers running windows operating systems
however I am unable to access the share 
I get asked for Username and Password,

the problem is I dont have a username and password to provide
Samba is installed 

When I open "Dash home"(ubuntu computer) and enter samba into the search I get a Samba Icon,
when I click the samba icon I get asked to enter my password
when I enter my password and click "ok" I get returned back to the desktop
My account is an Administrator account

any suggestions?

---

### Post by DirtyPC on 2012-02-25
If you want to access a file from windows partion, you can just go on filesystem, host, and it takes you to the windows home, presuming your dual booting, ofc.

---

### Post by Ewe Loon on 2012-02-25
separate computers
its network sharing

---

### Post by imachavel on 2012-02-25
Whoa, wait a minute, doesn't the samba.conf file need to be configured? With come code actually saved in the .conf file? How in the world were you allowed root access to configure the samba.conf file without being asked for a name and password? 

according to this:

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

it's very easy to reset your name and password. Which is a bit surprising, considering I've heard that Linux is renowned for security. I guess any OS is renowned for security, if you know how to set it up. In windows if you forget your password there is no way to reset it, unless you download a password reset .iso, burn it to disk, then boot to it when you restart your computer, and reset the password that way. I've never gotten one of those disks to burn correctly. I'd imagine that article is short cutting, and that you need to enter the old password to reset the password. Maybe you should remove your drive, back up all your files to another computer, then reformat and reinstall, this time taking note of the name and password that linux requests upon installation. Not trying to be rude, just being honest, I know it's a pain in the ***.

How in the world did you configure file sharing between a windows computer and linux computer without being prompted as root for a name and password????

---

### Post by imachavel on 2012-02-25
> **harrylucas1 said:**
> If you want to access a file from windows partion, you can just go on filesystem, host, and it takes you to the windows home, presuming your dual booting, ofc.

yes, linux has an interesting way of letting you get files from another partition if you are dual booting, but he isn't, he is trying to file share between computers using the i.p. address of the alternate computer, and assuming all folder properties of directories he is trying to grab files from, are shared appropriately :popcorn:

---

### Post by Ewe Loon on 2012-02-25
> **imachavel said:**
> Whoa, wait a minute, doesn't the samba.conf file need to be configured? With come code actually saved in the .conf file? How in the world were you allowed root access to configure the samba.conf file without being asked for a name and password? 
1: I didn't say it was configured
2: I did get asked for a password when trying to run samba, as already stated, but it doesn't ask for username (I assume cause im an administrator) 
 
> 
according to this:
...
it's very easy to reset your name and password.
...
I know my username and password, but not sure about root password, never been asked to enter it,
> 
How in the world did you configure file sharing between a windows computer and linux computer without being prompted as root for a name and password????
what I have done so-far has been done using my administrator account

---

### Post by Ewe Loon on 2012-02-26
more info, possibly related
I downloaded eclipse , wrote a base SWT app, when I run it , I don't get a blank window, could be related to problem with samba not showing, and help identify the problem

---

### Post by Ewe Loon on 2012-03-03
I got it working

if you are having problems follow this guide
[http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/]("http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/")

---

