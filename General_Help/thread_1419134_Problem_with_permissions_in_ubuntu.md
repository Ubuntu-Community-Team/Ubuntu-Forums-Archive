---
title: "Problem with permissions in ubuntu"
date: 2010-03-01
forum: General Help
---

### Post by aviramof on 2010-03-01
how can check that i have full permisions on anything should i set my self as root?
there are a lot of files it said your not the owner so you can't change but if i'm not the owner then who is?
there is no one eles but me.

thanks in advance.

---

### Post by Danawar on 2010-03-01
What are these files you are trying to change may i ask?

-Dan

---

### Post by namluc on 2010-03-01
keep this saved in a txt file, i find it is a recurring problem


i got my usb drive to work, combining sugestions from several threads, running hippo version.
first i did
sudo bash to become root

cd to media my drive was just labeled disk


sudo chown -R (username) disk
sudo chmod 777 disk

and now i own the drive and able to copy to it

(i found this a while ago myself!)

so for me as my drives are called big, small and blue i might


sudo chown -R luke blue
sudo chmod 777 blue

---

### Post by joeknoodle on 2010-03-01
delete

---

### Post by namluc on 2010-03-01
I've just seen a forum entry that says that this advice i gave was very bad, 

[http://ubuntuforums.org/showthread.php?t=1387822](http://ubuntuforums.org/showthread.php?t=1387822)

could someone explain the correct protocol, and why i've never had any problems with it.

---

### Post by nothingspecial on 2010-03-01
> **aviramof said:**
> how can check that i have full permisions on anything should i set my self as root?
there are a lot of files it said your not the owner so you can't change but if i'm not the owner then who is?
there is no one eles but me.

thanks in advance.

You shouldn`t set yourself as root, you should use sudo.

> **namluc said:**
> I've just seen a forum entry that says that this advice i gave was very bad, 

[http://ubuntuforums.org/showthread.php?t=1387822](http://ubuntuforums.org/showthread.php?t=1387822)

could someone explain the correct protocol, and why i've never had any problems with it.

Because he did it from the live cd /media/disk was the root partition of his main install. Chmodding that to 777 means he hosed his system.

That is one reason why you should use sudo.

See [[COLOR="Magenta"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=716201")

---

### Post by darolu on 2010-03-01
> **aviramof said:**
> how can check that i have full permisions on anything should i set my self as root?
there are a lot of files it said your not the owner so you can't change but if i'm not the owner then who is?
there is no one eles but me.

thanks in advance.

Read the links nothingspecial posted carefully.

I don't know if this is what you were asking but if you want to check what files do you own or who owns other files open a terminal and type "ls -l" at the desired directory.
```
me@ubuntupc:~/$ ls -l
total 0
-rw-r--r-- 1 me   me   0 2010-03-01 16:26 file1
-rwx------ 1 root root 0 2010-03-01 16:26 file2
-rwxr-xr-- 1 me   me   0 2010-03-01 16:26 file3
-r--r--r-- 1 root me   0 2010-03-01 16:26 file4
```
Learn more at: [http://en.wikipedia.org/wiki/File_system_permissions](http://en.wikipedia.org/wiki/File_system_permissions)

---

### Post by namluc on 2010-03-02
If i did help you hose your system OP, many apologies.

---

### Post by aviramof on 2010-03-02
the big question here is how can i take owenrship on a file even if i'm so call not the "owner" which i am i'm the only user on this personal computer.

thanks in advance.

---

### Post by QLee on 2010-03-02
> **aviramof said:**
> the big question here is how can i take owenrship on a file even if i'm so call not the "owner" which i am i'm the only user on this personal computer 

Don't confuse "ownership" of a file with "ownership" of a computer.

You're probably new with GNU/Linux operating systems and could benefit from reading a bit and understanding.

Try one of these links or one of the many others you can find for an explanation, come back and ask specific questions for anything you don't fully understand:

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/permissions#targetaudience](http://www.psychocats.net/ubuntu/permissions#targetaudience)
[http://www.tuxfiles.org/linuxhelp/filepermissions.html](http://www.tuxfiles.org/linuxhelp/filepermissions.html)

---

