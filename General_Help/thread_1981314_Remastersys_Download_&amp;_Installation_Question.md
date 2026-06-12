---
title: "Remastersys Download &amp; Installation Question"
date: 2012-05-16
forum: General Help
---

### Post by animaguy on 2012-05-16
Can anyone please share the correct procedure to downloading and installing Remastersys?

---

### Post by cmont899 on 2012-05-16
have you tried simply:

```
wget http://www.remastersys.com/repository/ubuntu/remastersys_2.0.12-1_all.deb

dpkg -i remastersys_2.0.12-1_all.deb
```

---

### Post by Karlchen on 2012-05-16
Hello, cmont899.

I am not quite sure whether recommending a manual download and installation of an outdated Remastersys is the best approach. 

Hello, animaguy.

As stated in the Linux Mint forum before, perhaps following Fragadelic's instruction, [**[SIZE=4]Where can I get remastersys?[/SIZE]**]("http://www.geekconnection.org/remastersys/ubuntu.html"), will be the better way.

Cheers,
Karl

---

### Post by spacecoastpete on 2012-06-10
Try this:

You can install Remastersys in Ubuntu 12.04

As root - issue

'sudo su' 

in the terminal window prior to the following command.

wget -O - [http://www.remastersys.com/ubuntu/remastersys.gpg.key](http://www.remastersys.com/ubuntu/remastersys.gpg.key) | apt-key add -

sudo gedit /etc/apt/sources.list

Add the following line

#Remastersys Precise
deb [http://www.remastersys.com/ubuntu](http://www.remastersys.com/ubuntu) precise main

Now open the terminal and type

sudo apt-get update && sudo apt-get install remastersys remastersys-gui

---

### Post by Hylas de Niall on 2012-06-10
[http://www.remastersys.com/ubuntu.html](http://www.remastersys.com/ubuntu.html)

Scroll down to the bottom of the page to where it says: **Important New information for Ubuntu Lucid and newer!** and follow the instructions there.
:)

---

### Post by varma1993 on 2012-06-10
The Manual Method

As root - issue 'sudo su' in the terminal window prior to the following command.

Download and apply the repository gpg key.

wget -O - [http://www.remastersys.com/ubuntu/remastersys.gpg.key](http://www.remastersys.com/ubuntu/remastersys.gpg.key) | apt-key add -

Add the following line that corresponds to your version of Ubuntu to your /etc/apt/sources.list

#Remastersys Lucid
deb [http://www.remastersys.com/ubuntu](http://www.remastersys.com/ubuntu) lucid main

#Remastersys Maverick
deb [http://www.remastersys.com/ubuntu](http://www.remastersys.com/ubuntu) maverick main

#Remastersys Natty
deb [http://www.remastersys.com/ubuntu](http://www.remastersys.com/ubuntu) natty main

#Remastersys Oneiric
deb [http://www.remastersys.com/ubuntu](http://www.remastersys.com/ubuntu) oneiric main

#Remastersys Precise
deb [http://www.remastersys.com/ubuntu](http://www.remastersys.com/ubuntu) precise main

Now just apt-get update or reload in Synaptic to have the new Remastersys signed repository ready to use!


source:[remastersys.com/]("http://remastersys.com/ubuntu.html")

---

