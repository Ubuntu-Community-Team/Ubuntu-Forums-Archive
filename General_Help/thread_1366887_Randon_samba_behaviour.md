---
title: "Randon samba behaviour"
date: 2009-12-28
forum: General Help
---

### Post by stanger192 on 2009-12-28
Hey all
Ive been experiencing some strange behaviour from ubuntu 9.10 with all the latest updates installed.

I have several shares that are accessible, but not writeable, to guests. the other share is a password protect share accessible by one user. i set all this up using system-config-samba. The issue that i was initially having was not being able to browse the guest shares from two win7 machines and a ubuntu machine, i was being told by windows that while 'server' existed it couldnt find the directory 'Movies'. I tried to access the passworded dir, entered in my credentials i am told that it is not accessible and access is denied, but now i can browse the guest directories. unfortunatley my ubuntu machine (not the server) is made from old parts and have built it to test xbmc and has been playing up, so i cant test if i can browse the guest share now, but i was having the first half of the problem with the ubuntu machine too so i imagine it will be the same...

Here is a copy of smb.conf

[ATTACH]141547[/ATTACH]

Any help will be greatly appreciated!!

---

### Post by msw on 2009-12-28
See the link in my sig. It will get you started on a basic Samba configuration.

---

### Post by stanger192 on 2009-12-29
Is ther something wrong with my smb.conf file or the way it has been setup?

---

