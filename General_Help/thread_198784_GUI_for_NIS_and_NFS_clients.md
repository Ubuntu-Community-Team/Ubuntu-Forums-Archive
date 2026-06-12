---
title: "GUI for NIS and NFS clients"
date: 2006-06-17
forum: General Help
---

### Post by Tortanick on 2006-06-17
I was wandering if there is a simple GUI ofr NIS and NFS, much like what SUSE has in YaST. It only has to work as a client though.

---

### Post by MemoryDump on 2007-01-02
I know this is an old post.. but I was just wondering about this as well.. is there a Gui for using NFS?
I was using Webmin in the past and found it extremly useful. Right now I'm using a shell to configure my mounts/etc but I would rather a nice little gui to make my life a little easier :P

thanks

---

### Post by fragos on 2007-01-02
System-> Administration-> Shared Folders.  If you don't have the necessary pieces  it will offer to install them.  Hopefully the configuration you do here will help you work out the rest.

---

### Post by trhermes on 2007-01-08
The first time I stared the "Shared Folders" utility (System->Administration->Shared Folders) I failed to check NFS to install.  Since then, I believe that I installed NFS through apt-get; but  when I use "Shared Folders" with the intention to add an NFS share, the option doesn't appear.  Any suggestions on how to have the option display within the utility?

---

### Post by fragos on 2007-01-08
I experimented a bit with having NFS shares but not Windows.  I get the same result with no option to install SMB.  A frequent solution for getting an application to return to installed state is to delete it's configuration file or directory from your home directory.  I poked around and can't find anything that looks like a configuration file for shared folders.  Perhaps its somewhere in /etc.  This looks to me like a bug that would be easy to fix.  Why don't you file it?

---

