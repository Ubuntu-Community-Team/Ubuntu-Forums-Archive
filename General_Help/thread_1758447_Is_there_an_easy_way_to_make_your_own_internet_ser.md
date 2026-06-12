---
title: "Is there an easy way to make your own internet server?"
date: 2011-05-14
forum: General Help
---

### Post by linuxuser12345 on 2011-05-14
Hey, I am thinking of making a website, but I decided, "hey, can't I just make and host the website myself without spending any money??"
I am just wondering, is this possible? Is there an easy way to have your own website and get it online for free by hosting it on your own computer dedicated to it? It would save me money.

Of course, I would be planning to use Ubuntu! :)

---

### Post by zealibib slaughter on 2011-05-14
Yes you can host your website to a computer you own but you would ne a dns record to point your domain name to your ip address.  Here is all the info you need for making a web server and DNS naming at lifehacker: [http://lifehacker.com/124804/geek-to-live--how-to-assign-a-domain-name-to-your-home-web-server](http://lifehacker.com/124804/geek-to-live--how-to-assign-a-domain-name-to-your-home-web-server)
[http://lifehacker.com/software/feature/how-to-set-up-a-personal-home-web-server-124212.php](http://lifehacker.com/software/feature/how-to-set-up-a-personal-home-web-server-124212.php)
Hope this helps.

---

### Post by linuxuser12345 on 2011-05-14
Thank you! :)

---

### Post by linuxuser12345 on 2011-05-14
Are there any other easier, shorter guides?

---

### Post by zealibib slaughter on 2011-05-14
The one you need really is how to set up DNS naming and really just need the link to [http://dyndns.com/](http://dyndns.com/). Then you need a spare machine, a copy of ubuntu server or cent os, and a little time and a whole lot of googling. Basicly the process goes as this, set up ubuntu server and configure apache, set up DNS to point to your IP address and upload your html files to your server. Its a little more work than that but not much if you don't have a forums or running an MX email server.
 
Here is a guide to setting up a home server with ubuntu.  Its longer than the others but gives you all the details for the LAMP.
 
[http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/](http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/)
 
I can't find any short ones.

---

### Post by drdos2006 on 2011-05-14
Here is a HOWTO which I found comprehensive and invaluable. Uses Webmin to allow your browser to connect and modify your server settings.
You could also install the Desktop and run the server as a virtual machine using Virtualbox.

> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
"Setting up a Linux Server, Start to Finish, using Webmin". By Kevin Elwood





```

Logon to your server and download from your server with :
sudo wget http://prdownloads.sourceforge.net/webadmin/webmin_1.550_all.deb

Install with :
sudo dpkg -i webmin_1.550_all.deb

Add extra libraries with :
sudo apt-get -f install

```

regards

---

### Post by Thewhistlingwind on 2011-05-14
You'll have to pay for a domain name if you want one.

And no, not really, but if your already a Linux user, you should find the process enjoyable enough.

That is, easy, no, free, yes.

---

### Post by linuxuser12345 on 2011-05-14
How do I do this using a GUI?

---

