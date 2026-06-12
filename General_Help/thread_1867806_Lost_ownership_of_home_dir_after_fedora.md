---
title: "Lost ownership of home dir after fedora"
date: 2011-10-23
forum: General Help
---

### Post by down_quark on 2011-10-23
I'm on a university computer that automatically mounts a remote filesystem.
I recently installed fedora locally and stupidly created a user with the same username.
And now I don't own my home directory even after recursively chowning.
I think if I give one of the accounts a new name and/or id I'd be fine.
but I can't be logged in to do that.
So I've tried creating a temp account in the terminal but I'm having issues giving the account a password.
I've also tried to no avail: ```
gksudo gnome-control-center
gksudo users-admin
```I've tried what's suggest [here]("http://ubuntuforums.org/showpost.php?p=10293947&postcount=3") but I'm not sure the fedora account's uid is 500.
Is there anything I can do, short of reinstalling ubuntu? I don't mind just getting rid of fedora.

---

### Post by hwttdz on 2011-10-23
I think if you make the users have the same userid on both sides it should be smooth sailing.

so as root, 
usermod -u newuid username

and then make sure everything in that directory is owned by the right person.

id -u username, will tell you what their current number is, so do that in either ubuntu or fedora, and then on the other change it to that number.

---

### Post by down_quark on 2011-10-23
Yeah, I guess this can't be fixed without having root.
Guess I'll ask the staff and wait and see.
Thanks for getting back so quickly!

---

### Post by neu5eeCh on 2011-10-23
This may not pertain but Ubuntu starts it's UID at 1000 whereas Fedora begins at 500. So, even though you might have the same name and password, if your UID in Ubuntu is 1001 and your UID in Fedora is 501, you won't be able to access Jack. If you think this is the issue, you can change the user name and password of your present account, then create a new one with the correct Username, Password, **and** UID.

---

