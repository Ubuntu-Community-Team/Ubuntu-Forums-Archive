---
title: "autofs and auto.master not working help"
date: 2006-04-04
forum: General Help
---

### Post by lleb on 2006-04-04
Hello, my Debian system (personal game box and my workstation) is also my NFS server for all of my media files for my house LAN.

In my LAN i have the following setup:

Debian workstation (NFS server) and game box
CentOS laptop
Media box has been Debian, CentOS, and FC5
IPCop firewall and DHCP server
Edubuntu, kids computer with dual boot for winXP Pro

All of the computers in the LAN that have a GUI can access my NFS shares with automounting and the /etc/auto.master with the following information:

```
### howto add to /etc/auto.master for automounting of the shares:

/etc/auto.master (append):

	/sharedisk	/etc/auto.sharedisk

	
create /etc/auto.sharedisk (append):

share   -rw,rsize=8192,wsize=8192,intr 192.168.2.100:/sharedisk/share
stuff   -rw,rsize=8192,wsize=8192,intr 192.168.2.100:/stuffdisk/stuff


restart autofs wtih:

service autofs reload

if error, then /etc/init.d/autofs start or restart will also work.
```

so that is the extact setup i have on my media box and my laptop.  i also have that setup on my Edubuntu system and it will not work there.

yes i have created the proper folders, yes i have double checked the permissions for my user to access those folders and no love.

I have to manually mount the shares with the following commands or it will not work.  

```
sudo mount -t nfs -o rw,rsize=8192,wsize=8192,intr 192.168.2.100:/sharedisk/share /home/user/share
```

problem with that is simple.  my kids will reboot that computer 3 - 10 times a day to change from linux to windows.  i do not allow that computer to have any internet access in Windows, but do in linux.  so they play their kids web sites like cartoon network and others in linux on firefox, but their jump start games they have to play in windows.  wine and Cedega do not work for the jumpstart games or i would use those options.

so not only do i have to manually type that command in every time they want to watch a movie or listen to music on my NFS server, but if something happens and their computer (the edubuntu one) has any kind of LAN issue, then it will lock up the system due to the hard mount to the share.

none of my other systems have this issue and there is nothing i can do to get it to work on the Edubuntu system including removing apt-get remove iptables to ensure the firewall was not the issue.

so help from the ubuntu community i am seeing more and more about this potentially great distro that is disapointing.

lack of SSH access, CUPS does not share properly via the LAN, and now autofs not working properly.

its great as a stand alone system, but for that i can use windows.  it is proving very frustrating in a network and near impossible for remote management.  help please.

---

### Post by lleb on 2006-04-05
ok, did i post this in the wrong forum?  if so could a mob please move it were it will get some attention so i can get this issue solved.

thank you.

---

### Post by lleb on 2006-04-05
guess there is no way to make autofs work in *buntu then.

thanks for the help.

---

### Post by bigpook on 2006-06-03
wow, I searched for autofs on this forum and this is all I found.

I too am having issues getting autofs to work under ubuntu/kubuntu. Using dapper now, but without autofs working it will be difficult to continue. 
I use SUSE and FC and have no problems setting up autofs. Its brain dead simple. But for some reason I cannot get it to work under ubuntu.

If someone has the answer or a how-to please let me know.
[email]bigpook@gmail.com[/email]

I will bang on it some more....

---

### Post by henriquemaia on 2006-06-08
[quote=bigpook]wow, I searched for autofs on this forum and this is all I found.

I too am having issues getting autofs to work under ubuntu/kubuntu. Using dapper now, but without autofs working it will be difficult to continue. 
I use SUSE and FC and have no problems setting up autofs. Its brain dead simple. But for some reason I cannot get it to work under ubuntu.

If someone has the answer or a how-to please let me know.
[EMAIL="bigpook@gmail.com"]bigpook@gmail.com[/EMAIL]

I will bang on it some more....[/quote]

I'm also having problems with autofs. Everything properly configured, still no luck. Any ideas on how to solve this?

---

### Post by henriquemaia on 2006-06-09
[quote=henriquemaia]I'm also having problems with autofs. Everything properly configured, still no luck. Any ideas on how to solve this?[/quote]

Well, I'll stick to WebDAV for now.

---

### Post by mathiraj on 2006-06-15
I'm too on the same boat. FC5 mounts all the exports of my NFS server with out any problem. without even changing any /etc/auto.* files.

I configured FC5 and ubuntu as nis clients and FC5 automatically mounted my home directory and let me login.

*ubuntu did not mount my home directory itself. I had to manually mount it.

Having difficulty to get autofs work with *ubuntu. somebody help!!!

---

### Post by vavoli on 2006-07-02
Hi all,
I'm a new Ubuntu user. On My lan I've an FC5  nfs server/client and an Ubuntu 6.06 (Dapper ?) nfs server client.
My autofs works both on FC5 and on Ubuntu. This is the only line I've on my auto.master:

/net        /etc/auto.net

If you do a ls /net/name_pc you will see the nfs exported. This system works both on Ubuntu and on FC5.

Vavoli

---

### Post by dir3wolf on 2006-11-11
> **vavoli said:**
> Hi all,
I'm a new Ubuntu user. On My lan I've an FC5  nfs server/client and an Ubuntu 6.06 (Dapper ?) nfs server client.
My autofs works both on FC5 and on Ubuntu. This is the only line I've on my auto.master:

/net        /etc/auto.net

If you do a ls /net/name_pc you will see the nfs exported. This system works both on Ubuntu and on FC5.

Vavoli
worked like a charm. ;-))))

---

