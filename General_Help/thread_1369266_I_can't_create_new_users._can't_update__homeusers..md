---
title: "I can't create new users. can't update  /home/users/.ICEauthority"
date: 2009-12-31
forum: General Help
---

### Post by marticc on 2009-12-31
Hi, I have recently re-installed my Ubuntu 9.10 (I used to have it inside the Windows partition -using wubi-, and I decided to create a new partition for it).

Now I'd like to create a desktop user but I can't. I mean, I was able to create the new desktop user, but everytime I have wanted to start a session with the new desktop user, I have got the following error messages:

"Couldn't update .ICEauthority file. /home/suario/.ICEauthority"
"There is a problem with the server settings (usr/lib/libconf2-4/ gconf-sanity-check2 has a value 256)"
"Nautilus couldn't create /home/user/Desktop,  /home/user/.nautilus. Before running nautilus create these folders or give Nautilus permissions to create them"

When I explore the new user desktop home folder I can only find one folder (/home/user/.fprint), and 4 documents /home/user examples, /home user/.bashrc, /home/user.bash_logout, and /home/user/.profiledidn't .

I tried giving the new user more permissions but it didn't work. I have also tried create the new user account using the root account but it didn't work either. As I had made a backup of my old home folder (before uninstalling wubi and creating the new partition), I copied all the files of the wubi  /home/user folder, and I pasted them in the new partition /home/user but yet again it didn't work.

I have also tried running the following commands in a root shell:

chown usuario /home/usuario/.ICEauthencity
chmod 644 /home/usuario/.ICEauthencity

But the problem is still there.

I have read taht the problem might be related with the fact that the default admin user home folder is encrypted, an that this problem might be solved by changing the passphrase but I don't know how to do it.

I would appreciate any help you can provide with me. Thanks and happy new year.

---

### Post by marticc on 2010-01-01
Doesn't anyone know how to help me?. I'd be really grateful if you could help me.

Thanks.

---

### Post by exquest on 2010-05-13
I just ran into the exact same problem with a clean install of ubuntu 9.10.  The strange thing is that I can't seem to create a new user unless I run the "Users and Groups" tool from the command line using gksudo.

I guess it's a bug.

---

