---
title: "rm /*   accident!"
date: 2011-06-06
forum: General Help
---

### Post by twicejr on 2011-06-06
Hi all..
On a production machine used as server, i accidentally typed rm /* instead of rm * (in a folder).
Now, I cannot open new shells, cannot execute commands!
How can I resolve this?

The only things removed (as far as a i can see) are symlinks.

initrd.img           /////   /boot/initrd.img-2.6.32-30-generic
lib64                 /////   /lib
vmlinuz            /////    /boot/vmlinuz...................

It should be easy to fix, but how can I? Once I lose this term i cannot do anything anymore.

Errors i get for every command (except exec and export and cd):
-bash: /bin/ls: No such file or directory

OR if a command does not exist
-bash: /usr/bin/python: No such file or directory

---

### Post by twicejr on 2011-06-06
Tried copying all binaries form a test machine (with same Ubuntu 10.04 version), to /var/www (samba mount still working).

Tried doing declare -x PATH=/var/www/

And then ls says
/var/www/ls no such file or directory (while it does exist!)

---

### Post by matt_symes on 2011-06-06
Hi

> 
Errors i get for every command (except exec and export and cd):These are bash builtin commands so bash, i suspect, is running entirely in memory.

[http://linux.about.com/library/cmd/blcmdl1_builtin.htm](http://linux.about.com/library/cmd/blcmdl1_builtin.htm)

> 
-bash: /bin/ls: No such file or directory

OR if a command does not exist
-bash: /usr/bin/python: No such file or directoryThese are not builtin commands and,  after an rm /*, you might have wiped (part of) your hard drive (Although you did not use the recursive option so you may be lucky but that would depend on how you system is setup).

What makes you think it only the symlinks that have disappeared.

The symlinks are easy to recreate under / and point to your newest kernel and initramfs in the /boot directory.

You could boot into a liveCD and check the state of your filing system but that would mean bringing down your production server.

I hope you have good backups just in case.

Kind regards

---

### Post by matt_symes on 2011-06-06
Hi

> **twicejr said:**
> Tried copying all binaries form a test machine (with same Ubuntu 10.04 version), to /var/www (samba mount still working).

Tried doing declare -x PATH=/var/www/

What is your current path variable

```
echo $PATH
```Post that back here.

> And then ls says
/var/www/ls no such file or directory (while it does exist!)That sounds more than just an rm /* if it exists. Can you check the privileges of the directory ?

Kind regards

---

### Post by twicejr on 2011-06-06
> **matt_symes said:**
> Hi

What makes you think it only the symlinks that have disappeared.

The fact that I did not use -r, and the fact that our test server, has no files other than symlinks in the root directory makes me conclude this.
Also, the website is still runnin' fine.

> 
The symlinks are easy to recreate under / and point to your newest kernel and initramfs in the /boot directory.
Yes, I have tried to, but ls gives:
-bash: /bin/ln: No such file or directory

> 
You could boot into a liveCD and check the state of your filing system but that would mean bringing down your production server.
True, that is not really an option right now, plus the fact that it might not reboot, scares me.

> 
I hope you have good backups just in case.
I have backups of all PHP and database files, so that is a fact.

---

### Post by hawthornso23 on 2011-06-06
I'm not a linux expert - just some schmuck. I'm sure an expert will be along shortly. In the meantime what happens if you simply try to recreate the missing links.
```

cd /
sudo link lib64 lib
``` ... and so forth


Oops - and the experts are here already. I'll just quietly go away now. Good Luck!

---

### Post by twicejr on 2011-06-06
> **matt_symes said:**
> Hi

What is your current path variable

That is:
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/var/www

I cannot check the priveleges, but I assume 0755

---

### Post by twicejr on 2011-06-06
> **hawthornso23 said:**
> I'm not a linux expert - just some schmuck. I'm sure an expert will be along shortly. In the meantime what happens if you simply try to recreate the missing links.
```

cd /
sudo link lib64 lib
``` ... and so forth
I then get:
-bash: /usr/bin/sudo: No such file or directory

Isn't there an alternative method of creating symlinks? With PHP I have had no succes using symlink('/lib', '/lib64');

---

### Post by matt_symes on 2011-06-06
Hi

> The fact that I did not use -r, and the fact that our test server, has  no files other than symlinks in the root directory makes me conclude  this.
Also, the website is still runnin' fine.
Are you sure they are not running in memory. Linux loves to cache in memory.

I have to say, i think you might need to restore from a backup as it seems your filing system is gone. Everything is pointing to that.

You need to check by booting into a live environment, mounting the drive and having a look.

Kind regards

---

### Post by twicejr on 2011-06-06
> **matt_symes said:**
> Hi

Are you sure they are not running in memory. Linux loves to cache in memory.

Well, when I do cd /bin and then TABTABTAB, I can see all the files exist!

> 
I have to say, i think you might need to restore from a backup as it seems your filing system is gone. Everything is point to that.

What do you mean with "filing system"? Is that a file containing ... the file system? I dont have any backups other than /var/www/ and the sql databases

---

### Post by twicejr on 2011-06-06
> **matt_symes said:**
> Hi

Are you sure they are not running in memory. Linux loves to cache in memory.

I have to say, i think you might need to restore from a backup as it seems your filing system is gone. Everything is point to that.

You need to check by booting into a live environment, mounting the drive and having a look.

Kind regards
Well, I can still use the website and its mysql / mongodb databases insert and select works fine.

---

### Post by matt_symes on 2011-06-06
Hi

> **twicejr said:**
> What do you mean with "filing system"? Is that a file containing ... the file system? I dont have any backups other than /var/www/ and the sql databases

The filling system in your hard drive. The filling system contains all the files on your hard drive including commands such as ln, sudo, chmod. 

These are the commands required to administer your PC. Most if not all the files are gone. I would place money on that.

```
matthew@matthew-laptop:~$ which ln
/bin/ln
matthew@matthew-laptop:~$ which sudo
/usr/bin/sudo
matthew@matthew-laptop:~$ which ls
/bin/ls
matthew@matthew-laptop:~$ 
```

You have lost at least /bin and /usr/bin by the looks of it.

You have no backup of your drive and that is a _huge_ problem. Your looking at a reinstall and reconfiguring all the installed software.

Sorry to be the bearer of bad news, however i would place money on this is your current position.

Backup, Backup, Always Backup.

Kind regards

---

### Post by matt_symes on 2011-06-06
Hi

> **twicejr said:**
> Well, I can still use the website and its mysql / mongodb databases insert and select works fine.

I will ask again. Are you sure they are not running memory ?

I will reiterate again. You need to check to see if you have a filling system left. Don't guess. Check this.

Kind regards

---

### Post by twicejr on 2011-06-06
> **matt_symes said:**
> Hi

I will ask again. Are you sure they are not running memory ?

Fully sure now, ran this script in pHP:
```

<?php 
date_default_timezone_set('Europe/Amsterdam'); error_reporting(E_ALL);ini_set('display_errors',1);

$tempdir = '/var/www/tttt'; //copied all file from test server to here..
$dir = '/bin'; //checkin'

if ($handle = opendir($tempdir))
{
    $files = array();
    /* This is the correct way to loop over the directory. */
    while (false !== ($file = readdir($handle))) {
        if($file != '.' && $file != '..')
      $files[$file] = $file;
    }
    closedir($handle);
}

foreach($files as $file)
{
    $frompath = '/var/www/tttt/'.$file;
    $topath = "$dir/$file"; //bin/file
    
    $content  = file_get_contents($topath);
    $len = strlen($content);
    
    echo file_exists($topath) ? "$dir/$file".' exists and has length '.$len.'<br>' : '';
    /*
    file_put_contents("$dir/$file", $content);
    chmod("$dir/$file", 0777);*/
}

```This outputs 126 times a row like these:

/bin/ln exists and has length 55912.

I can even echo these files content!

---

### Post by blind2314 on 2011-06-06
A *production server* and you have no backups other than your databases? Yikes, that's bad news. Do you know for a fact that you don't have any other backups? What kind of solution does your company use to manage its backups?
 
There's a good chance that you didn't touch the directory your actual SQL database is stored in, and that's why inserts/deletes still work. Though, have you tried to actually *committ* these changes? I ask this because if you're only modifying what is cached in memory, as has been said, that really doesn't prove anything. However, if you're committing the database changes as they happen, then that's a good sign.
 
It really does sound like re-installing is becoming your only option here, which is unfortunate. Not to sound rude, so please don't take it like that, but you really need to re-consider not having full backups of production machines. I have a hard time believing that many IT departments worth their salt would overlook this (unless it was a forced decision from higher up, in which case, that brings up a whole new set of issues/problems).
 
Good luck, post back if we can help more.

---

### Post by matt_symes on 2011-06-06
Hi

> **twicejr said:**
> /bin/ln exists and has length 55912.

The plot thickens. That was good work with the script. I am not expert with php as i develop in C and C++, but the script looks like it should be displaying ls for the directory /bin. Maybe someone who knows PHP can take a look.

Can we assume it is copying the binaries with the same privileges (755) from your test server to the /bin directory ? Can you test this in PHP ?

I assume the server is 64 bit and the executables seems to be there. Therefore, if it is 64-bit, it also might not be able to find the libraries it needs to run as the symlink /lib64 is gone.

You said you were having problems creating symlinks in PHP. What were the problems ?

My machine is 64 bit.

```
matthew@matthew-laptop:~$ ldd /bin/ln
        linux-vdso.so.1 =>  (0x00007fff44925000)
        libc.so.6 => /lib/libc.so.6 (0x00007ff2032fc000)
        **/lib64/ld-linux-x86-64.so.2** (0x00007ff2036a2000)
matthew@matthew-laptop:~$ 
```As you can see it uses a 64 bit library.

Have you considered modifying your PATH variable to point to the 64 bit libraries directory ? That may or may not help.

Kind regards

---

### Post by twicejr on 2011-06-06
> **matt_symes said:**
> Hi



The plot thickens. That was good work with the script. I am not expert with php as i develop in C and C++, but the script looks like it should be displaying ls for the directory /bin. Maybe someone who knows PHP can take a look.

Can we assume it is copying the binaries with the same privileges (755) from your test server to the /bin directory ? Can you test this in PHP ?

It has not copied anything, because all the files are still in place.
> 
I assume the server is 64 bit and the executables seems to be there. Therefore, if it is 64-bit, it also might not be able to find the libraries it needs to run as the symlink /lib64 is gone.

You said you were having problems creating symlinks in PHP. What were the problems ?

That is true, it just doesnt happen.. Problem with the rights of the PHP user I gues..
Chmod does not work on / with this php user also.

> 
Have you considered modifying your PATH variable to point to the 64 bit libraries directory ? That may or may not help.
Tried it like this:
declare -x PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/lib64:/usr/lib"
Did not help though.

Thansk so far.

---

### Post by twicejr on 2011-06-06
Following might be worth noting:

root@xxx:/boot# ls
-bash: /bin/ls: No such file or directory
root@xxx:/boot# gzip
-bash: /bin/gzip: No such file or directory
root@xxx:/boot# ldd
-bash: /usr/bin/ldd: /bin/bash: bad interpreter: No such file or directory
root@xxx:/boot# service
-bash: /usr/sbin/service: /bin/sh: bad interpreter: No such file or directory

Note that it points to the right directory every time, yet it seems like BASH itself misses or something? Am i close?

---

### Post by matt_symes on 2011-06-06
Hi

> 
declare -x PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/lib64:/usr/lib"

On my (dektop version) machine

/lib64 points to the /lib folder. 

```

matthew@matthew-laptop:~$ ls -l /lib64
lrwxrwxrwx 1 root root 4 2011-05-24 13:59 /lib64 -> /lib
matthew@matthew-laptop:~$ 
```

Try modifying the path again.

```
declare -x PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/lib64:/lib
```

Kind regards

---

### Post by matt_symes on 2011-06-06
Hi

I can confirm the smslink for /lib64 is the issue as i just renamed it on my machine and i am now getting the same issue as you.

You need to find a way to recreate that symlink.

I have to fix my machine now :) 

Kind

---

### Post by twicejr on 2011-06-06
> **matt_symes said:**
> Hi



On my (dektop version) machine

/lib64 points to the /lib folder. 

```

matthew@matthew-laptop:~$ ls -l /lib64
lrwxrwxrwx 1 root root 4 2011-05-24 13:59 /lib64 -> /lib
matthew@matthew-laptop:~$ 
```Try modifying the path again.

```
declare -x PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/lib64:/lib
```Kind regards

Thanks, yet still no change when I did it:
declare -x PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/lib64:/lib"
hash -r
ls
-bash: /bin/ls: No such file or directory

---

### Post by hawthornso23 on 2011-06-06
Can you cd into the 64 bit libraries directory and try running from there?

---

### Post by twicejr on 2011-06-06
> **matt_symes said:**
> Hi

I can confirm the smslink for /lib64 is the issue as i just renamed it on my machine and i am now getting the same issue as you.

You need to find a way to recreate that symlink.

I have to fix my machine now :) 

Kind
Thanks very much. For sacrificing your own machine!

Now I know what I look for, when booting into Live CD or have to find another way to recreate this file

---

### Post by matt_symes on 2011-06-06
Hi

See my post #20. The symlink to /lib64  is the issue.

Kind regards

---

### Post by twicejr on 2011-06-06
> **matt_symes said:**
> Hi

See my post #20. The symlink to /lib64  is the issue.

Kind regards
Thanks man.
Now I'm Just trying to fight to find a way to re-create the symbolic link without rebooting..

---

### Post by matt_symes on 2011-06-06
Hi

If you can afford down time for a couple of minutes then all you need to do is boot into a liveCD/USB, open a terminal and type

```
sudo ln -s /lib /lib64
```

EDIT: Edited this post as previous suggestion will not work.

You need a root shell and that is going to be your problem. I think the only way may be a reboot.

Kind regards

---

### Post by twicejr on 2011-06-06
> **matt_symes said:**
> Hi

If you can afford down time for a couple of minutes then all you need to do is boot into a liveCD/USB, open a terminal and type

```
sudo ln -s /lib /lib64
```EDIT: Edited this post as previous suggestion will not work.

You need a root shell and that is going to be your problem. I think the only way may be a reboot.

Kind regards

Well I'll have to do it at night-time then, I guess.
I do have a root shell open, but that is the one which says "no such file" every time.

---

### Post by matt_symes on 2011-06-06
Hi

You have a root shell open ? There may be hope.

Create a script on your test pc (_ensure_ it is made by root <so create it in a root shell on your test pc> and has chmod 777 privileges)

```

#!/bin/bash
ln -s /lib /lib64
```Copy it to /var/www/ttttt directory (or what ever you called it) as you did for the other files on your production PC.

Run it from your root shell on the production PC. It should create the link.

I have to pop out. If that does not work don't reboot yet. Your root shell on your production PC could be the life line required.

Kind regards

---

### Post by twicejr on 2011-06-06
> **matt_symes said:**
> Hi

You have a root shell open ? There may be hope.

Create a script on your test pc (_ensure_ it is made by root <so create it in a root shell on your test pc> and has chmod 777 privileges)

```

#!/bin/bash
ln -s /lib /lib64
```Copy it to /var/www/ttttt directory (or what ever you called it) as you did for the other files on your production PC.

Run it from your root shell on the production PC. It should create the link.

I have to pop out. If that does not work don't reboot yet. Your root shell on your production PC could be the life line required.

Kind regards

I have created the file and copied it. The only problem is I don't know how to run it.
The root shell says::

root@xxx:/var/www# ./do.sh
-bash: ./do.sh: /bin/bash: bad interpreter: No such file or directory

(while /bin/bash does exist, of course)

---

### Post by matt_symes on 2011-06-06
Hi

That would create a new bash shell and you would be in the same position. Try sourcing it to run it in the existing root shell.

```
. ./do.sh
```That is: <dot> <space> <dot> <slash>do.sh

Kind regards

---

### Post by matt_symes on 2011-06-06
Hi

That would create a new bash shell as you would be in the same position. Try sourcing it to run it in the existing root shell.

```
. ./do.sh
```That is: <dot> <space> <dot> <slash>do.sh

EDIT: Actually, i'm not sure if this will work as it will still try to run the ln command on the drive. Chicken and egg situation. I cannot think of any way around it. Even with a root shell.

I think a reboot may be the only option. Sorry i have been wracking my brains while i went down the shops.

The only thing i can think of is maybe trying to use the 32bit version of ln -s. Maybe putting that and the libraries it requires on the production PC. That command and it's libraries are the only binaries you need to fix the issue i think.

Let me break my system and try to fix it again without using a livecd.

Kind regards

---

### Post by matt_symes on 2011-06-06
Hi

This may be fixable if we can use the 32 bit libraries. 

I have the 32 bit libraries on my 64 bit machine. Do you have them on your production PC ?

Have a look at this

```
matthew@matthew-laptop:~$ sudo -i
[sudo] password for matthew:
root@matthew-laptop:~# ls /
bin  boot  cdrom  dev  etc  home  initrd.img  initrd.img.old  lib  lib32  lib64  lost+found  media  mnt  opt  proc  root  sbin  selinux  srv  sys  tmp  usr  var  vmlinuz  vmlinuz.old
root@matthew-laptop:~# rm /lib64
root@matthew-laptop:~# ls
-bash: /bin/ls: No such file or directory
root@matthew-laptop:~# /home/matthew/ln32 -s /lib /lib64
root@matthew-laptop:~# ls
Desktop  DSDT.dat  DSDT.dsl  DSDT.hex
root@matthew-laptop:~# 
```I copied the 32 bin ln command onto my home directory beforehand. You would be copying it into your /var/www/tttt folder.

I entered a root shell and deleted the link to /lib64.

As you can see, i was not able to list the directory contents like you. 

This happens for all commands that are not bash builtins. 

I then recreated the link using the 32 bit ln command in my home directory. I was then able to use the 64 bit ls command again.

Can you do something similar if you have the 32 bit libraries ?

Kind regards

---

### Post by georgemc on 2011-06-06
Matt is doing a good job and I feel your pain.  Been there :)
 

 Just another suggestion.
 

 If you can mount a CD/DVD on the ailing system:
 Create a &#8220;tool kit&#8221; CD/DVD on a known good system that is of the same vintage and type of the ailing system.
 

 Place your tools on the CD/DVD with all permissions set properly.
 

 If you can mount a share from the ailing system:
 As an alternative mount a r/w share from the ailing system to a know good system and place tools there with the proper permissions.
 

 Then see if you can launch the tools using absolute paths.
 

 Suggested tools:
 bash
 ls
 ln
 chmod
 and any and every thing that is currently missing
 

 <<<>>>
 

 Other thoughts and suggestions.
 

 With your root terminal we can at least attempt to use the &#8220;built in&#8221; commands of bash.
 

 Can you &#8220;cd&#8221; into /bin and /usr/bin ?
 

 If you can, type in  
 ```

 echo *
 
``` This will display any files in the directory; at least you can verify if you still have stuff in the /bin and /usr/bin directories.
 

 George

P.S. "echo" might not be a built in

---

### Post by twicejr on 2011-06-06
> **matt_symes said:**
> Hi

This may be fixable if we can use the 32 bit libraries. 

I have the 32 bit libraries on my 64 bit machine. Do you have them on your production PC ?

Kind regards
I don't seem to have the 32bit ln. I did a netinstall, that might be the reason I haven't?
Tomorrow I will try to fix it. It's time to go home for dinner.
I think I'll grab the ISO of 10.04 tomorrow and then extract the ln command to my homedir using the samba mount to /var/www/ I still have open...
Maybe, just maybe, you can attach the ln command here?

Thanks so much for all your great efforts!

---

### Post by matt_symes on 2011-06-06
Hi

> P.S. "echo" might not be a built inEcho is a built in command and echo * is an excellent suggestion. I wish i had though of that.

I think he might have trouble mounting in the borked production PC though as everything is relying on the /lib64 symlink as far as i can tell. It's worth a try though.

It's this that seems to be causing the issues i think.

```
matthew@matthew-laptop:~$ ldd /bin/mount
        linux-vdso.so.1 =>  (0x00007fff8edff000)
        libblkid.so.1 => /lib/libblkid.so.1 (0x00007fee3c29b000)
        libuuid.so.1 => /lib/libuuid.so.1 (0x00007fee3c096000)
        libselinux.so.1 => /lib/libselinux.so.1 (0x00007fee3be77000)
        libsepol.so.1 => /lib/libsepol.so.1 (0x00007fee3bc3b000)
        libc.so.6 => /lib/libc.so.6 (0x00007fee3b8b8000)
        **/lib64/ld-linux-x86-64.so.2** (0x00007fee3c4dd000)
        libdl.so.2 => /lib/libdl.so.2 (0x00007fee3b6b3000)
matthew@matthew-laptop:~$ 
```On my latop, the 64 bit version of ln uses these libraries

```

matthew@matthew-laptop:~$ ldd /bin/ln 
        linux-vdso.so.1 =>  (0x00007fff6c5ff000)
        libc.so.6 => /lib/libc.so.6 (0x00007f9bf6e58000)
        /lib64/ld-linux-x86-64.so.2 (0x00007f9bf71fe000)
matthew@matthew-laptop:~$
```and the 32 version of ln uses these libraries

```
matthew@matthew-laptop:~$ ldd ln32 
        linux-gate.so.1 =>  (0xf772d000)
        libc.so.6 => /lib32/libc.so.6 (0xf75b0000)
        /lib/ld-linux.so.2 (0xf772e000)
matthew@matthew-laptop:~$ 
```This may be an option ( i have never used it though so it will require some research)

A statically linked ln command.

[http://linux.about.com/library/cmd/blcmdl8_sln.htm](http://linux.about.com/library/cmd/blcmdl8_sln.htm)
[http://linux.die.net/man/8/sln](http://linux.die.net/man/8/sln)

Any suggestions are most welcome in this thread.

Kind regards

---

### Post by matt_symes on 2011-06-06
Hi

I think i have found you a solution. The problem you have been having is loading the dynamic libraries pointed to at /lib64.

As you don't have the 32 bit libraries we cannot go down that route.

sln is a statically linked ln command that does not require the dynamic libraries, however it is not part of a Ubuntu distribution (or any of the others i looked at) and i could not find it in any packages i looked in.

However, we do have the  /lib/ld-linux-x86-64.so.2 symlink :)

This points to whatever dynamic loader is currently in use and using that we can specify where the library files are for the executable we want to run. The dynamic loader itself is statically compiled. It has to be by nature. Because it is statically compiled it has all the libraries it needs to runs complied into it, so we get around the chicken and egg situation where we cannot load the dynamic libraries for an executable because the symlink is gone and we cannot create the symlink because we cannot load the dynamic libraries to create the symlink.

So type this in the root terminal.

```
/lib/ld-linux-x86-64.so.2 --library-path /lib /bin/ln -s /lib /lib64
```Have a look through this.

```
root@matthew-laptop:~# ls
Desktop 
root@matthew-laptop:~# rm /lib64
root@matthew-laptop:~# ls
-bash: /bin/ls: No such file or directory
root@matthew-laptop:~# /lib/ld-linux-x86-64.so.2 --library-path /lib /bin/ln -s /lib /lib64
root@matthew-laptop:~# ls
Desktop 
root@matthew-laptop:~# 

```This worked for me and it will, hopefully, also work for you.

I would like to thank you because i have learnt something very useful today.

if you want more info

```
man ld-linux
```

Kind regards

---

### Post by Rubi1200 on 2011-06-06
> **matt_symes said:**
>  Any suggestions are most welcome in this thread.

I don't have a suggestion, but I do have a comment.

Kudos to Matt, and others, who have pulled together to help twicejr try and sort this out. The dedication and sacrifice (using your own laptop to test the possible solutions) is a credit to the community.

My hat off to you sir.

Best regards.

---

### Post by twicejr on 2011-06-07
> **matt_symes said:**
> Hi

I think i have found you a solution. The problem you have been having is loading the dynamic libraries pointed to at /lib64.

As you don't have the 32 bit libraries we cannot go down that route.

sln is a statically linked ln command that does not require the dynamic libraries, however it is not part of a Ubuntu distribution (or any of the others i looked at) and i could not find it in any packages i looked in.

However, we do have the  /lib/ld-linux-x86-64.so.2 symlink :)

This points to whatever dynamic loader is currently in use and using that we can specify where the library files are for the executable we want to run. The dynamic loader itself is statically compiled. It has to be by nature. Because it is statically compiled it has all the libraries it needs to runs complied into it, so we get around the chicken and egg situation where we cannot load the dynamic libraries for an executable because the symlink is gone and we cannot create the symlink because we cannot load the dynamic libraries to create the symlink.

So type this in the root terminal.

```
/lib/ld-linux-x86-64.so.2 --library-path /lib /bin/ln -s /lib /lib64
```Have a look through this.

```
root@matthew-laptop:~# ls
Desktop 
root@matthew-laptop:~# rm /lib64
root@matthew-laptop:~# ls
-bash: /bin/ls: No such file or directory
root@matthew-laptop:~# /lib/ld-linux-x86-64.so.2 --library-path /lib /bin/ln -s /lib /lib64
root@matthew-laptop:~# ls
Desktop 
root@matthew-laptop:~# 

```This worked for me and it will, hopefully, also work for you.

I would like to thank you because i have learnt something very useful today.

if you want more info

```
man ld-linux
```Kind regards
Man, you rock!

Thanks so much for your efforts!
I can see what a strong community can do now!

---

