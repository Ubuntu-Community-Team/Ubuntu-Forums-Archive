---
title: "Sharing Folders and Files with Windows 7"
date: 2012-01-31
forum: General Help
---

### Post by ChemMeister on 2012-01-31
I have installed Samba and shared one folder. However I cant seem to see the folder on my Windows 7 machine. Any ideas? Thanks

---

### Post by maverickaddicted on 2012-02-01
Is your machine in the same workgroup as your Windows 7 machine is? You can edit /etc/samba/smb.conf file and can set the workgroup option there.
You can also use this tool for sharing file, it is very easy to use.

```
sudo apt-get install system-config-samba
```

---

### Post by raja.genupula on 2012-02-01
step by step tutorials

[http://www.liberiangeek.net/2011/04/share-files-folders-ubuntu-11-04-natty-narwhal/](http://www.liberiangeek.net/2011/04/share-files-folders-ubuntu-11-04-natty-narwhal/)

[http://www.youtube.com/watch?v=Ad17kma8rNM](http://www.youtube.com/watch?v=Ad17kma8rNM)

hope they help you

---

### Post by scarleo on 2012-02-01
And also some help from Ubuntu: [https://help.ubuntu.com/11.04/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/11.04/serverguide/C/samba-fileserver.html)

---

### Post by Morbius1 on 2012-02-01
> I have installed Samba and shared one folder.Using what method? There are 2 ways to create a Samba share and you really should use one method or the other. If you post the output of these commands the folks here can be help you better:
```
testparm -s
``````
net usershare info --long
```> However I cant seem to see the folder on my Windows 7 machine.I'm assuming you mean you can't see the Ubuntu share from the Win7 machine. Ubuntu has both a Samba client and a Samba server. Can the client see the server on the same machine? To find out post the output of this command:
```
smbtree
```

---

### Post by linux6994 on 2012-02-02
I have a Win7 & XP to Ubuntu problem as well. Via nautilus, and other linux machines real and virtual I can see myself however from anything Win7 no. Ubuntu can access Win7 shares just fine, just not the other way around. 

Linux VM or real --> Ubuntu OK
Ubuntu --> Win7 OK
XP virtual --> Ubuntu not OK

Any idea?

---

