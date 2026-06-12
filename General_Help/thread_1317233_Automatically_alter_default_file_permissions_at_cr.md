---
title: "Automatically alter default file permissions at creation"
date: 2009-11-06
forum: General Help
---

### Post by Mururmir on 2009-11-06
Hi,

First of all I want to thank you for allowing me to be part of the Ubuntu community. I hope I'm able to provide support to people who actually are less familiar with Ubuntu than I am, as well as receiving help for my issues. Since this is my first post and I'm from Austria I want to apologize for bad English ;)

But now to my issue. At my place I've set up an Ubuntu Server (9.10) and nearly everything works as i expected it. I've got a samba server up and running which enables my flat-share colleagues to access  a common drive.
A download client places the downloaded files there. Is there any possibility for me forcing the client to alter the default file permission when he creates the files in order to give write rights to the groups the client belongs? It's terrible annoying to accomplish this by hand with chmod so that the files can be deleted by everybody in the group.

I would be very glad about any help.

Thanks in advance

---

### Post by alphaniner on 2009-11-06
umask controls the permissions of all created files and folders.  The umask is defined in the file /etc/profile.  The default is 0022.  Changing it to 0002 will accomplish what you want to do.  The change is universal and will affect *all* files and folders created by *all* users.  I don't know if it is possible to set it on a user-by-user basis.

---

### Post by Mururmir on 2009-11-10
Hi!
Thanks for the help I'll use it until I find something more suitable.

---

### Post by Mururmir on 2009-11-14
Hi all!

I tried the solution above but the result was somehow confusing.
The first strange thing was the fact that my default setting of umask in /etc/profile was 022. Since I didn't know that the umask exists I expected the value to be 0022 such as postet before.
I alterd the value anyway but there's no change in the permissions of the newly created files or directories. I first set it to 0002 and afterwards to 002 which seemed logical to me since my default value missed the first zero anyway. I also tried to reboot in oder to make the changes take aktion (I sorry for this try but I'm afraid I'm damaged by windows X-/ )
Any guesses what I've done?

Thanks in advance

---

### Post by bluefrog on 2009-11-14
you might want to look at ACL default mask;

package: acl

setfacl -m d:g:my-user-group:w TestDir

all new files in TestDir will be writable by the group my-user-group

---

### Post by Mururmir on 2009-11-14
Heyho,

I've used setfacl to achiev what I wanted. Right now it works like i should. Thanks for the help.
Just a hint for somebody who has simmilar problems, I had to enable the acls in a  certain file.
A description can be found here: [http://www.linuxquestions.org/questions/mandriva-30/setfacl-test-operation-not-supported-266804/](http://www.linuxquestions.org/questions/mandriva-30/setfacl-test-operation-not-supported-266804/)

Thanks for the help

---

