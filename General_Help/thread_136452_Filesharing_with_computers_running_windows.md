---
title: "Filesharing with computers running windows"
date: 2006-02-26
forum: General Help
---

### Post by anubix on 2006-02-26
OK,
so i got stuf working, did automatix, etc etc etc

whenever i try to access my shared folder in ubuntu from say... windows, it asks for a user/pass and nothing will work (not even my ubuntu login)

whenever i try to access a shared folder on a windows computer on my network,  linneighborhood wont mount it, and i'm willing to bet it is to due with samba.

so how do i make samba communicate with windows?
and side issue, what is "nautulis"??? could it have something to do with my issue?

i'm trying to make my nix laptop share files as seamlessly as possible
any insight is greatly appreciated
thx
pz

---

### Post by anubix on 2006-02-26
c'mon, someone has to have SOME insight!

---

### Post by schatz on 2006-02-26
have a look at the /etc/samba/smb.conf

check for something like:
# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/ServerType.html in the samba-doc
# package for details.
# security = user  
security = share

and change the security level. This makes it more insecure, but should solve the password problem, at least for some testing.

---

### Post by huckem on 2006-02-26
Anubix---I have been having a TON of problems even getting my Windoze machineto SEE my Ubuntu box...  Automatix helped you?  What did you do to get the server so its visible to your windows machine?

---

### Post by bosonflux on 2006-02-26
Here are some things that worked for me.

1. I found samba to work better using static ip addresses, so change to that if you can.

2. Add  your computer names and ip addresses to your /etc/hosts file on Ubuntu and to windows/system32/drivers/etc/hosts on your Windows box. This should look something like:    192.168.1.25     computer name  .

3. Edit the /etc/samba/smb.conf file under [global] settings to have these entries.

workgroup = <your ms workgroup name>
netbios name = <your ubuntu computer name>
security = share
hosts allow = <windows ip address>  127.0.0.1
(or hosts allow = all for testing)
encrypt passwords = true
name resolve order = lmhosts host hosts wins bcast 

4. Save and restart samba or reboot.

5. Then you need to add yourself as a samba user. In a terminal:
    Type smbpasswd -a <your username>
    Things are simpler if you use the same username and pw as windows.

6. You can add some shares by going to system/administration/shared folders.

7. I assume you have file sharing enabled on windows and something shared.

8. In a terminal: type#  smbclient -L computername -U username . It should list your shares.

9. Make sure any firewalls you are using are not blocking tcp,udp,or icmp from 
either end. Best to disable them for trouble shooting.

10. If all else fails go to /usr/share/doc/samba/ and go through the diagnosis.html test procedures.

---

### Post by huckem on 2006-02-26
[QUOTE=bosonflux]Here are some things that worked for me.

1. I found samba to work better using static ip addresses, so change to that if you can.

2. Add  your computer names and ip addresses to your /etc/hosts file on Ubuntu and to windows/system32/drivers/etc/hosts on your Windows box. This should look something like:    192.168.1.25     computer name  .

3. Edit the /etc/samba/smb.conf file under [global] settings to have these entries.

workgroup = <your ms workgroup name>
netbios name = <your ubuntu computer name>
security = share
hosts allow = <windows ip address>  127.0.0.1
(or hosts allow = all for testing)
encrypt passwords = true
name resolve order = lmhosts host hosts wins bcast 

4. Save and restart samba or reboot.

5. Then you need to add yourself as a samba user. In a terminal:
    Type smbpasswd -a <your username>
    Things are simpler if you use the same username and pw as windows.

6. You can add some shares by going to system/administration/shared folders.

7. I assume you have file sharing enabled on windows and something shared.

8. In a terminal: type#  smbclient -L computername -U username . It should list your shares.

9. Make sure any firewalls you are using are not blocking tcp,udp,or icmp from 
either end. Best to disable them for trouble shooting.

10. If all else fails go to /usr/share/doc/samba/ and go through the diagnosis.html test procedures.[/QUOTE]

Thanks for the great reply!  I will go through these steps when I get out of work

---

