---
title: "Trying to share."
date: 2012-03-10
forum: General Help
---

### Post by uRock on 2012-03-10
I have a partition I have a bunch of movies in an NTFS partition which I want to share with other systems on my network for the purpose of letting my kid watch them in her room as well as having the ability to watch them on a system connected to my entertainment system. I can't seem to make them visible to other systems. The folder shows on the network, but it is not mountable. Is this due to the partition being NTFS and ubuntu not being capable of applying permissions?

---

### Post by Morbius1 on 2012-03-10
There's not enough information in your post to answer the question. For example if I assume:

* You shared the folder using Nautilus.
* The ntfs partition is not being automounted at boot but mounted when you need it through Nautilus.

Then it will mount with access only to you and no one else. You may have set up the share to allow guests to access it but Samba cannot override Linux permissions. There is a way out of this problem and that's to force all remote users to look like you:

Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add the following line to the [global] section - right under the workgroup line:
```
force user = what-ever-your-user-name-is
```Save smb.conf and then restart samba:
> sudo service smbd restartIf you used Classic samba it would be better to put that line in the share definition itself. If you are automounting the NTFS partition then a simple change to the options should fix it assuming you are using Samba. If you are using NFS then this will do zip. 

If the above does nothing for you please explain how you created the share and how you are mounting the NTFS partition.

---

### Post by uRock on 2012-03-10
I am mounting, then right clicking and sharing to all. I guess I will have to format it to EXT4, so that I can give permissions for the files.

---

### Post by Morbius1 on 2012-03-11
Still haven't answered the question but each time you post you leave another clue. If you are contemplating reformatting to ext4 it suggests that it is in fact an NTFS partition. Then rather than reformat you could use "force user" in smb.conf as I suggested above.

"force user" will convert the remote guest to you once it passes through Samba's limitations. You set up the share to allow guest access without write access. When the remote user tries to access the share she will be converted to you but Samba will prevent her from writing to the share.

---

### Post by uRock on 2012-03-11
> **Morbius1 said:**
> Still haven't answered the question but each time you post you leave another clue.

I do not see the question you are wanting answered.

I just ran the commands you offered. They got it working. Thanks for the help. ;)

---

