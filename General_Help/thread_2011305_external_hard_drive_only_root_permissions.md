---
title: "external hard drive only root permissions"
date: 2012-06-26
forum: General Help
---

### Post by graham70 on 2012-06-26
good day I got passion fingers the other day and made my external hard drive only have root permissions ,can't access it with out running Nautilus as root. I think the command "sudo chmod -r/dev/sdd1/owner" will do it or dig my hole deeper. 
thanks for any help

---

### Post by graham70 on 2012-07-02
gday again just a bump for this thread if anyone knows where I can get help with this somewhere else please let me know thanks

---

### Post by miegiel on 2012-07-02
> **graham70 said:**
> good day I got passion fingers the other day and made my external hard drive only have root permissions ,can't access it with out running Nautilus as root. I think the command "sudo chmod -r/dev/sdd1/owner" will do it or dig my hole deeper. 
thanks for any help

```
sudo chmod -r/dev/sdd1/owner
```
Can't be right. First of all there needs to be a space between "-r" and "/dev/". Second, */dev/* is where your devices are. Where you want to change modes (chmod) or ownership (chown) is where the device is mounted (probably in */media/*). And finally, is it really the modes (read, write, execute permissions) or the ownership (root vs user) that's the problem?

As an example here is the *ls* output of my little external disk.
```
user@machine:~$ **[COLOR="Red"]ls -alFt /media/[/COLOR]**
total 32
drwxr-xr-x  5 root    root     4096 Jul  1 14:22 ./
drwxr-xr-x 23 root    root     4096 May 18 03:29 ../
drwxr-xr-x  2 user    root     4096 May  8 10:27 remote/
drwxr-xr-x  2 root    root     4096 Feb 18 02:48 cdrom/
lrwxrwxrwx  1 root    root        4 Feb 18 02:45 usb -> usb0/
drwxr-xr-x  5 user    user    16384 Jan  1  1970 usb0/

user@machine:~$ **[COLOR="Red"]ls -alFt /media/usb0[/COLOR]**
total 8740
drwxr-xr-x 5 root    root       4096 Jul  1 14:22 ../
drwxr-xr-x 2 user    user       8192 May 16 20:36 DCIM/
drwxr-xr-x 2 user    user       8192 May 16 20:36 MISC/
drwxr-xr-x 3 user    user       8192 May 16 20:36 PRIVATE/
-rwxr-xr-x 1 user    user      56164 May  8 07:33 menu.c32*
-rwxr-xr-x 1 user    user        145 May  8 07:33 syslinux.cfg*
-r-xr-xr-x 1 user    user      32256 May  8 07:33 ldlinux.sys*
-rwxr-xr-x 1 user    user    6600596 May  8 07:33 ubninit*
-rwxr-xr-x 1 user    user    2189312 May  8 07:33 ubnkern*
-rwxr-xr-x 1 user    user        422 May  8 03:34 unetbootin.clean.disk.sh*
drwxr-xr-x 5 user    user      16384 Jan  1  1970 ./
```

---

### Post by rubylaser on 2012-07-02
I'm not exactly sure what you are trying to accomplish, but if you just want your user to be able to read and write to the drive, you'll want to chown it to your user. 
```
sudo chown -R user:user /path/to/external drive
```

* Replace the two user sections above with your username.

---

### Post by graham70 on 2012-07-03
thanks rubylaser and miegiel for your help I am not a great one for command line as my example shows. I have found a way by moving the files back to a ntfs  drive sort out the permissions there. then formatted the ext4 drive they came from to ext4 . At this stage a found the drive to have only root permissions so I changed the ownership to me and gave user create and delete folders option .Now I am in the process of moving by files back with Nautilus with out using root. this sound a long winded way of doing it and I don't know what windows file permissions got to do with Linux file permissions and don't understand why when I formatted the ex4 hard drive it only gave root permissions. Any ways there is more then one way to skin a cat I use a spoon :)
thanks again

---

