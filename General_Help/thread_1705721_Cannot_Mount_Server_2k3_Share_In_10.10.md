---
title: "Cannot Mount Server 2k3 Share In 10.10"
date: 2011-03-12
forum: General Help
---

### Post by Hugh971 on 2011-03-12
Hi,

I installed Ubuntu on my PC the other day (I've used it before but have strayed form Linux for a while). I am ashamed to say I'm struggling to mount a network share (simple as it should be!).

The share is on a Windows Server 2003 box. I'm not running a domain so the credentials I'm using are local to the server. The command I'm putting in is this.

```
sudo smbmount //my.internal.ip/media /home/hugh/media -o username=myuser,password=mypassword
```

When doing this it throws up a generic error saying.

```
mount error(13): Permission denied
```

I can map a share to a Windows XP Home computer on my network with no issue and I can browse to the Server 2K3 share by going through Places > Connect to server.

I've literally spent hours doing this and am quite embarrassed that I'm having to ask it here!

I'm sure it's something simple anyway. Any ideas/suggestions?


Thanks

Hugh

---

### Post by Hugh971 on 2011-03-13
I've been playing around with it again today and have created a new smb.conf file and checked all the workgroup settings are set to the same as the server but am still getting the same error.

I'm pretty sure it's permissions based. Any other commands you can suggest for me to throw in and see if I can get past this?

I'm pretty sure it's possible as the built in wizard can browse to them.

---

### Post by securitymeddler on 2011-03-13
Maybe a silly question, but does this work from the GUI? 

How about if you just goto \\servernameorip can you see all the shared items? That is to say, don't drill to the specifc share itself. Just see if you can see the shared items root folder?

Can you also verify both the share and NTFS permission on the shared folder? Maybe post them here?

---

### Post by Hugh971 on 2011-03-13
Thanks for the response,

I can browse to the share using the connect to server option within Nautilus. 

The share permissions are set up so everyone has full control and the NTFS permissions are set up so the user I'm trying to map as has full control.

Running ```
smbclient -L myip
``` gives me a list of all the shares on the server.

---

### Post by Hugh971 on 2011-03-16
If anyone's interested, I fixed this by removing a couple of rogue characters in my password that it appears samba doesn't like. A complete stab in the dark but it worked!

---

