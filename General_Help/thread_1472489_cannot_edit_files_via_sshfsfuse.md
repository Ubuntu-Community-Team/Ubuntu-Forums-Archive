---
title: "cannot edit files via sshfs/fuse"
date: 2010-05-04
forum: General Help
---

### Post by headlessspider on 2010-05-04
sometimes i edit files in a remote server. i normally mount the remote drive via sshfs and edit a configuration file or two and some text files using gedit. after i upgraded to 10.04 i cannot save the files that i edit anymore. i can rename the file. but the weird thing is that i cannot save the file after i edit it. one of the files that i was editing is crontab.

does anyone have an idea how i can solve this particular problem?

---

### Post by headlessspider on 2010-05-05
is it fuse/ssh?

---

### Post by jokerejoker on 2010-05-05
I very much has the same problem..

I have some files at a server that I would like to edit through sshfs/sftp. I use eclipse as editor and I would like to have the remote folder some how as a project in eclipse.

Any idea??

---

### Post by headlessspider on 2010-05-06
i got to solve this problem. the problem was with gedit. here are the steps i took:

1. on gedit click on edit - preferences
2. click on the editor tab
3. make sure that the "create a backup copy of files before saving" is checked
4. click on close

that's it.

---

### Post by m0ns00n on 2010-06-17
But why? I don't want to create a backup file. What then? It's already a time since this version of Ubuntu was released, and this bug is still haunting me.

---

