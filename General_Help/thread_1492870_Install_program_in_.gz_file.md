---
title: "Install program in .gz file"
date: 2010-05-25
forum: General Help
---

### Post by chejose on 2010-05-25
For varios reasons I would like to install Thunderbird 2.0.0.24. I have downloaded the file, but so far I have not found out how to install the program.

I am running Ubuntu 10.04

It is a tar.gz file

Thanks,  José

---

### Post by philinux on 2010-05-25
[http://ubuntu-tutorials.com/2007/05/18/manually-install-thunderbird-2-ubuntu-704/](http://ubuntu-tutorials.com/2007/05/18/manually-install-thunderbird-2-ubuntu-704/)

Give evolution a try out. Nothing to loose.

---

### Post by Ozymandias_117 on 2010-05-25
The thunderbird you downloaded from mozilla doesn't need to be installed. Just untar it and click on the "thunderbird" script.

edit: Sorry, I misread part of your post, my first bit of advice wouldn't have helped :D

---

### Post by scouser73 on 2010-05-25
Download the **.tar.bz2** file from

[[COLOR="Red"]**Mozilla Messaging: Thunderbird 3.01**[/COLOR]]("http://www.mozillamessaging.com/en-US/thunderbird/all.html")


**1** - Extract the **.tar.bz2** file

**2** - Enter **gksudo nautilus** in terminal

**3** - Go to the folder **/opt**

**4** - Copy & paste the Thunderbird file that you extracted to **/opt**

**5 -** Enter these commands into **Terminal** > **sudo -i**

*Enter your password if asked.*

> **cd /opt**
> **chown -R username filename**

[COLOR="Red"]**Obviously the username refers to you, and the filename to the file**[/COLOR]

**6** - Go to **System > Preferences > Main Menu**

**7** - In Main Menu, click on **New Item**

**8** - In the **Name** field enter **Mozilla Thunderbird Mail/News**

**9** - In the **Command** field enter **/opt/thunderbird/thunderbird**

**10** - In the **Comment** field enter **Mozilla Thunderbird Mail/News**

[[IMG]http://img121.imageshack.us/img121/7329/screenshot2c.png[/IMG]](http://img121.imageshack.us/img121/7329/screenshot2c.png/)

---

### Post by chejose on 2010-05-25
Well, I am afraid that I am a bit thick headed. I have been searching your suggestions but am not at all clear what to do. Hopefully someone can give instructions for an empty head.

Thanks...José

---

### Post by obscurant1st on 2010-05-25
why dont you install it via apt-get?
I think it will not work it in Karmic with the default sources.
check this link for more info on that.

[**Here**]("http://obscurant1st.biz/blog/how-to-install-latest-firefox-using-apt-get-command/")

after doing all the things discussed in there, you wil be able to install using the command
> sudo apt-get install thunderbird-mozilla-build

---

### Post by chejose on 2010-05-25
Sorry, I didn't see the last one. So will see what I can do.

Thanks

---

### Post by obscurant1st on 2010-05-25
It should work. Coz I installed thunderbird and sunbird like this only! :)

---

### Post by chejose on 2010-05-25
I am afraid that this is getting to be a mess.

To "untar" the file I used tar -zxvf 

The result was a list of files, that I suppose are in the file, with "Cannot open. No such file or directory". VERY strange since it just made list of the files!

I also tried tar xzf with the same result.

I am afraid that I have no idea as to how to open the file correctly, but have followed instructions I have found.

José

---

### Post by obscurant1st on 2010-05-26
I dont know why are you not trying the easier method. anyway here is the thing that you have been asking for.

first download thunderbird
then  issue this command in terminal 

> sudo tar xvjf filename.tar.bz2

Now move it to the installation folder by issuing the command,
 > sudo mv thunderbird /usr/lib/

Now Update all thunderbird Shortcuts in the System by creating a link in  /usr/bin. For that type in the following command.
 > sudo ln -sf /usr/lib/thunderbird/thunderbird /usr/bin/thunderbird 

PS: After issuing the first command the system may ask for  administrator password., So type in the password. Or if you already are  the administrator or logged in as root, just avoid the sudo from each  command.

---

