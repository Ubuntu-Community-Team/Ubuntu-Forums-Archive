---
title: "Urgent help needed!"
date: 2011-05-21
forum: General Help
---

### Post by Condor Cluster on 2011-05-21
I think I just ruined my netbook! 

I was removing a load of packages I thought I wouldn't need. Now when I boot up, it says 'ubuntu is running in low graphics mode', so I click ok, but it just goes to command line login.

Not too bothered about reinstalling, but I really need to get some important files of the system onto a usb hard drive first.

I'm having to use someone elses laptop to type this!

Please help :(

---

### Post by Quackers on 2011-05-21
Boot from the live cd/usb and make your backups from there.

---

### Post by sidzen on 2011-05-21
use [puppy]("http://www.puppylinux.com/")

---

### Post by Condor Cluster on 2011-05-21
Can i access the hard drive using live cd and copy to usb drive?

Aren't all the contents encrypted or something?

---

### Post by Quackers on 2011-05-21
Only if you encrypted them! Not sure how that affects things tbh.

---

### Post by Random_Dude on 2011-05-21
Since you are in command line, can't you just reinstall what you removed doing a "sudo apt-get install <package name>"?

---

### Post by Condor Cluster on 2011-05-21
Tried to do that, but it fails as it cannot get online.

---

### Post by Quackers on 2011-05-21
You can chroot into your installed system from the live desktop and re-install things from there.

---

### Post by Random_Dude on 2011-05-21
> **Condor Cluster said:**
> Tried to do that, but it fails as it cannot get online.

If you have saved the password of a wireless connection at the place that you are now, try:

```
nm-applet &
```and then


```
sudo apt-get install <package name>
```EDIT: Or follow a guide like this: [http://www.ghacks.net/2009/04/14/connect-to-a-wireless-network-via-command-line/](http://www.ghacks.net/2009/04/14/connect-to-a-wireless-network-via-command-line/)

---

### Post by Condor Cluster on 2011-05-21
Going to try to boot live cd (well, usb drive), and see if I can retrieve the files that way.

Fingers crossed.

 ](*,)

---

### Post by idoitprone on 2011-05-21
next time your in this situation. learn to connect to the internet with the command line



```
ifconfig
``` 
make sure you wireless interface is up.
if not```
]ifconfig wlan0 up

```
I am using wlan0 since it a common wireless interface. Other may be wlan1 or ath0 or whatever.
```

iwlist wlan0 scan

```
find the your internet essid

```
iwconfig wlan0 essid "your essid" key "dawm if i know its a secret"

```
if your wifi is unprotected, you do not need to enter a key like me
if you have a wpa key, skip the iwconfig step and you will have to use wpa_supplicant instead
here is a link and it will get more annoying to set up since you have to edit files with the command line
[https://wiki.archlinux.org/index.php/WPA_supplicant](https://wiki.archlinux.org/index.php/WPA_supplicant)
[https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

```
dhcpcd wlan0
```


here some random links to show I am not insane lol
[http://www.ghacks.net/2009/04/14/connect-to-a-wireless-network-via-command-line/](http://www.ghacks.net/2009/04/14/connect-to-a-wireless-network-via-command-line/)
[https://bbs.archlinux.org/viewtopic.php?id=44784](https://bbs.archlinux.org/viewtopic.php?id=44784)
[http://www.linuxforums.org/forum/ubuntu-linux/126364-how-connect-wireless-network-ubuntu.html](http://www.linuxforums.org/forum/ubuntu-linux/126364-how-connect-wireless-network-ubuntu.html)
 btw dhclient and dhcpcd basically does the same thing

---

### Post by Wim Sturkenboom on 2011-05-21
@idoitprone
thanks for the above post; I was just going to research it to figure it out because I realised I was lacking this knowledge

---

### Post by Wim Sturkenboom on 2011-05-21
> **Condor Cluster said:**
> ... but I really need to get some important files of the system onto a usb hard drive first.
Make it a habit to backup before you start an attempt to destroy your system :D

Or verify the existing ones (more than likely you don't do backups as you don't consider that important) so you know that you can still read the backups.

---

### Post by Condor Cluster on 2011-05-22
Managed to get all the important stuff off using a live usb disc. (apart from the porn folder :frown:)

So now to re-apply Lucid and all the apps I like... <sigh>

Moral of the story, don't be a smart-*** and remove/meddle with stuff you don't understand #-o

---

### Post by Wim Sturkenboom on 2011-05-22
Congratulations. You can mark your thread as solved using the thread tools just above the first post on a page.

And you still did not learn the most important lesson :D Make backups; what if you would have had a solid physical HD crash? With some luck and plenty of money you might have been able to get that, obviously not so important, data back.

---

### Post by Spyderkid on 2011-05-22
Note for future...

Don't manually clean up your computer use a program like computer janitor, or bleachbit.

---

### Post by Lateralis on 2011-05-22
Meddling is fine, but I do so in a virtual machine!  If something goes wrong its no biggie. =P

---

