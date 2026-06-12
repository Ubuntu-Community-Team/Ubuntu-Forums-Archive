---
title: "Folder Sharing?"
date: 2009-09-17
forum: General Help
---

### Post by Mercenary(FH) on 2009-09-17
So I want to share a folder on our network (which is called blah) (not really but for all sense and purposes lets say it is)

I made a folder. put stuff in it. then right clicked went to sharing etc...


So......according to this ANYONE connected on this network (on ubuntu) should be able to see it?

Or is there something they have to do to see it? where do they go to see it?
It's mainly for my roomies, I installed ubuntu on all of their machines. but I share alot of files with them.

BTW with this file sharing folder can they copy stuff FROM that folder to their computer?

But what else would I need to do? I saw something about installing samba and changing the conf. file and stuff.
but one part said "Change workgroup to your home network?"
does that mean literally call it "home" or call it "blah" which is the name of my router network?

sorry for the nub question. just trying to learn :)

---

### Post by sahabcse on 2009-09-17
Hi

Simply do the below steps

open the terminal and type "sudo nautilus" then browser your folder and right click select sharing options.

---

### Post by StuartN on 2009-09-17
> **Mercenary(FH) said:**
> So......according to this ANYONE connected on this network (on ubuntu) should be able to see it?

Ubuntu or any system, anyone on the network can see your share, i.e. they can see that there is a share called blah. If you set no security then anyone can access it, otherwise they need to log in. The Linux permissions (rwx) determine what they can do with it. If you set a folder to no-execute (eg: "chmod o-x blah") then they (others, not owner or group) can't browse the folder. If you set a file to read-only ("chmod -w blah/blah.odt") it can't be changed and if you set it to unreadable ("chmod -r blah/blah.odt") then it can't be read, but they can still see the filename.

> **Mercenary(FH) said:**
> BTW with this file sharing folder can they copy stuff FROM that folder to their computer?

Of course, if they have read access then they can do any read operation including copying.

---

### Post by Mercenary(FH) on 2009-09-17
Alrighty thx a ton. where will the shared folder "show up" for them though?
just on their desktop. or do they have to do some special command for it to show up?

---

### Post by StuartN on 2009-09-17
> **Mercenary(FH) said:**
> Alrighty thx a ton. where will the shared folder "show up" for them though?
just on their desktop. or do they have to do some special command for it to show up?

They have to choose to connect. Having done so, they could add a bookmark to Nautilus or create a desktop link to reconnect.

One way to connect is to browse the network. From the Places menu select Network and then open the Windows Network (it is a Samba share, so it is called Windows) and find the workgroup your computer belongs to. If nothing has been shared on your computer then it will not show up, nor will your workgroup. You can bookmark when connecting.

A more direct method is to connect to your computer under Places, Connect to Server. The Server is the same as the name appearing on the prompt in Terminal. The Service type is Windows share, the Share is the name of your share and the Folder is blank unless you want a subfolder in the Share. The User name should be a limited account on your computer, such as Guest (password Guest) created specifically for sharing.

Beware that anyone on the network can see your share, and then try logging in, FTP or any other service your computer might be running, so switch off unnecesaary services and use a secure password.

---

