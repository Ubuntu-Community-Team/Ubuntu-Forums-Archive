---
title: "FTP server with User rights in config file?"
date: 2011-09-08
forum: General Help
---

### Post by Cryonicblue on 2011-09-08
Hi.

I'm trying to find FTP software that allows you to set user privileges to upload/download/list and stuff inside a config file or similar solution?

Why? Well I have already used user and group permissions to set upp varios access to the folders and now I want to add additional user specific rights to the same maps.

Since I only found a way to set 2 different rights to maps/files using user and group permissions I'm out of room for more specific rights.

Take slimftpd for win for example, it's THIS easy to set up rights for the FTP server:

<User "bob">
    Password "abc123"
    Mount / C:\ftproot
    Allow / Read List
    Mount /files D:\files
    Allow / Read List
    Allow /upload Write
#</User>

Is there anything similar at all for Linux? Spent 2 hours searching without result.

---

### Post by rcayea on 2011-09-08
I'm not sure if there is a Ubuntu installation available but have you looked at FTP Rush. I think that might do what you want. Here is the link: [http://www.wftpserver.com/ftprush.htm](http://www.wftpserver.com/ftprush.htm).

---

### Post by Cryonicblue on 2011-09-14
Hi Rcayea, Thanks but I'm looking for an FTP Server, not a client.

---

### Post by Cryonicblue on 2011-09-20
*BUMP*

(Sorry if bumping is inappropriate but I'm still stuck)

---

