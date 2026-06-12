---
title: "permission to add new file to usr, How do I??"
date: 2011-09-21
forum: General Help
---

### Post by gringo loco on 2011-09-21
Dell Inspiron 1545 running ubuntu 11.04 32bit

After successfully installing 11.04 from my live USB drive on my new (used) laptop, I downloaded a game I like (Bos Wars) from the Ubuntu software center. It works great EXCEPT When I try to add a couple of new maps (created by me on a different computer) in usr/share/games/boswars/maps (This is where the maps were put on the download) my computer tells me I don't have permission to do that. 
I know there must be a way to get this permission but I have not run into this message before so I need help.

---

### Post by puca mor on 2011-09-21
You'll be needing to open the destination folder usr/share/games/boswars/maps with root privilege...

This might help ya out - [http://lifehacker.com/5596006/create-an-application-shortcut-to-open-nautilus-as-root-in-ubuntu]("http://lifehacker.com/5596006/create-an-application-shortcut-to-open-nautilus-as-root-in-ubuntu")

Alternatively, as I have, you can create a launcher (right click on desktop and select create launcher) then name it something like Root File Browser and in the "Command to run on click" write ```
gksudo nautilus
```
That will create a desktop shortcut to browse your files with root privilege.

Then when you open as root you can navigate to destination folder and put your maps in there :)

---

### Post by patryk77 on 2011-09-21
Alternatively, change the folder's permissions.

In the terminal, run:
```
sudo chown `stat -c %U /usr/share/games/boswars/maps/`.`id -gn` /usr/share/games/boswars/maps/
sudo chmod 775 /usr/share/games/boswars/maps/
```

This will change the owner to the current owner and your group as the folder's group.

chmod 775 makes the folder writable to your group, so you can now copy files without running as root.

---

### Post by gringo loco on 2011-09-21
Thank You thank you and Gracias muchisimo.
I successfully changed the file permission and everything is working great:P

---

