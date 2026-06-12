---
title: "Locked files"
date: 2012-03-06
forum: General Help
---

### Post by asearle on 2012-03-06
Hi Everyone,

I have a network drive (an external hard-disk that connects to my router) that contains many files copied there at various times in the past from various profiles (both Windows and Linux).

Indeed, some files were copied from CD and (as such) have the delete option removed from their permissions.

However, I am now trying to clean up the drive and find that these files with the permissions blocked cannot be deleted.  I tried to change the permissions but found that I did not have permission to do this either.

Can anyone help me here?  Is there a way to delete them?  Or do I need to do something horribly drastic like reformat the drive?  Arrgghh!

Anyway, many thanks for any tips that you guys can give me.

Regards,
Alan Searle

Cologne, Germany

---

### Post by 23dornot23d on 2012-03-06
Easiest way I find is to do ...... sudo  ( gives you root privileges from the file manager )


sudo thunar

[IMG]http://img6.imageshack.us/img6/47/thunarroot.jpg[/IMG]

or

sudo nautilus

or

sudo dolphin



Depends what you have installed ..... and anyone else reading this .... this is dangerous
you can delete files that your system may need ..... so be careful .....

---

### Post by winh8r on 2012-03-06
try:

```
sudo chown -R asearle /path/to/directory
```

where asearle is your username on the machine.

The -R option will change ownership to you recursively throughout the named directory.

then just use 
```

sudo rm -r /path/to/directory
```



OR: you can just enter:

```
gksudo nautilus
```

and remove them that way, but be very careful when running nautilus as it gives you the ability to delete/move/alter just about everything on your system.

hope this helps

---

### Post by asearle on 2012-03-07
Hi guys,

Many thanks for these tips and, yes, on a physically connected drive this would certainly be the solution.

However, the files are on a Lacie Network Drive (i.e. an external hard disk connected to the network) and I find that when I start nautilus as administrator, it won't let me access my network.

I wanted to connect the network drive via usb but Lacie doesn't seem to allow this.

And I am a bit worried that files on a network drive may not be available/accessible for my local administrator.

Anyway, I'll try accessing them with a windows PC to see if windows more clunky security will let me delete those.

Many thanks,
Alan Searle

---

### Post by asearle on 2012-03-10
I solved this problem by logging on with windows and deleting the locked files via Windows.

It's rather ironic that Windows' technical weakness turned out to be an advantage.

Not ideal but I'm pleased to have it sorted out.

Regards,
Alan

---

