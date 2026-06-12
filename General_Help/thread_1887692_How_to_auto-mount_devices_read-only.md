---
title: "How to auto-mount devices read-only?"
date: 2011-11-27
forum: General Help
---

### Post by guest534252 on 2011-11-27
Is there a way to instruct Ubuntu (or Xfce in my case) to auto-mount certain devices read-only for certain users? What I basically want is to protect data on my Windows partitions and USB HDD/flash drives from my kid when he plays chess/watches cartoons. :)

---

### Post by oldtimer7777 on 2011-11-27
> **guest534252 said:**
> Is there a way to instruct Ubuntu (or Xfce in my case) to auto-mount certain devices read-only for certain users? What I basically want is to protect data on my Windows partitions and USB HDD/flash drives from my kid when he plays chess/watches cartoons. :)

What I do for clients is just make them hidden folders instead.  Much easier that way too.

That is what we do on Windows Server systems too, fyi for big huge office networks.

Nobody ever thinks to look for hidden file folders.

---

### Post by guest534252 on 2011-11-27
Actually I don't want my kid not to be able to see his cartoons, I want him not to be able to accidentally delete them. :)

---

### Post by Morbius1 on 2011-11-27
The Windows partition problem is easy enough:
* Unmount the partition if you mounted it manually

* Run the follwoing command to get the correct UUID number:
```
sudo blkid -c /dev/null
```You'll get back something like this:
> /dev/sda1: LABEL="WinXP" UUID="DA9056C19056A3B3" TYPE="ntfs" * Create a permanent mount point:
```
sudo mkdir /media/windows
```* Then add a line to /etc/fstab:
```
UUID=DA9056C19056A3B3 /media/windows ntfs defaults,nls=utf8,uid=1000,umask=022,windows_names 0 0
```[COLOR=Blue][I]uid=1000 will make you the owner of the mounted partition.
umask=022 will give read/write access to you and remove write ( also delete ) access to everyone else.

[/I][COLOR=Black]Then run the following command that will test for errors and if there are none mount the partition:
[/COLOR][/COLOR]```
[COLOR=Black]sudo mount -a[/COLOR]
```[COLOR=Black]

If you want to expand the ownership so that you and spouce have write and others have read only then:

* Create a new group:
[/COLOR]```
[COLOR=Black]sudo groupadd parents[/COLOR]
```* Add yourself and spouse to the new group:
```
sudo gpasswd -a bob parents
sudo gpasswd -a edna parents
```[COLOR=Blue]*Bob and Edna will have to log out and log back in again for the group membership to take affect.*[/COLOR]

* Then change the line in fstab to this:
```
UUID=DA9056C19056A3B3 /media/windows ntfs defaults,nls=utf8,gid=parents,umask=002,windows_names 0 0
```[COLOR=Black]

gid=parents will make the group "parents".
umask=002 will enable the owner (root) and all members of the "parents" group to have read/write access and limit others to read only.
[/COLOR]

---

### Post by guest534252 on 2011-11-28
Morbius1, thank you for the detailed explanation. But it still doesn't explain how to restrict permissions on removable devices. Besides, I don't very much like the idea of writing anything to /etc/fstab. Xfce somehow manages without that when it mounts partitions on boot-up and flash drives. 

There is the users-admin utility that seems to handle user privileges, but as far as I can see it's not so flexible as to both grant the user access without a password and make it read-only.

I guess I should now look in the direction of udisks/PlicyKit rules...

---

