---
title: "Read-only file system"
date: 2010-11-15
forum: General Help
---

### Post by pnw on 2010-11-15
hello,

I've recently been getting weird crashes on my ubuntu system. It seems to start of with not being able to open programs, but i had a open terminal so i tried to open the programs through that:

i've changed my username to "me" and my computer name to "mycomputer", not really sure why it just seemed that I should when I started writing this...

```

me@mycomputer:~$ chromium-browser
Failed to create temp directory for chroot: Read-only file system

```I tried the mkdir command

```
me@mycomputer:~$ mkdir /test/
mkdir: cannot create directory `/test/': Read-only file system
me@mycomputer:~$ sudo mkdir /test/
[sudo] password for me: 
sudo: Can't open /var/lib/sudo/me/1: Read-only file system
mkdir: cannot create directory `/test/': Read-only file system

```I found I was able to open the gnome calculator, but it had to be force quit. i opened it from terminal
```

me@mycomputer:~$ gcalctool 

(process:7444): Gtk-CRITICAL **: set_table: assertion `buffer->tag_table == NULL' failed
^C
me@mycomputer:~$ 
```I just noticed my computer was at running at 100% cpu (I have System Monitor on my gnome panels) i am unable to open the System Monitor application, so i ran the "top" command

> me@mycomputer:~$ top

top - 21:07:22 up  4:25,  4 users,  load average: 2.34, 2.56, 2.58
Tasks: 194 total,   3 running, 188 sleeping,   0 stopped,   3 zombie
Cpu(s): 66.8%us, 33.1%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.0%hi,  0.2%si,  0.0%st
Mem:   2059744k total,  1946452k used,   113292k free,   372360k buffers
Swap:  1999868k total,     3188k used,  1996680k free,   492168k cached

  PID  USER   PR   NI  VIRT   RES  SHR    S  %CPU %MEM     TIME+     COMMAND            
 4861 me      20   0   28300 4496 3716   R     93     0.2       18:29.07    gvfsd-http         
 4592 me      20   0   34820 5480 4236   R     84     0.3       55:50.49    gvfsd-smb          
 2836 me      20   0   333m  67m  31m   S      4      3.3       2:47.72      rhythmbox I don't know what gvfsd-smb & gvfsd-http but they are staying in the range of 80% and 95% of my cpu switching around of which one is on top. 

I am still able to explore the / file system except every file seems to be only have read-only permissions for example, a photo's permissions (under properties) are:

> 

Owner: Me - My Name
Acess: Read and write

Group: me
Access: Read-only

Others
Access: Read-only

when i try to change the permissions for "me" i get this:

> 

The permissions could not be changed.

Sorry, could not change the permissions of "1920-x-1200.jpg": Error setting permissions: Read-only file system

My fear is my hard drive has failed and i'm going to have to send it off (for the second time), it shouldn't cost me anything, but it would me a massive effort to get both widows and ubuntu systems back to how they are now. I'm posting this in vain hope that it isn't that and there is something I can do.

Thanks

EDIT: also another weird symptom is the search box in firefox has stopped working.

---

### Post by galvatron408 on 2010-11-15
Linux will remount your drive "read only" when some problem is detected. Look in your /etc/fstab and you might even see something like "errors=remount-ro"

You can usually find out what happened if you look in /var/log/messages.

So, what does /var/log/messages say?

---

### Post by SeijiSensei on 2010-11-15
I'd start by booting from a Live CD, opening a terminal, and running "sudo fsck /dev/sda2" or whichever partition has your Linux filesystem installed.  If Linux finds a filesystem has errors, it will only mount it read-only.  It's important to fix the filesystem first if you can.  If you don't know which partition has Linux installed, you should try "sudo fdisk -l /dev/sda" to show all the partitions on your drive and their partition types.

Note that you must do this from a Live CD.  Do not try to fix the filesystem while it is mounted in Linux.

---

