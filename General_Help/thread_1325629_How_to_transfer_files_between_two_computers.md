---
title: "How to transfer files between two computers?"
date: 2009-11-13
forum: General Help
---

### Post by thermobee on 2009-11-13
Hey guys, 

I need to transfer some files between my netbook and PC. They are both running 9.10, I just never had to do this and I have no idea how. Please throw some suggestion at me so I can make this work. Thanks

---

### Post by hwttdz on 2009-11-13
From the computer hosting the files call it "earth", type "ifconfig -a|grep "inet addr"" and write down that number, it's the address of "earth".  From the other computer, "mars", 

scp useronearth@earthaddress:/path/to/file /path/to/save/file/on/mars

---

### Post by fragos on 2009-11-13
I use NFS between my Desktop and Laptop as my server. Both being on the same LAN. My desktop direct connects to a wireless router and the laptop connection is WiFi. On the server there must be an /etc/exports with the following. Replace the fields in {} with your information. In my example I'm giving access to the entire home folder tree. There can be multiple entries giving more clients permission.

/home/{Laptop user} {Desktop hostname}.local(rw)

This allows the Desktop to access the home folder of the laptop. Prior to Ubuntu 8.04 you need to run "sudo exportfs -rv" for the system to read /etc/exports. New versions do this for you at boot.

On the Desktop create a folder to mount to. In my case I placed that folder in my home folder.

On the Desktop side I run

sudo mount {Laptop hostname}.local:/home/{Laptop user} /home/{Desktop user}/{folder to mount to}

To un-mount I run

sudo umount {Laptop hostname}.local:/home/{Laptop user} /home/{Desktop user}/{folder to mount to}

You can extrapolate what to do from this working example. I chose not to use fstab to mount and wrote a couple of bash scripts that supply the parameters to the mount and umount commands.

---

### Post by hwttdz on 2009-11-13
I'm also fond of sshfs, which works in much the same way as ssh, and mounts the drive locally.

---

### Post by audiomick on 2009-11-13
Bear in mind that it is only ok to open up your complete home folder if you are really sure that no one (other users in the network, the kids next door who have managed to break in through your fire wall...)  can get in that you don't want to. If there is any doubt about this, just make one folder accessible, in which you only put stuff that you want to transfer

---

### Post by thermobee on 2009-11-13
Ok this sound so complicated, its not even funny.

---

### Post by cgb on 2009-11-13
and a gui way of setting this up would be to right click on a folder you would like to share files from, select "sharing options", then select "share this folder".  Now on the computer you would like to access the files from you can goto Places\Network on the top panel and you should see your other computer listed in this window.  Double click on the computer and you should now see the shared folder as well.

---

### Post by thermobee on 2009-11-13
Ok I think im going to look for alternatives, like USB or DVDs

---

### Post by thermobee on 2009-11-13
> **cgb said:**
> and a gui way of setting this up would be to right click on a folder you would like to share files from, select "sharing options", then select "share this folder".  Now on the computer you would like to access the files from you can goto Places\Network on the top panel and you should see your other computer listed in this window.  Double click on the computer and you should now see the shared folder as well.

Thats it?

---

### Post by cgb on 2009-11-13
yes, for the most part that is all you need to do in order to connect to another computers shared folder.  Let me know if you have any problems.

---

### Post by thermobee on 2009-11-13
> **cgb said:**
> yes, for the most part that is all you need to do in order to connect to another computers shared folder.  Let me know if you have any problems.

Will do, thanks dude.

---

