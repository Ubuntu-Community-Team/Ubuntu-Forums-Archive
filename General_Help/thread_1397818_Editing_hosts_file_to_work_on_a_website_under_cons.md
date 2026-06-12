---
title: "Editing hosts file to work on a website under construction"
date: 2010-02-03
forum: General Help
---

### Post by edanto on 2010-02-03
I'm very new to Ubuntu and am just finding my way.  I have no idea how to operate a terminal though.... so I'm a bit nervous about changing things deep in my ubuntu.

I have a half-made website that I want to finish (it's on a different server to the existing, live, site) and when I was using Windows I edited the hosts file to tell Windows which IP to look at for this particular address.

In Ubuntu, in etc/hosts I've found a file that looks similar, and opened it with gedit

It shows me something that looks like the Windows hosts file...

127.0.0.1    localhost
127.0.1.1    eoin-laptop

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

and I think I should edit it to include the line:

127.0.0.1    localhost
127.0.1.1    eoin-laptop
**12.34.56.78 website.com**

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Two questions, is that the right thing to change to do what I want to do? And how do I do it, since that file is read-only when I open it with gedit?

thanks

---

### Post by Ordes on 2010-02-03
so this is a online server right? how you normally connect to it? FTP?

you dont need to edit localhost.
In nautilus (= my comp on win) > File > connect to server.

----
if you really want to change the hosts

sudo gedit /etc/hosts

read more on sudo....

---

### Post by edanto on 2010-02-03
Just to explain why I'm choosing this route, it's a wordpress install, and I want to edit through the CMS. I can add files by ftp, but don't know how to build a website that way.

I'll look up 'sudo'  I've seen it a few times, it sounds important. 

thx

---

### Post by Ordes on 2010-02-03
ok.. never used wordpress.. but how does wordpress connect to your server? shouldnt there by a connection option in wordpress?

---

### Post by edanto on 2010-02-04
I'm not sure of the exact terminology, but I'll try and explain how things are laid out at the moment.

Currently, mysite.com is live on Hosting provided by XYZ Ltd at ip 87.65.43.21, and those are the DNS settings.

I'm making a new version of mysite.com, on a different host, and it's almost finished (the fact that it's in Wordpress isn't that relevant).  This new host is showing the site on ip 12.34.56.78 , but if I just browse with firefox to mysite.com then it takes instructions from the nearest DNS server and brings me to 87.65.43.21, so I can't see the almost finished site, I just see the existing one.

In Windows, I edit a file called hosts and tell windows that if I try to browse to mysite.com, I want it to bring me to 12.34.56.78  ..... and I want to find the equivalent in Linux.

I think the file I mentioned in the first post is the equivalent, it looks like the hosts file that was in Windows and it's called the same thing.  What I'm unsure of is what to do next, since I'm nervous about breaking my Ubuntu by messing something up. 

I'm off to look up sudo now.... if I sort it out I'll post back here.

---

### Post by Ordes on 2010-02-04
mhm.. than just use the IP instead the DNS to connect.

e,g [http://74.125.127.104/](http://74.125.127.104/)  would bring u to google
----

you could also just make the whole site first on your pc, and when its done,  upload it to your server

---

### Post by edanto on 2010-02-04
I get what you're saying, but it doesn't work in this case since the IP refers to a shared hosting environment and there are many, many other websites using the same IP address.

For that reason, the tech support people at the hosting company told me to edit the hosts file. I'll contact them and ask if they know how to do it in Ubuntu, but I imagine they'll tell me to look it up in a forum!

---

### Post by edanto on 2010-02-08
Just for the sake of anyone that's looking at this thread in the future wondering how to solve this problem - the answer is to use sudo gedit /etc/hosts to make the changes in the hosts files that I had in bold in the first post.

I bit the bullet, tried it, and I can connect to the website... and everything else seems to be working!

thanks Ordes

---

