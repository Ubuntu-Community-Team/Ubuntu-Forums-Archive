---
title: "How do i share the files?"
date: 2011-02-27
forum: General Help
---

### Post by mastablasta on 2011-02-27
I just installed Kubuntu 10.10. Everything seems to work nice. But i can't share the files or printer. Printer is on WinXP computer and worked just fine in Ubuntu.

How do i share the files? In Dolphin i tried to configure it for sharing but nothing comes up as i click it. at first i thought samba is not installed but it is. also I thought that issue is WinXP but it's not because i can't access any files from Kubuntu as well. Basically i can't mark the folder to be shared. I don't know how to do it. i even tried with smb4k or something like thta but that programmes also doesn't see any folders on local system. 

my brother even tried to create a share folder thoguh CLI but he wasn't succesfull cause he uses Ubuntu. for some reason UBuntu and windows can see that folder but they can't access it.

Edit: I am attaching a picture of windows that opens iafter i click to configure the file sharing. when i enter the password nothing happens shouldn't this command be related to samba?

---

### Post by mastablasta on 2011-02-28
page 9 and no reply. i can't believe this. i am going to bump this anyway.
 
i can't believe no one knows an answer to such a basic question. or how to enable these nowadays essential function in OS. How do i share files with other systems withouth turning my computer into a server maschine.

---

### Post by mastablasta on 2011-02-28
I solved this one. Found a solution here: [http://www.ghacks.net/2010/02/18/easy-folder-sharing-in-kde-4-4/](http://www.ghacks.net/2010/02/18/easy-folder-sharing-in-kde-4-4/)

You need:

Samba
Samba Client
kdenetwork-filesharing

Problem is that kdenetwork-filesharing applicaiton is not installed. And it doesn't say you need to install it or anything. this is really stupid.

Anyway solution is found in that link in case someone else is also stuck.

---

