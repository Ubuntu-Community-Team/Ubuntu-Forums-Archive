---
title: "I can only run NVU with sudo command - help!"
date: 2005-03-05
forum: General Help
---

### Post by Jonathan_ on 2005-03-05
I used this guide to install NVU - [http://www.ubuntuguide.org/#nvu](http://www.ubuntuguide.org/#nvu)
However when I want to run it, it will not let me run it as my own user, I must use the sudo command and enter a password each time in the terminal. How can I change it so my user has access to it?

Thanks!

---

### Post by p!=f on 2005-03-05
[QUOTE=Jonathan Steel]I used this guide to install NVU - [http://www.ubuntuguide.org/#nvu](http://www.ubuntuguide.org/#nvu)
However when I want to run it, it will not let me run it as my own user, I must use the sudo command and enter a password each time in the terminal. How can I change it so my user has access to it?

Thanks![/QUOTE]
Looks like a permission problem.
If you install NVU to /opt/nvu, run something like this
```

sudo chown -R root:users /opt/nvu

```
Be sure group "users" has sufficient permissions to run NVU and you're in that group
```

sudo adduser <your_account_name> users

```

Let us know if it works.

---

### Post by crane on 2005-03-05
What error are you getting when you try to run as user?
Also check the place where you installed the program and make sure you have permissions to un it as a user.

---

### Post by Jonathan_ on 2005-03-05
Thanks, i've changed the permissions now so my user has full control over all files and folders in /opt/nvu-0.81/ however when I run it as my user i get a window saying 'Choose user profile'. I can rename, create and delete profiles but when I try and click 'Start NVU' nothing happends atall, the window just stays there untill I press exit. When I run NVU with the sudo command, it goes right into the program. (This is the same problem as I had before when root was the owner/group but now my user is but its still the same problem)

---

### Post by p!=f on 2005-03-05
Please, post here an output of:
```

ls -al /opt/nvu-0.81

```
Try to run NVU from the terminal
```

/opt/nvu-0.81/nvu

```
and post here error messages if any.

---

### Post by kassetra on 2005-03-05
[QUOTE=Jonathan Steel]Thanks, i've changed the permissions now so my user has full control over all files and folders in /opt/nvu-0.81/ however when I run it as my user i get a window saying 'Choose user profile'. I can rename, create and delete profiles but when I try and click 'Start NVU' nothing happends atall, the window just stays there untill I press exit. When I run NVU with the sudo command, it goes right into the program. (This is the same problem as I had before when root was the owner/group but now my user is but its still the same problem)[/QUOTE]

In your /home/username directory is a special directory named .nvu -- right now, this directory (even though it's in your home directory) is owned by root.

You need to change the owner and the group of the .nvu directory to your username and your group.

If you don't know how to do this, let me know.

---

### Post by Jonathan_ on 2005-03-05
Thanks kassetra, I forgot there was the hidden folder as well as the other. It works perfectly now :)

---

### Post by kassetra on 2005-03-05
[QUOTE=Jonathan Steel]Thanks kassetra, I forgot there was the hidden folder as well as the other. It works perfectly now :)[/QUOTE]

I'm so glad I could help!  :)
Oh!  You might also like Peacock, a simple wysiwyg html app.  :)  (it's in the apt repositories)

---

