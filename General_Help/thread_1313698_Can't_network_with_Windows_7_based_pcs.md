---
title: "Can't network with Windows 7 based pcs"
date: 2009-11-03
forum: General Help
---

### Post by JigglyWiggly_ on 2009-11-03
So my server runs server 2k8r2, and my desktop runs Windows 7 x64. Then my spare pc runs Vista. I can connect to vista fine, but I can't connect to server 2k8r2 or Windows 7. I just go to places > network, and click the Windows server 2k8r2 pc, and it prompts, I type in the right password, but I just get 
Failed to retrieve server list from server.

My other laptop running ubuntu 9.04 runs fine, I am upgrading it though. I am on a netbook right now, asus 1005ha (ubuntu 9.10) any suggestions? I installed samba4 from the sources as well, didn't do anything.


EDIT: It has to do with Ubuntu 9.10, my other laptop has 9.04 and it networked fine, now with ubuntu 9.10, I can't do it!.

---

### Post by JigglyWiggly_ on 2009-11-04
bump

---

### Post by radu.ro on 2009-11-04
Unfortunately this is not Ubuntu's fault. I am really curious how have you managed to browse Vista and 7 shared folders from Ubuntu 9.04 (as I am running the same OS here) because that's impossible using only Nautilus.

To properly mount a Windows share (whether it's Vista or 7) you have to manually execute the following command in the terminal:
```
sudo mount -t cifs -o username=windowsUserName,password=windowsPassword //pcRunningVistaOr7/shareName theFolderWhereYouWantTheMount
```

Have fun!

---

### Post by JigglyWiggly_ on 2009-11-04
I just went to> places > network > windows network > visualwin > clicked the server 2k8r2 pc.

However I tried that here is my syntax
sudo mount -t cifs -o username=administrator,password=Iamnottelling //3DSLICE-HOST/ docs

It just said: mount error: could not resolve address for 3DSLICe-HOST: Name or serevice not known
No ip address specified and hostname not found

Then I tried
sudo mount -t cifs -o username=administrator,password=Iamnotteling \\192.168.1.118\ docs

Then it gives me mount error: can not change directory into mount target docs

---

### Post by ST3ALTHPSYCH0 on 2009-11-05
I had full read/write access both directions between Win7 x64 and Jaunty x86.... Karmic seems to hate the concept of home network. I've just crossed 3 posts about it before getting here.

---

### Post by JigglyWiggly_ on 2009-11-05
Well at least I know I'm not alone. This is a really big bug if I'm honest. It is really inconvenient this.

---

### Post by kixome on 2009-11-05
Its not just karmic, for some reason server 08, vista and 7, all rely on ipv6 for some services, don't know why it worked for vista, but i do know they use ipv6 for some of the file sharing services as i had a problem with my router being only ip v4 and sharing with win 7 without enableing certian advanced permissions in 7,

---

### Post by radu.ro on 2009-11-05
You cannot mount all the shared folders at once. The command I've shown you specifically tells you to mount one shared folder to one folder on your Ubuntu machine. Try it again.

Good luck!

---

### Post by ST3ALTHPSYCH0 on 2009-11-05
@ OP
I don't know if this helps you at all, but I now have full access to my Karmic shares from my Win 7 box. All it required was installing Samba 4. I noticed that all users already have a password, ut it differs from the log on PW, and can be set to nothing.

---

### Post by MofoVideo on 2009-11-05
Hi I have been having the same problem...And a temp work around!

I have a folder shared on Win 7 called Cake.

When I try to access it through ubuntu 9.10 I got the same error messages as you, but if I go in through Nautilus and type in 

smb://toki/cake/silk

I have access to the silk folder and everything inside it. I can open documents and write documents. 

As soon as I try to go in the the cake folder None of the folders are listed and I get the error "The folder contents could not be displayed. 

Sorry, Could not display all the contents of cake on toki: invalid argument".

Try going in through natilus and let me know what you get.


update again. It seems I have it working now.....I shared my hold windows drive to everyone and I can access it in ubuntu.

I have full sharing access from Ubuntu 9.10 Fresh installed today on an Acer aspre one to a win 7 share folder. Only when I use smb://CompName/SharedFolder

---

