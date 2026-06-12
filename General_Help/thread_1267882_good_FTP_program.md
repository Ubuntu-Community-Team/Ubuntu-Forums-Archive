---
title: "good FTP program"
date: 2009-09-16
forum: General Help
---

### Post by RFXCasey on 2009-09-16
What's considered the best ftp program? VSFTP? Is GFTP any good or secure?

---

### Post by sunchiqua on 2009-09-16
Depends on what you need .. Personally, I like Filezilla ( client ) and vsftp ( server ).

---

### Post by howlingmadhowie on 2009-09-16
i've only ever used vsftpd as a server, but it does all i want it too.  as a command line client, lftp is excellent.

in general i'd recommend using openssh instead. security is a lot better and performance isn't a problem on modern computers.

---

### Post by jondkent on 2009-09-16
Unless you really have a need for ftp (can't really think why...but may there is one), I'd second using openssh and its sftp daemon.  Just way way way safer.

---

### Post by XCan on 2009-09-16
Also remember that you usually can connect to sftp servers by simply changing the protocol in your favorite FTP-client. For me, I use gFTP (only doing trivial stuff), but Filezilla is nice as well.

---

### Post by Finalfantasykid on 2009-09-16
Filezilla is pretty good, I use it on Windows.

However on Ubuntu, I find it much easier to just go "Connect to Server..." and choose FTP with login.  That way I can easily view all the files on a server in a nautilus window, and edit them using gedit or whatever, save and the change is made immediatly.  With Filezilla, you would have to download the file, change it, then re-upload it.

---

### Post by beavis69 on 2009-09-16
SFTP is just a lot more convenient than using ssh. It is trivial to force vsftp to use ssh so you get the best of both worlds.

---

### Post by sudojack on 2009-09-16
> **RFXCasey said:**
> What's considered the best ftp program? VSFTP? Is GFTP any good or secure?

ncftp works great for me, its cli though (although shouldn't be a problem since I'm pretty new to Linux and i use it just fine!)

---

### Post by Ratscallion on 2009-09-16
At the moment, I'm going FileZilla on Windows and Ubuntu... I really like it.. 

> **Finalfantasykid said:**
> Filezilla is pretty good, I use it on Windows.

However on Ubuntu, I find it much easier to just go "Connect to Server..." and choose FTP with login.  That way I can easily view all the files on a server in a nautilus window, and edit them using gedit or whatever, save and the change is made immediatly.  With Filezilla, you would have to download the file, change it, then re-upload it.

Ooh, might try this... If it works, I recommend it now!

---

### Post by lovinglinux on 2009-09-16
> **XCan said:**
> Also remember that you usually can connect to sftp servers by simply changing the protocol in your favorite FTP-client. For me, I use gFTP (only doing trivial stuff), but Filezilla is nice as well.

I also like gFTP. It works great with FTP or ssh and the interface is simple.

---

### Post by RFXCasey on 2009-09-16
> **howlingmadhowie said:**
> i've only ever used vsftpd as a server, but it does all i want it too.  as a command line client, lftp is excellent.

in general i'd recommend using openssh instead. security is a lot better and performance isn't a problem on modern computers.

> **jondkent said:**
> Unless you really have a need for ftp (can't really think why...but may there is one), I'd second using openssh and its sftp daemon.  Just way way way safer.

So if I have a relatively fresh Ubuntu server install how do I install openssh over the currently installed ssh or does it already come with the server edition? I am fairly extreme in my noobiness. 

> **Finalfantasykid said:**
> Filezilla is pretty good, I use it on Windows.

However on Ubuntu, I find it much easier to just go "Connect to Server..." and choose FTP with login.  That way I can easily view all the files on a server in a nautilus window, and edit them using gedit or whatever, save and the change is made immediatly.  With Filezilla, you would have to download the file, change it, then re-upload it.

HOw do you get this working with openssh. How can I be sure if I am doing this I am encrypting my connection? Like I said, really quite noobish to all of this encrypting connections especially where Linux in concerned. Simple answers will suffice, I don't have the energy right now to read through tons of links.

---

### Post by lovinglinux on 2009-09-16
> **RFXCasey said:**
> So if I have a relatively fresh Ubuntu server install how do I install openssh over the currently installed ssh or does it already come with the server edition? I am fairly extreme in my noobiness. 



HOw do you get this working with openssh. How can I be sure if I am doing this I am encrypting my connection? Like I said, really quite noobish to all of this encrypting connections especially where Linux in concerned. Simple answers will suffice, I don't have the energy right now to read through tons of links.

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)
[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)
[https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)

---

### Post by itsjareds on 2009-09-16
I may sound like a complete FTP noob, but for my simple web hosting FTP uses, FireFTP client (Firefox Addon) makes a good solution.

---

### Post by RFXCasey on 2009-09-16
> **lovinglinux said:**
> [https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)
[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)
[https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)

So am I to understand that OpenSSH is already installed in Ubuntu server edition? What is the difference between SSH and OpenSSH? How do you know which one you have installed or can you have both installed at the same time and if so how do you know which one you are using? If your running something like VSFTP how do you know that the transfers are taking place over an OpenSSH conncetion? We're talkin super noob here, super.:lolflag:

---

### Post by michaelzap on 2009-09-17
> **itsjareds said:**
> I may sound like a complete FTP noob, but for my simple web hosting FTP uses, FireFTP client (Firefox Addon) makes a good solution.

+1

I find that FireFTP is one of the best simple GUI FTP clients available for Linux. I use Filezilla when I need to do things that FireFTP can't (such as move directories on a remote server), but I don't really like it. I was gravely disappointed by the GUI FTP client programs available for Linux when I switched from Windows; none of them holds a candle to WS_FTP or WinSCP imho.

I've tried oodles of GUI FTP apps for Linux, but I'm still looking for one that I like.

---

### Post by RFXCasey on 2009-09-17
> **michaelzap said:**
> +1

I find that FireFTP is one of the best simple GUI FTP clients available for Linux. I use Filezilla when I need to do things that FireFTP can't (such as move directories on a remote server), but I don't really like it. I was gravely disappointed by the GUI FTP client programs available for Linux when I switched from Windows; none of them holds a candle to WS_FTP or WinSCP imho.

I've tried oodles of GUI FTP apps for Linux, but I'm still looking for one that I like.

What is not to like about Filezilla, I find it to be somewhat of a defacto standard.

---

### Post by michaelzap on 2009-09-17
> **RFXCasey said:**
> What is not to like about Filezilla, I find it to be somewhat of a defacto standard.

I find its interface to be really clunky. It never seems to obey the options I set in terms of keep-alive commands and whatnot. I hate that I have to click on "Synchronized Browsing" every bleeping time that I connect to a new server instead of it just doing that all the bleeping time.

Mostly it's just feature-poor and lacks flexibility and elegance when compared to WS_FTP and WinSCP (which were the two programs that I used and liked in Windows, the first being commercial and the second free).

---

### Post by Bachstelze on 2009-09-17
> **jondkent said:**
> Unless you really have a need for ftp (can't really think why...but may there is one), I'd second using openssh and its sftp daemon.  Just way way way safer.

SFTP is not FTP. Also, FTP with SSL encryption is no less secure than SFTP, but much more flexible.

> **RFXCasey said:**
> What is the difference between SSH and OpenSSH?

SSH is a protocol. OpenSSH is an implementation of SSH.

> **RFXCasey said:**
> If your running something like VSFTP how do you know that the transfers are taking place over an OpenSSH conncetion?

It doesn't. As I said, FTP and SFTP are two different protocols.

---

### Post by RFXCasey on 2009-09-17
[QUOTE=

It doesn't. As I said, FTP and SFTP are two different protocols.[/QUOTE]


Well it has sftp in it's name.:roll:

---

### Post by XCan on 2009-09-18
Yah, that can be, or rather is, misleading. FTP and FTPS can, however, be considered to be the same protocol.

About Filezilla, indeed it's powerful, but I think it's still rather new for *nix, and I found a lot of buttons untrivial for a new user to understand their functions.

---

### Post by scheuri on 2009-09-18
> **RFXCasey said:**
> What's considered the best ftp program? VSFTP? Is GFTP any good or secure?

Hi there

Sorry, but I think you mix up things or...at least...I have a hard time to understand what you need.

There is FTP as a service or deamon running on a computer/server which shall SHARE the content and there is FTP as a client programme running from a computer you wish to connect to a server running a ftp service and get the data with.

I know vsftp only as vsftpd (see the d at the end, it stands for deamon) and that is running on a server. gFTP on the other hand I know only as a client programm.

So....depending what you need I personally suggest the following for the client:
gFTP worked very well for me so far. It is easy to understand, lightweight in my opinion and is not overloaded with features. It can do ftp and sftp (ftp with the openssh protocol). However, it can not do anything in the line of ftps (ftp over ssl).
Filezilla is another choice if you want to have more features.
But I am sure there several good programms out there.
I personally suggest you start with those you can easily install by using aptituve/adept or whatever you use in (k)ubuntu to install software from the repository. There is no need to start downloading third party programs or sources and compile yourself.

As for the server:
There are again several. I personally use vsftpd and proftpd depending in what feature I need.
vsftpd is - as the name suggests - rather secure but only gives you limited features compared to other ftpd. You may need those features or you may not...that is up to do.
Both services can be installed using aptitude and their are available in the official repository.

hope I could help
cheers
scheuri

---

### Post by RFXCasey on 2009-09-18
I've been seeing some things about proFTPd have major security hole and how VSFTPd is much better. Most of the things I've read are rather old so I was wondering if this was still the case? Does proFTPd support SSH or SSL?

---

### Post by hansdown on 2009-09-20
RFXCasey,

> Trying to get vsftp 

I hope this helps.

[http://www.jonathanmoeller.com/screed/?p=905](http://www.jonathanmoeller.com/screed/?p=905)

---

### Post by RFXCasey on 2009-09-20
Ok, PRIME example, I am following what all of the vsftp install tutorials say to a "T". After installing vsftpd and tweaking you config file they all say to restart the server go to /etc/init.d/ and type vsftpd restart. Well, that don't work. I got this 500 OOPS: cannot open the config file restart. WEEEEEELLLLLLLLL, what they don't freaking say is that if you are IN the working directory that crap don't work. Why the heck not? SOOOOOOOO I got to another directory and type out the whole freaking /etc/init.d/vsftpd restart and the damn thing works. What a load of crap. So I use filezilla from another machine on my local network and log in. Well first off my custom banner isn't showing up, second this damn thing is giving me access to my entire server. I hope it only does that for local logins. I could download any system file I wanted and to an outsider that would only be a password away. Any way to secure that crap and jail people to a specific directory and subdirectories? DAMNIT MAN!#-o

---

### Post by odinb on 2009-09-20
Well, as a server, I use vsftp, and a guide for installing it with virtual users and mySQL is here:
[http://ubuntuforums.org/showpost.php?p=7977503&postcount=5](http://ubuntuforums.org/showpost.php?p=7977503&postcount=5)

As a client, I like gnome-commander (sudo apt-get install gnome-commander).

---

### Post by hansdown on 2009-09-20
RFXCasey,

> Trying to get vsftp to work 

[http://linuxpoison.blogspot.com/2008/06/vsftp-server-installation-and.html](http://linuxpoison.blogspot.com/2008/06/vsftp-server-installation-and.html)

I hope this helps.

---

### Post by ve4cib on 2009-09-20
> **RFXCasey said:**
> Trying to get vsftp to work was like pulling teeth and it still doesn't work.

Not sure what your problem is, but VSFTP has worked pretty much straight out-of-the-box for me on four different computers (two laptops, one desktop/server, and one VM).  Install the package off the repos, edit the config file to allow local users to log in and allow write operations (if necessary) -- and that requires changing at most 2 lines in the file -- and then restart the daemon (or reboot your computer if you're lazy).  Presto, done.  You can now FTP into your machine using your local username and password.

What is your particular problem with it?

---

### Post by morningboat on 2009-09-20
You can have a look at [this]("http://www.gnomefiles.org/subcategory.php?sub_cat_id=44") for a list of available FTP clients in Linux Gnome. Personally I like the multi-tabbed [CrossFTP client]("http://www.crossftp.com/").

---

### Post by RFXCasey on 2009-09-21
How does this crossFTP server stack up against vsFTPd where security is concerned?

---

### Post by morningboat on 2009-10-02
> **RFXCasey said:**
> How does this crossFTP server stack up against vsFTPd where security is concerned?

The security level is same since they are all based on the FTPS/TLS and FTPS/SSL protocols. The setup is relatively easier for CrossFTP Server. As to the performance, if you need a FTP server under very heavy burden, you can choose vsFTPd, proFTPd, etc.

---

### Post by Bachstelze on 2009-10-02
> **morningboat said:**
> The security level is same since they are all based on the FTPS/TLS and FTPS/SSL protocols.

I disagree. vsFTPd implements many features that are not part of the protocol *per se*, but greatly improve security. For example, it will refuse to run if anon_root is writable by the ftp user. Most other FTPd's won't even throw a warning.

---

