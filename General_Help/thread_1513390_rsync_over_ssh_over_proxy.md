---
title: "rsync over ssh over proxy"
date: 2010-06-19
forum: General Help
---

### Post by tmfs on 2010-06-19
Hey,

My computer currently has access to the internet only through a proxy, thus I'm forwarding my ssh connection to port 8080 through corkscrew.

I need to run rsync over this ssh connection - does anyone know how to make it work? Just typing "rsync username@destination-ssh-server:folder-name" doesn't work since this doesn't forward the ssh traffic to port 8080.

I'm using Ubuntu 10

Thanks

---

### Post by Jeroensum on 2010-06-20
Try this:

rsync -v -e ssh username@remote-system:/sync_dir /path/to/local/sync_dir

---

### Post by tmfs on 2010-06-20
> **Jeroensum said:**
> Try this:

rsync -v -e ssh username@remote-system:/sync_dir /path/to/local/sync_dir

That works thanks!

PS - to those who are using corkscrew - I had to replace username@remote-system with a custom Host I had configured in my .ssh/config file which used corkscrew.

---

