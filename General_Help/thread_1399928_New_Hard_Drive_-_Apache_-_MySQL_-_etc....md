---
title: "New Hard Drive - Apache - MySQL - etc..."
date: 2010-02-06
forum: General Help
---

### Post by dv310p3r on 2010-02-06
I've got a new installation of Ubuntu 9.10. I've got Apache, MySQL and PHP all setup and working properly. My issue is this. The Ubuntu installation is on my 160 GB hard drive. I also have a 1 TB drive that I just put in. Here's what I want to to with the new drive.

 - I want all my development projects through apache to be on that drive. So basically the /var/www/ folder. I need to be able to access and edit these files from my windows machine for editing html, php files, etc...
 - I want to create some new folders on that drive so that I can store and use the files from my windows machine, things like my images library, web templates, and other files I use for development.
 - I would like to have the MySQL database files on this drive as well.

Basically I don't mind if all 160 GB of the main drive never get touched. I just want all the data on the 1 TB drive. This way I only need to backup one drive to keep all my stuff in case of emergency. Or if I needed to I can pull the drive and put into new machine to at least get the data.

Thanks for any help.

---

### Post by nc_jed on 2010-02-06
> **dv310p3r said:**
> 
 - I want all my development projects through apache to be on that drive. So basically the /var/www/ folder. I need to be able to access and edit these files from my windows machine for editing html, php files, etc...
 - I want to create some new folders on that drive so that I can store and use the files from my windows machine, things like my images library, web templates, and other files I use for development.

- Sounds like you need a symlink from 160 GB /var/www/ to 1TB drive (destination folder of your choice.
- I think WebDAV or Samba is what you may want to do here.

> **dv310p3r said:**
> 
 - I would like to have the MySQL database files on this drive as well.


Can't help here.  Probably a matter of crating a new DB on the drive and importing existing DB to it.  I'm sure there's a config setting to set the default location for DB creates.  If not, more symlinks!

Hope this helps.
- Jed

---

### Post by sandyd on 2010-02-06
> **dv310p3r said:**
> I've got a new installation of Ubuntu 9.10. I've got Apache, MySQL and PHP all setup and working properly. My issue is this. The Ubuntu installation is on my 160 GB hard drive. I also have a 1 TB drive that I just put in. Here's what I want to to with the new drive.

 - I want all my development projects through apache to be on that drive. So basically the /var/www/ folder. I need to be able to access and edit these files from my windows machine for editing html, php files, etc...
 - I want to create some new folders on that drive so that I can store and use the files from my windows machine, things like my images library, web templates, and other files I use for development.
 - I would like to have the MySQL database files on this drive as well.

Basically I don't mind if all 160 GB of the main drive never get touched. I just want all the data on the 1 TB drive. This way I only need to backup one drive to keep all my stuff in case of emergency. Or if I needed to I can pull the drive and put into new machine to at least get the data.

Thanks for any help.
1. Create one EXT3 partition on the drive. this will be used for /var/www . You can mount this in windows using fs-driver.
2. Create an NTFS volume for the images/windows stuff.

run```

sudo blkid

```In the output, one of the lines should end with "TYPE="ext3"
Copy what is says in the first colum (EXAMPLE: /dev/sda1)
type this in
```

sudo mkdir /media/disk-100
sudo mount -t ext3 *stuff you just coppied* /media/disk-100

```Then copy all of the stuff in /var/www to /media/disk-100
Not sure if this is necessary, but
```

sudo mv /var/www /var/www.bak
sudo mkdir /var/www

```Then using the output from blkid again,
Copy the UUID section. (only the stuff between the quotes. For example, mine is
```

e8446c84-064e-4df6-b757-36a1e591c911

```Put that into a new line at the bottom of /etc/fstab

It should look like this
```

UUID=*uuid*_you_just_copied  /var/www               ext3    errors=remount-ro 0       1

```which, when you copy your UUID in, should look like
```
 UUID=e8446c84-064e-4df6-b757-36a1e591c911 /var/www               ext3    errors=remount-ro 0       1
``` (except for the UUID of course"

To test if you did everything correctly, run```
 sudo mount -a
ls /var/www

```that will hopefully list your files
For the other partition,
```

sudo ntfs-config
```should do the trick

---

### Post by dv310p3r on 2010-02-06
Thanks for the awesome reply. I have however decided to eliminate the 160 GB drive and just reinstall 8.04 LTS Server 64 Bit onto the 1 TB directly. That should eliminate a huge headache. 

Anyone want a 160 GB Drive?

---

### Post by sandyd on 2010-02-06
> **dv310p3r said:**
> Thanks for the awesome reply. I have however decided to eliminate the 160 GB drive and just reinstall 8.04 LTS Server 64 Bit onto the 1 TB directly. That should eliminate a huge headache. 

Anyone want a 160 GB Drive?
sigh....

Do you know ANYTHING at all about data security?
That your hard drive could possibly contain credit card info, bank info, and personal info even if you de partition / format it?

---

### Post by dv310p3r on 2010-02-06
Actually, I most certainly do. I would rewrite the drive to 0's a few times, or shred it using some app before letting it go. I don't think I have anything of any real importance on that thing anyways. Besides, no one wants my identity, lol, they could only help my credit score.

Thanks for caring though.

Great to see pretty ladies that know so much about Linux, hopefully my daughter will take such an interest.

---

