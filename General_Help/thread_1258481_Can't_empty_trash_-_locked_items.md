---
title: "Can't empty trash - locked items"
date: 2009-09-05
forum: General Help
---

### Post by 10i on 2009-09-05
Hi,

When I try to empty the trash I get an error saying that Root has locked these files. 

I deleted these files before re-installing Ubuntu  if that helps. It's about 350 MB of mp3 files. 

My system:
eeepc 702 4G
2 GB RAM
4 GB HDD

Easy Peasy 1.01 Ubuntu 8.10

any help would be appreciated.

---

### Post by fluffman86 on 2009-09-05
Notice, if you type this wrong you can hose your system!

Open Terminal and type:
```
cd ~/.local/share/Trash/files
sudo rm -rf *
```

---

### Post by Efwis on 2009-09-05
and if your not comfortable using the command given above, do 
```
$ gksudo nautilus
```
then navigate to /.local/share/Trash/files in nautilus. highlight all the files by selecting all and hit shift+delete

that rm-rf* command if used incorrectly will wipe your entire hdd.

---

### Post by P4man on 2009-09-05
please make a habit of using **gk**sudo (or gksu) for launching graphical programs such as nautilus as root. So use:

```
gksudo nautilus
```

---

### Post by Efwis on 2009-09-05
not to go off topic here, but curiosity killed the cat. What is the difference between using gksudo and sudo? they both do the same thing.

---

### Post by P4man on 2009-09-05
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by wojox on 2009-09-05
You may also want to look in:

```
gksudo nautilus ‘/root/.Trash/’
```

See whats in there.

---

### Post by Efwis on 2009-09-05
thanks P4man

---

### Post by 10i on 2009-09-05
used the gksudo command, and now I get a different error message...

---

### Post by Shazaam on 2009-09-05
Four places...
gksudo nautilus /home/yourusername/.local/share/Trash/files
gksudo nautilus /home/yourusername/.local/share/Trash/info
gksudo nautilus /root/.local/share/Trash/files
gksudo nautilus /root/.local/share/Trash/info

Note 1=
You will need to enable "Show hidden and backup files" in user nautilus AND root nautilus. Go to Edit>Preferences and check the box.
Note 2=
If you right-click and choose "Move to Trash" while deleting what is in root's Trash/files and Trash/info the deleted files will reappear as a copy. Highlight the files then hit your shift+delete buttons. Be aware that doing this will permanently delete those files and you will need advanced tools to recover them.

---

### Post by 10i on 2009-09-05
Problem sorted, I restored them then changed the permissions to read and write, then deleted them again.

This time they will stay away, thanks for all the advice guys.

---

