---
title: "Windows Commands to Linux"
date: 2009-08-03
forum: General Help
---

### Post by Zuke24 on 2009-08-03
I've just started to get my feet wet in Linux, and so far I really like how I can program things to do nearly anything I want.

Only issue is that all the servers here at work are Windows.  I would like to learn the commands to be able to do things on the windows machines, but from my Linux notebook.  I'm having problems finding how to translate Windows commands to Linux, and the manpages aren't exactly laid out in a helpful manner.

For instance:
Windows machine has a service that stalls and I need to restart it from time to time.  I've written a batch file that goes something like this-
@echo off
sc {server name} stop {service name}
sc {server name} start {service name} 

Now according to [this site]("http://www.yolinux.com/TUTORIALS/unix_for_dos_users.html") I'd just use the "service" command (though it doesn't specify the syntax for remote machines).  According to the manpages though, that command doesn't exist.

Can anyone help point me in a helpful direction?  Thank you so much.

---

### Post by Locutus_of_Borg on 2009-08-03
sorry to not be of much help, but i wonder if you can just directly run the commands/batch files after loading up a 'wineconsole cmd' command prompt?

should you have wine installed that is.

---

### Post by finch127 on 2009-08-03
well here are some I know:

1. Service - Yeah it does exist, its usage is like this:

sudo service <service name> stop [or you can use restart, or start]

for example:

sudo service network restart

2. echo is the same

3. dir from windows is like ls

so for example 

ls -al will list all the files in a directory, including the hidden ones (-a is for all) and will give you long (-l) listings

4. mkdir is self explanatory

5. find allows you to scan your filesystem for a file

6. grep is used to search text files for a line and has many options

7. cat is used to display text files in the terminal, IE cat <filename>

8. cp is used to copy files, like this: cp <file1> <file2>

9. mv is used to move files, just like the cp command

10. rm is used to delete files permanently, rmdir is used to delete directories permanently. it is often used with the -rf flags, f for forcefully, and r for recursively. Be careful with this one

There are more, but here are some helpful ways to find information about linux commands

You already know how to use man I assume? 

You can also do this:

whatis <programname> and this will give you a summary of the commands function from the man page

usually you can also use

<programname> --help to get a statement about its usage and all of its options, or <programname> -h usually works too as well is just typing the program without anything.

---

### Post by wojox on 2009-08-03
You might want dosemu:
[http://dosemu.sourceforge.net/](http://dosemu.sourceforge.net/)

---

### Post by Zuke24 on 2009-08-03
I did not know the whatis command, that's kinda cool.  I've been using the man command, but it still doesn't give me the syntax to use in this instance.  I can do whatever I want on my local machine using it, but it doesn't tell me how to do it for remote machines.

---

### Post by finch127 on 2009-08-03
Yeah I almost forgot too, if you really want you can use alias to change linux commands into your windows syntax. I am no expert on its configuration or use but basically it works by substituting what you want with the actual command. For example, when I came from windows, I used dir instead of ls alot, so in my aliases file i set dir=ls so that way whenever i used dir it would use ls instead and I didnt have to keep typing ls or remember it [eventually i did and got rid of my aliases].

---

### Post by finch127 on 2009-08-03
Oh yeah, almost forgot, for remote Linux machines you have to learn how to use ssh which basically gives you remote shell access. You can use ssh from linux to windows i believe, though I really have no expertise here. Basically it allows you to access the remote machine with a terminal like you are there and any commands you use affect that remote machine.

---

### Post by whitethorn on 2009-08-03
Is it possible for you to remote login to your windows machine?  You should be able to start a ms-dos console and then run your batch files.

---

### Post by Zuke24 on 2009-08-03
Well, sure.  But it's so much faster to do things straight from the CLI (or build a script to do it for me) than remote into a server and do it from there.

---

### Post by asmoore82 on 2009-08-03
Yes, it sounds like you'll be wanting ssh: ```
sudo apt-get install openssh-server
```
 
the OpenSSH daemon opens 1 port(22) which and gives you
remote shell access(ssh), remote file access(scp or sftp),
and remote sync access(rsync) all securely and encrypted.

an excellent free ssh client for windoze is PuTTY: [http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)

---

### Post by Zuke24 on 2009-08-03
Yeah, I've used Putty to control our Webserver in the past, but have never tried to do it in reverse!

So, SSH commands should work on Windows then too?

---

### Post by asmoore82 on 2009-08-03
This illustrates how backwards-thinking the whole windoze world is ...

why should the developers of the `service` or `sc` command have to fiddle around with networking code? ...
it is a waste of their time and the end result will almost certainly be worse **_and_** **insecure**.

The existence of SSH frees all developers to do what they do best -
if people need to use their command remotely, they are covered, now and forever.

The ssh method also means that all of your admin tools don't have to be installed on your client -
all your client needs is ssh. This also instamagically solves the problem
of version mismatches between your client and the server.

ssh is capable of running a "one-shot" command on a remote machine, simply specify the command:
```
ssh <user>@<remote-host> <command>
```

SSH can also "throw" GUI apps across the 'net - you have to enable X11 port forwarding ...
then you can do something like this to edit user accounts on the server graphically:
```
ssh -fY <user>@<remote-server> users-admin
```

I almost forgot, add another to the laundry list of features of the ssh server:
ssh, scp, sftp, rsync, X11, and **SSL Tunneling**. You can forward arbitrary
ports back and forth and have them all protected with SSH's strong encryption.
And remember, SSH provides ^all of this^ but still only listens/exposes 1 port on the server(22).

**You will probably want to look into password-less ssh with public keys.**
That reopens the possibility of your batch file approach with minimal interaction.
But again, it will do it in the most secure way possible.

---

### Post by Zuke24 on 2009-08-03
OK, so I have freeSSHd running on my Windows machine, ssh installed on my laptop.

ssh 10.0.0.9 -l Admininstrator
Asks for my password, and I enter it, then nothing.  No prompt, no blinking cursor, nothing.  Did I miss a step?

---

### Post by finch127 on 2009-08-04
Could be a usage issue? Idk I dont use ssh but it looks like you must use:

ssh Administrator@10.0.0.9 blah blah

---

### Post by Zuke24 on 2009-08-05
Still having issues.

I try and connect to the remote server now, and it won't accept my password!  So I create a user that has no password . . . and it still won't accept it.

---

### Post by asmoore82 on 2009-08-10
Oh!!

the whole time you have wanted a command on a Linux box
to restart a service on a Windows "server" ...
I just caught on to this.

I haven't a clue, Windoze doesn't play well with others.

---

### Post by finch127 on 2009-08-11
this may sound dumb but you may want to try Telnet instead of SSH

---

