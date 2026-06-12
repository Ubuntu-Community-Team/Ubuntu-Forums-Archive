---
title: "Anyone know of a SSH2 Client?"
date: 2010-03-29
forum: General Help
---

### Post by paulrogers on 2010-03-29
I used to use CuteFTP on windows to connect to my webserver, which would list the folders and work like a normal FTP client would

I have CuteFTP installed via Wine but its really un-responsive.

Does anyone know of any software I can install on the latest version of ubuntu for connecting to a SSH2 server?

---

### Post by steev182 on 2010-03-29
What about SSHFS?

It will mount it like it's part of your file system so it shows up in Nautilus.

---

### Post by DavePlummer on 2010-03-29
gftp will do the trick.

---

### Post by zuerston on 2010-03-29
**gftp** is great FTP software(has bookmarks too), ,**stunnel **is great SSL add on for encrypted connections for many types of internet clients, I don't know if it (stunnel) will do SSH2,but you can check it out.

[http://www.stunnel.org/about/](http://www.stunnel.org/about/)

---

### Post by 2hot6ft2 on 2010-03-29
> **paulrogers said:**
> I used to use CuteFTP on windows to connect to my webserver, which would list the folders and work like a normal FTP client would

I have CuteFTP installed via Wine but its really un-responsive.

Does anyone know of any software I can install on the latest version of ubuntu for connecting to a SSH2 server?
I can connect to my SSH2 Server in a lot of ways, here are some.
I guess gFTP would be the one you're looking for.
I'm sure there are many, many more like FileZilla which is also in the repos..

**Tranferring files using a GUI (Graphical User Interface) like nautilus or krusader**

Nautilus (Ubuntu)
Places > Connect to server
Service Type: SSH
Server: IP Address of the server
Port: The port you set the server to
Folder: /home/<your-user-name-on-the-server>/
You can check the "Add Bookmark" box and it will show up under Places as Whatever you name it so you can just click on it like a folder.
Click on Connect

krusader (Kubuntu)
Tools > New Net Connection
Protocol: fish://
Host: IP Address of the server
Port: The port you set the server to
Username: Your username on the host computer
Password: Your password on the host computer
Click on Connect

gFTP
Host: IP Address of the server
Port: The port you set the server to
Username: Your username on the host computer
Password: Your password on the host computer
Select SSH2
Click on the icon to the left of Host that has 2 computers to connect (and disconnect)

Dolphin (also has a split view to work on 2 folders at one time)
Click on Networks on the left
Click on Add Network Folder
Select Secure shell (ssh)
Click on Next
Put in your Name
Put in your Username (username on the host computer)
Server: The IP Address of the server
Port: The port you set the server to
Folder: /home/<your-user-name-on-the-server>/
Encoding: Change to (Unicode UTF-8) or whatever works for you
Checking "Create an icon for this remote folder" is up to you
Click on Connect

Gigolo
Click on Connect
Service type: SSH
Server: IP Address of the server
Port: The port you set the server to
Username: Your username on the host computer
Click on Connect
The server will show up in the window (sftp for (username) on (IP Address of the server))

---

### Post by paulrogers on 2010-03-29
Thankyou all

I will try some of the options now.

---

### Post by eudemus on 2010-05-25
This hasn't worked for me.
In dolphin and konqueror I get "unexpected SFTP error: 2 Error encountered while talking to ssh"

---

### Post by CharlesA on 2010-05-25
Try filezilla, it's in the repos.

---

### Post by eudemus on 2010-05-25
Yeah, filezilla works. Should have mentioned that.
But it's super-clunky, and I have previously been able to use network folders just in the same way as I use folders on my own machine direct from Dolphin.

It used to work.
I'm foxed as to why it doesn't any more.

I have openssh-client (and -server) installed.
????

---

### Post by DavePlummer on 2010-05-30
From the menu, select Places -> Connect to Server. In the resulting dialog box, select Service type: SSH, enter the IP address or host name of the SSH server, enter the User Name, and click the "Connect" button. You should then be prompted for the user's password (unless you previously set up public key authentication). Once the connection is made, you will be able to browse the remote machine in Nautilus. Hope this helps.

---

### Post by bakegoodz on 2010-05-30
I just use the built in support in Gnome. Just do a alt-F2 and type in stfp://user@servername
Then you get a regular gnome file window that you can copy files to or from

---

### Post by BoneKracker on 2010-05-30
I haven't used Ubuntu, Gnome, or KDE in years, but it used to be you could simply type it into the address bar of Nautilus or Krusader.```
ssh://hostname
```
That would work fine as long as you had local name resolution, wanted to log in as your present username on the client machine, and the sshd was running on the default port.

If not, you could vary any or all parameters accordingly:
```
ssh://fred@bedrock
ssh://fred@bedrock:8080
ssh://192.168.1.101
ssh://192.168.1.101:8080
ssh://fred@192.168.1.101:8080
ssh://fred:password@192.168.1.101:8080
```

It handled it using the Gnome vfs (fuse-based sshfs, I think), and KDE handled it via FISH, I believe.  This is probably at least partly wrong by now, but it might be useful to someone to know if you can just type it in.   (Oh, and I think including the password is probably a bad idea, as I suspect it's possible for it to end up in an address history or a log somewhere in the event of an error).

---

