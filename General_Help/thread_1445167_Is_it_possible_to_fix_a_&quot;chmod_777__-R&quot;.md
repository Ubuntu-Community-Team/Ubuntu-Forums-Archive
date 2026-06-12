---
title: "Is it possible to fix a &quot;chmod 777 / -R&quot;"
date: 2010-04-02
forum: General Help
---

### Post by josir on 2010-04-02
Hi folks, 

a freshman just issued an "chmod 777 / -R" on our servers.
Shame on me that gave root access to him...
:twisted:

On a RPM based system, I could issue an

for i in $(rpm -qa); do rpm --setperms $i; done
for i in $(rpm -qa); do rpm --setugids $i; done

But I don't know how to do the same with apt ou aptitude.

Is it possible to fix it in Ubuntu instead of restoring the backup??...

Thanks in advance,
Josir.

---

### Post by Chesamo on 2010-04-02
You can ```
user@server:~$ sudo chmod u+rwx / -R
user@server:~$ sudo chmod g+rw / -R
user@server:~$ sudo chmod o-rwx / -R
```
Thus resetting the access permissions of the files.

Also: You should never enable the root account in Ubuntu. sudo is much, **much** easier to control access to.

---

### Post by Simian Man on 2010-04-02
> **Chesamo said:**
> You can ```
user@server:~$ sudo chmod u+rwx / -R
user@server:~$ sudo chmod g+rw / -R
user@server:~$ sudo chmod o-rwx / -R
```
Thus resetting the access permissions of the files.
That doesn't do it correctly, because not all files have those permissions.  Fore one, it would make all text configuration files executable for root which is not correct.

> **Chesamo said:**
> Also: You should never enable the root account in Ubuntu. sudo is much, **much** easier to control access to.
Or you could just not give out the root password.  This is totally irrelevant.

---

### Post by benderisgreat on 2010-04-02
can't do that automatically on an apt based system afaik. i'd suggest editing a file permissions script like this:

[http://anti-trend.homelinux.org/pub/resources/tighten-file-perms.sh](http://anti-trend.homelinux.org/pub/resources/tighten-file-perms.sh)
( found here:[http://anti-trend.org/index.php?option=com_content&task=view&id=56&Itemid=46](http://anti-trend.org/index.php?option=com_content&task=view&id=56&Itemid=46))

i'd comment out the chown and note that the script doesn't change all file permissions recursively. sometimes just the directories.

---

### Post by Chesamo on 2010-04-02
> **Simian Man said:**
> That doesn't do it correctly, because not all files have those permissions.  Fore one, it would make all text configuration files executable for root which is not correct.
Whoops, my mistake. Should just be u/g+rw and o-rwx.

Executables can be given permission as needed.
> **Simian Man said:**
> Or you could just not give out the root password.  This is totally irrelevant.
I know of no application that must be done as root (with one exception, but it's a hardware-specific problem) that can't be done more securely with sudo or gksu. Why do you think root is disabled by default in the first place, and giving instructions on how to enable it is banned on this forum? Additionally, access to sudo can be controlled in the sudoers file. root actions aren't controlled.

---

### Post by Simian Man on 2010-04-02
> **Chesamo said:**
> Whoops, my mistake. Should just be u/g+rw and o-rwx.

Executables can be given permission as needed.
Well your solution leaves a lot to be desired.  Do you know how hard it will be to go through and give all the executables permission on an individual basis?  How do you give chmod itself executable permissions?  Even with your correction this is still a horrible idea.

> **Chesamo said:**
> I know of no application that must be done as root (with one exception, but it's a hardware-specific problem) that can't be done more securely with sudo or gksu.
Sudo is no more secure than su.  In this case, if he had given his friend his password or added him to sudoers, he'd be in the same boat.  You have to think about what you're doing no matter what security model you use.

> **Chesamo said:**
> Why do you think root is disabled by default in the first place, and giving instructions on how to enable it is banned on this forum?
Because Ubuntu doesn't want to confuse people new to Unix with 2 passwords, so they do it the way Windows does it.  I'm not arguing that sudo's worse.  It's just not better.

> **Chesamo said:**
> Additionally, access to sudo can be controlled in the sudoers file. root actions aren't controlled.
That makes no sense, you control access to root by not telling people the root password.  Also notice that you can still use sudo and/or policykit to manage finer-grained permissions in addition to having a root account.  They aren't mutually exclusive.

---

### Post by geirha on 2010-04-02
I guess the easiest option is to reinstall all installed packages.

Something like:
```
aptitude -F '%?p' search '~i' | sudo xargs aptitude reinstall
```

---

### Post by josir on 2010-04-08
Thanks for replying geirha. I tried:
 
aptitude -F '%?p' search '~i' | sudo xargs aptitude reinstall

and I got (translated to English):

It was not possible to locate file to package linux-image-2.6.24-16-server: This means that you need to fix this package manually. E: Writing extende stat information... Ok.
It was not possible to locate file to package linux-image-2.6.24-16-server: This means that you need to fix this package manually. Writing extende stat information... Ok.
E: Internal error: couldn't generate list of packages to download xargs: aptitude: exited with status 255: aborting

Do you have any suggestions?

---

### Post by wojox on 2010-04-08
Looks like old kernels. What does this command produce:

```
uname -a
```

---

### Post by prodigy_ on 2010-04-08
Well, the general idea would be to make a temporary fresh installation and use a script that walks all inodes saving names, ownership info and permissions. Actually, just ```
sudo ls -ARQl /|grep -v '^total '|grep -v '^l' > <some_file>
``` might be enough but I'm not 100% sure.

Then another script that parses the saved data (while read line) and cds/chmods/chowns wherever possible. 

If done properly this should automate most of the process. I'm sorry that I can't provide a complete implementation right now. Need to think first.

---

### Post by geirha on 2010-04-10
> **josir said:**
> Thanks for replying geirha. I tried:
 
aptitude -F '%?p' search '~i' | sudo xargs aptitude reinstall

and I got (translated to English):

It was not possible to locate file to package linux-image-2.6.24-16-server: This means that you need to fix this package manually. E: Writing extende stat information... Ok.
It was not possible to locate file to package linux-image-2.6.24-16-server: This means that you need to fix this package manually. Writing extende stat information... Ok.
E: Internal error: couldn't generate list of packages to download xargs: aptitude: exited with status 255: aborting

Do you have any suggestions?

Instead of translating the output of aptitude back into english, you can turn of the translations in the first place by changing the LANG environment variable.

```
export LANG=C
```

After running that, any new program started from that shell will not be translated.

Those error messages though, it sounds like either that linux package is removed from the repositories, or that the local list of packages is out of date. See if «sudo aptitude update» helps.

Also, what does this say?
```
aptitude show linux-image-2.6.24-16-server
```

---

### Post by pbrane on 2010-04-10
I thought 
```

sudo dpkg-reconfigure -a

```
would fix file permissions. No?

---

### Post by geirha on 2010-04-10
> **pbrane said:**
> I thought 
```

sudo dpkg-reconfigure -a

```
would fix file permissions. No?

Unfortunately not. I tried that in a VM

```
sudo aptitude install hello
ls -l /usr/bin/hello # 755
sudo chmod 777 /usr/bin/hello
sudo dpkg-reconfigure hello
ls -l /usr/bin/hello # 777

```

---

