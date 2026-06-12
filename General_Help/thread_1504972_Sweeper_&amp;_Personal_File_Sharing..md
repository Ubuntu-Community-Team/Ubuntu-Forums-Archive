---
title: "Sweeper &amp; Personal File Sharing."
date: 2010-06-08
forum: General Help
---

### Post by PinchedNerve on 2010-06-08
Hello.

   Couple questions. Is "Sweeper" a good tool for cookies web history & such? 

Also, I want to set up personal file sharing for my house & it says I do not have the correct packages installed, but it also doesn't say which packages I need to install.

---

### Post by Morbius1 on 2010-06-08
Don't know about Sweeper but just so you know "Personal File Sharing" is not samba.

You need to install the following packages:

apache2.2.bin
libapache2-mod-dnssd

It will only allow you to share one folder: /home/username/Share

If someone can figure out how to get it to work with a windows client I'd like to see it. It will work linux to linux but not consistently. This thing needs more work. I think you'd be better off with sharing folders using Samba and Nautilus - but that's just my opinion :wink:

---

### Post by PinchedNerve on 2010-06-08
1 folder shared on each computer is fine, but I would like it to work consistently without hassles, so would Samba or Nautilus do that better?

---

### Post by Morbius1 on 2010-06-08
Just from my own personal experience with "Personal File Sharing" you'd be better off with anything else. There may be others that have gotten this to work but it eludes me personally.

You can easily do a very quick test of Nautilus-share ( Using Nautilus to invoke Samba to share folders ):

Open Nautilus
Right click on say ... /home/user_name/Documents
Select "Sharing Options"
Select "Share this Folder", "Allow others to create and delete files..", and "Guest Access"
Select "Create Share"
It will ask you if you want to modify permissions - you do.

If the samba gods are smiling upon you today then that's all you have to do.

If you don't have samba installed it will ask you if you want to install it ( I think it calls it Windows Networking or something ) when you select "Sharing Options"

---

### Post by PinchedNerve on 2010-06-08
Ok, so now when I go to Network/Windows Network/Workgroup I get the error "unable to mount location".

---

### Post by Morbius1 on 2010-06-08
Why samba works without incident for some and not for others ....

Here is a checklist I go through every time this sort of thing happens:

On the machine that has the share you're trying to access:

(1) Chack to see if samba is running:
```
sudo service smbd status
```If it's not running start it:
```
sudo service smbd start
```(2) If you have configured the firewall in any way I disable it.

(3) Check the netbios name ( has to be <= 15 characters )
It's what's after your username@ when you bring up a terminal

(4) See if you can access the share directly by ip address from the other machine:
```
nautilus smb://192.168.0.100
```[COLOR=Blue]*Changing 192.168.0.100 by the actual ip address of the machine that has the share.*[/COLOR]

---

### Post by PinchedNerve on 2010-06-08
Meh!   Some work some don't.  None of the computers will let me access all the others. Each one will allow access to another, but not the same & not all, strange...

---

### Post by Morbius1 on 2010-06-08
Not sure I quite understood you last post but are all of these machines linux or are there Windows boxes in the mix. If there are Windows are any of them Win7?

From a linux box that cannot access your linux share post the output of the following commands:
```
smbtree
findsmb
```From a Windows box that cannot access your linux share post the output of this command from the Command Prompt:
```
net view
```

---

### Post by PinchedNerve on 2010-06-08
All are 10.04 x64.  Here is the example of what I meant before. There are 4 total computers. Comp 1 may be able to access comps 2,3,4, however comp 2 can only access comp 3, while comp 4 can access comp 1,2.  

Strange to say the least.  Think I am giving up atm.  I have a flash drive which I guess I'll continue to use if I need to put a file on another computer.

---

