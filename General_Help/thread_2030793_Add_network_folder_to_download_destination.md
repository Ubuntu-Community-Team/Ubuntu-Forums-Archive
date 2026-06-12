---
title: "Add network folder to download destination"
date: 2012-07-21
forum: General Help
---

### Post by DeMartini on 2012-07-21
When I download a file (video), save link as, how do i add a network folder from my network on my server where I host files as one of the options? Hope i'm explaining this question accurately..

---

### Post by Habitual on 2012-07-21
mount the host host://mnt/share/directory you wish to save it to first prior to saving.

---

### Post by Morbius1 on 2012-07-21
> **DeMartini said:**
> When I download a file (video), save link as, how do i add a network folder from my network on my server where I host files as one of the options? Hope i'm explaining this question accurately..
Based on how you described the problem I'm guessing you are connecting to the server via Nautilus. When you do that it mounts the remote share in your home directory: 
> home/you-user-name/.gvfs/share-name on server-nameYou can make it easier to find if you do this:
> nautilus $HOME/.gvfsThen Bookmark it: Bookmarks > Add Bookmark. You can rename it to LAN or something so it makes more sense if you'd like.

Now it will show up in the left side panel of nautilus and in the "Save As" box.

---

### Post by DeMartini on 2012-07-22
Thank you great advice, probably should have thought of that, thanks again......:popcorn:

---

