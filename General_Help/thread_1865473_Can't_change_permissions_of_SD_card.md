---
title: "Can't change permissions of SD card"
date: 2011-10-20
forum: General Help
---

### Post by ticktick on 2011-10-20
Hi there!

Because I work on different Ubuntu machines, I put all my personal files on a SD card. This mounts at 
  /media/mycard/ 
and I created a link
  cd ~
  ln -s /media/mycard/
so that I have access to my files from my Ubuntu home place. This works fine!

But the problem is, that I have some PHP files that need to run on the local web servers of each machine. So I tried to get a global server access to my card contents by creating another link with
  cd /var/www
  ln -s /media/mycard
The link to mycard does now appear in /var/media and I can access my files from there as well.
When I open the browser and try 
  [http://localhost/mycard/](http://localhost/mycard/)
then I receive the message:
  Forbidden
  You don't have permission to access /mycard/ on this server.

My problem now is, that I am not able to change the permissions.
When I open Konqueror and the "Properties" of /media/mycard/, I select the "Permissions" tab and change all Access Permissions to "Can View & Modify Content" (including "Apply changes to all subfolders and their contents"), a Progress Dialog seems to indicate that the work is done. But the permissions are not changed afterwards.
It does not help, if I repeat all that after opening Konqueror as root.
Also a (sudo) call of
  chmod 777 -R /media/mycard
does not change anything.

Why am I not able to change to global access??

Thank you.

---

