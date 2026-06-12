---
title: "Sharing Folders?"
date: 2011-05-24
forum: General Help
---

### Post by PsyclonJohn on 2011-05-24
Hello, I have 3 PC's in my household and I wanted to know if I can share folders with them lively. For example, I have LAMP server set up on all three, would it be possible for me to work on one PC then work on another and everything would automatically be shared?

Thanks,

John

---

### Post by jamesjenner on 2011-05-24
Well if your willing to use a Cloud, you could use Ubuntu One or the other popular option is dropbox. I've tried both and they're fine (though I'm having problems with Ubuntu One for bookmark sharing and note sharing). I think firefox has online sharing of bookmarks now built in, though I've never used it.

But if you wish to do it via your computers in your network then the first question I have is do you always have one computer on or do you have a NAS? NAS are getting damn cheap now and that may be the better way to go if you don't have a computer on all the time. If you wish to use one of your computers then there is Samba. Maybe someone else here will know if there is a non windows way of sharing files, I'm used to having to work with windows based pc's or laptops and Samba is the way to go for that.

Otherwise I think you will need to look at the cloud option.

Cheers,

James.

---

### Post by nothingspecial on 2011-05-24
If they are all running linux, one solution would be to mount the folder remotely using sshfs.

So the folder will only actually exist on one computer - this is not a backup solution.

So you have pc1, pc2 & pc3

On pc1 there is a folder /home/john/work

On pc2 and pc3 you make a folder also /home/john/work, then you type

```
sshfs -o idmap=user john@<ipaddress_of_pc1>:/home/john/work /home/john/work
```

on both machines. And you can change stuff on any of the 3 computers.

If you would like to make this happen automatically you can add a line to your fstab.

However there is probably a better way. Have a go anyway. :P

---

### Post by nothingspecial on 2011-05-24
You can do this without all that cli gobbldygook.

Assuming you are running ubuntu 11.04 on all 3 pcs, 

First you need to install openssh-server on the computer that actually has the folder. Then on the other two computersopen the file browser. On the top bar click file > connect to server.

In the box that says "service type" choose ssh

In the "server" box put the other computers ipaddress eg 192.168.1.3

 In the "folder" box put the full path to the folder on the other computer eg /home/john/work

Put the username of the other computer in the "User Name" box

Give the bookmark a name, eg work

Tick the "Add bookmark" box then click connect

It will ask you for a password. This is the password from the other computer.

Choose to remember the password forever.

Then you will be able to access the folder from the sidebar of the file browser with one click.

---

### Post by Mze on 2011-05-24
Check out this how to on OmgUbuntu and see if some of the suggestions meet your needs.

[5 ways to make using multiple computers and devices more efficient with Ubuntu]("http://www.omgubuntu.co.uk/2011/05/5-ways-to-bring-your-desk-to-order-with-ubuntu/")

---

### Post by PsyclonJohn on 2011-06-14
I haven't tried out any solutions yet, I've been pretty busy lately. We aren't all using the same Version of Ubuntu, one has 11.04, one has 10.10 and the other has 10.04. 

I know that I can enter my modem IP to view local host files as a read-only, but I was wondering if there's a way around that to make them modified. There probably isn't, but I just want to make sure. 

Thanks for all your replies so far!

---

