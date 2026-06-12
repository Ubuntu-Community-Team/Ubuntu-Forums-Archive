---
title: "Sharing /var/www folder"
date: 2010-05-10
forum: General Help
---

### Post by Quarum on 2010-05-10
I have installed the new Ubuntu on my home network.

My reason for doing this was to have a local LAMP environment for testing updates before I publish them to my live websites.

I have everything installed and running but I am lost on how to do one thing.

I do not have permissions to create folders in the /var/www folder. Ideally I want to open permissions on that folder so that I can map a network drive to that folder and be able to copy/paste files to the folders.

Once again this is just local in my home, so I am not at all worried about security on this box.

What/how do I set up sharing on the /var/www folder so that I can start setting up test environments?

Thanks for your help - have a great day.

---

### Post by WorMzy on 2010-05-10
```
sudo chown <username> /var/www
```

Should do the trick. Replace <username> with your username, obviously. :)

EDIT: Skipped over the last of your post; you probably don't even need to do that. Just run ```
sudo mount /dev/name /var/www
``` substituting name with the actual partitions name (e.g. sda4) and it should work.

EDIT EDIT: Make it automount by adding an entry to /etc/fstab.

---

### Post by Quarum on 2010-05-10
Perfect - that did it.

Thank you very much! I appreciate your time and your help.

Have fun!

Q

---

### Post by utnubuuser on 2010-05-10
sudo chown -R username /var/www

-R for recursive

---

