---
title: "Samba share permissions issue - says I can't copy files but copies them anyway"
date: 2011-04-18
forum: General Help
---

### Post by Mr Bean on 2011-04-18
I have a weird issue concerning my (Synology) NAS box 

I have the share mounted via fstab, which works fine. But whenever I try to paste a folder full of files to the NAS it will say "Permission denied" do you want to skip, cancel etc.

Well if I press skip, it only skips the first file in the folder, then proceeds to copy all the other files normally. If I then try to paste the folder a second time it will ask if I want to merge, etc. I click merge and it copies across the first file. Giving me the complete copy that I actually wanted.

So basically, it works, but it is forcing me to paste everything twice, to make sure I get all the files. Why?

On the NAS box, I have the share configured to give full access to everyone. This is how I have mounted it:

//192.168.1.200/media    /mnt/raid    cifs    guest,_netdev    0    0

I have also tried mounting it with credentials, and even though I gave the login details for the "owner" of the files, I still got the same problem. The command I used was:

//192.168.1.200/media /mnt/raid cifs exec,credentials=/etc/cifspw 0 0

and other variations on that theme.

It didn't always do this, and I can't figure out what I have changed that would make this happen. If it was really a permissions issue, it shouldn't let me copy files at all, right? Can anybody help?

If you need any additional info, don't hesitate to ask.

---

### Post by Mr Bean on 2011-04-21
This is a real problem for me. Please can anyone help?

---

