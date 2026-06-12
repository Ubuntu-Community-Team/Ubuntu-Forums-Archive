---
title: "Mythbuntu 10.04 - Environment settings file location"
date: 2010-12-16
forum: General Help
---

### Post by scar1 on 2010-12-16
Hi,

Now I am becoming more familiar with ubuntu and using applications from terminal I have been able to write some simple scripts for common tasks that I perform.
My current issue is that to run the script I always need to give the full path or when in the location of the script need to provide ./ in front of the script name.

When I check the PATH Variable 

> steve@MediaCentre:/$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/gamesI would like to add my scripts directory to this path variable however cannot locate the file which has this line. I have checked in various bash* files however still cannot locate. Also tried using the find with grep command see below;

> 
sudo find . -name profile* -exec grep "/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games" '{}' \; -print
Which does not return any results, I expanded the search out to all files however this gave me a string of files with "Permission denied" messages.

Can any tell help me to find this file so I can update this setting.

My other option would be to copy all my scripts to one of these directories;
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games however whilst this will achieve what i need the scripts will be mixed up with lots of other files. Just would like to keep them separate.

Once again any help much appreciated.
Thanks
Scar1

---

### Post by flyingbear on 2010-12-16
Hi! I'm using another distro (not Debian based). My $PATH variable is configured in **~/.bash_profile** file. I'm not sure where this is configured in Ubuntu but you can try ```
find ~/.bash_profile
``` If such file exists just add your scripts containing directory to the PATH variable by adding **:/alabala/scripts**. If there is no such file you can search in your home directory for hidden files that may contain information about your PATH variable. The PATH is configured for each user so it should be somewhere in your home directory.

---

### Post by nothingspecial on 2010-12-16
```
nano .bashrc
```

put this in it

```
PATH=$PATH:/path/to/scripts
export PATH
```

Then get bash to reread your .bashrc

```
. ~/.bashrc
```

check it worked
```

echo $PATH
```

---

### Post by scar1 on 2010-12-16
Thanks....

> 
 	Code:
 	nano .bashrc 
put this in it

 	Code:
 	PATH=$PATH:/path/to/scripts
export PATH 
Then get bash to reread your .bashrc

 	Code:
 	. ~/.bashrc 
check it worked
 	Code:
 	echo $PATH 


By following the above I now can run my scripts without writing the full path at any location.
Again by doing this I have learnt another technique, I have just added an extra argument to my $PATH variable...
Nice one!

Thanks
Scar1

---

