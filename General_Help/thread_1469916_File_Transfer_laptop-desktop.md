---
title: "File Transfer laptop-desktop"
date: 2010-05-02
forum: General Help
---

### Post by sonet1c on 2010-05-02
Hi guys,
I have a laptop and a desktop both running lucid, and a router ( the laptop uses wifi and the desktop lan) so i have some files that i want to share between them - how do i do this?
Thanks.

---

### Post by spiky001 on 2010-05-02
I would start with installing ssh server it's in the repos

---

### Post by sonet1c on 2010-05-02
in windows you just make homegroup and the pcs are connected :|

---

### Post by parm289 on 2010-05-02
You should just be able to go to Places -> Network and navigate to the other computer from there.  It will take a minute to load.

---

### Post by sonet1c on 2010-05-02
in Places->Network there is just Windows Network ,which is empty

---

### Post by spiky001 on 2010-05-02
Thats looking for a WINDOWS share I use _SSHopen server_ get it from synaptic manager download it on desktop machine

---

### Post by sonet1c on 2010-05-02
thanks this works , but pretty slow 2.5MB/s :( 50 GB info

---

### Post by spiky001 on 2010-05-02
are you doing it from terminal?

---

### Post by Morbius1 on 2010-05-02
Open Nautilus ( your Home Folder )
Right click on /home/your_username/Public [COLOR=Blue]( just an example )[/COLOR]
Select "Sharing Options"
Select all three boxes
Select "Create Share"

It will ask you if you want it to modify permissions - you do.

You've just created a guest share using samba and Nautilus-share.

See if the other machine can access your share.

---

### Post by sonet1c on 2010-05-02
now it finds in Windows Share Workgroup and when i try to open it says "Unable to mount location.Failed to retrieve share list"

---

### Post by spiky001 on 2010-05-02
Have you set the windows to share? and check the firewall on windows

---

### Post by sonet1c on 2010-05-02
i have no windows..

---

### Post by Morbius1 on 2010-05-02
On the machine that does not have the share:

Open **Terminal**
Type **nautilus smb://192.168.0.100**

*[COLOR=Blue] replacing 192.168.0.100 with the ip address of the machine that has the share.[/COLOR]*

Can you access the "Public" share?

---

### Post by spiky001 on 2010-05-02
You said that you had got it to transfer data, The network share is for windows

---

### Post by sonet1c on 2010-05-02
everything works now, both machines are visible in Places->Network along with some Windows Network

---

### Post by spiky001 on 2010-05-02
You could take a look at Filezilla it's in the repos as well I have used that with ssh

---

