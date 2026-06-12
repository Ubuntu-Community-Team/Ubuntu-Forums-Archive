---
title: "Help! CP -r command"
date: 2012-07-21
forum: General Help
---

### Post by HoCo xXSamXx on 2012-07-21
Hello all. So for the last few days I have been trying to sync my BlackBerry Playbook with my laptop running Ubuntu Desktop v12.04. I am at my wits end. Here is what I tried.

To connect to the PlayBook's file system, I simply connected it via usb and opened a Windows Share server, using the device name as the IP. The PlayBook then appeared as a connected server.

Now that I have access to the files it sould be easy to sync right? WRONG! I thought a simple copy/paste command would work the is what I tried:

```
cp -r smb://sam_playbook/media/music /home/sam/music
```

I then got this:

> cp: cannot stat `smb://sam_playbook/media/music': No such file or directory

So I tried to enter the path of the of the music folder differently

> //sam_playbook/media/music
/sam_playbook/media/music
sam_playbook/media/music

I am at my wits end here. Any ideas guys? How to make the cp command work? Other methods?

---

### Post by UltimateCat on 2012-07-21
I'm not the expert here but I am trying to help.

I wonder if there is an application that would help the playbook communicate with your computer.  I acknowledge that you connect via usb and the playbook then is your ip-

In my case I went to AT&T and obtained a driver.  Not sure if a driver is your answer but I am thinking.

The Blackberry website might be of assistance

[http://us.blackberry.com/playbook-tablet.html?CPID=KNC-kw473299_p6&HBX_PK=rim|5c92c33c-da90-2349-9b6c-000007f3d8](http://us.blackberry.com/playbook-tablet.html?CPID=KNC-kw473299_p6&HBX_PK=rim|5c92c33c-da90-2349-9b6c-000007f3d8)

Here's the manual to the playbook in pdf form there might be troubleshooting strategies/instruction that will aid you.

[http://docs.blackberry.com/en/smartphone_users/subcategories/?userType=1&category=Chargers&subCategory=BlackBerry+](http://docs.blackberry.com/en/smartphone_users/subcategories/?userType=1&category=Chargers&subCategory=BlackBerry+)

---

### Post by HoCo xXSamXx on 2012-07-21
Thanks for your reply, but I have done my research :) There is no program out there that will sync the playbook. let alone any BlackBerry device to a Linux based computer. The BlackBerry device manager is only for Windows and Mac. I understand that I may be able to create a virtual machine to run Windows, but I want that to be a last resort.

---

### Post by netopalis45 on 2012-07-22
To access a Windows share from the command line you will have to use smbclient. Part of smbclient is smbget which works similar to wget and you should be able to use it to copy your files.

```
man smbclient
```
```
man smbget
```

I have never had to use them but hope they will work for you

---

