---
title: "include sudo password in bash script"
date: 2011-02-14
forum: General Help
---

### Post by daveli on 2011-02-14
Hi,

I have a bash script that would like to end with a call to shutdown, but it would need to be run as sudo. I checked on the web and this forum but with not much luck. How can I include the sudo passwd in the script and pass it to shutdown command? I tried running it as sudo but of course all the files created are owned by root and would have to change owners.

Thanks for your help,

D.

---

### Post by DaithiF on 2011-02-14
one solution is to edit /etc/sudoers to allow your user id to sudo shutdown without providing a password.  This is covered in the ubuntu community documentation for sudoers here: [https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers), see the first item under the heading Common Tasks

---

### Post by hawkmage on 2011-02-14
I would say that the best solution is setting up sudo to allow the user that will be running your script to run the command to shutdown without a password and use the sudo command in the script.  Embedding a password in a script is a bad idea.

---

