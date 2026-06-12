---
title: "Newbie server question"
date: 2011-09-02
forum: General Help
---

### Post by Pujims on 2011-09-02
Hello! I am terribly stuck on windows type environment. If I am setting up a server to host a website, can I put gnome on it to feel more comfortable? I am trying hard to learn Linux, I have books and such but it makes my head hurt. HELP please

---

### Post by CharlesA on 2011-09-02
Just install ubuntu desktop and install whatever services you want to play around with. If it's a web site - then you'd need to install apache:

```
sudo apt-get install apache2
```

---

### Post by Pujims on 2011-09-02
I already have the desktop installed on one PC. So, I can just add the 'server' pieces?

---

### Post by CharlesA on 2011-09-02
> **Pujims said:**
> I already have the desktop installed on one PC. So, I can just add the 'server' pieces?
Yep. :)

---

### Post by tgalati4 on 2011-09-02
You can use desktop Ubuntu as a server.  The differences in performance are minor.  Just keep adding services until your machine is no longer fast enough for your purposes.  Then put Ubuntu server (command line only) on real server hardware (like a used Dell PowerEdge server).

To be good at server administration, you need to learn the command line.

---

### Post by Pujims on 2011-09-03
Thank you

---

### Post by drdos2006 on 2011-09-03
I was a newbie with Ubuntu server too.

Here is a HOWTO which I found comprehensive and invaluable. Uses Webmin to allow your browser to connect and modify your server settings.
You could also install the Desktop and run the server as a virtual machine using Virtualbox. Check out Kevins webpages.

> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
"Setting up a Linux Server, Start to Finish, using Webmin". By Kevin Elwood



And on your server..........

```

Logon to your server and download from your server with :
sudo wget http://prdownloads.sourceforge.net/webadminwebmin_1.550_all.deb

Install with :
sudo dpkg -i webmin_1.550_all.deb

Add extra libraries with :
sudo apt-get -f install

```

regards

---

