---
title: "How to map a drive in Ubuntu?"
date: 2010-07-06
forum: General Help
---

### Post by schwabdale on 2010-07-06
Hello,
I installed an Application through Wine. This application requires two things I do not know how to do in Ubuntu. 
First, it requires an ODBC Connection.
Second, it requires a Mapped network drive. 

I don't know how to do either. Can someone please help me with this?

---

### Post by bodhi.zazen on 2010-07-06
You do not "map" network drives in Linux, you mount them.

To have them automatically mount, use fstab.

The tools to do this are called samba, in your case samba client.

```
sudo mkdir /media/share
sudo mount -t cifs //server_name_or)ip/share /media/share
```

You can call the share anything you like and there are some variations (user name / password) depending on how you configured your server.

For ODBC see :

[http://www.easysoft.com/developer/interfaces/odbc/linux.html](http://www.easysoft.com/developer/interfaces/odbc/linux.html)

Again, it depends on what you are wanting to do. It sounds as if you are running some kind of complex windows application on wine and you may or may not have success, hard to say without more details.

---

### Post by schwabdale on 2010-07-06
In Wine, through this application (Made2Manage) it is looking for a network database 
location. It seems to be looking for a location in the \\servername\share format... And I 
have a button to find the database location. When I click the find button, my options are C:\ and D:\. 

On a Windows box, I would map a drive to the share. This drive would have a drive letter. 
I would then click the same find button and click the drive letter. 

When I use the //servername/share format it does not work
[IMG]file:///tmp/moz-screenshot.png[/IMG][IMG]file:///tmp/moz-screenshot-1.png[/IMG]

---

### Post by bodhi.zazen on 2010-07-06
You can try mounting the share and making a link.

Mount the share at say /media/share

Then make a link to your wine directory, I think it is in ~/.wine/dosdevices

```
ln -s /media/share /home/your_user/.wine/dosdevices/e:
```

Are you trying to mount a share or connect to a database ?

---

### Post by schwabdale on 2010-07-07
> **bodhi.zazen said:**
> You can try mounting the share and making a link.

Mount the share at say /media/share

Then make a link to your wine directory, I think it is in ~/.wine/dosdevices

```
ln -s /media/share /home/your_user/.wine/dosdevices/e:
```Are you trying to mount a share or connect to a database ?

I'm trying to connect to a database and all the database files under a specific folder on the network. I think the software is looking for the Database and all the containers and whatever else it needs under a specific folder. 

I can go into winecfg and give it a new drive mapping and this will show up under home/user name/.wine..... but it does not work. 

When I go into winecfg and give it a new drive mapping, it does not seem to allow me to access the network. The only option I have is on the local machine. So, I would think I could just make a link on the local linux installation and then point the wine application to the shortcut,,, but that doesn't work either. I get an error "The target does not support symbolic links"

---

### Post by schwabdale on 2010-07-08
.



```
sudo mkdir /media/share
sudo mount -t cifs //server_name_or)ip/share /media/share
```You can call the share anything you like and there are some variations (user name / password) depending on how you configured your server.




How do I plug in the username and password?
sudo mount -t cifs //server_name_or)ip/share /media/share -U administrator -p *******

---

### Post by bodhi.zazen on 2010-07-08
Use the -o user=your_user,password=your_password

mount -t cifs -o user=your_user,password=your_password //server_name_or)ip/share /home/your_user/.wine/dosdevices/e:

See also : [http://linux.die.net/man/8/mount.cifs](http://linux.die.net/man/8/mount.cifs)

---

### Post by schwabdale on 2010-07-08
Thank you for all your help. I'm pretty new at this. Is this how it should look?

mount -t cifs -o administrator ********  //server_name_or)ip/share /home/your_user/.wine/dosdevices/e:

---

### Post by bodhi.zazen on 2010-07-08
You forgot the user= and password= , and the options are comma delimitated


-o user=administrator,password=********

---

### Post by schwabdale on 2010-07-08
Well, so far so good. Now I am getting a mount error. I know the user name and password for the domain is correct. I am supplying the credentials for the domain right?
[IMG]file:///tmp/moz-screenshot.png[/IMG][IMG]file:///tmp/moz-screenshot-1.png[/IMG]

---

### Post by bodhi.zazen on 2010-07-08
Try installing smbfs

```
sudo apt-get install smbfs
```

Then try mounting the share again.

---

### Post by schwabdale on 2010-07-08
Same thing. 
Is the user and pass the domain credentials? 

I shouldn't have to do anything on the server right? This computer is not part of the domain, maybe thats the problem. But,,, the everyone group has at least read permissions. So I should be able to access the share.

---

### Post by bodhi.zazen on 2010-07-08
> **schwabdale said:**
> Same thing. 
Is the user and pass the domain credentials? 

I shouldn't have to do anything on the server right? This computer is not part of the domain, maybe thats the problem. But,,, the everyone group has at least read permissions. So I should be able to access the share.

No, user and password should be a user name and (login) password on the Windows server.

Yes, you need to have the Ubuntu computer join the Windows Domain.

[http://onlamp.com/pub/a/onlamp/2008/04/01/step-by-step-using-samba-to-join-a-windows-domain.html](http://onlamp.com/pub/a/onlamp/2008/04/01/step-by-step-using-samba-to-join-a-windows-domain.html)

That tutorial is for a Samba SERVER, I am not sure how much of it applies to the Client.

---

### Post by schwabdale on 2010-07-08
I will give it a try and let you know. Thanks, 


If you have time... Only if you have time, can you explain to me in _***layman's terms***_what those commands are doing. 

It looks like I am creating a file that is a link to a share. Then I am trying to give that share a drive letter associated that Wine can use...

---

### Post by bodhi.zazen on 2010-07-08
That tutorial is for Samba servers and it explains how to add a Linux Samba Server to an existing Windows Domain.

In your case, you are running a linux client wanting to join a Windows domain.

You may only need to edit the samba config file and change one line, 

> workgroup = MYWORKChange "MYWORK" to your windows domain.

See also : [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

In terms of explaining those commands, first I do not know much about setting up a windows domain, so I can not help on that side of things.

Second, although I am familiar with samba and kerberos, I am not sure I can explain the integration with a windows.

Although in deed of revision, the ubuntu wiki samba page is a good place to start.

---

