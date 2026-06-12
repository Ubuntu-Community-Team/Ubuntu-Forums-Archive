---
title: "Showing wrong disk usage."
date: 2010-10-29
forum: General Help
---

### Post by wigglestix on 2010-10-29
[IMG]http://i1223.photobucket.com/albums/dd502/xYETIx/ubuntu.png?t=1288401922[/IMG]



I have benn using ubuntu on an old laptop to run a samba server and a torrent server and it has been working fine till a few days ago when it stopped letting me write any files to the disk, So i tried deleting some of the files i no longer needed to free up some space and the disk usage didnt decrease so i checked it out using the disk usage analyzer and it says its full but i know for sure its not.

[IMG]http://s1223.photobucket.com/albums/dd502/xYETIx/?action=view&current=ubuntu.png[/IMG]

---

### Post by psusi on 2010-10-29
What makes you think it's not?

---

### Post by wigglestix on 2010-10-29
Its a 250 gb disk why is saying 100% full at 108 gb and deleted about 20gb of files and there was no change.

---

### Post by dcstar on 2010-10-29
> **wigglestix said:**
> Its a 250 gb disk why is saying 100% full at 108 gb and deleted about 20gb of files and there was no change.

```
gksudo baobab
```
and empty the Trash.

---

### Post by psusi on 2010-10-29
Where did you delete the files from, and what does df -h show?

---

### Post by wigglestix on 2010-10-29
df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             222G  209G  1.5G 100% /
none                  1.4G  292K  1.4G   1% /dev
none                  1.4G  196K  1.4G   1% /dev/shm
none                  1.4G  368K  1.4G   1% /var/run
none                  1.4G     0  1.4G   0% /var/lock
none                  1.4G     0  1.4G   0% /lib/init/rw


i deleted the files from my sharepoint folder wich is where i store files to be shared on my network.

---

### Post by psusi on 2010-10-30
Well it looks like you need to delete some more since it is using 94 out of 208 gb.

---

### Post by wigglestix on 2010-10-30
Ive tried this i deleted a 15 gb collection of tv shows and there was no increase in storage space.

---

### Post by luvshines on 2010-10-30
> **wigglestix said:**
> Ive tried this i deleted a 15 gb collection of tv shows and there was no increase in storage space.

Did you just deleted it by pressing delete button, or emptied the trash as well ?

---

### Post by wigglestix on 2010-10-30
Yes i did empty the trash the first time but the second time when i went to empty it after deleting the 15 gb of tv shows it did not show up in the trash.

---

### Post by psusi on 2010-10-30
You realize you need to run the scan again to update the space right?

---

### Post by pxxc on 2010-11-02
Dear all,

I'm facing a similar problem.
Each time I type **df** I see my disk with less free space available:
/dev/sda5              7598060   3857020   3355084  54% /
/dev/sda5              7598060   3858316   3353788  54% /
/dev/sda5              7598060   3860532   3351572  54% /
Some days ago I had 94% of used disk.
After a reset it came to 50%.

This is not a problem for a desktop switched off every day, but I' concerned about a small "server" that I'm installing in an industrial PC...  
Any ideas on how to overcome this?

Regards.

Paulo

---

### Post by psusi on 2010-11-02
> **pxxc said:**
> Dear all,

I'm facing a similar problem.
Each time I type **df** I see my disk with less free space available:
/dev/sda5              7598060   3857020   3355084  54% /
/dev/sda5              7598060   3858316   3353788  54% /
/dev/sda5              7598060   3860532   3351572  54% /
Some days ago I had 94% of used disk.
After a reset it came to 50%.

This is not a problem for a desktop switched off every day, but I' concerned about a small "server" that I'm installing in an industrial PC...  
Any ideas on how to overcome this?

Regards.

Paulo

Look in /tmp and see if something is filling it up.

---

### Post by pxxc on 2010-11-03
> **psusi said:**
> Look in /tmp and see if something is filling it up.

I've found that my app is responsible for that. If I stop it, the space consumption almost stops. As it only exchanges data through the serial port, my guess is that it can be only caused by the open() syscall, invoked over and over again.  Despite close() being also invoked, I suppose that resources are never freed. This is odd because apparently no disk space is used.

---

### Post by psusi on 2010-11-03
> **pxxc said:**
> I've found that my app is responsible for that. If I stop it, the space consumption almost stops. As it only exchanges data through the serial port, my guess is that it can be only caused by the open() syscall, invoked over and over again.  Despite close() being also invoked, I suppose that resources are never freed. This is odd because apparently no disk space is used.

Yea, that isn't it.  Are you using a temp file?  Did you check /tmp?

---

### Post by mrnelson1986 on 2010-11-03
Also check lost&found, sometimes mine gets gunked up with stuff that it "recovers" thinking I didn't really mean to delete it

---

### Post by BeeDee on 2010-11-04
> **wigglestix said:**
> Yes i did empty the trash the first time but the second time when i went to empty it after deleting the 15 gb of tv shows it did not show up in the trash.
I had this with my / partition after re-installing 10.10 and adding Mint to another partition and moving /home and my personal data to their own partitions to be shared by 10.10 and Mint. DCSTAR in his:

Code:
gksudo baobab
and empty the Trash.
provided the clue. In Root was a .local file that contained, among other things, a Trash file that had in it copies of the partition jigger-pokery I had just done amounting to 4.5Gb.

Maybe worth looking there.

---

