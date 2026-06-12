---
title: "Unable to remove file over pendrive"
date: 2011-06-15
forum: General Help
---

### Post by Gaurav_kataria on 2011-06-15
I have a Pen-drive which is affected by virus. I wish To format it, i tried to format it in GUI mode but i was unable to do so, then i tried to remove the files in pen drive by using rm command but an error msg that the file system has the read only permission so can't be deleted occur, then i tried to remove the read only permission by using chmod command but still the error that the file is read only permission was unable to change. I searched a lot over google for help but was unable to get correct solution can anyone help me.
:KS

---

### Post by seawolf167 on 2011-06-15
Welcome to the forums

If you open GParted (System -> Administration -> GParted) can you format it from there?

---

### Post by StrayEddy on 2011-06-15
unmount the drive before formating it, try it again.

---

### Post by Gaurav_kataria on 2011-06-16
Thanks for your kind reply

I tried using G-parted it is an very nice software. I Tried to formate it so was not successful, later i unmount it and tried once again to formate it but still was unable.

Then i tried using sudo rm -f  * (that will remove all files drive memory forcefully) but it again showd the error that files here are read only

then i came back to G parted then firstly i deleted the drive so it showed full unallocated memory it was success full then i format it gives an error that 

GParted 0.6.2
 Libparted 2.3
    **Delete /dev/sdb1 (fat16, 1.84 GiB) from /dev/sdb**  00:00:00    ( SUCCESS )             calibrate /dev/sdb1  00:00:00    ( SUCCESS )             [I]path: /dev/sdb1
start: 135
end: 3858623
size: 3858489 (1.84 GiB)[/I]          delete partition  00:00:00    ( SUCCESS )       ========================================
    **Create Primary Partition #1 (ext2, 1.84 GiB) on /dev/sdb**  00:00:03    ( ERROR )             create empty partition  00:00:03    ( ERROR )       libparted messages    ( INFO )             *Can't have overlapping partitions.*          ========================================

Then i tried to formate it using GUI mode again then, i was very surprise to see the result that it showed that the formate is completed but when i open the pen drive so item in it was as it is even the name/label of the drive was not change.
tried to do it again but still there was the same result, i later thought is there any fault in my laptop so tried on my friends pc but still the result was same.

i am very serious about this problem now, because its not the matter of pen drive but if this virus stuff is so strong then if it gets over hard  disk of pc so it will be very dangerous.

please find me a way over it..

reply soon :)

---

### Post by seawolf167 on 2011-06-16
Do not use that sudo rm ---- command you posted earlier!

Please run the following command

```
sudo chown -R $USER:$USER /dev/sdb1
```then open GParted, unmount the drive and try reformatting it again.

---

### Post by Gaurav_kataria on 2011-06-16
Thanks for your kind reply.

I did so as you said but when i open and formate it using GParted then  it is showing that it is formate but in some time it refresh and sill  the files are not gone from it.

what should i do now..
please convey me that the command you have given
sudo chown -R $USER:$USER /dev/sdb1
 
here USER should be writen  as USER as it is or by meaning user here (gaurav)..

please reply soon :)

---

### Post by Gaurav_kataria on 2011-06-16
Hello there,

its really not working. how this can be possible linux is sayig it had formated the drive completely but still data does't goes off.. :(

i tried replacing USER with its mean 'user' here it is 'gaurav' then unmounted as did as u said.. no effect still it is same as it was..

reply soon lukg over it..

---

### Post by HotForLinux on 2011-06-16
> "...then i tried to remove the read only permission by using chmod command  but still the error that the file is read only permission was unable to  change..."I do not understand what you did, but it seems that you should give write permission, not to remove read permission.

For this, with the unit mounted you should:

1.  mount the drive and search for the mount point or the directory where the usb drive is mounted

2.  execute something like:

**sudo chmod 755 -v -R  **/media/usb/*

3. and then try to remove everything with:

**sudo rm -v -f -R **/media/usb/*

BUT INSTEAD OF "/media/usb"  use the real mount point of your usb drive, which you can find examining the output of the **mount** command.

---

### Post by HotForLinux on 2011-06-16
```
sudo chown -R $USER:$USER /dev/sdb1
```

Should be written exactly like that. If you want to understand why type:

```
echo $USER
```

---

### Post by Gaurav_kataria on 2011-06-16
Hello there,

thanks you reply. when i tried to apply

$ sudo chmod 755 -v -R /media/lable/*

so it showed an error as

chmod: changing permission of file ' /media/___  ' Read only file system
failed to change mode of file ' /media/___  '  to 0755 (rwxr -xr -x)

so what to do now..
reply soon :)

---

### Post by Gaurav_kataria on 2011-06-18
I tried a lot of things do over come this problem please anyone help me.. :/

---

