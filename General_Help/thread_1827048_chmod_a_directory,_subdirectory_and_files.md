---
title: "chmod a directory, subdirectory and files"
date: 2011-08-17
forum: General Help
---

### Post by duf on 2011-08-17
Hi everybody,

I had to fresh install Ubuntu on my laptop. I made a directory /data where my documents are placed and then I made a softlink from /home/me/Documents to /data/Documents (this is the place where all my documents are stored).

So I have a directory /home/me/Documents which softlinks to /data/Documents

I did a 'sudo chown -R me:me /data/Documents'
I also did a 'sudo chmod -R 777 /data/Documents'

A strange thing happens: when I cd to / and then 'ls-l' I see all my directories except /data, but when I do 'ls' I see all my directories /data inclusive.

Also there I an odt document in a subdirectory of /home/me/Documents (which links to /data/Documetns) that I wish to change, but it opens in read-only
When i go into that subdirectory and do a 'ls -l' that document is listed: "-rwxrwxrwx" and owner is "me:me"

And the most curious thing is that my other documents open in Libreoffice as editable. Of course I could open that read-only file in Libreoffice and save a copy, but I am just curious to know the reason.

Here follows the line I added to /etc/fstab: 
'/dev/sda5 /data ext4 users,rw,suid,dev,exec,auto 0 2'

Who has the solution? so that I can open my files with write permission.

Thanks

---

### Post by dino99 on 2011-08-17
777= opened door for everyone around the world ;), very risky, 660 is enough

---

