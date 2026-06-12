---
title: "FTP server installed, now what?"
date: 2011-07-26
forum: General Help
---

### Post by L a r r y on 2011-07-26
From Ubuntu Software Center in Ubuntu 10.04:

> **FTP server with SSL encryption support**
ftpd-ssl

Top line is the large-font title, second line is the description.

I installed this program so I could do an FTP file transfer from my Windows computer to over here on my Ubuntu computer.

There is no sign of it in my Applications menu, so it appears to be a command-line program with the file name "ftpd-ssl."

So, to the command line terminal:

```
this-computer@fast:~$ ftpd-ssl help
No command 'ftpd-ssl' found, did you mean:
 Command 'ftp-ssl' from package 'ftp-ssl' (universe)
ftpd-ssl: command not found

         (OK try this)

this-computer@fast:~$ ftp-ssl help
The program 'ftp-ssl' is currently not installed.  You can install it by typing:
sudo apt-get install ftp-ssl
this-computer@fast:~$
```

At issue here, is, if I have successfully installed an FTP server, I need to configure it to set up accounts on the server, I need to be able to either access a menu item in Applications or type something in the Terminal to gain access to this configuration screen, and so on.
There is no reference to it in the Apps menu, like there is for my gFTP client, and there is no ftpd-ssl on the command line, and ftp-ssl is not installed, so that's a different program entirely.

?????

I can successfully remove it easily enough, but that's the only thing I know how to do with it.

So how do I configure this thing?



Thank you.

---

### Post by neu2buntu on 2011-07-26
im by no means an expert on this , but i have been able to transfer files between 2 ubuntu boxes connected by wire(auto eth0). you will need the ftp server to be installed on your windows machine and any ftp client on your ubuntu machine.  in the terminal i would just type ```
ftp open [ip address of the windows machine]
```  << i have no knowledge about windows ftp protocol, but this info may get the ball rolling for you at least.  you will need to look at the ```
man ftp
``` for further commands.   also iirc firefox can be used for transfering the files between the 2 machines, but i cant clearly remember how this is done, possibly by typing ```
[ftp://then]("ftp://then/")_the_ip_of_the_server_here
```t[his link may help with firefox setup as ftp client ]("http://support.mozilla.com/en-US/kb/Accessing%20FTP%20servers")

---

### Post by L a r r y on 2011-07-27
> **neu2buntu said:**
> ... you will need the ftp server to be installed on your windows machine ...

You gave me an idea, for I have an FTP client here.  I think I should be able to find some free FTP servers for Windows XP, and rather than push a file from Windows, I can pull it from here.  That would bypass the conundrum that I found myself in.

It would still be interesting to find a Linux FTP server that can be installed and configured, better than I encountered to date.

Besides this FTP solution, there is a way to share files between networked computers both running Windows and Ubuntu, but my Windows computer was crippled with an ooVoo video chat software installation that installed without my agreeing to its EULA, and without doing a fresh install of Windows, I don't know my limitations in that area.

---

