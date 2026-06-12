---
title: "Chmod and folders...."
date: 2009-09-21
forum: General Help
---

### Post by Adrienk on 2009-09-21
I have made a SVN repository and recently checked out a project, the issue is the whole folder has a lock on it. due to this i cannot edit/add/delete file from that folder.

How do I change the premision of ther folder to remove the lock?

Becvause i thought it was chmod 664 - but that dosent remove the lock on the folder.

Side note: - I apparently do not have ownership of the folder -

SVN 1.6.4 
Gnome (Latest version) 2.26.1

---

### Post by Adrienk on 2009-09-21
bump

---

### Post by Krupski on 2009-09-21
> **Adrienk said:**
> I have made a SVN repository and recently checked out a project, the issue is the whole folder has a lock on it. due to this i cannot edit/add/delete file from that folder.

How do I change the premision of ther folder to remove the lock?

Becvause i thought it was chmod 664 - but that dosent remove the lock on the folder.

Side note: - I apparently do not have ownership of the folder -

SVN 1.6.4 
Gnome (Latest version) 2.26.1

You can either access the folder as root, or you can change it's permissions, or you can change ownership.

Access as root:

```

sudo su (enter the admin password)
(do whatever you need to do to the directory)
(when done, type "exit")

```

Change it's permissions:

```

sudo chmod 0777 directory

```

Change who owns it:

```

sudo chown -R you:you directory

```

Obviously, "you" is your username. The -R means "recursive" (change ownership on all files in the directory).

Hope this helps.

-- Roger

---

### Post by lloyd_b on 2009-09-21
For directories (folders), you'll probably want 775 rather than 664 - you need "x" (execute) permission on a directory before it'll let you "cd" into that directory.

Lloyd B.

---

### Post by Adrienk on 2009-09-21
> **Krupski said:**
> You can either access the folder as root, or you can change it's permissions, or you can change ownership.

Access as root:

```

sudo su (enter the admin password)
(do whatever you need to do to the directory)
(when done, type "exit")

```Change it's permissions:

```

sudo chmod 0777 directory

```Change who owns it:

```

sudo chown -R you:you directory

```Obviously, "you" is your username. The -R means "recursive" (change ownership on all files in the directory).

Hope this helps.

-- Roger

So wait would it be say:

chown -R adam:adam /home/usr/documents/java - assuming Java is the folder that needs to be "owned" by me?

---

### Post by Krupski on 2009-09-21
> **Adrienk said:**
> So wait would it be say:

chown -R adam:adam /home/usr/documents/java - assuming Java is the folder that needs to be "owned" by me?

Yup.

---

