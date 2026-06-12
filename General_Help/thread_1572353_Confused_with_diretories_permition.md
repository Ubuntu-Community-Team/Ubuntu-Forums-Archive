---
title: "Confused with diretories permition"
date: 2010-09-10
forum: General Help
---

### Post by urieljuliatti on 2010-09-10
Hello to everyone, i'm a new Ubuntu user and starting with programming, i've already installed XAMPP for LINUX at /opt directory and the Eclipse app to code php, java etc..

When I try to write or create a file inside htdocs XAMPP directory the Eclipse outputs this message to me:

"Parent of resource: /opt/lampp/htdocs/site/includes/include.php is marked as read-only.
/opt/lampp/htdocs/site/includes/include.php (Permission denied)"

Whats the matter with this possible error?

Thanx.

---

### Post by uRock on 2010-09-10
If you are using the command line to create the file, then add sudo in front of it to give the process permission to write to files in the root file system. For more on root and sudo, please read this link.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by urieljuliatti on 2010-09-11
Thanks for the reply uRock, but i'm not creating the file through comand lines, i'm creating through Eclipse itself..

Best wishes,

Uriel

---

### Post by lykwydchykyn on 2010-09-11
By default on Ubuntu (and most other Linux systems) anything outside your home directory is read-only except for the root user.

If you want to be able to write files to these directories you need to give yourself permissions to write to that folder.  Quickest thing to do is just make yourself owner of the directory, like so:

```

sudo chown -R myuser /opt/xampp/htdocs


```

Then you should be able to write to the directory.

---

### Post by uRock on 2010-09-11
If you don't want to run the program as root, I don't know if devs do that, then you can save to /home then use cli or **gksu nautilus** to place the file/directory where you want it.

I don't knw much about using dev software, so I can't give much more than that.
> **lykwydchykyn said:**
> ```

sudo chown -R myuser /opt/xampp/htdocs


```Then you should be able to write to the directory.
That should work.

Good luck,
uRock

---

### Post by gadolinio on 2010-09-11
> **lykwydchykyn said:**
> by default on ubuntu (and most other linux systems) anything outside your home directory is read-only except for the root user.

If you want to be able to write files to these directories you need to give yourself permissions to write to that folder.  Quickest thing to do is just make yourself owner of the directory, like so:

```

sudo chown -r myuser /opt/xampp/htdocs


```then you should be able to write to the directory.

+1.

---

### Post by urieljuliatti on 2010-09-11
> **lykwydchykyn said:**
> By default on Ubuntu (and most other Linux systems) anything outside your home directory is read-only except for the root user.

If you want to be able to write files to these directories you need to give yourself permissions to write to that folder.  Quickest thing to do is just make yourself owner of the directory, like so:

```

sudo chown -R myuser /opt/xampp/htdocs


```Then you should be able to write to the directory.

Damn!! Thanks man, you save me!! That worked properly!
;)

---

### Post by gadolinio on 2010-09-12
Great. Please remember to mark the thread as [SOLVED] =)

---

