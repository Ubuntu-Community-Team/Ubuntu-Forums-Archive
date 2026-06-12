---
title: "Samba share v's UNC pathname"
date: 2006-05-30
forum: General Help
---

### Post by jethro10 on 2006-05-30
Hi
On windows I can basically type :-
cd \\server\sharename
but i'm stuck with Ubuntu from the command line.I can get to my share via nautilus but not command line.
When I right click my share, i see its got SMB infront of it so I tried this, at least other threads seems to imply what I do is this :-

cd smb://server/sharename
but I get "No such file or directory"

am I close ?

Jeff

---

### Post by sinaen on 2006-05-30
[QUOTE=jethro10]Hi
On windows I can basically type :-
cd \\server\sharename
but i'm stuck with Ubuntu from the command line.I can get to my share via nautilus but not command line.
When I right click my share, i see its got SMB infront of it so I tried this, at least other threads seems to imply what I do is this :-

cd smb://server/sharename
but I get "No such file or directory"

am I close ?

Jeff[/QUOTE]

Im not shure you can do that from the command-line in linux. 

if you do so you got to have the shares setup like an NFS (network file system - share) instead and put into your /etc/fstab. 
if you look up NFS and how to set up that it should work. 
but you still could try testing to setup SAMBA it in your /etc/fstab - file (its the file that holds all local/nonlocal mounted or avalible to mount filesystems :) 
And i dont know if you can set SAMBA up to do like you ask. i think you need to mount it somewhere like an nfs-mount or try to put in your //server/ in your /etc/hosts in the format that stands there. the hosts works like a dns but for ip's and it could be to the favourite ftp-sites as well as the computers in your network :D 
and i dont think the shell works that way with linux. :)
you should use ssh instead. if its a linux computer you run your samba-shares on its much easier

BTW
Why do you go to your samba shares in the command line in windows? its useless if you ask me (i dont use windows anymore but that much i know)


or you might test cd smb:/server/share too :) that might work but i think you thougt of that already :D

EDIT!:
Hello. after a little reading here. and so it seems like you can settup your samba share to mount on your local computer. if you want it to :) and it wasnt so hard as it seemed
i dont remember all the steps but if you install smbfs -package and then read the manual you should get it working. or if you just check up smbfs here on the forum you should find the thread i found about it :)

---

### Post by jethro10 on 2006-05-30
[QUOTE=sinaen]Im not shure you can do that from the command-line in linux. 

if you do so you got to have the shares setup like an NFS (network file system - share) instead and put into your /etc/fstab. 
if you look up NFS and how to set up that it should work. 
but you still could try testing to setup SAMBA it in your /etc/fstab - file (its the file that holds all local/nonlocal mounted or avalible to mount filesystems :) 
And i dont know if you can set SAMBA up to do like you ask. i think you need to mount it somewhere like an nfs-mount or try to put in your //server/ in your /etc/hosts in the format that stands there. the hosts works like a dns but for ip's and it could be to the favourite ftp-sites as well as the computers in your network :D 
and i dont think the shell works that way with linux. :)
you should use ssh instead. if its a linux computer you run your samba-shares on its much easier

BTW
Why do you go to your samba shares in the command line in windows? its useless if you ask me (i dont use windows anymore but that much i know)


or you might test cd smb:/server/share too :) that might work but i think you thougt of that already :D[/QUOTE]

I just wanted to setup a simple script for my wife to click on to offer a rudimentary backup solution.

J

---

