---
title: "Can't connect to OS X SMB share"
date: 2006-02-11
forum: General Help
---

### Post by rbanzai on 2006-02-11
I have an OS X 10.4 machine set up for Windows sharing. I can connect to it with my XP box but I cannot connect to it from my new kubuntu setup. I have searched and seen lots of conflicting information on connecting to SMB including some posts saying "delete X and reinstall Y!" and others saying "No! Reinstall Z and delete J!" and so on and so on.

I looked at SMB setup and everything was dimmed out. I tried the "admin" button but that didn't do anything even the one time it asked for my user password. The File Sharing control panel is similarly dimmed.

I found a post with some hints for getting the SMB panel to light up so I could access it but it still didn't help.

I feel that if I can easily connect to the OS X SMB share with XP then I should be able to do it with Kubuntu but I am lost as to where the problem is.

I'm happy to post any config info anyone needs, but at this point I'm not sure what people would need to see.

If Ubuntu simply can't connect to an OS X Samba share can someone help me figure out how to at least see the Ubuntu box from the Mac and the XP machine? That would be better than no sharing at all.

thank you

---

### Post by jonathan_c on 2006-02-11
Where can't you see the shares in? In konqueror? smb4k? You have the samba libraries installed I assume? If you want to share a directory or two on your Kubuntu machine in KDE, it's as simple as installing the samba libraries, and then right click on a folder in konqueror file manager and click share.

---

### Post by rbanzai on 2006-02-12
Over on the mac support forum they said it will not work without some kind of SMB brain surgery.

I've installed every SMB package I could find to no avail. No changes I make will allow me to see the OS X machine's SMB share from ubuntu. The closest I got was with some kind of network browser tool (can't recall the name) that was able to automatically discover and display the iBook by name but didn't offer a way to mount the shared folder.

The SMB sharing control panel in ubuntu STILL will not activate even when I hit the Administrator button and put in my password. I was able to activate the SMB setup panel but two of the tabs don't even work, and the Local Network Browser panel just generates an error message. There is no 'Share' option when I right click a folder so I can't test the ability for my other machines to at least see the ubuntu box, even if there cannot be 2 way sharing.

I am suprised to see that this is less functionality than even my Gentoo install offered last year. With such little traffic on the ubuntu forums this looks like just another dead-end distro test for me.:( 

I need a linux distro that will support my OS X SMB share that I already access fine from my XP machine. If it will require a herculean effort to get that module to work it is easier to just wipe and try something else. That's probably the greatest strength of linux!:D

---

### Post by Prospero2006 on 2006-02-12
What's the output when you type:

smbclient -L  (IP Address of OS X Machine)

---

### Post by Jason_25 on 2006-02-12
I think there is a bug with browsing osx shares on breezy.  You should be able to directly connect with it through whatever samba client kde has.  If not, smbclient at the command line should.

---

### Post by rbanzai on 2006-02-12
I will have to hook it all back up and see if those command line approaches work. I think it still comes down to needing the standard tools to work though.

---

### Post by Jason_25 on 2006-02-12
smbclient, which is the standard tool for connecting to smb shares, is installed by default.  No need to further confuse things by installing more packages.  Also, like I said before, KDE probably has a built in smb client as well.    I just haven't used it in years.

---

### Post by rbanzai on 2006-02-14
SMB4k was not installed by default on my machine so I went ahead an used adept to install it.

When I activate it I see my OS X machine, and can sometimes get it to pop open and display the user share but I get no further. If it prompts me for authentication I use my OS X username and password just like I do from XP and it fails and tells me access is denied.

I ran that command smbclient command and got this:

roberth@pengo:~$ smbclient -L 192.168.0.4
timeout connecting to 192.168.0.4:445
Password:
session setup failed: NT_STATUS_LOGON_FAILURE


I entered my OS X pass word at the prompt and it immediately produced that logon failure. I know that anywhere I am asked for authentication I am using my OS X username and password.

---

### Post by WelterPelter on 2006-02-26
The version of Samba in the repositories is broken in Tiger. You need to get Samba 3.0.21. Then go to your keychain in Tiger and delete all your old Samba keys so that you get prompted again to enter your password. Then it will work.

---

### Post by ipstone on 2006-06-01
Dear All,

I had the same problem with smb client connection at my work

basically we have a windows network, and several computers that I need to connect to , using smb, in the past when using suse linux in kde, I have no problem just access then with konqueror

however, both in breezy and dapper, I cannot access those anymore
(with the right path, usrname, passwd, it keeps prompting to ask password, usrname without real connection)


it's a pain that I have to access those using mac os x, and then using ubuntu to connect to my os x machine through fish ...

some ideas?

---

