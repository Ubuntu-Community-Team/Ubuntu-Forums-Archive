---
title: "Problem connecting to windows shared network via samba"
date: 2006-03-19
forum: General Help
---

### Post by tezas87 on 2006-03-19
I have recently installed Ubuntu linux and have come across a problem regarding my connecting to another windows pc in my local network.

I have properly installed samba thourgh synaptic and the network works fine whenever i turn on my pc (I can see the windows computer's shared folders in network servers window.

The problem is that once i have entered my password to use synaptic or a disk mounter tool (the default user password), then it becomes impossible to connect to the shared network, since the system keeps asking me for my username and password to connect to the domain, but although i enter everything correctly (or so i think) it keeps asking me for a password over and over...

I have searched the forums for a fair couple of days and I am getting desperate...
I have no intention of switching to kde, and i am not quite sure if such an action will solve the proble...

Any help would be appreciated...

---

### Post by BitTorrentBuddha on 2006-03-19
same problem

---

### Post by mr.p on 2006-03-19
[QUOTE=tezas87]I have recently installed Ubuntu linux and have come across a problem regarding my connecting to another windows pc in my local network.

I have properly installed samba thourgh synaptic and the network works fine whenever i turn on my pc (I can see the windows computer's shared folders in network servers window.

The problem is that once i have entered my password to use synaptic or a disk mounter tool (the default user password), then it becomes impossible to connect to the shared network, since the system keeps asking me for my username and password to connect to the domain, but although i enter everything correctly (or so i think) it keeps asking me for a password over and over...

I have searched the forums for a fair couple of days and I am getting desperate...
I have no intention of switching to kde, and i am not quite sure if such an action will solve the proble...

Any help would be appreciated...[/QUOTE]
Please post a screenshot of what dialog your entering your username/password into. I think I know the problem.

---

### Post by Bradl3yJ on 2006-03-19
In that dialog you need to enter the username and password of a windows account on the computer hosting the files that is authorized

So if i have shared files with the account "brad" and password "password" on my windows box, i would need to use "brad" and "password" to log in using samba on ubuntu. I can remember if you are supposed to put in your workgroup name for the domain or not, try leaving the domain field blank, then try putting your workgroup name in there...

---

### Post by Dragineez on 2006-03-19
Installing kde will have no effect. Not that I'm against kde in any way, but if you were planning to install it to make this problem go away - it won't work.

By any chance is your ubuntu machine now acting as the primary domain controller on your network? Or do you have a Windows machine operating in that role?

---

### Post by tezas87 on 2006-03-19
It's in greek but I think you get the picture ;) 
Though I enter the password, these keep coming up, one after the other....

---

### Post by tezas87 on 2006-03-19
[QUOTE=Dragineez]
By any chance is your ubuntu machine now acting as the primary domain controller on your network? Or do you have a Windows machine operating in that role?[/QUOTE]

I just tried to connect to an allready set up windows pc
Both of them are connected directly to hub/router

---

### Post by tezas87 on 2006-03-19
[QUOTE=Bradl3yJ]In that dialog you need to enter the username and password of a windows account on the computer hosting the files that is authorized

So if i have shared files with the account "brad" and password "password" on my windows box, i would need to use "brad" and "password" to log in using samba on ubuntu. I can remember if you are supposed to put in your workgroup name for the domain or not, try leaving the domain field blank, then try putting your workgroup name in there...[/QUOTE]


Tried every possible combination, but to no avail!!
I reboot and its okay but once I enter my password to run a sytem tool, it goes nuts like this!!

(terribly sorry for the multiple posts...)

---

### Post by mr.p on 2006-03-20
[QUOTE=tezas87]It's in greek but I think you get the picture ;) 
Though I enter the password, these keep coming up, one after the other....[/QUOTE]
Ok is the computer you trying to connect to IP address 10.0.0.1? Or is that the PC your trying to connect from?

---

### Post by tezas87 on 2006-03-20
This (10.0.0.1) is the pc i'm trying to connect from although i get htese kind of messages for both mine and the windows one (10,0,0,2)
By the way, when the network is up and running, i can see both mine and the windows pc in the workgroup they belong to (which of course is not MSHOME).

Additionaly, these connection dialoges ask me to verify access to both _my_ workgroup, and this MSHOME which I have never created...

---

### Post by mr.p on 2006-03-20
Ok when you on the machine 10.0.0.1 and you see that particular login box appear (the one you posted in the screenshot with "10.0.0.1") hit cancel and see what the next box says, it should be the PC your trying to connect to.

---

### Post by shadww on 2006-03-20
hmmm i get a similar problem, and i think it all begin when i tried to share a folder

when i try to enter i get these stuff

[http://img72.imageshack.us/my.php?image=screenshot011wm.gif](http://img72.imageshack.us/my.php?image=screenshot011wm.gif)
i just hit enter an get this free!!!
[http://img95.imageshack.us/my.php?image=screenshot026fo.gif](http://img95.imageshack.us/my.php?image=screenshot026fo.gif)

so iam confused here, did you solve the problem 
any guide link ?

sorry for my fool language

*BTW i can enter my share files by smb://the_computer_network_id_or_ip*

---

### Post by mr.p on 2006-03-20
[QUOTE=shadww]hmmm i get a similar problem, and i think it all begin when i tried to share a folder

when i try to enter i get these stuff

[http://img72.imageshack.us/my.php?image=screenshot011wm.gif](http://img72.imageshack.us/my.php?image=screenshot011wm.gif)
i just hit enter an get this free!!!
[http://img95.imageshack.us/my.php?image=screenshot026fo.gif](http://img95.imageshack.us/my.php?image=screenshot026fo.gif)

so iam confused here, did you solve the problem 
any guide link ?

sorry for my fool language

*BTW i can enter my share files by smb://the_computer_network_id_or_ip*[/QUOTE]
I don't really know how to fix the problem, or even if it is a problem. For some reason it asked for a username/password for the local machine and then for the remote when using Nautilus to access a SMB share so I always press cancel on the first one and then enter my creditenals in the second which actually shows the remote machine's name.

---

### Post by tezas87 on 2006-03-20
[QUOTE=mr.p]I don't really know how to fix the problem, or even if it is a problem. For some reason it asked for a username/password for the local machine and then for the remote when using Nautilus to access a SMB share so I always press cancel on the first one and then enter my creditenals in the second which actually shows the remote machine's name.[/QUOTE]

Well, as I previously posted, It doesn't logon to any IP address...
I cancel the 1st dialog box and enter my credentials in the socond one appearing, and so on...
messages are as follows:
You must login to access "COMPUTERNAME" (domain MSMSHOME)
<I enter the psswd>
You must login to access "username"@"COMPUTERNAME" (domain MSMSHOME)
<enter the passwd nothing again. It just keeps asking me to re enter my psswd, even if I change the workgroup name to "MYWRKGRP" (supposedly my workgroup name), even if I cancel the first dialog and reply to the 2nd, or various combinations of the above...)

It's really starting to get to me...
What use is a computer running linux when I need to reboot it or enter a gazillion passwords every gorram( ;)  ) time I need to access the windows shared network??????

(Please excuse my bad temper, but my patience is running thin...)

---

### Post by Robor on 2006-03-20
Have you added your local Ubuntu login's username and password to the Windows system you're trying to connect to?

I'm very new to Ubuntu & Linux in general and I still get prompted for credentials when I attempt to access my remote Fedora Core 4 'server' and WinXP Pro desktop.  However, I just escape or cancel the credential prompts and I'm still able to access the remote shares.

I do have my Ubuntu username/password setup on the WinXP Pro desktop and the Fedora Core 4 box though.

---

### Post by Zaskoda on 2006-03-20
I've been dealing with this same problem.. Ubuntu keeps prompting me for my username and password on samba shares. If I enter it correctly once, than cancel the next time - it WILL show me the share and allow me to access it. However, after a certain amount of time, it will ask me for my username and password again - even if I'm not actively browsing the share (iow, the window is open, but I haven't been using it). Checking the option to save my password does not help.

I'm also having read permission issues.

I've just been crossing my fingers for a fix in Breezy.

---

### Post by tezas87 on 2006-03-20
Guys, problem solved... sort of!
I installed komba2 via synaptic and I manage everything through that... No login problems no nothing, and it mounts the desired shared folders to my system...

I sincerely hoped that gnome would spare me the grief this time...

---

### Post by Robor on 2006-03-20
tezas87:  

Glad to hear you got it working and thanks for the follow-up with your solution!  I'll try it later on tonight if I have the time.

---

### Post by Zimmer on 2006-03-20
For Samba / windows sharing info..
[http://ubuntuforums.org/showthread.php?t=108950](http://ubuntuforums.org/showthread.php?t=108950)  post #5
and
[http://ubuntuforums.org/showthread.php?t=133100](http://ubuntuforums.org/showthread.php?t=133100)   post#4

May help you with Samba User/share problems.
Regards
Zimmer

---

### Post by tezas87 on 2006-03-20
Maybe we didn't find quite what we were looking for but thanks everyone!!!
It's really nice seeing that people are willing to help in these forums
Again, thank you all for your eagerness to help:KS

---

