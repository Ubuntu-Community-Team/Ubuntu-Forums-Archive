---
title: "Setting up a server &amp; auto backup"
date: 2012-05-24
forum: General Help
---

### Post by rwonder on 2012-05-24
Hey guys,

I'm looking to setup a server and have a few questions.
I've been learning about linux and networking and I'm just looking to learn.  I'm looking for some help.

I want to be access my file system from anywhere.
So if I want to stream a movie or download a word doc I can do that.

Is Ubuntu the right platform for this?
What other pieces of software would I need to set this system up?
What security software should I use?
Is there software that will allow me to create a ghost of my hard drive automatically?
How can I create users and assign them their own file system and permissions?

Thanks guys!

I really appreciate it if you can help guide me :)

---

### Post by lukeiamyourfather on 2012-05-24
> **rwonder said:**
> 
I want to be access my file system from anywhere.
So if I want to stream a movie or download a word doc I can do that.


Two things to point out. This can be very dangerous as anyone on the internet could potentially breach the security and delete the files or worse steal them. The level of functionality to expect varies based on the bandwidth available. Streaming movies remotely is not realistic with a typical broadband connection (a few megabits per second upload). Also some ISP specifically prohibit hosting servers on their connections.

> **rwonder said:**
> 
Is Ubuntu the right platform for this?
What other pieces of software would I need to set this system up?
What security software should I use?
Is there software that will allow me to create a ghost of my hard drive automatically?
How can I create users and assign them their own file system and permissions?


Ubuntu is capable of doing this but so are many other operating systems. Whether Ubuntu is the right choice or not depends on what you already know or are willing to learn. The "proper" way to go about this would be to setup a VPN which would allow remote users to connect as if they were on the LAN. Shares could be setup on the Ubuntu machine with NFS, Samba, or whatever other server you want to use.

If you plan to access the files from machines that are not your's then the VPN might not work for you since it requires client side software. In that case an FTP server would allow access to files remotely (as long as the client has FTP software which is more common than VPN software) but it might not work for all of the purposes like streaming a video. The video would have to be downloaded by the client and then opened rather than streamed. 

For backing things up I'd check out Dejadup (default backup utility in Ubuntu) or rsync which is a command line backup tool that can be scheduled with cron (daemon that runs scheduled tasks). Files could be backed up to another server on the network or a local disk.

There are probably a thousand other ways to do it but those should help you get started on researching the best option.

---

### Post by drdos2006 on 2012-05-24
Here is a HOWTO which I found comprehensive and invaluable for me to start learning about server requirements. 
Uses Webmin to allow your browser to connect and modify your server settings on your network.
You could also install the Desktop plus install and run the server as a virtual machine using Virtualbox and that is how I run my testing websever.

> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
"Setting up a Linux Server, Start to Finish, using Webmin". By Kevin Elwood



And on your server..........

```

Logon to your server and download from your server with :
sudo wget http://prdownloads.sourceforge.net/webadmin/webmin_1.580_all.deb

Install with :
sudo dpkg -i webmin_1.580_all.deb

Add extra libraries with :
sudo apt-get -f install

```
Uses a browser pointed to [https://your_server_IP:10000](https://your_server_IP:10000) to edit files, create shares, startup daemons etc..

regards

---

### Post by rwonder on 2012-05-24
> **lukeiamyourfather said:**
> This can be very dangerous as anyone on the internet could potentially breach the security and delete the files or worse steal them. 

...

If you plan to access the files from machines that are not your's then the VPN might not work for you since it requires client side software.

Thanks for the advice!
Is there some security software I can use?
Yes, I would be accessing it from machines that are not mine.

I guess I am looking to set something like my university network.  I can ssh into any machine from anywhere, access my file system, the entire network, and even some applications.

Or even if I don't use ssh that's fine as long as no software is required.

---

### Post by lukeiamyourfather on 2012-05-25
> **rwonder said:**
> Thanks for the advice!
Is there some security software I can use?
Yes, I would be accessing it from machines that are not mine.

I guess I am looking to set something like my university network.  I can ssh into any machine from anywhere, access my file system, the entire network, and even some applications.

Or even if I don't use ssh that's fine as long as no software is required.

What do you mean by "security software" because that's pretty vague. Different softwares have security features like passwords and encryption but there's no holy grail of software that will magically make everything secure.

Since you mentioned ssh you could just use that. To get the server component on the host install the ssh package (installs the server and other dependencies). To use graphical applications connect with X tunneling like this from the client.

```
ssh -X user@remotehost
```

Note the case of X in the command. If you launch a graphical application like VLC it will show the GUI on the client side. This requires more bandwidth than ssh without X tunneling so bandwidth is still a factor. Also if the client is Windows this won't work.

---

