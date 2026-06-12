---
title: "SSH configuration help"
date: 2012-08-28
forum: General Help
---

### Post by hhaydoura on 2012-08-28
Hello guys, I'm new to this and to ubuntu well I want to configure ssh in a way that I can log in to another computer from my admin pc, in other words, i want remote accessing, what are the steps to do this??

Hello guys, I'm new to this and to ubuntu well I want to configure ssh in a way that I can log in to another computer from my admin pc, in other words, i want remote accessing, what are the steps to do this??

Well, the whole problem is that I need help in the steps to do this :D what am i supposed to write on my pc and what should i write on the user pc so that everything goes well

---

### Post by Lars Noodén on 2012-08-28
All that's needed is that you install the package openssh-server on the target server.  Then you can log in using ssh or sftp.  

It would be a good idea to disable password authentication and use only [keys for authentication](https://help.ubuntu.com/community/SSH/OpenSSH/Keys).  Another good idea would be to [disable remote root login](http://www.howtogeek.com/howto/linux/security-tip-disable-root-ssh-login-on-linux/).  But other than that, it's ready to go out of the box.

---

### Post by The Cog on 2012-08-28
For the admin PC, everything should already be there. Just open a command prompt and enter the command:
> ssh user@server
changing "user" to the username you want to log in as, and changing "server" to the server name or IP address of the server you want to administer.

For the server, you need to install the package openssh-server. This command will do it:
> sudo apt-get install openssh-server
But remember that this server allows remote access by anyone who can connect and guess a username and password. There are password guessing bots on the internet that hunt for SSH servers and spend all day guessing passwords. These guides might help:
[https://www.google.co.uk/?q=securing+ssh+server](https://www.google.co.uk/?q=securing+ssh+server)

---

### Post by Lars Noodén on 2012-08-28
To install the package [openssh-server](apt://openssh-server) on the target machine, use Synaptic or the Software Center, or in the terminal enter [font=Courier New]sudo apt-get update && sudo apt-get install openssh-server[/font].  See also the links provided in the previous post.

To connect from the user's machine to the target machine, there are many ways.  In the terminal you can use [ssh](http://manpages.ubuntu.com/manpages/precise/en/man1/ssh.1.html) or [sftp](http://manpages.ubuntu.com/manpages/precise/en/man1/sftp.1.html).

```

sftp hhaydoura@*192.168.100.25*

```

Or you can use the file manager.  In Nautilus, go to File->Connect to Server, then enter the login credentials for the target machine.  The remote machine will then be available just like your other files.

---

### Post by hhaydoura on 2012-08-28
well my case is a bit more complicated, i'm working on a command-line-only ubuntu OS, no GUI, I created the user, lets say its called "userA" , the domain is "ubuntu", when I log in as root I'm supposed to write ssh userA@ubuntu ???  then sudo apt-get install openssh-server should be written where?? after that how do I test it??

---

### Post by Lars Noodén on 2012-08-28
[font=Courier New]sudo apt-get update && sudo apt-get install openssh-server[/font] should be written over on the target machine (called 'ubuntu' in your example).  

From the admin machine you can connect to the other machine using ssh or sftp in the terminal: [font=Courier New]ssh userA@ubuntu[/font]  The syntax is the same for sftp.

---

### Post by hhaydoura on 2012-08-28
I guess the target machine here is the user's machine,  I'm getting the error saying userA is not in the sudoers file. this incident will be reported. I guess am lost right now :p

---

### Post by The Cog on 2012-08-29
You need administrator (root) priviledges to be able to install the openssh-server. In Ubuntu, members of the **admin** group can use the **sudo** command to run other commands as though they are root. It would seem that userA is not allowed to do that. You will need to contact the administrator of the Ubuntu server and ask them to install openssh-server for you.

---

