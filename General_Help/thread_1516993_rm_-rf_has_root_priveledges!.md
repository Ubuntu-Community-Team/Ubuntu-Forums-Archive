---
title: "rm -rf has root priveledges??!?"
date: 2010-06-24
forum: General Help
---

### Post by J V on 2010-06-24
On directories, nothing I seem to do is able to stop an rm -rf command...

mkdir test
chmod 000 test
sudo chown root:root test
rm -rf test

And it's gone...

How can I stop this? I'm writing a script to delete everything in ~ when a user logs off, but I need to set certain files/folders off limits (Settings, the script itsself, etc)

---

### Post by doas777 on 2010-06-24
not sure why you are getting that result, though it would help if your terminal headers showed in your output. 

regardless, setting the permissions as such to perform the task is probably not the best approach, since they would have to be reset before the next login. 
if that is the case, your script would have to set the permissions on the folders you want to keep, delete everything, and then set those permissions back.

if that is the case, then it makes more sense to explicitly call the rm -rf for the folder you specifically want to delete, rather than setting the permissions on the ones you want to keep. a good bit safer as well.

---

### Post by Brandon Williams on 2010-06-24
With standard rwx permission access, you can't set an individual file as off limits, because you only need access to the directory in order to delete items from within the directory. For example, if want to prevent ~/dir/file from being deleted, you have to turn off write access of ~/dir, which prevents deletion of any file in ~/dir, not just the specific ones you want.

Look into extended access control. I don't use it myself, so I can't tell you exactly what to do, but I know that it provides the more fine-grained control that you're looking for. [Here](http://manpages.ubuntu.com/manpages/jaunty/man5/attr.5.html) is a good place to start.

Alternatively, consider using find to manage the deletions instead of the recursive rm call. With find, you may be able to filter out the specific files/directories you want to leave untouched.

---

### Post by imbjr on 2010-06-24
> **J V said:**
> On directories, nothing I seem to do is able to stop an rm -rf command...

mkdir test
chmod 000 test
sudo chown root:root test
rm -rf test

And it's gone...

How can I stop this? I'm writing a script to delete everything in ~ when a user logs off, but I need to set certain files/folders off limits (Settings, the script itsself, etc)

I just tried it and sure enough the directory is gone. All I can think of is that the containing directories rights may have some bearing on this.

---

### Post by 3Miro on 2010-06-24
I just tried this:

```
 miro@miro-laptop:~/Test$ ls -al
total 16
drwxr-xr-x  2 miro miro  4096 2010-06-24 12:38 .
drwx------ 48 miro miro 12288 2010-06-24 12:36 ..
miro@miro-laptop:~/Test$ touch some_file
miro@miro-laptop:~/Test$ sudo chown root:root some_file 
miro@miro-laptop:~/Test$ sudo chmod 000 some_file 
miro@miro-laptop:~/Test$ ls -al
total 28
drwxr-xr-x  2 miro miro  4096 2010-06-24 12:38 .
drwx------ 48 miro miro 12288 2010-06-24 12:36 ..
----------  1 root root     0 2010-06-24 12:38 some_file
miro@miro-laptop:~/Test$ rm -fr some_file 
miro@miro-laptop:~/Test$ ls -al
total 16
drwxr-xr-x  2 miro miro  4096 2010-06-24 12:39 .
drwx------ 48 miro miro 12288 2010-06-24 12:36 ..
miro@miro-laptop:~/Test$ 

```
:confused: :shock: :shock: :shock:

WTF I am scared now, how is this possible? Does it remember the sudo authentication and keeps working with it? Why is rm capable of removing a 000 root file? I tried it for 644 too and it also removed the file. It also removes 000 files owned by me.

---

### Post by sisco311 on 2010-06-24
> **3Miro said:**
> 
THIS IS A MAJOR BUG!

It's not a BUG. Without the sticky bit set, any user with write and execute permissions for the directory can rename or delete contained files, regardless of owner.

---

### Post by 3Miro on 2010-06-24
> **sisco311 said:**
> It's not a BUG. Without the sticky bit set, any user with write and execute permissions for the directory can rename or delete contained files, regardless of owner.

So basically the directory permissions supersede the file ones. This is definitely odd.

---

### Post by J V on 2010-06-24
I think I found it...

It only throws a permissions error if the folder permissions are set AND theres something in them...

This could be a security risk (Someone could delete an empty folder someone set up and then make a new one with more lenient permissions)

```
j@jubuntu:~/tfol$ mkdir test
j@jubuntu:~/tfol$ touch test/test
j@jubuntu:~/tfol$ sudo chown root:root test
j@jubuntu:~/tfol$ sudo chmod 555 test
j@jubuntu:~/tfol$ rm -rf test
rm: cannot remove `test/test': Permission denied
j@jubuntu:~/tfol$ sudo rm -f test/test
j@jubuntu:~/tfol$ ls
test
j@jubuntu:~/tfol$ rm -rf test
j@jubuntu:~/tfol$ ls
j@jubuntu:~/tfol$ 
```Unfortunately, setting the sticky bit doesn't help...
```
j@jubuntu:~/tfol$ mkdir test
j@jubuntu:~/tfol$ touch test/test
j@jubuntu:~/tfol$ chmod 1555 test/test
j@jubuntu:~/tfol$ rm -rf test
j@jubuntu:~/tfol$ ls
j@jubuntu:~/tfol$ 
```

---

### Post by doas777 on 2010-06-24
that kinda makes sense. since you have write on ~, and test is in ~, test is using ~'s permissions, whereas all files within test get the 000. afterall write on a folder grants you the ability to write contents to that dir, not the dir itself.

---

### Post by Chame_Wizard on 2010-06-24
:o rm -rf?Good luck ,if you want to destroy everything.

---

### Post by J V on 2010-06-24
> **doas777 said:**
> that kinda makes sense. since you have write on ~, and test is in ~, test is using ~'s permissions, whereas all files within test get the 000. afterall write on a folder grants you the ability to write contents to that dir, not the dir itself.So you're not allowed to change anything in a directory, just delete everything in it... right, I get it...

Also, when someone makes a folder that *is* locked down, but doesn't put anything in it yet, someone can just walk in and delete it, replace it with one that's got permissions more to their liking...

Yes, I totally see the logic in this...

Especially seeing as the sticky bit is broken... The only use in a default Linux system for a sticky bit is to stop people from deleting other users files from /tmp. Seeing as anyone can just delete all of /tmp, it might as well not exist!

---

### Post by bodhi.zazen on 2010-06-24
> **J V said:**
> On directories, nothing I seem to do is able to stop an rm -rf command...

mkdir test
chmod 000 test
sudo chown root:root test
rm -rf test

And it's gone...

How can I stop this? I'm writing a script to delete everything in ~ when a user logs off, but I need to set certain files/folders off limits (Settings, the script itsself, etc)

I believe you need to review linux permissions.

> bodhi@ufbt:~$ ls -l /mnt
total 0

bodhi@ufbt:~$ sudo mkdir /mnt/test
[sudo] password for bodhi:

bodhi@ufbt:~$ touch /mnt/test/foo                             
touch: cannot touch `/mnt/test/foo': Permission denied

bodhi@ufbt:~$ sudo !!                                         
sudo touch /mnt/test/foo

bodhi@ufbt:~$ ls -l /mnt                                      
total 4
drwxr-xr-x 2 root root 4096 2010-06-24 11:24 test

bodhi@ufbt:~$ ls -l /mnt/test                                 
total 0
-rw-r--r-- 1 root root 0 2010-06-24 11:24 foo

bodhi@ufbt:~$ rm -rf /mnt/test                                
rm: cannot remove `/mnt/test/foo': Permission denied

bodhi@ufbt:~$ rm -rf /mnt/test/foo                            
rm: cannot remove `/mnt/test/foo': Permission denied

bodhi@ufbt:~$ sudo rm /mnt/test/foo                          
bodhi@ufbt:~$ rm -rf /mnt/test                                
rm: cannot remove directory `/mnt/test': Permission denied

Since you are the owner of ~ , and since you have rwx access to ~, and since you do not have the sticky bit set on ~ , you can delete files in ~ even if you are not the owner.

This does not mean you can simply delete anything on the system.

---

### Post by doas777 on 2010-06-24
> 
...
bodhi@ufbt:~$ sudo !!                                         
sudo touch /mnt/test/foo
...


does that line do what i think it does? most cool. you learn something every day.

---

### Post by sisco311 on 2010-06-24
> **doas777 said:**
> does that line do what i think it does? most cool. you learn something every day.

```
man bash | less +/"Event Designators"
```

---

### Post by doas777 on 2010-06-24
> **sisco311 said:**
> ```
man bash | less +/"Event Designators"
```
thank you. very enlightening. I never thought of manipulating the history that way.

---

### Post by J V on 2010-06-24
Does the owner of a folder with a sticky bit have the right to delete the folder even if other users have stuff inside it?

Cause at the moment that's the only explanation for the test I'm seeing here...

scenario 1: I own the folder, can delete both folder and file belonging to someone else```
j@jubuntu:~/tfol$ mkdir test
j@jubuntu:~/tfol$ chmod 1777 test
j@jubuntu:~/tfol$ touch test/test
j@jubuntu:~/tfol$ sudo chown root:root test/test
j@jubuntu:~/tfol$ rm -rf test
j@jubuntu:~/tfol$ ls
```scenario 2: I own the file, can delete (And can delete the empty folder afterwards essentially)```

j@jubuntu:~/tfol$ mkdir test
j@jubuntu:~/tfol$ chmod 1777 test
j@jubuntu:~/tfol$ touch test/test
j@jubuntu:~/tfol$ sudo chown root:root test
j@jubuntu:~/tfol$ rm -rf test
j@jubuntu:~/tfol$ ls
```scenario 3: Don't own folder or file```

j@jubuntu:~/tfol$ mkdir test
j@jubuntu:~/tfol$ chmod 1777 test
j@jubuntu:~/tfol$ touch test/test
j@jubuntu:~/tfol$ sudo chown root:root test
j@jubuntu:~/tfol$ sudo chown root:root test/test
j@jubuntu:~/tfol$ rm -rf test
rm: cannot remove `test/test': Operation not permitted
```I'm missing the thought process here...

These permissions seem completely arbitrary... could someone explain exactly what the machine is doing step by step, because this doesn't make sense...

---

### Post by bodhi.zazen on 2010-06-24
It depends on ownership of tfol , not test.

```
bodhi@ufbt:~$ mkdir tfol
                                      
bodhi@ufbt:~$ sudo chown root.root tfol                       
bodhi@ufbt:~$ ls -la | grep tfol                              
drwxr-xr-x  2 root  root   4096 2010-06-24 12:53 tfol

bodhi@ufbt:~$ sudo mkdir tfol/test                     
       
bodhi@ufbt:~$ ls -la tfol                                     
total 8
drwxr-xr-x  3 root  root   4096 2010-06-24 12:53 .
drwxr-x--- 31 bodhi bodhi 12288 2010-06-24 12:53 ..
drwxr-xr-x  2 root  root   4096 2010-06-24 12:53 test

bodhi@ufbt:~$ rm -rf tfol/test                               
rm: cannot remove directory `tfol/test': Permission denied

bodhi@ufbt:~$ sudo chown bodhi.bodhi tfol                          

bodhi@ufbt:~$ ls -la tfol                                     
total 8
drwxr-xr-x  3 bodhi bodhi  4096 2010-06-24 12:54 .
drwxr-x--- 31 bodhi bodhi 12288 2010-06-24 12:54 ..
drwxr-xr-x  2 root  root   4096 2010-06-24 12:53 test

bodhi@ufbt:~$ ls -la | grep tfol                              06/24/10 12:54 PM
drwxr-xr-x  3 bodhi bodhi  4096 2010-06-24 12:54 tfol

bodhi@ufbt:~$ rm -rf tfol/test                                06/24/10 12:54 PM

bodhi@ufbt:~$ ls -la tfol                                     06/24/10 12:54 PM
total 4
drwxr-xr-x  2 bodhi bodhi  4096 2010-06-24 12:54 .
drwxr-x--- 31 bodhi bodhi 12288 2010-06-24 12:54 ..
```So if I have rw access on tfol, as owner, group, or other permissions (including I believe ACL), I can delete at will,unless I set the sticky bit on tofl, and then I can only delete what I own in tfol.

Now with sticky bit set / unset :

```
[COLOR=darkred]# SET STICKY BIT
bodhi@ufbt:~$ sudo chmod 1770 tfol                            

bodhi@ufbt:~$ ls -la tfol                                     

total 4
drwxrwx--T  2 root  bodhi  4096 2010-06-24 12:59 .
drwxr-x--- 31 bodhi bodhi 12288 2010-06-24 12:59 ..

bodhi@ufbt:~$ sudo mkdir tfol/test                            

bodhi@ufbt:~$ ls -la tfol                                     
total 8
drwxrwx--T  3 root  bodhi  4096 2010-06-24 13:00 .
drwxr-x--- 31 bodhi bodhi 12288 2010-06-24 13:00 ..
drwxr-xr-x  2 root  root   4096 2010-06-24 13:00 test

bodhi@ufbt:~$ rm -rf tfol/test                                
rm: cannot remove directory `tfol/test': Operation not permitted[/COLOR]

[COLOR=navy]# REMOVE STICKY BIT
bodhi@ufbt:~$ sudo chmod 0777 tfol                            

bodhi@ufbt:~$ ls -la tfol                                     
total 8
drwxrwxrwx  3 root  bodhi  4096 2010-06-24 13:00 .
drwxr-x--- 31 bodhi bodhi 12288 2010-06-24 13:00 ..
drwxr-xr-x  2 root  root   4096 2010-06-24 13:00 test

bodhi@ufbt:~$ rm -rf tfol/test                               

bodhi@ufbt:~$ ls -l tfol                                      
total 0[/COLOR]
```[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

---

### Post by bodhi.zazen on 2010-06-24
Now you try it, set the sticky bit on ftol, make a directory test, make test owned by root:j (assuming your user name is "j").

chmod test to 770

you will not be able to delete tfol/test

Now remove the stiky bit on tfol

Now you can remove tfol/test

Permissions seem arbitrary when you do not understand them.

---

### Post by J V on 2010-06-24
Well I understand this, this follows the logic.

What I'm confused about is why the file (Not directory) inside tfol/test/, depending on permissions of both tfol/test and itsself (tfol/test/test) may or may not inhibit the deletion of the tfol/test directory. (As shown in the scenarios, it only stops deletion when both the directory and file are owned by root)

Does this mean that when checking for permissions, the system only checks one level into the tree? Because if:

```
j@jubuntu:~/tfol$ ls -l
total 12
drwxr-xr-T 1 j j 0 2010-06-24 21:37 test
j@jubuntu:~/tfol$ ls -l test
total 12
-rw-r--r-- 1 root root 0 2010-06-24 21:37 test

```Then I can delete both of them. Why? Shouldn't it check to see weather I have permission to delete the file (Which, according to the sticky bit, I don't)

---

### Post by bodhi.zazen on 2010-06-24
> **J V said:**
> Well I understand this, this follows the logic.

What I'm confused about is why the file (Not directory) inside tfol/test/, depending on permissions of both tfol/test and itsself (tfol/test/test) may or may not inhibit the deletion of the tfol/test directory. (As shown in the scenarios, it only stops deletion when both the directory and file are owned by root)

Does this mean that when checking for permissions, the system only checks one level into the tree? Because if:

```
j@jubuntu:~/tfol$ ls -l
total 12
drwxr-xr-T 1 j j 0 2010-06-24 21:37 test
j@jubuntu:~/tfol$ ls -l test
total 12
-rw-r--r-- 1 root root 0 2010-06-24 21:37 test

```Then I can delete both of them. Why? Shouldn't it check to see weather I have permission to delete the file (Which, according to the sticky bit, I don't)

I am not following what you are asking with that.

If it have a directory, tfol, which is a sticky bit, the "sticky" affect only applies to the contents of tfol

If I have a directory, test, in tfol, and the sticky bit is NOT set on tfol/test , I can delete things in tfol/test/* as long as I have rw access to them, ownership does not matter.

```
[COLOR=darkred]# Sticky bit is set on tfol
bodhi@ufbt:~$ ls -l | grep tfol
drwxrwx--T 3 root  bodhi 4096 2010-06-24 13:51 tfol[/COLOR]

[COLOR=blue]# no sticky bit on tfol/test
bodhi@ufbt:~$ ls -l tfol
total 4
drwxrwx--- 2 root bodhi 4096 2010-06-24 13:52 test

bodhi@ufbt:~$ sudo touch tfol/test/file[/COLOR][COLOR=blue]
bodhi@ufbt:~$ sudo chown root.bodhi tfol/test/file[/COLOR]
[COLOR=blue] bodhi@ufbt:~$ sudo chmod 660 tfol/test/file                   
bodhi@ufbt:~$ rm tfol/test/file                               
rm: remove regular empty file `tfol/test/file'? y[/COLOR]

[COLOR=green]# Set sticky bit on tfol/test
bodhi@ufbt:~$ sudo touch tfol/test/file                       
bodhi@ufbt:~$ sudo chown root.bodhi tfol/test/file            
bodhi@ufbt:~$ sudo chmod 660 tfol/test/file                   
bodhi@ufbt:~$ sudo chmod 1770 tfol/test/                      
bodhi@ufbt:~$ rm tfol/test/file                               
rm: remove regular empty file `tfol/test/file'? y
rm: cannot remove `tfol/test/file': Operation not permitted
bodhi@ufbt:~$[/COLOR]
```Permissions are one directory deep, the do not apply to subdirectories

---

### Post by J V on 2010-06-24
Ah, but the test directory in tfol has a sticky bit set, yet with the previously posted settings I can delete test and it's contents.

---

### Post by bodhi.zazen on 2010-06-24
> **J V said:**
> Ah, but the test directory in tfol has a sticky bit set, yet with the previously posted settings I can delete test and it's contents.

I still do not follow what you are asking, can you post the details ?

Please use ls -l to show the permissions of tfol , test, and the file you are asking about as well as the exact rm -rf command you use.

---

### Post by sisco311 on 2010-06-24
> **J V said:**
> Ah, but the test directory in tfol has a sticky bit set, yet with the previously posted settings I can delete test and it's contents.

The owner of the directory is not affected by the sticky bit, if the owner has write and execute permissions he is allowed to remove and rename any file from the directory.

---

### Post by J V on 2010-06-24
```
j@jubuntu:~$ ls -l | grep tfol
drwxr-xr-x  2 j j             4096 2010-06-24 22:28 tfol
j@jubuntu:~/tfol$ mkdir test
j@jubuntu:~/tfol$ chmod 1777 test [COLOR=Blue]# Notice the sticky bit[/COLOR]
j@jubuntu:~/tfol$ sudo touch test/file
j@jubuntu:~/tfol$ ls -l test
total 12
-rw-r--r-- 1 root root 0 2010-06-24 22:30 file [COLOR=Blue]# Owned by root, NOT me, I shouldn't have permission to delete because of sticky bit[/COLOR]
j@jubuntu:~/tfol$ rm -rf test
j@jubuntu:~/tfol$ ls -l
total 0 [COLOR=Blue]# Boom[/COLOR]
```@ Sisco, thanks. I guess this clears it all up... Now just to figure out how to use it :)

Edit: One more question:
```
j@jubuntu:~/tfol$ sudo mkdir test
j@jubuntu:~/tfol$ sudo mkdir test/test
j@jubuntu:~/tfol$ rm test/test
j@jubuntu:~/tfol$ rmdir test/test
rmdir: failed to remove `test/test': Permission denied [COLOR=Blue]# Expected[/COLOR]
j@jubuntu:~/tfol$ rm -rf test
rm: cannot remove directory `test/test': Permission denied [COLOR=Blue]# Ehm... So I can't remove these empty folders owned by root without deleting the folder above them? Taking a lot of time to fix afterwards?.[/COLOR]
```

---

### Post by bodhi.zazen on 2010-06-24
> **sisco311 said:**
> The owner of the directory is not affected by the sticky bit, if the owner has write and execute permissions he is allowed to remove and rename any file from the directory.

This ^^

Ownership of the diectroy and permissions as owner take precidence to the sticky bit.

So , you own the directory "test" and you have rwx permission to the directory , so you can delete files in the directory.

The sticky bit prevents people who do not own either the directory or the file from deleting the file due to permissions granted via group membership or "other".

Or another way to say that is the sticky bit applies to group and other permissions and does not over ride outright ownership.

You can not, for example, do that in /tmp

```
bodhi@ufbt:~/tfol$ sudo touch /tmp/file                      
bodhi@ufbt:~/tfol$ rm /tmp/file                               
rm: remove write-protected regular empty file `/tmp/file'? y
rm: cannot remove `/tmp/file': Operation not permitted
```

See ? The sticky bit prevents me from deleting the file (the sticky bit is set on /tmp).

But you can if you own the directory:

```
bodhi@ufbt:~/tfol$ mkdir /tmp/test                           
bodhi@ufbt:~/tfol$ chmod 1777 /tmp/test                       
bodhi@ufbt:~/tfol$ sudo touch /tmp/test/file

bodhi@ufbt:~/tfol$ ls -l /tmp/test                           
total 0
-rw-r--r-- 1 root root 0 2010-06-24 16:59 file

bodhi@ufbt:~/tfol$ rm /tmp/test/file                          
rm: remove write-protected regular empty file `/tmp/test/file'? y
bodhi@ufbt:~/tfol$
```

In the second example, I own the directory /tmp/test so I can delete /tmp/test/file even though it is owned by root and I do not have w access to the file.

---

### Post by J V on 2010-06-24
So if I wanted to make a legitimately annoying linux virus, I would just make an elf that creates 1000 double directories under ~ with root 700 permissions?

That way the user would have to delete the account or get an administrator on the phone to get rid of them...

Potential flaw in the proverbial armor?

---

### Post by sisco311 on 2010-06-24
> **J V said:**
> 

Edit: One more question:
```
j@jubuntu:~/tfol$ sudo mkdir test
j@jubuntu:~/tfol$ sudo mkdir test/test
j@jubuntu:~/tfol$ rm test/test
j@jubuntu:~/tfol$ rmdir test/test
rmdir: failed to remove `test/test': Permission denied [COLOR=Blue]# Expected[/COLOR]
j@jubuntu:~/tfol$ rm -rf test
rm: cannot remove directory `test/test': Permission denied [COLOR=Blue]# Ehm... So I can't remove these empty folders owned by root without deleting the folder above them? Taking a lot of time to fix afterwards?.[/COLOR]
```

In order to remove or rename a file from a directory you need write and execute permission for the directory. e.g.:
```
[sisco@acme ~]$ sudo touch /sisco
[sisco@acme ~]$ sudo chown sisco\: /sisco 
[sisco@acme ~]$ rm /sisco 
rm: cannot remove `/sisco': Permission denied

```
even if:
```
[sisco@acme ~]$ ls -alh /sisco 
-rw-r--r-- 1 sisco users 0 Jun 25 02:20 /sisco
```
write permission for a file means that you can write to it:
```
[sisco@acme ~]$ echo damn it\'s 2:23AM > /sisco
[sisco@acme ~]$ cat /sisco 
damn it's 2:23AM

```
but to remove or rename it you must have write and execute permission for the directory in which the file is located.


The rm command, by default, removes a file & rmdir removes an empty directory. The -r flag of the rm command means remove directories and their contents recursively. The pseudocode of rm -r looks like this:
```

rm-r whatever:
if whatever is a file; then
  rm whatever || exit with error
elis whatever is an empty directory; then 
  rmdir whatever || exit with error
else 
  for all **file**s in whatever; do
    rm-r file
  done
  rmdir whatever || exit with error ???
end

```

**rm -rf test** fails because you don't have rights to remove test/test.

---

### Post by bodhi.zazen on 2010-06-24
> **J V said:**
> So if I wanted to make a legitimately annoying linux virus, I would just make an elf that creates 1000 double directories under ~ with root 700 permissions?

That way the user would have to delete the account or get an administrator on the phone to get rid of them...

Potential flaw in the proverbial armor?

If you wrote a program to do annoying things there is almost no end to the types annoying things you can do.

The trick is to either fool someone into running it (social engineering) or take advantage of some security flaw so that it runs on it's own, more power to you if you can escalate to root privileges and circumvent apparmor and selinux.

Very few, if any, security measures will stop you from opening a terminal, writing a nasty script, and then executing such a script as root.

If you are interested in security or are managing a shared data directory, understanding the nuances of Linux permissions is irreplaceable.

Linux permissions go a long way in securing Linux, but they do have limits, and thus tools such as apparmor, ACL, and selinux were created to tighten up the place.

If the basic permissions do not offer you as much control as you feel you need, take a look at ACL, apparmor, selinux, etc.

If you are interested , read these

[http://docs.fedoraproject.org/en-US/Fedora/13/html/Security-Enhanced_Linux/chap-Security-Enhanced_Linux-Introduction.html](http://docs.fedoraproject.org/en-US/Fedora/13/html/Security-Enhanced_Linux/chap-Security-Enhanced_Linux-Introduction.html)

And for Ubuntu

[[all variants] Introduction to AppArmor - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1008906")

---

### Post by sisco311 on 2010-06-24
> **J V said:**
> So if I wanted to make a legitimately annoying linux virus, I would just make an elf that creates 1000 double directories under ~ with root 700 permissions?

That way the user would have to delete the account or get an administrator on the phone to get rid of them...

Potential flaw in the proverbial armor?

You need root permissions to create a file(directories are files too) with root permissions. So no, it's not a flaw.

& btw, non-root user do not have enough permissions to delete their account. :)

By default, they can delete everything from their $HOME (/home/username) directory, but not the $HOME (/home/user), because, once again, by default, they don't have write permissions for $HOME/.. (/home) ;)

---

### Post by J V on 2010-06-24
What I mean is, if you run this:

```
cd
sudo mkdir test
sudo mkdir test/test
```You won't be able to delete either of them without elevating privileges... Unless you're willing to delete your home directory (And I'm not sure that's possible, depends on who owns /home)

You could swamp a standard user with folders "Locked" like this, and they would need an admin to fix it...

@Sisco: This works with other accounts too... if 2 standard users are on a system, and one gets write access to another's ~, he can swamp them with "Locked" folders...

---

### Post by sisco311 on 2010-06-24
> **J V said:**
> 

@Sisco: This works with other accounts too... if 2 standard users are on a system, and **one gets write access to another's ~**, he can swamp them with "Locked" folders...

Still not a security issue... The real question is: how/why one can gain write access to another's home directory?

---

### Post by bodhi.zazen on 2010-06-24
> @Sisco: This works with other accounts too... if 2 standard users are on a system, and one gets write access to another's ~, he can swamp them with "Locked" folders...

Your system is only as secure as your users.

Users could swamp /tmp or fill /var/log or any number of things, use your imagination ...

If you wish to have a more private $HOME , chmod 700 $HOME

But listing all the annoying behaviors and "fixes" would fill up many a thread.

Selinux would be the easiest thing to deploy on such a system as selinux, among other things, allows administrators to set system wide polices. selinux, unlike standard permissions, makes it difficult for users to override such policies.

The standard permissions work well for single users on desktops, but in a multiuser environment you may want to look at ACL or selinux, depending  on how permissive / restrictive you feel you need to be and the sensitivity of the data you keep.

---

### Post by sisco311 on 2010-06-24
Back to the OP :)

> **J V said:**
> I'm writing a script to delete everything in ~ when a user logs off, but I need to set certain files/folders off limits (Settings, the script itsself, etc)

Are you trying to implement something like "kiosk mode" or a "guest account"? 

Dirty fix: 
[list=i]
[*]save the default files in another directory
[*]remove everything from the home directory
[*]copy the default files back to the user's home
[/list]

But if you want to accomplish your task efficiently, then please elaborate your question.

---

### Post by J V on 2010-06-24
@bhodi: ACL seems more my type, but I don't think it's necessary really.

@Sisco: I was thinking of rigging the permissions so the .bash_logout wouldn't be able to delete certain config files (I simultaneously need those files to be admin only, so this works well) I could use .bash_login to copy them over, sure, but would that be overkill?

---

### Post by doas777 on 2010-06-25
> **J V said:**
> @bhodi: ACL seems more my type, but I don't think it's necessary really.

@Sisco: I was thinking of rigging the permissions so the .bash_logout wouldn't be able to delete certain config files (I simultaneously need those files to be admin only, so this works well) I could use .bash_login to copy them over, sure, but would that be overkill?

whether it is overkill, is somthing only you can decide, but I would suggest that if you do go down that road, that you destroy the files first, and then copy them back out of persistent storage. that will ensure that only the files you want are there, and in exactly the state you want them. I suggest it just cause it's a little more failsafe.

---

