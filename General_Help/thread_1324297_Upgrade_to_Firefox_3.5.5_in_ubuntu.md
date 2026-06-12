---
title: "Upgrade to Firefox 3.5.5 in ubuntu"
date: 2009-11-12
forum: General Help
---

### Post by simartem on 2009-11-12
Hi,

I am using Ubuntu 9.04
I have the following version of firefox installed. It seems to be 3.0.15

[img]http://img691.imageshack.us/img691/9837/moz.png[/img]


How can i upgrade to the latest firefox version ? I dont know the command to install.
I have download  3.5.5 archive file from the official website to the folder **My Documents**.
_The filename is  firefox-3.5.5.tar.bz2_ 

But i dont know how to make it work :(

---

### Post by Tiganjero on 2009-11-12
You could install it from a tarball you downloaded, but it's much easier to just use a command. Open up terminal(Applications>Accessories>Terminal) and enter this
```
sudo apt-get install firefox-3.5
```
When sudo asks for your password just enter your normal user password you use to login. It will ask you if you want to use the space to install this package and then just type Y and press enter. It will then continue with the installation. The alternative is to open the Synaptic Package Manager(System>Administration>Synaptic Package Manager) and search for firefox-3.5. It's basically the same.
Hope I helped. :)

George

---

### Post by Irony on 2009-11-12
First make sure you back up your bookmarks by going Bookmarks > Organise Bookmarks > Import & Back-up > Export HTML

Now uninstall Firefox via synaptic.

Now go to your .mozilla file in your home directory and rename it to .mozilla1 - it probably won't work with the new firefox hence rename it and you can test it later.

Right click your tar.gz file and extract it - it will form a folder called firefox. Bin your tar.gz file.

Open a terminal and issue the command

```
firefox
```

The new firefox should start up - you might have to specify the path, I can't remember.

I then moved the firefox folder to

```
/opt
```

issued the command

```
sudo chown -R root:root /opt/firefox
```

and then created a firefox link in

```
/usr/local/bin
```

You might have to create a link in your menu but firefox will now work for all users.

---

### Post by aysiu on 2009-11-12
This will help you get that .tar.bz2 installed:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by Tiganjero on 2009-11-12
@Irony, @aysiu
It's much easier to use the Synaptic then to mess around with tarballs, though it's quite useful to know how to work with them.

---

### Post by scouser73 on 2009-11-12
**1** - Right click & Extract the Firefox tar.bz2

**2** - Enter **gksudo nautilus** in Terminal

**3** - Copy & paste the Firefox file that you have just extracted to **/opt**

**4** - Right click on the Ubuntu start logo, select **Edit Menus**, 

**5** - Highlight the Internet sub menu & click New Item

You will now see a small dialogue box appear

**6** - In the Name field, type **Firefox**

**7** - In the Command field type **/opt/firefox/firefox**

**8** - In the Comment field type **Firefox**

You will now have firefox installed.

---

### Post by aysiu on 2009-11-12
> **Tiganjero said:**
> @Irony, @aysiu
It's much easier to use the Synaptic then to mess around with tarballs, though it's quite useful to know how to work with them.
It's actually easier to paste **one** command into the terminal than to use Synaptic.

More importantly, when it comes to Firefox, there are generally two types of people--those who need the absolute latest version the second it comes out, and those who are fine using the repositories version, knowing that security updates will come shortly.

If someone wants the .tar.bz2, she's far more likely to be the former than the latter, in which case Synaptic isn't going to cut it. *firefox-3.5* will always be a step behind the official Mozilla release.

---

### Post by Tiganjero on 2009-11-12
> **aysiu said:**
> 
More importantly, when it comes to Firefox, there are generally two types of people--those who need the absolute latest version the second it comes out, and those who are fine using the repositories version, knowing that security updates will come shortly.

If someone wants the .tar.bz2, she's far more likely to be the former than the latter, in which case Synaptic isn't going to cut it. *firefox-3.5* will always be a step behind the official Mozilla release.

Agreed.

---

### Post by simartem on 2009-11-12
> **scouser73 said:**
> **1** - Right click & Extract the Firefox tar.bz2
**2** - Enter **gksudo nautilus** in Terminal
**3** - Copy & paste the Firefox file that you have just extracted to **/opt**
**4** - Right click on the Ubuntu start logo, select **Edit Menus**, 
**5** - Highlight the Internet sub menu & click New Item
You will now see a small dialogue box appear
**6** - In the Name field, type **Firefox**
**7** - In the Command field type **/opt/firefox/firefox**
**8** - In the Comment field type **Firefox**
You will now have firefox installed.

I have done the things and now i have firefox 3.5.5 
The thing i want to know is does the previous version exist somewhere in the computer and should i remove it ? If yes, how to remove ? Where is that located.

---

### Post by Irony on 2009-11-12
Note when using the extraction method to follow aysiu's commands to create shortcuts so that the menu commands and plugins work;

```
sudo ln -s /opt/firefox/firefox /usr/bin/firefox
sudo ln -s /usr/lib/xulrunner-addons/plugins /opt/firefox/plugins
```

---

### Post by Irony on 2009-11-12
> **simartem said:**
> I have done the things and now i have firefox 3.5.5 
The thing i want to know is does the previous version exist somewhere in the computer and should i remove it ? If yes, how to remove ? Where is that located.
As I said earlier uninstall the old firefox from synaptic, see my earlier post - I don't know if it will effect anything by uninstalling it afterwards, maybe it will remove a few links which you might have to recreate.

---

### Post by Irony on 2009-11-12
> **aysiu said:**
> If someone wants the .tar.bz2, she's far more likely to be the former than the latter, in which case Synaptic isn't going to cut it. *firefox-3.5* will always be a step behind the official Mozilla release.
Also sometimes it is just useful knowing the extraction method, for example I use kompozer and the repository version crashed every time I hit the format menu, so I searched for kompozer on the kompozer site and extracted it and ran it and find it completely stable and it has a few new functions.

---

### Post by simartem on 2009-11-12
thank you very much..

---

