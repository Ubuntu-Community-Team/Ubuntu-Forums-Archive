---
title: "making myself owner of &quot;file system ... &quot; folder"
date: 2010-10-05
forum: General Help
---

### Post by strnad on 2010-10-05
Hello guys,

I would like to add some emblems files to folder "/file system/usr/share/pixmaps" so they are all on one place.

The problem is that I cannot write into it, since I am not the owner "root" is.

How can I make myself the owner of these folders so I can upload them there? I would preffer to log in as a "root" but I am not aware of creating such an account.

Thanks for help

Peter

---

### Post by sisco311 on 2010-10-05
Either start the file manager as root, press Alt+F2 and run:
```
gksu nautilus --no-desktop
```
or use the terminal to copy the files as root:
```
sudo cp path/to/file /usr/share/pixmaps
```

See: [uhelp]community/RootSudo[/uhelp]

Be careful when doing administrative tasks -- you might damage your system!

---

### Post by pricetech on 2010-10-05
Use the process in the above post is best.  You could chown the folder, or chmod it, but that's not recommended.

For future reference, you might change your group to root, which should give you access pretty much anywhere you need it.

---

### Post by mike555 on 2010-10-05
or you could install "nautilus-gksu" , that way you will be able to right click on any file to open it as admin/root.

---

