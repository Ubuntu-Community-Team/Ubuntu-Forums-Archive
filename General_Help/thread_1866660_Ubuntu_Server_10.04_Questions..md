---
title: "Ubuntu Server 10.04 Questions."
date: 2011-10-21
forum: General Help
---

### Post by tdinwoodie on 2011-10-21
I have an old computer, so I figured I might as well play around with Ubuntu server.  I've barely used Ubuntu at all, but I figured that it would be a nice little project.  I got it to (sort of) work with the help of these two tutorials:

1- [http://www.ubuntugeek.com/ubuntu-serverinstall-gui-and-webmin-in-ubuntu-810-intrepid-ibex-guide.html](http://www.ubuntugeek.com/ubuntu-serverinstall-gui-and-webmin-in-ubuntu-810-intrepid-ibex-guide.html)

2- [http://www.kelvinwong.ca/2010/05/22/installing-webmin-on-ubuntu-server-10-04-lts-lucid/](http://www.kelvinwong.ca/2010/05/22/installing-webmin-on-ubuntu-server-10-04-lts-lucid/)


I have a few general questions about what I've done:

-In the first tutorial, I was instructed to install ubuntu-desktop, which I did successfully.  Why would I have to do this, and how am I supposed to use the server with a GUI like this?  In the second tutorial I was shown how to install Webmin, and I did.  Was I only supposed to install one or the other?

-I'm not able to connect to the web server, and I'm sure it's because I messed up a few (probably a lot) of things in the first step.  I try to connect with another computer by typing in "https://[192.168.100.1:10000/"]("http://192.168.100.1/") and using my routers ip address.  I'm much more concerned about fixing the first issue and then coming back to this once I understand what I'm doing better.

-Is it possible for me to do exactly what the second tutorial did and then upgrade everything afterwards?


Thanks for any help you can give me.  Sorry if this is a difficult question to answer, but to be completely honest I have almost no idea what I'm doing now.  If I'm not able to solve the problem with your help, I'll probably start fresh and try another time.

---

### Post by drdos2006 on 2011-10-21
Here is a HOWTO which I found comprehensive and invaluable. Uses Webmin to allow your browser to connect and modify your server settings.
You could also install the Desktop plus install and run the server as a virtual machine using Virtualbox and that is how I run my testing websever.

> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
"Setting up a Linux Server, Start to Finish, using Webmin". By Kevin Elwood



And on your server..........

```

Run and logon to your server and download from your server with :
sudo wget http://prdownloads.sourceforge.net/webadmin/webmin_1.550_all.deb

Install with :
sudo dpkg -i webmin_1.550_all.deb

Add extra libraries with :
sudo apt-get -f install

```

regards

---

