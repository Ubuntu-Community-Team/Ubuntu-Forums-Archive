---
title: "can't write to my file system"
date: 2006-05-20
forum: General Help
---

### Post by bobby19 on 2006-05-20
I have just installed ubuntu 5.10 and I went to the Computer and right clicked filesystem and then properties. I then saw in the permissions that owner, group, and  others can't write or execute to it, I can only read. everything is also grayed out and at the bottom it says that I am not the owner and I can't change the permissions. I don't understand because I have only one password and account and I am loged into it now. If anyone could help, that would be appreciated.

---

### Post by Ramses de Norre on 2006-05-20
That's absolutely normal. And the contents of / should be owned by root and you shouldn't have write permissions on it, this makes Linux much safer..

But of course you are able to edit those files when needed;)

Read this: [http://wiki.ubuntu.com/RootSudo]("http://wiki.ubuntu.com/RootSudo")

---

### Post by Isoss on 2006-05-20
looks like you're new to linux. you need to use terminal commands in order to get permissions. 

to change the permission of any folder, go to Applications -> Accessories -> Terminal. And type:

```
sudo chmod *permission_number* *folder_destination*
```

Now permission number might be 777, 775 ... folder destination is the folder to which you want to grant permission. e.g: /var/www/ (if you have a localhost) ... 

youn can also download nautilus using synaptic package manager and then type this in terminal:
```
sudo nautilus /folder/
```
in both situation terminal will ask you to enter your password (you will type it but it will not appear).
Nautilus will open the folder for you with a root permission.

Hope this is sufficient and helpful.

Isos

---

### Post by bobby19 on 2006-05-20
thank you so much, know i understand. I do have one more question, I have been having trouble installing the linux version of Real player can you tell me how to sucessfully install it. thanx

---

### Post by Isoss on 2006-05-21
Can u please explain the problem?

Anyway, I'll tell you how to install it. Pretty easy.

Go to [www.real.com/linux](www.real.com/linux), download Advanced Installation [Download RPM Package]("http://www.real.com/realcom/R?href=http%3A%2F%2Fforms.real.com%2Freal%2Fplayer%2Fdownload.html%3Ff%3Dunix%2FRealPlayer10GOLD.rpm%26amp%3Bproduct%3Dplayerplus%26amp%3Bsystem%3Dlinux&pageid=unagi.8083677&pageregion=advanced_install&src=linux&pcode=rn&opage=linux") and download it to your Desktop. It's 6.3 MB
Then fire up the terminal and type the following command:
(make sure that you have "alien" installed in synaptic.
```
sudo alien /home/isos/Desktop/RealPlayer10GOLD.rpm
```
of course replace /isos/ with your user name. 
After you hit enter and enter your password it'll tell you: ```
realplayer_10.0.7.785-20060202_i386.deb generated

```
By default, it's generated in /home/isos/
Then enter the following command: ```
sudo dpkg -i /home/isos/realplayer_10.0.7.785-20060202_i386.deb
```
then hit enter. it should output the following:
```
Selecting previously deselected package realplayer.
(Reading database ... 129884 files and directories currently installed.)
Unpacking realplayer (from .../realplayer_10.0.7.785-20060202_i386.deb) ...
Setting up realplayer (10.0.7.785-20060202) ...

```
And then enjoy your linux RealPlayer.

---

