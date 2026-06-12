---
title: "Cant make a file executable"
date: 2011-06-16
forum: General Help
---

### Post by kanishkdudeja on 2011-06-16
I downloaded eclipse from the eclipse site..

i had to make the main eclipse file executable..

but i cant do that..

when i click on "Allow executing file as program"..the tick disappears in a second..

---

### Post by seawolf167 on 2011-06-16
In a terminal you can do this via

```
sudo chmod +x [I]/path/to/filename.extension
```

[/I]where you substitute in the correct path and file name

---

### Post by kanishkdudeja on 2011-06-16
what will be the extension for an executable file?

---

### Post by seawolf167 on 2011-06-16
The extension won't change or be added, it will just be flagged as executable - I just put *filename.extension* in case the file had an extension on it. If not, you don't have to worry about it

---

### Post by kanishkdudeja on 2011-06-16
ok done. still doesnt work..:(

---

### Post by seawolf167 on 2011-06-16
As in doesn't execute? What errors or output do you get? What were the exact commands you entered?

```
cd */path/to/filename*
sudo chmod +x *filename*
./*filename*
```

---

### Post by kanishkdudeja on 2011-06-16
```
kanishk@kanishk-Inspiron-1525:~$ cd /media
kanishk@kanishk-Inspiron-1525:/media$ cd Home
kanishk@kanishk-Inspiron-1525:/media/Home$ cd eclipse
kanishk@kanishk-Inspiron-1525:/media/Home/eclipse$ sudo chmod +x eclipse
[sudo] password for kanishk: 
kanishk@kanishk-Inspiron-1525:/media/Home/eclipse$ ./eclipse
bash: ./eclipse: Permission denied
kanishk@kanishk-Inspiron-1525:/media/Home/eclipse$ 
```

---

### Post by Topsiho on 2011-06-16
A user can only manipulate his/her files, in the /home/<your_name> directory. So using chmod etc. you can not do without using sudo, and the root password.

Topsiho

---

### Post by amauk on 2011-06-16
> **kanishkdudeja said:**
> I downloaded eclipse from the eclipse site..Any reason you're not using the software repositories?

---

### Post by seawolf167 on 2011-06-16
Try adding a *sudo *in front of the final command

```
sudo ./*filename
```*

---

### Post by seawolf167 on 2011-06-16
> **amauk said:**
> Any reason you're not using the software repositories?

+1 for this

```
sudo apt-get install eclipse
```

---

### Post by mcduck on 2011-06-16
> **kanishkdudeja said:**
> ```
kanishk@kanishk-Inspiron-1525:~$ cd /media
kanishk@kanishk-Inspiron-1525:/media$ cd Home
kanishk@kanishk-Inspiron-1525:/media/Home$ cd eclipse
kanishk@kanishk-Inspiron-1525:/media/Home/eclipse$ sudo chmod +x eclipse
[sudo] password for kanishk: 
kanishk@kanishk-Inspiron-1525:/media/Home/eclipse$ ./eclipse
bash: ./eclipse: Permission denied
kanishk@kanishk-Inspiron-1525:/media/Home/eclipse$ 
```
Is the file located on a non-linux filesystem (like FAT or NTFS)? You can't chnage the permisisons of files on those filesystems, as they lack support for ownerships and permissions as they are used on Unix & Linux operating systems.

Move the file to a Linux filesystem and you should be able to enable the execute permission. Or, better yet, use the package management to install Eclipse unless you have a specific reason why you'd need the latest version.

---

### Post by kanishkdudeja on 2011-06-16
@topsiho..as you can see ive used sudo and given the root password.

@amauk: i had downloaded eclipse pretty earlier, around an year back. so thought of using that only. plus i thought if i install it using the repositories it will take an additional 200 mb in my ubuntu system. so thought if i had it in a separate partition, it would be better so that i can use whenever i can and not install it everytime i install a new ubuntu system...although 200 mb is not as issue.

@seawolf:
it says
sudo: ./eclipse: command not found

---

### Post by kanishkdudeja on 2011-06-16
@mcduck..yes it is an ntfs filesystem...:(

---

### Post by seawolf167 on 2011-06-16
> **kanishkdudeja said:**
> @mcduck..yes it is an ntfs filesystem...:(

Didn't even think about this - I just assumed you were running from an ext3/4 formatted drive. I'd say the best way to proceed from here is to install the program from the repos, see my last post #11

---

### Post by kanishkdudeja on 2011-06-16
yeah..

thanks a lot everybody..cheers..:)

---

### Post by seawolf167 on 2011-06-16
Glad it got worked out :P

---

### Post by kanishkdudeja on 2011-06-16
lol yeah..:) :P

---

