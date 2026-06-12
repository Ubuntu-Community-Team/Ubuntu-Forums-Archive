---
title: "A nice , easy hassle free FTP server"
date: 2010-04-11
forum: General Help
---

### Post by Power-Inside on 2010-04-11
I need to get a nice free **SIMPLE** FTP server for my kubuntu 9.10 karmic koala..

A working , stable userfriendly GUI is preferred something like FileZilla server.. but FileZilla server is only available for windows I guess.

I've tried Gadmin -Proftpd , pureadmin + pure-ftpd but those are buggy , especially the GUI doesnt respond to stuff properly and I mostly need to sudo on them , start/stop the service.. and stuff but it never lets me log in via my another computer (windows)..And The log simply says "password failed" (gadmin proftpd) even though I put the right password..

I need a FTP server setup with least configurations.. im talking about a simple one where I need to create a user abc with password xyz and that this should work with the ftp login on a windows computer on my LAN.

I'd even go for a non GUI one if all I had to do was to edit some SINGLE config file and start the service... pls state the steps anyway..

thanks n if required, do reply for any clarifications..

---

### Post by cogier on 2010-04-11
Have you tried Firefox with the FireFTP add-on. Open Firefox go to **Tools>Add-ons>Get Add-ons**and search for FireFTP and install. Restart Firefox when done. See attached picture. But I am not sure this is a server - Opps.

---

### Post by HermanAB on 2010-04-11
Hmm, if you install either proftpd or vsftpd and then resist the temptation to change anything, it should immediately work.

Both proftpd and vsftpd are preconfigured to work out of the box, so it can't be easier.  If however, you insist on modifying the configuration files, then of course all bests are off.

Absolutely any GUI and command line FTP clients should work, such as Nautilus, Dolphin, Firefox+FireFTP, Konqueror, Gftp, FileZila Client and the default Linux and Windows ftp command line clients.

---

### Post by Power-Inside on 2010-04-12
There are loads of working GUI CLIENTS... but I need SERVER.. FireFTP addon for firefox is a client not a server..

@hermanAB , for some reason , im going for vsftpd as it seems i've not tried it.. is it GUI?  will it appear in the kde app launcher menu in my kubuntu 9.10 ? and how to create a user abc with password xyz to be able to connect to the FTP server?

---

### Post by editrix on 2010-04-12
I think you're looking for something that isn't there, and doesn't have to be. I installed proftpd and, as Herman says, it just works out of the box.


> **Power-Inside said:**
> will it appear in the kde app launcher menu

If you're using KDE, then Konquerer is what you use. In your **client**, just split the window (Ctrl-Shft-L) and then type in [ftp://whatever_the_IP](ftp://whatever_the_IP) address_or-name_of_host_is and you should see the files on your server box. Then you can drag and drop from one pane to the other.

---

### Post by Power-Inside on 2010-04-12
> **editrix said:**
> I think you're looking for something that isn't there, and doesn't have to be. I installed proftpd and, as Herman says, it just works out of the box.




If you're using KDE, then Konquerer is what you use. In your **client**, just split the window (Ctrl-Shft-L) and then type in [ftp://whatever_the_IP](ftp://whatever_the_IP) address_or-name_of_host_is and you should see the files on your server box. Then you can drag and drop from one pane to the other.
isnt that method simply asking the ftp server to log in by an anonymous ftp user which must be configured out of the box? I need to set up a username and password login to the ftp server.

how to do that in vsftpd or proftpd... i've seen options such as virtual users and local users.. im really confused

---

### Post by editrix on 2010-04-13
> **Power-Inside said:**
> isnt that method simply asking the ftp server to log in by an anonymous ftp user which must be configured out of the box? I need to set up a username and password login to the ftp server.

IIRC--and it's been a while, so I can't be sure--it does ask for a username and password. And you get to tick a box to store the password.

> how to do that in vsftpd or proftpd... i've seen options such as virtual users and local users.. im really confused

At this point, so am I ;-) I'm sure there's documentation, though. Again, IIRC, there's a config file for proftpd where you can comment out or uncomment the settings.

Sorry I can't be more help, but the only thing I'm positive about is that you don't need to launch anything from any menu.

---

### Post by Power-Inside on 2010-04-13
Thanks for the replies , but my problem remains unsolved.. seems like I will have to experiment and dig myself into the documentations...

I thought server administration on linux was easier because people say linux is good for a server..

It was a lot easier on windows..

---

### Post by Power-Inside on 2010-04-13
Ok , i just installed pureadmin + pureftpd and I cant login with a user abc and password xyz (virtual user)..

the log :-

```

Apr 13 18:12:46 Power-inside pure-ftpd: (?@localhost) [INFO] New connection from localhost
Apr 13 18:12:48 Power-inside pure-ftpd: (?@localhost) [INFO] PAM_RHOST enabled. Getting the peer address
Apr 13 18:12:53 Power-inside pure-ftpd: (?@localhost) [WARNING] Authentication failed for user [abc]

```

---

### Post by cryptotheslow on 2010-04-13
I started from the same point as you...  not a clue how to do it :D

I found using proftpd then following setup option B. from this thread:
 [http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588)

had me up and running in minutes. I used the standard GUI for the ftp user creation rather than the commands as recommended.

One thing to note - with proftpd you do not login with the ubuntu username, you setup an alias for it in the proftpd config and use that.

It's not as complicated as it looks. I can post up my proftpd.conf if it helps.

Good Luck

---

### Post by Sub101 on 2010-04-13
> **Power-Inside said:**
> Thanks for the replies , but my problem remains unsolved.. seems like I will have to experiment and dig myself into the documentations...

I thought server administration on linux was easier because people say linux is good for a server..

It was a lot easier on windows..

If your interested in creating a complete server you might want to use webmin.

[http://www.webmin.com/](http://www.webmin.com/)

From there you can setup an ftp server, as well as apache, ssh etc.

---

### Post by Power-Inside on 2010-04-13
Thanks cryptotheslow & Sub101..

Webmin could be of use to me as I like administration via browser.. its more convenient

@cryptotheslow , the proftpd thread you gave is interesting.. might have to try it. thx

---

### Post by FiReiSFuN on 2010-04-13
OK. I wouldn't say that admin of a linux server is "easier", but it is certainly more robust and tends to give you a lot of options.

Use vsftpd. Very easy to install and administrate. Here's the basics:

1. In terminal, do: sudo apt-get install vsftpd
[INDENT]This installs the server and starts it running. Now we have to edit the configuration.[/INDENT]

2. Edit (with root priveliges) /etc/vsftpd.conf - this is the configuration file for vsftpd and controls the server.

3. You will (probably) want to set the following parameters:
anonymous_enable=NO (unless you want to allow anonymous access)
local_enable=YES (so local users can login)
write_enable=YES (so users can upload)
local_umask=022 (sets permissions of the uploaded files)
ftpd_banner= (you can set this to be "Welcome to blah ftp")
chroot_local_user=YES (I'll discuss this below)

The rest you will probably ignore for now.

4. Since you edited the config file, you must now reload it with: sudo /etc/init.d/vsftpd reload

5. Go to another computer (or test it from the local computer), open an ftp client, and login with the ip of the server computer, your Ubuntu username, and your Ubuntu password. It should just work (provided you don't have a firewall blocking port 21).

You will find yourself inside your home directory, free to upload and download files. This this the chroot_local_user option. If you don't set this, users will be able to browse the whole filesystem and have permissions according to how permissions are set on the files.

To give someone else access to your ftp, you will have to make them a local user account on the server: sudo useradd whatevername, then sudo passwd whatevername, to change the user's password. You can also make virtual users (i.e. users that don't have a local login) but I think that might be a bit advanced and overkill for what you probably need - it involves setting up mysql. One option is to make a single user for all ftp logins (ie, ftpuser or such) and give that out to everyone who you want to have ftp access. Then make /home/ftpuser a mountpoint for a large storage partition to isolate it from the rest of the filesystem, and store things in there you want people to have ftp access to.

Any questions? Leave a post and I'll reply. I've been using vsftpd in a business environment for a little over six months (taking over from a buggy Windows ftp server) and I have been impressed with the speed and low system resource requirements.

---

### Post by FiReiSFuN on 2010-04-13
I forgot to add:

Installing the server this way means that it will start up when your computer starts up, and stop when it shuts down. You won't have to run a program to start it, so it won't be in any menu.

If you ever wanted to stop it, you could go to the terminal and do:

sudo /etc/init.d/vsftpd stop

And then to start it again (it will restart on reboot though):

sudo /etc/init.d/vsftpd start

To make it so that it doesn't start automatically on boot (you will have to start it manually every time):

sudo update-rc.d -f vsftpd remove

If you change your mind, and want it to start automatically:

sudo update-rc.d vsftpd defaults

Hope this helps!

---

