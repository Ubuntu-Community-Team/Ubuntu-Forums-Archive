---
title: "How do I host my own Mumble Server?"
date: 2010-05-25
forum: General Help
---

### Post by Nick.Sth on 2010-05-25
Hello. I am running Ubuntu 10.04 Desktop, and I'm pretty fed up with having to pay companies to host my Mumble server, while its something I could handle to do.

But I just don't know how to do, nor what to do.
Ive scowled the Internet for legit tutorial but nothing adds up.

How can I host my own Mumble Server?
Can somebody give me a detailed tutorial?
Or at least a link to a good one?

Cheers. Nick.

---

### Post by jerome1232 on 2010-05-25
I actually host my own simple one, How many users do you have? How fast is your upload rate?

murmurd (that is the mumble server) is actually in the ubuntu repositories.

```
sudo apt-get install mumble-server
``` Mumble's faq's have some good stuff about setting your server up initially, most if it can be done from within a mumble client.

[http://mumble.sourceforge.net/FAQ/English#Server](http://mumble.sourceforge.net/FAQ/English#Server)

---

### Post by Nick.Sth on 2010-05-25
Hi.
It's around 1000kb/s (1mbps). 
I just want to hold around like 10 slots so I presume it will be fine.
I used the command u told me, how can I open it up now?
How do I find my Address/Label/Port/IP I need to use?

---

### Post by jerome1232 on 2010-05-25
It's running already, it auto starts when you install it and will auto start when you turn your computer on. 

You will want to run the following command to set a few things up initially
```
sudo dpkg-reconfigure mumble-server
```

>   What sort of bandwidth will I need for the server?

Worst case scenario: Number of users × Number of talking users × 133,6 kbit/s. With less aggressive quality settings, it's ~60 kbit/s, and the bare minimum is 17.4kbit/s. Note that Mumble is geared towards social gaming; its quality enables people to talk naturally to each other instead of just barking short commands, so the amount of "users talking at the same time" can be somewhat higher than expected.

This means that a server with 20 players and 2 players talking at once requires 1-3 Mbit/s, depending on quality settings. In the server's .ini file, you can specify the maximum allowed bitrate for users as well as the maximum number of clients to allow. 

>   What is the default server port for Murmur?

The default port for Murmur is UDP and TCP 64738. 

Alot of the info is in that faq, how much do you know about networking?

If your mumble server is behind a router you will need to forward that port tcp and udp to the computer hosting mumble. You can goto [http://www.whatismyip.com/](http://www.whatismyip.com/) to figure out your ip (it will change from time to time, which is why I use dyndns to get a hostname and ddclient autoupdates my hostname with my new ip everytime my ip changes)

Somewhere I found a good guide that walks you through setting your user as the admin and such.

You will want to edit /etc/mumble-server.ini and set up a server password, read through the comments in the file to figure it out.

I'm trying to find the guide that walks you through setting your account up as the admin and such, might take me a minute.

---

### Post by Nick.Sth on 2010-05-25
> **jerome1232 said:**
> 
 how much do you know about networking?
 you will need to forward that port tcp and udp to the computer hosting mumble. 


I don't know too much about networking. 
I guess I can manage to forward the tcp and udp, but the thing is for example in windows, I could click on internet options, and see my local ip for example 10.0.0.1 how can I see it here on ubuntu?

---

### Post by jerome1232 on 2010-05-25
Right click your Connection Manger Applet, click connection information.

---

### Post by Nick.Sth on 2010-05-25
OK I set the TCP and stuff. Have you found that tutorial yet?
It mentions how I can change Label etc right? 
BTW thanks a lot man :)
uh and I used sudo ifconfig to find my local ip ;)

---

### Post by Nick.Sth on 2010-05-25
Hurray! I got it working THANKS A HELL OF A LOT MATE!!

I just have 1-2 more questions.
How can I add a password to my server so people must enter it to enter, so random people don't join it. 
And also how can I change its label? :)

---

### Post by Nick.Sth on 2010-05-25
O.o another error just came up.
I try to change the .ini in the etc folder BUT
once i try to save it tells me permission denied :S

---

### Post by jerome1232 on 2010-05-25
I'm googling like a lost madman and can't find it :S

Well first edit /etc/mumble-server.ini

gui

```
gksu gedit /etc/mumble-server.ini
```

cli
```
sudo nano /etc/mumble-server.ini
```


If you want users to have to enter a generic password (same for everyone) to enter your server at all, set a password here, if you want anybody to be able to join leave it blank. Also just leave host blank.

```
# Specific IP or hostname to bind to.
# If this is left blank (default), murmur will bind to all available addresses.
host=

# Password to join server
serverpassword=

```

Now to set your server name, look for the section below, delete the '#' in front of registerName= , put whatever you want your servername to be after registername= 
```
# To enable public server registration, the serverpassword must be blank, and
# this must all be filled out.
# The password here is used to create a registry for the server name; subsequent
# updates will need the same password. Don't lose your password.
# The URL is your own website, and only set the registerHostname for static IP
# addresses.
#
#registerName=
#registerPassword=secret
#registerUrl=http://mumble.sourceforge.net/
#registerHostname=

```

Now restart mumble-server for the setting to take affect
```
sudo service mumble-server restart
```

Log into your server with a client, for the ip just use 127.0.0.1 use the user name you want, once logged in click your username, click self, click register. Log out.

Log in as SuperUser, enter the superuser's password. Once logged in Right click your root channel, click edit, click the groups tab, edit the admin group and add your user. 

This site is for windows put should give you a visual idea of what I'm talking about. 
[http://mmo-mumble.com/help/AdministrationGuide](http://mmo-mumble.com/help/AdministrationGuide)

---

### Post by Nick.Sth on 2010-05-25
Man thank you so much!!!! You really are a life saver :D

just one last thing ;)
I have a website. Is it possible to use the website/it's ip insted of mine since its static?
Cuz my home's IP aint.

---

### Post by jerome1232 on 2010-05-25
nope.

But this is what I do, goto [http://www.dyndns.com/](http://www.dyndns.com/) and sign up for a free account, add a hostname to it (mine for example is voiceserv.homelinux.net)

Once that has been setup install ddclient on your machine hosting mumble. Then Configure it to update that hostname everytime your ip changes.

```
sudo apt-get install ddclient
sudo dpkg-reconfigure ddclient
```

Mostly keep defaults, add your username and password to it, I have it check my ip every 30 seconds and update the hostname if the ip changes. Then you can give your users that hostname as the address to connect to and it will never change.

---

### Post by Nick.Sth on 2010-05-25
Thanks so much man !! :)
If there is ANYTHING I can ever do for you, don't hesitate to ask!!

---

