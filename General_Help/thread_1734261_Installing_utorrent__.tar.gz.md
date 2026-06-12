---
title: "Installing utorrent ? .tar.gz"
date: 2011-04-20
forum: General Help
---

### Post by tunechi on 2011-04-20
hi guys , i am trying to download utorrent .tar.gz after i downloaded it i can open in it , but now how can i install it ??

thank you guys

---

### Post by spikoley on 2011-04-20
First you need to extract the tar file.  A tar file is like a zip with Windows.

```
tar zxvf filename.tar.gz
```

Then take a look at the README file for directions.

---

### Post by jerome1232 on 2011-04-20
So tar.gz files are like zip files on windows, they can contain anything. So I looked up utorrent, downloaded their version for linux and took a look inside the archive.

Looks like it's a ready made exectuable. So you'd just move it to somewhere in your path, make a shortcut to it in your menu and your good to go.

ie if you **extracted** it to a folder called utorrent on your Desktop

```
sudo mv Desktop/utorrent /usr/local/
sudo ln -s /usr/local/utorrent/utserver /usr/local/bin/utserver
```

Then add a menu item in your menu that launches "utserver", if you want an icon one is included, in my example it would be in /usr/local/utorrent/docs/ut-logo.gif

---

### Post by tunechi on 2011-04-20
> **jerome1232 said:**
> So tar.gz files are like zip files on windows, they can contain anything. So I looked up utorrent, downloaded their version for linux and took a look inside the archive.

Looks like it's a ready made exectuable. So you'd just move it to somewhere in your path, make a shortcut to it in your menu and your good to go.

ie if you **extracted** it to a folder called utorrent on your Desktop

```
mv Desktop/utorrent /usr/local/
ln -s /usr/local/utorrent/utserver /usr/local/bin/utserver
```Then add a menu item in your menu that launches "utserver", if you want an icon one is included, in my example it would be in /usr/local/utorrent/docs/ut-logo.gif

hi , thanks for helping me out , i extracted .tar.gz to a utorrent folder on my desktop 
then i opened terminal and copied your code , here is what i get
"ln: creating symbolic link `/usr/local/bin/utserver': Permission denied
"

---

### Post by daweefolk on 2011-04-20
To write into /usr/ you need root privaleges.
Try ```
 sudo ln -s /usr/local/utorrent/utserver /usr/local/bin/utserver 
```
I can't tell by your post if you used sudo the first time, so my apologies if you did

---

### Post by jerome1232 on 2011-04-20
my bad I forgot to add the sudo bit. :D

Edited my OP to reflect that.

---

### Post by tunechi on 2011-04-21
> **daweefolk said:**
> To write into /usr/ you need root privaleges.
Try ```
 sudo ln -s /usr/local/utorrent/utserver /usr/local/bin/utserver 
```I can't tell by your post if you used sudo the first time, so my apologies if you did

done here is what i got "creating symbolic link `/usr/local/bin/utserver': File exists" , now what do i do next , how do i add it to the menu , thank you , lol im still very noob i've been using ubuntu for 3 days , so ya :D

---

### Post by sunasia on 2011-06-27
Hi I cant extract the file , this is all new to me on ubuntu, I cant get my utorrent installed HELP

---

### Post by jerome1232 on 2011-06-27
Why not just use deluge? I understand alot of utorrent fans like it. It's in synaptic/software center, easy to install.

---

### Post by Unhackmee on 2011-08-08
Flexget is a hassle and i dare say that no newbie can setup that rss in under 30 minutes, while the rss-feeds in utorrent cannot take more than 15 minutes to setup.

---

### Post by Nithogger on 2011-08-08
Why bother with Utorrent? there is already a download program installed there... no need to download more and install other stuff. Just check under /Applications/internet/Transmission BitTorrent client. 
It downloads as well.

---

### Post by fendijr on 2011-08-10
> **Nithogger said:**
> Why bother with Utorrent? there is already a download program installed there... no need to download more and install other stuff. Just check under /Applications/internet/Transmission BitTorrent client. 
It downloads as well.
tried all already but nothing successful.
anyone can help me here?
why quite tough to install from .tar.gz file almost al the times??

---

### Post by phuongdt3 on 2011-08-10
yes,i'm newbie,i have installed successfull,thanks so much :D

---

### Post by phuongdt3 on 2011-08-10
> **sunasia said:**
> Hi I cant extract the file , this is all new to me on ubuntu, I cant get my utorrent installed HELP

yes,ubunto is all new to us but you can find HELP on youtube ^^

---

