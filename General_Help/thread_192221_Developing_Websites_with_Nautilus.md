---
title: "Developing Websites with Nautilus"
date: 2006-06-08
forum: General Help
---

### Post by fishhead on 2006-06-08
Hello,

I am a newer developer who just switched over from windows (much more efficient now) and I am trying to find the best method for me to manage my sites...

So far I have created a connection to my web server in ubuntu and am very happy with the browsing features over what I was using back in the windows days.

There are just 2 issues that I have relating to editing the files directly on the server.
[LIST]
[*]When I click on a file to edit it opens as a read only file, therefore I cannot save it without save-as > selecting file location on server > replacing it (not the end of the world, but it would make my life much easier if I could just click save)
[*]My file permissions are showing up as unknown, and I cannot edit them in nautilus the way I would like to.
[/LIST]



My appologies if this has already been addressed, I did about 30 minutes of searching and could not find what I wanted.

---

### Post by Shay Stephens on 2006-06-08
I am using bluefish for editing webpages.  I can use the connection made (connect to server) to open (file - open - select the webserver) and save files on the webserver directly as you mentioned.  I have not tried doing so directly through nautilus.

---

### Post by scxtt on 2006-06-08
i just connected to my old college account via "connect to server" in "places" - and noticed this problem as well - when i viewed the properties of a file existing in the folder nautilus made for me once i connected, it listed the owner as if i was using my breezy box and not my college account ...

are the usernames identical for you on the 2 accounts?  and what connection type are you making (SSH, WebDAV, etc.)?

[color=red]EDIT:[/color] it worked flawlessly for me today [as it did in the past, just not that instance, i guess] ...

---

### Post by ketsugi on 2006-06-09
I noticed the same issue yesterday via an FTP connection. User names are definitely not identical but that shouldn't be a problem.

---

### Post by fishhead on 2006-06-09
I've got it working the way I want it now after making a few changes to my user with my webhost and setting up a SSH connection in nautilus (the ftp connection did not work the way I wanted it to).  SSH works great though, I can edit all of my files with gedit right on the server, just like it was another folder on my computer.

I am still having a few problems getting other programs (like gimp and gphpedit) to edit the files directly on the server, I will let you know if I can get them to work.

---

### Post by scxtt on 2006-06-09
when i did it, i used the SSH option ... the only reason i can come up w/ for the user name discrepancy is that it creates a tmp file that IS mine, until i upload it back to the account i've SSH'd to ...

---

### Post by kthakore on 2006-06-09
definatly check out quanta plus as a web developing tool, because I believe it gets as close to dreamweaver as possible. Also for flash check out synfig studio. What type of web developing do u do?

---

