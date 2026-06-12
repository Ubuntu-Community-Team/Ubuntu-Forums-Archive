---
title: "Stupid Permissions"
date: 2011-08-21
forum: General Help
---

### Post by kensclark15 on 2011-08-21
Every time I download something all the files and folders have root permission. So I can't do anything. I can change them all to have permission for me but it takes like an hour for one download. How do I make EVERYTHING accessible to me?

---

### Post by e79 on 2011-08-21
In which folder are you downloading your files ?

You can check the permissions and owner of this folder with :
```
ls -alh /foldername
```Where folder is the name of that folder your are using for downloads

The result should look like :
```
drwxr-xr-x  5 testuser testuser 4.0K 2011-08-21 19:50 .
```'testuser' will be replaced by w/e username/group that is owner of this folder and assuming the folder is located in your /home directory the permission should look like the example.

To become owner of the folder if your are not the one, type :
```
sudo chown username /foldername
```Obvisouly replacing 'username' with yours.

If not sufficient to give access to all your file, cd into the folder and change owner for all files :
```
cd /foldername
```
```
sudo chown username *
```

Hope this help

---

### Post by kensclark15 on 2011-08-21
It still doesn't work. Look at this screen shot: [http://imageshack.us/photo/my-images/850/screenshotal.png/](http://imageshack.us/photo/my-images/850/screenshotal.png/)

---

### Post by ClientAlive on 2011-08-21
I don't have much experience with that particular issue but i do have an ebook that seems to have some basic information in it. I don't know if it'll let me but I can try to post some information from it here now so you can look at it. I'll then read through that part too and see if I can identify any thing(s) in there that seem useful. Sorry I can't be more help than that but I do hope it helps a little.

The book is called: "The Linux Command Line" by: William Shotts.

It can be downloaded here: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)  (for what it's worth).

It can also be read online here: [http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php)  -but I don't think that is the same as the book you download.

For the info you can read on the site it's chapter 7 "Permissions," for the ebook it pp. 107 - 126 in the reader.

Here's some information from it that may be useful. I don't think I can post that much here to be posting all of it. I'll read through that chapter again too though and see what I see.


> 
. . . In this chapter we are going to look at this essential part of system security and introduce the following commands:

&#9679; id &#8211; Display user identity
&#9679; chmod &#8211; Change a file's mode
&#9679; umask &#8211; Set the default file permissions
&#9679; su &#8211; Run a shell as another user
&#9679; sudo &#8211; Execute a command as another user
&#9679; chown &#8211; Change a file's owner
&#9679; chgrp &#8211; Change a file's group ownership
&#9679; passwd &#8211; Change a user's password

------------------

Edit:

The example here isn't the same as your problem but it looks pretty informative:

> 
Exercising Our Privileges

Now that we have learned how this permissions thing works, it's time to show it off. We
are going to demonstrate the solution to a common problem &#8212; setting up a shared
directory. Let's imagine that we have two users named &#8220;bill&#8221; and &#8220;karen.&#8221; They both
have music CD collections and wish to set up a shared directory, where they will each
store their music files as Ogg Vorbis or MP3. User bill has access to superuser
privileges via sudo.

The first thing that needs to happen is creating a group that will have both bill and
karen as members. Using the graphical user management tool, bill creates a group
called music and adds users bill and karen to it: . . .

. . . Next, bill creates the directory for the music files:

[bill@linuxbox ~]$ sudo mkdir /usr/local/share/Music
Password:

Since bill is manipulating files outside his home directory, superuser privileges are
required. After the directory is created, it has the following ownerships and permissions:

[bill@linuxbox ~]$ ls -ld /usr/local/share/Music
drwxr-xr-x 2 root root 4096 2008-03-21 18:05 /usr/local/share/Music

As we can see, the directory is owned by root and has 755 permissions. To make this
directory sharable, bill needs to change the group ownership and the group permissions
to allow writing:

[bill@linuxbox ~]$ sudo chown :music /usr/local/share/Music
[bill@linuxbox ~]$ sudo chmod 775 /usr/local/share/Music
[bill@linuxbox ~]$ ls -ld /usr/local/share/Music
drwxrwxr-x 2 root music 4096 2008-03-21 18:05 /usr/local/share/Music

So what does this all mean? It means that we now have a directory,
/usr/local/share/Music that is owned by root and allows read and write
access to group music. Group music has members bill and karen, thus bill and
karen can create files in directory /usr/local/share/Music. Other users can
list the contents of the directory but cannot create files there.

But we still have a problem. With the current permissions, files and directories created
within the Music directory will have the normal permissions of the users bill and
karen:

[bill@linuxbox ~]$ > /usr/local/share/Music/test_file
[bill@linuxbox ~]$ ls -l /usr/local/share/Music
-rw-r--r-- 1 bill bill 0 2008-03-24 20:03 test_file

Actually there are two problems. First, the default umask on this system is 0022 which
prevents group members from writing files belonging to other members of the group.
This would not be a problem if the shared directory only contained files, but since this
directory will store music, and music is usually organized in a hierarchy of artists and
albums, members of the group will need the ability to create files and directories inside
directories created by other members. We need to change the umask used by bill and karen to 0002 instead.

Second, each file and directory created by one member will be set to the primary group of
the user rather than the group music. This can be fixed by setting the setgid bit on the
directory:

[bill@linuxbox ~]$ sudo chmod g+s /usr/local/share/Music
[bill@linuxbox ~]$ ls -ld /usr/local/share/Music
drwxrwsr-x 2 root music 4096 2008-03-24 20:03 /usr/local/share/Music

Now we test to see if the new permissions fix the problem. bill sets his umask to
0002, removes the previous test file, creates a new test file and directory:

[bill@linuxbox ~]$ umask 0002
[bill@linuxbox ~]$ rm /usr/local/share/Music/test_file
[bill@linuxbox ~]$ > /usr/local/share/Music/test_file
[bill@linuxbox ~]$ mkdir /usr/local/share/Music/test_dir
[bill@linuxbox ~]$ ls -l /usr/local/share/Music
drwxrwsr-x 2 bill music 4096 2008-03-24 20:24 test_dir
-rw-rw-r-- 1 bill music 0 2008-03-24 20:22 test_file
[bill@linuxbox ~]$

Both files and directories are now created with the correct permissions to allow all
members of the group music to create files and directories inside the Music directory.
The one remaining issue is umask. The necessary setting only lasts until the end of
session and must be reset. In the next part of the book, we'll look at making the change to umask permanent.


---

### Post by e79 on 2011-08-21
Looking at your pic, can I assume your are trying to install OpenJDK for Linux ? Why aren't you using the repositories. it is simpler :

```
sudo apt-get install openjdk-6-jre
```

---

### Post by kensclark15 on 2011-08-21
Does anyone know how to install Java3D to Eclipse?

---

### Post by e79 on 2011-08-21
I don't know about that but you can still look here if its what you search for :

[http://sourceforge.net/projects/java3d-eclipse/develop](http://sourceforge.net/projects/java3d-eclipse/develop)

---

