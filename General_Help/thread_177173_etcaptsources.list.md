---
title: "/etc/apt/sources.list????"
date: 2006-05-15
forum: General Help
---

### Post by mojogil on 2006-05-15
Hi,
I've been trying to learn Linux, Ubuntu, Window managers and other things.  I'm having a lot of fun with it! I love reading these forums for info.
I'm trying to get my Supra Max usb modem working and I went to linmodems.org (found it on this forum).  It says to add a line to /etc/apt/sources.list.  From what I gather that is a repository or the like.  
My question is "How exactly do you add something to this folder?"
Thank you!
gil

---

### Post by johnc4510 on 2006-05-15
please post what they told you to add to this file

---

### Post by Sutekh on 2006-05-15
You backup the file and edit it using these commands
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list
```use your password when prompted, then add the line from the linmodems.org website.

Once you are finished editing, save the file and use this command to update the repository lists```
sudo apt-get update
```

---

### Post by aysiu on 2006-05-15
You're going to have a tough time. The /etc/apt/sources.list draws on on-line repositories to install software. If you're trying to get your USB modem to work, I'm guessing you're not connected to the internet... so you wouldn't be able to use online repositories.

---

### Post by mojogil on 2006-05-15
The Website says:
"Alternatively you could add one of the following two lines to your /etc/apt/sources.list and let apt-get do the rest for you:

deb [http://www.physcip.uni-stuttgart.de/heby/ltmodem/dists/debian/](http://www.physcip.uni-stuttgart.de/heby/ltmodem/dists/debian/) ./
deb [http://www.sfu.ca/~cth/ltmodem/dists/debian/](http://www.sfu.ca/~cth/ltmodem/dists/debian/) ./ "

I'm not quite sure what to apt-get when I'm done but I'll give this a shot.
I am connected to the internet, I just need the modem for faxing.  
I'm a Plumbing forman for a hospital construction job and I probably have the only linux jobsite construction computer in Minneapolis!
Thanks,
Gil

---

### Post by Sutekh on 2006-05-15
Once you change the sources.list to include those lines you will be able to install the linmodem driver (I guess) using apt-get and the name of the package.
```
sudo apt-get install <some linmodem driver>
```
If you post the linmodem.org link, it would help out to know what steps you are told to follow.

---

### Post by aysiu on 2006-05-15
Read this:
[http://www.monkeyblog.org/ubuntu/installing.html](http://www.monkeyblog.org/ubuntu/installing.html)

and this:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

They'll give you a better idea about repositories and how to use them.

---

### Post by mojogil on 2006-05-15
Thank you,
I'll read these and learn from them.
Here's the link to the website instructions but it just occured to me that it may be from Germany.  I don't know if that will be a problem.
Thanks everyone for the advise.  I'll do some more reading and see if I can solve this If I do I'll post a victory, if not then I'll post more questions.
Take care,
Gil

---

### Post by Mustard on 2006-05-15
I think you forgot to post the link. :)

---

