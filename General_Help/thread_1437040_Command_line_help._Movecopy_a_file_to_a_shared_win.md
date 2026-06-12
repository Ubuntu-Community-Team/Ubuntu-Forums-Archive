---
title: "Command line help. Move/copy a file to a shared windows folder?"
date: 2010-03-23
forum: General Help
---

### Post by shawn.bordeaux on 2010-03-23
I am able to view my windows network from my UBUNTU desktop after being prompted for a username and password to the windows network. No problem. But how can I accomplish this from the command prompt?

Here is my windows directory;
smb://corpserver/d$/Data

And here is what I am trying to accomplish;
```

mv /var/lib/mysql/RSecuredData.csv smb://corpserver/d$/Data/Common/Secured%20R%20Reports/$(date +%Y%m%d)_RSecuredData.csv

```

Basically taking a csv file and moving it from mysql directory on my Ubuntu machine to a network folder on my windows server. (Windows Server 2003)

When I try that command from the command prompt I recieve;
```

mv: cannot move `/var/lib/mysql/RepoSecuredData.csv' to `smb://corpserver/d$/Data/Common/Secured%20Repo%20Reports/20100323_RepoSecuredData.csv': No such file or directory

```

Please help.
Regards,
Shawn

---

### Post by patchwork on 2010-03-23
Once you have mounted the share, you can navigate to it in the ~/.gvfs directory.   This makes it an easy ```
mv /path/to/file ~/.gvfs/shared/directory/name/filename
```

---

### Post by shawn.bordeaux on 2010-03-23
Thanks. I have the driver shared and mounted as corpserver/$d

When I try using this command
```

mv /var/lib/mysql/RSecuredData.csv ~/.gvfs/corpserver/$\d/RSecuredData.csv

```

I receive this error;

```

mv: cannot move `/var/lib/mysql/RSecuredData.csv' to `/home/ftpaccount/.gvfs/corpserver/$d/RSecuredData.csv': No such file or directory

```

Any suggestions? Thank you!

---

### Post by patchwork on 2010-03-23
Can you 'see' the share in terminal?

```
cd ~/.gvfs && ls
```

---

### Post by shawn.bordeaux on 2010-03-23
Yes, I can see both of my shares listed;

```

ftpaccount@administrator-ubuntu:~$ cd ~/.gvfs && ls
d$ on corpserver  profiles$ on corpserver
ftpaccount@administrator-ubuntu:~/.gvfs$ 

```

---

### Post by -grubby on 2010-03-23
ls accepts directory arguments, no need to cd :). Also, mv doesn't accept protocol arguments like Nautilus does (smb://)

---

### Post by patchwork on 2010-03-23
> **d$** on corpserver  profiles$ on corpserver
> /home/ftpaccount/.gvfs/corpserver/**$d**/RSecuredData.csv

Don't put corpserver in the line.  it should be /home/ftpaccount/.gvfs/$d/RSecuredData.csv

---

### Post by doas777 on 2010-03-23
I've always found content in .gvfs to be locked down to the extent that you can't really do anything with it from the cli. every time i try to get it to work, I get 
"file not found"

---

### Post by shawn.bordeaux on 2010-03-23
Thanks. I just tried that but same result :\

```

ftpaccount@administrator-ubuntu:/$ mv /var/lib/mysql/RSecuredData.csv ~/.gvfs/$\d/RSecuredData.csv
mv: cannot move `/var/lib/mysql/RSecuredData.csv' to `/home/ftpaccount/.gvfs/$d/RSecuredData.csv': No such file or directory


```

I have been using $\d   for   $d  so I the console wouldn't think the $ as a function

---

### Post by patchwork on 2010-03-23
> I've always found content in .gvfs to be locked down to the extent that you can't really do anything with it from the cli. every time i try to get it to work, I get 
"file not found"

I've used it often, with no troubles.  I even use it to virus scan with clam over the network.

---

### Post by patchwork on 2010-03-23
Sorry, it's d$, not $d

EDIT: And you may need to escape the $ with \ like this 

/d\$/

---

### Post by shawn.bordeaux on 2010-03-23
:) Thanks but not yet. Same error.


```

ftpaccount@administrator-ubuntu:/$ mv /var/lib/mysql/RSecuredData.csv ~/.gvfs/d\$/RSecuredData.csv
mv: cannot move `/var/lib/mysql/RSecuredData.csv' to `/home/ftpaccount/.gvfs/d$/RSecuredData.csv': No such file or directory


```

---

### Post by patchwork on 2010-03-23
Arghhh.   

I feel terrible....I told you to put the filename in the destination.   For the cp command you do, but not for the mv command.

/home/ftpaccount/.gvfs/d\$/

EDIT:  You can specify the name, but you would need the -T option
without the -T option and the filename, it will keep the same name and move it to the target directory

---

### Post by shawn.bordeaux on 2010-03-23
Hey man it's no problem.  I appreciate you trying to help.

Well this time I at least got a different error :)

```

ftpaccount@administrator-ubuntu:/$ mv /var/lib/mysql/RSecuredData.csv /home/ftpaccount/.gvfs/d\$/mv: cannot create regular file `/home/ftpaccount/.gvfs/d$/': Is a directory


```

---

### Post by patchwork on 2010-03-23
EDIT:  Please ensure you have this file backed-up before trying this...though it shouldn't cause damage, it's always safer to back-up first


```
 
mv -t /home/ftpaccount/.gvfs/d\$/ /var/lib/mysql/RSecuredData.csv
```Or ```
 mv -T /var/lib/mysql/RSecuredData.csv /home/ftpaccount/.gvfs/d\$/
```The first line will attempt to move the file into the specified directory (listed first in this instance).
The second line will attempt to move the file into the directory, treating it as a file

from ```
man mv
```

---

### Post by shawn.bordeaux on 2010-03-23
Well thanks again for trying. It would seem that it's hopeless :\
I tried another file this time just in case it had something to do with that. Same results though...


```

ftpaccount@administrator-ubuntu:/$ mv -t /home/ftpaccount/.gvfs/d\$/ /var/lib/mysql/result.txt
mv: accessing `/home/ftpaccount/.gvfs/d$/': No such file or directory

```
```

ftpaccount@administrator-ubuntu:/$ mv -T /var/lib/mysql/result.txt /home/ftpaccount/.gvfs/d\$/
mv: cannot create regular file `/home/ftpaccount/.gvfs/d$/': Is a directory

```

---

### Post by patchwork on 2010-03-23
Are you able to cd into ~/.gvfs/d\$ ?

---

### Post by shawn.bordeaux on 2010-03-23
Does not appear that I can...

```

ftpaccount@administrator-ubuntu:~/.gvfs$ cd ~/.gvfs/d\$
bash: cd: /home/ftpaccount/.gvfs/d$: No such file or directory

ftpaccount@administrator-ubuntu:~/.gvfs$ cd ~/.gvfs && ls
d$ on corpserver  profiles$ on corpserver


```
Noticed I used the ls command to list the shared folders though. I can also CD to
```

ftpaccount@administrator-ubuntu:~/.gvfs$ cd ~/.gvfs
ftpaccount@administrator-ubuntu:~/.gvfs$ 

```

---

### Post by patchwork on 2010-03-23
AHHH.

the directory name is 'd$ on corpserver'

EDIT:  Ever have one of those days...

---

### Post by shawn.bordeaux on 2010-03-23
Well great! I think we have that part but now I seem to be getting a permissions error.

```

ftpaccount@administrator-ubuntu:~$ mv -t /home/ftpaccount/.gvfs/'d$ on corpserver'/ /var/lib/mysql/result.txt
mv: preserving times for `/home/ftpaccount/.gvfs/d$ on corpserver/result.txt': Operation not supported
mv: failed to preserve ownership for `/home/ftpaccount/.gvfs/d$ on corpserver/result.txt': Function not implemented
mv: setting permissions for `/home/ftpaccount/.gvfs/d$ on corpserver/result.txt': Operation not supported


```

I am logged in as the owner of the mysql folder and file so it must be with the shared folder? I was able to create a new file to the share folder using the GUI so I must have access to it...

---

### Post by patchwork on 2010-03-23
Can you change the mv -t to cp -tp

This will copy the file while preserving the timestamp and ownership.  If this works, you will need to go back and rm the original file (since only a copy is being made)

---

### Post by shawn.bordeaux on 2010-03-23
Well guess what? It seems to be working even with that error!

I checked the directory and the file was copied over. Awesome! I am going to create a script now to mount the drive on startup and then automate this process. Thanks a bunch patchwork!

---

### Post by patchwork on 2010-03-23
The file may have been moved, but the timestamps and ownerships weren't preserved.  If this causes a problem, you may need to look into the cp -tp command instead (I don't know how to preserve ownership etc. with the mv command)

Glad it's working for you though.

---

### Post by shawn.bordeaux on 2010-03-23
Thanks again. I decided to co with the copy command and just delete the file after it is copied. Works great! Thank you again.

---

