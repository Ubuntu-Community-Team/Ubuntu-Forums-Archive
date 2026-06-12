---
title: "Samba and Symbolic Links"
date: 2011-09-03
forum: General Help
---

### Post by sxminister on 2011-09-03
I have one folder shared on Samba, everything is ok, and i can access it from windows clients with no problems.
 
My problem is that in that folder i have some symbolic links to other folders, and theese symbolic links don't show up on windows clients.
 
I've been reading in the web about adding these configuration settings on the [global] section
 
follow symlinks = yes
wide links = yes
unix extensions = no
 
have also placed the same settings on the share section, but none seams to work
 
Help is welcome :(

---

### Post by e79 on 2011-09-03
Have you tried :

[http://www.howtogeek.com/howto/16226/complete-guide-to-symbolic-links-symlinks-on-windows-or-linux/](http://www.howtogeek.com/howto/16226/complete-guide-to-symbolic-links-symlinks-on-windows-or-linux/)

Another question : What if you turn on the option to "Show hidden drives and folders" in your Windows installation, does that help ? If not, try to uncheck with the option 'Hide operating system files and folders" ?

Hope this helps

---

### Post by sxminister on 2011-09-03
My problem is not creating the symbolic links, those are fine and using linux terminal i can browse ok.
 
The problem is that the folder are inside a samba share, and on windows they don't show up.
 
Example
 
i have the folder /mnt/raid1/public
 
in this folder i have a 
 
media
games -> /mnt/usb1/games
 
On windows the share shows only the media folder and not the gamese

---

### Post by e79 on 2011-09-03
even if "Show hidden drives and folders" is turned on and "Hide operating system files and folders" is turned off in Windows ?

---

### Post by sxminister on 2011-09-03
> **e79 said:**
> even if "Show hidden drives and folders" is turned on and "Hide operating system files and folders" is turned off in Windows ?
 
Yes, changing that has no effect

---

### Post by e79 on 2011-09-03
Dumb question but is possible because your value are set to True/False instead of Yes/No in your smb.conf file as :

```

follow symlinks = yes
wide links = yes
unix extensions = no

```

Found at : [http://ubuntuforums.org/showthread.php?t=1439092](http://ubuntuforums.org/showthread.php?t=1439092)

---

### Post by sxminister on 2011-09-03
> **e79 said:**
> Dumb question but is possible because your value are set to True/False instead of Yes/No in your smb.conf file as :
 
```

follow symlinks = yes
wide links = yes
unix extensions = no

```
 
Found at : [http://ubuntuforums.org/showthread.php?t=1439092](http://ubuntuforums.org/showthread.php?t=1439092)
 
Sorry, error is on the thread post, my smb.conf is using yes just like you posted here

---

### Post by e79 on 2011-09-03
I dont' have any other clues at the moment to be honest but I'll keep searching and will let you know if I find anything.

---

### Post by brucehohl on 2011-09-03
See "man smb.conf".

follow symlinks (S)
This parameter allows the Samba administrator to stop smbd(8) from following symbolic links in a particular share. Setting this parameter to no prevents any file or directory that is a symbolic link from being followed (the user will get an error). This option is very useful to stop users from adding a        symbolic link to /etc/passwd in their home directory for  instance. However it will slow filename lookups down slightly.

This option is enabled (i.e.  smbd will follow symbolic links) by default.

THIS DOES WORK AS I DO USE THIS FEATURE.
BELOW IS SOME INFO FROM MY CONFIGURATION.
MAKE SURE FILE PERMISSIONS ARE NOT CAUSING YOUR PROBLEM.

My file share from /etc/samba/smb.conf
(Updated after Morbius1's post 10 below.)

[global] 
# Wide links allow Samba to follow symlinks to non-exported file
# system areas. Unix extension must be no to use wide links.i
unix extensions = no
wide links = yes

[hp-3500]
        path = /home/user1
        comment = hp-3500
        available = yes
        browseable = yes
        public = yes
        writable = yes
        map archive = no
        force user = user1

Here is what is in "path = /home/user1" which includes links (->):
user1@HP-3500:~$ ls -l /home/user1/
total 12
lrwxrwxrwx 1 user1 user1   11 2011-04-23 21:03 Books -> /data/Books
drwxr-xr-x 3 user1 user1 4096 2011-08-31 20:44 Desktop
lrwxrwxrwx 1 user1 user1   15 2010-09-11 23:26 Documents -> /data/Documents
drwxr-xr-x 2 user1 user1 4096 2011-08-29 20:44 Downloads
lrwxrwxrwx 1 user1 user1   11 2010-09-11 23:26 Music -> /data/Music
lrwxrwxrwx 1 user1 user1   14 2010-09-11 23:26 Pictures -> /data/Pictures
drwxr-xr-x 2 user1 user1 4096 2011-05-10 20:29 Public
lrwxrwxrwx 1 user1 user1   15 2010-09-11 23:27 Wallpaper -> /data/Wallpaper

This shows the ownership and permission on the linked directory and files:

user1@HP-3500:~$ ls -l /data | grep Books
drwxr-xr-x  2 user1 user1  4096 2011-06-28 20:52 Books

user1@HP-3500:~$ ls -l /data/Wallpaper/
total 6584
-rw-r--r-- 1 user1 user1  262349 2009-05-25 14:06 Atlantic_Ocean_1280x1024.jpg
-rw-r--r-- 1 user1 user1  488966 2007-10-29 19:35 cliff_1440x900.jpg

It will work!

---

### Post by Morbius1 on 2011-09-03
Following symbolic links in Samba was effectively turned off by default some time ago because of a security risk: [http://www.samba.org/samba/news/symlink_attack.html](http://www.samba.org/samba/news/symlink_attack.html)

Your addition should have fixed it ( assuming you ignore the possible security problem ):
> follow symlinks = yes
wide links = yes
unix extensions = noYou did restart samba, right?
```
sudo service smbd restart
```It's possible as stated above that the permissions on /mnt/usb1/games could be the problem. If it's sitting there as 0700 and you are allowing guest access then the link is invisible.

If all else fails don't use symlinks use bind instead:
```
sudo mount --bind /mnt/usb1/games /mnt/raid1/public/mediagames
```You can set that up as an Upstart job to run at every boot.

EDIT: Should have told you how to undo the bind:
```
 sudo umount /mnt/raid1/public/mediagames
```

---

### Post by e79 on 2011-09-05
Nice info there **Morbius1**, didn't know about 'bind', thanks for sharing.

---

