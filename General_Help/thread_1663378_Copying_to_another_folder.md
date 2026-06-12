---
title: "Copying to another folder"
date: 2011-01-09
forum: General Help
---

### Post by neokyle on 2011-01-09
I need a way to copy a folder to another folder every X minutes. I dont want it to sync the folders, i want it to create a new copy of the specified folder and keep adding another copy every x minutes without deleting the old copy.

I know i can use crontab to make it do it every x minutes, im just missing the command to copy it.

Im new to linux so its pry a simple command that i need.

Thanks in advance

---

### Post by TeoBigusGeekus on 2011-01-09
In the form of a tiny script
```
#!/bin/bash
a=$(date)
cp -r "/path/foldername" "/newpath/foldername$a"
```
On every backup, the script will copy the folder from its path to another path, appending the current date and time to its name.
The quotes ensure that the script will work even with folder names with spaces in them.

---

### Post by neokyle on 2011-01-10
cant get that script to work.

Im typing, #!/bin/bash a=$(date) cp -r "/testfolder/" "testfolder2/$a"

After i hit enter it appears as the command worked but no new files are in testfolder2.

When i do cp -r /testfolder/ testfolder/ It copies testfolder to testfolder2 just fine.

---

### Post by TeoBigusGeekus on 2011-01-10
No, don't run it straight from terminal.
Save the script to a text file (using nano, gedit, geany or whatever you want).
Name the file, say copy_script, and save it.
```
chmod +x copy_script
```
to make it executable and
```
./copy_script
```
while you're in its folder to execute it.

---

### Post by Grenage on 2011-01-10
> **neokyle said:**
> cant get that script to work.

Im typing, #!/bin/bash a=$(date) cp -r "/testfolder/" "testfolder2/$a"

After i hit enter it appears as the command worked but no new files are in testfolder2.

When i do cp -r /testfolder/ testfolder/ It copies testfolder to testfolder2 just fine.

Also, your example is copying *testfolder* into a directory that doesn't exist ($a). TeoBigusGeekus' initial example did not.

---

### Post by neokyle on 2011-01-10
I get the following when i run it from a text file.


cp: cannot create directory `testfolder2/Mon Jan 10 14:23:46 MSK 2011': No such file or directory

Edit, removed the &a, now i get this.


cp: cannot copy a directory, `/testfolder/', into itself, `testfolder2/'

---

### Post by Grenage on 2011-01-10
> **neokyle said:**
> I get the following when i run it from a text file.


cp: cannot create directory `testfolder2/Mon Jan 10 14:23:46 MSK 2011': No such file or directory

See my above post.

---

### Post by TeoBigusGeekus on 2011-01-10
Could you post us the exact implementation of the script, ie. the exact script you've used?

---

### Post by neokyle on 2011-01-10
I edited my post after you quoted it.

So if i have to run this text file with the script in it from the folder the text file is in will crontab be able to execute it?


#!/bin/bash
a=$(date)
cp -r "/testfolder/" "testfolder2/"

---

### Post by Grenage on 2011-01-10
```
#!/bin/bash
a=$(date +"%Y.%m.%d")
mkdir "/testfolder/$a"
cp -r "/testfolder/" "testfolder2/$a/"
```

What about this?

I'd personally use explicit paths:

/home/USER/testfolder
/home/USER/testfolder2

---

### Post by neokyle on 2011-01-10
cp: cannot create directory `testfolder2/2011.01.10/': No such file or directory

explicit paths huh, this is just a test i didn't think there locations would matter.

---

### Post by TeoBigusGeekus on 2011-01-10
Have you tried executing my script?
If so, please post the exact script you executed.

---

### Post by neokyle on 2011-01-10
I posted it right after your post asking me to post the script im using. Here it is.

#!/bin/bash
a=$(date)
cp -r "/testfolder/" "testfolder2/"

---

### Post by TeoBigusGeekus on 2011-01-10
Make it
```
#!/bin/bash
a=$(date)
cp -r "testfolder" "testfolder$a"
```
and run it.

---

### Post by neokyle on 2011-01-10
> **TeoBigusGeekus said:**
> Make it
```
#!/bin/bash
a=$(date)
cp -r "testfolder" "testfolder$a"
```
and run it.

that made a folder named 2011.01.10 in testfolder. the folder has nothing in it.

So how do we get it to copy testfolder into testfolder2 now

---

### Post by TeoBigusGeekus on 2011-01-10
Where do you run the script from? Are you in testfolder?

---

### Post by neokyle on 2011-01-10
> **TeoBigusGeekus said:**
> Where do you run the script from? Are you in testfolder?

I placed the script in testfolder and i run it from the terminal whilst in testfolder.

---

### Post by TeoBigusGeekus on 2011-01-10
No. The script can't find the folder testfolder IN testfolder.
Go up a folder, taking the script with you, and run it from there.

---

### Post by neokyle on 2011-01-10
> **TeoBigusGeekus said:**
> No. The script can't find the folder testfolder IN testfolder.
Go up a folder, taking the script with you, and run it from there.

Testfolder is in root, so i moved the script from testfolder to root then tried to execute it via root from the terminal and got this.


-bash: ./copy_script.sh: No such file or directory

---

### Post by TeoBigusGeekus on 2011-01-10
Are you in root yourself? Bash won't find the script if you're still in testfolder.

PS: No need for the .sh extension.

---

### Post by neokyle on 2011-01-10
> **TeoBigusGeekus said:**
> Are you in root yourself? Bash won't find the script if you're still in testfolder.

PS: No need for the .sh extension.

yes im in root. root@neokyle

---

### Post by TeoBigusGeekus on 2011-01-10
Post output of
```
ls
```

---

### Post by neokyle on 2011-01-10
> **TeoBigusGeekus said:**
> Post output of
```
ls
```

testfolder2 is all it lists..

---

### Post by TeoBigusGeekus on 2011-01-10
> **neokyle said:**
> testfolder2 is all it lists..
So, you have neither the script, nor the testfolder in root; no wonder it doesn't work.
Copy the script in your root folder.
```
mkdir testfolder
```
to create the testfolder.
While you're at root
```
./copy_script
```
to run the script

---

### Post by neokyle on 2011-01-10
oops , i wasnt in root when i did ls.

this is what is in root when i type ls.

aquota.group    etc       lib64                                  opt      sys
aquota.user     fastboot  me.crontab                             proc     tmp
bin             file      media                                  root     usr
boot            hello     testfolder                              sbin     var
copy_script.sh  home      testfolderMon Jan 10 14:53:58 MSK 2011  selinux
dev             lib       mnt

---

### Post by neokyle on 2011-01-10
now the script and testfoler are both in root and im in root in the terminal. i get the same thing when i run ./copy_script.


-bash: ./copy_script: No such file or directory

im positive im in root this time and that i have made the testfolder directory in root and placed the copy_script in root.

---

### Post by TeoBigusGeekus on 2011-01-10
Ok, now that you're on root
```
./copy_script.sh
```
to run the script.

---

### Post by TeoBigusGeekus on 2011-01-10
> **neokyle said:**
> now the script and testfoler are both in root and im in root in the terminal. i get the same thing when i run ./copy_script.


-bash: ./copy_script: No such file or directory

im positive im in root this time and that i have made the testfolder directory in root and placed the copy_script in root.

Only that you've named your script copy_script.sh and not plain copy_script.
See my previous post.

---

### Post by neokyle on 2011-01-10
now nothing happens when i run the script. Just have an empty testfolder1 and testfolder2 along with the copy_script all in root.

---

### Post by TeoBigusGeekus on 2011-01-10
```
nano copy_script.sh
```
Are you running my version or grenade's?

---

### Post by neokyle on 2011-01-10
> **TeoBigusGeekus said:**
> ```
nano copy_script.sh
```
Are you running my version or grenade's?

#!/bin/bash
a=$(date)
cp -r "/testfolder" "/testfolder$a"

im running the above script.

---

### Post by TeoBigusGeekus on 2011-01-10
As you may recall from post#14, the slashes are wrong.
Delete them, making the script
```
#!/bin/bash
a=$(date)
cp -r "testfolder" "testfolder$a"
```
ctrl+x to exit (answer yes to save it) and run it again.

---

### Post by neokyle on 2011-01-10
It works but there is a problem.

It creates a dated folder in root, what do i need to change to specify a diffrent location for the backed up folders to be placed.

thanks again for all the help :)

---

### Post by TeoBigusGeekus on 2011-01-10
If your testfolder is in a folder in root called ARandomFolder and you want to copy it to your home folder for example, your script should be
```
#!/bin/bash
a=$(date)
cp -r "/ARandomFolder/testfolder" "/home/yourusername/testfolder$a"
```

---

### Post by neokyle on 2011-01-10
I,ll test it out when i actually have the real files ready, its very late where i live, you could also say its very early :P gonna get some sleep.

I appreciate all the help you have given me :) 

thank you.

EDIT: one more quick question, will i be able to execute ./copy_script.sh with crontab? to automate the backing up of my files. dont see why not but figured i would ask

---

### Post by TeoBigusGeekus on 2011-01-10
> **neokyle said:**
> EDIT: one more quick question, will i be able to execute ./copy_script.sh with crontab? to automate the backing up of my files. dont see why not but figured i would ask

Sure, that's what crontab is there for: executing scripts at specific time intervals.

Go get some sleep, cause in the last few posts I don't think you were yourself - no offense. :P

---

### Post by neokyle on 2011-01-10
> **TeoBigusGeekus said:**
> Sure, that's what crontab is there for: executing scripts at specific time intervals.

Go get some sleep, cause in the last few posts I don't think you were yourself - no offense. :P

Yeah i will , but i wont get much. Got allot of stuff to setup.

Thank you again for all the help :)

---

### Post by TeoBigusGeekus on 2011-01-10
> **neokyle said:**
> #!/bin/bash
a=$(date)
cp -r "/testfolder" "/testfolder$a"

im running the above script.

Now that I read it again, the above should work as well.
Maybe it did work and you didn't notice.
Ah well...

---

### Post by neokyle on 2011-01-11
I have had time to setup my files and i have the script working, it places dated folders in the directory i specify, and combined with crontab its automated so it works wonderfully. 

The files im backing up are large and take up allot of space, for this reason i only can keep about 50 backups then i need to delete some. These files also have a ton of directories in them. this means they take a really long time to delete manually.  

Is there a way to make the script auto delete older ones, so when it goes to backup again and there are already 50 backups it deleted backup 50, then makes the backups so there are still only 50 backups and disk space is not exceeded.

EDIT: also a way to possibly zip the backups it makes? this would allow me to have more than 50 backups.

---

### Post by TeoBigusGeekus on 2011-01-11
I have created a folder called uu in my Desktop to test your problem. Let's say that this is the folder that I want my backups to be saved into.
I have also created there a folder called testfolder, along with a new script:
```
#!/bin/bash
c=$(ls -1 /home/teo/Desktop/uu |wc -l)
if (("$c" >= 5))
then
 f=$(ls -tr /home/teo/Desktop/uu |head -n 1)
 rm -r "/home/teo/Desktop/uu/$f"
fi
a=$(date)
cp -r "testfolder" "/home/teo/Desktop/uu/testfolder$a"
```
The script checks the number of items in the uu folder. If the number is greater or equal to 5, it deletes the oldest folder and then proceeds to create a new backup.
Change 5 to 50, change the paths as well (to fit your situation) and you should be ok.

---

### Post by Grenage on 2011-01-11
Use such commands with extreme caution, and test them thoroughly first.  Here's something I have 'crontabed' to run on a server:

```
find /var/log/syslog_server/ -type f -mtime +90 -exec rm {} \;
find /var/log/syslog_server/ -depth -type d -empty -exec rmdir {} \;
```

The first command deletes anything that meets the following criteria:
Exists in /var/log/syslog_server/
Is a file (-type f)
Is 90 days old or more (-mtime +90)

The second command deletes any empty folders.

Once again, I cannot fully express the importance of checking these sorts of commands; you can easily end up wiping a lot of data.


Edit: Beaten to it by TeoBigusGeekus!

---

### Post by TeoBigusGeekus on 2011-01-11
> **Grenage said:**
> Edit: Beaten to it by TeoBigusGeekus!
I cheated; he had PMed me first. :P

---

### Post by neokyle on 2011-01-11
> **TeoBigusGeekus said:**
> I have created a folder called uu in my Desktop to test your problem. Let's say that this is the folder that I want my backups to be saved into.
I have also created there a folder called testfolder, along with a new script:
```
#!/bin/bash
c=$(ls -1 /home/teo/Desktop/uu |wc -l)
if (("$c" >= 5))
then
 f=$(ls -tr /home/teo/Desktop/uu |head -n 1)
 rm -r "/home/teo/Desktop/uu/$f"
fi
a=$(date)
cp -r "testfolder" "/home/teo/Desktop/uu/testfolder$a"
```
The script checks the number of items in the uu folder. If the number is greater or equal to 5, it deletes the oldest folder and then proceeds to create a new backup.
Change 5 to 50, change the paths as well (to fit your situation) and you should be ok.

so basically replace my current copyscript with this script then change the paths to my paths and i should be good. Im going to test this out and post my results.

thankyou.

grenage your script is a little bit scarier than teo's :P with the warnings and all

---

### Post by Grenage on 2011-01-11
> **TeoBigusGeekus said:**
> I cheated; he had PMed me first. :P

Yours solution was better, and less likely to result in an *oops*. :)

---

### Post by TeoBigusGeekus on 2011-01-11
> **Grenage said:**
> Yours solution was better, and less likely to result in an *oops*. :)

We'll see about that 8-[ ....
I'm ready to start a new account, just in case :lolflag:

---

### Post by neokyle on 2011-01-11
Ok problem with your script teo. I have not tested this yet but i see a conflict.

Is there a way to make it exclude a folder? I have a separate folder in with my backups that wasn't generated by the script, this folder is the oldest folder in my backups folder.

---

### Post by TeoBigusGeekus on 2011-01-11
Change these lines
```
c=$(ls -1 /home/teo/Desktop/uu |wc -l)
...
f=$(ls -tr /home/teo/Desktop/uu |head -n 1)
```
to
```
c=$(ls -1 /home/teo/Desktop/uu/testfolder* |wc -l)
...
f=$(ls -tr /home/teo/Desktop/uu/testfolder* |head -n 1)
```

---

### Post by neokyle on 2011-01-11
> **TeoBigusGeekus said:**
> Change these lines
```
c=$(ls -1 /home/teo/Desktop/uu |wc -l)
...
f=$(ls -tr /home/teo/Desktop/uu |head -n 1)
```
to
```
c=$(ls -1 /home/teo/Desktop/uu/testfolder* |wc -l)
...
f=$(ls -tr /home/teo/Desktop/uu/testfolder* |head -n 1)
```

I dont think that would work. The folder that i dont want deleted needs to be in the same folder as the backups that the scripts create.

---

### Post by TeoBigusGeekus on 2011-01-11
The change in the script makes it count only the folders that begin with testfolder
```
c=$(ls -1 /home/teo/Desktop/uu/testfolder* |wc -l)
```
and then finds the oldest folder of the folders that begin with testfolder
```
f=$(ls -tr /home/teo/Desktop/uu/testfolder* |head -n 1)
```

Run it in a folder that has another folder with a different name-the latter won't be affected.

---

### Post by neokyle on 2011-01-11
Oh i misread :P

Than thats perfect, im going to go test it out soon :)

thanks again :)

---

### Post by neokyle on 2011-01-11
I changed the script and ran it. It creates a backup still :P so i guess that means it works :)

thanks again

---

### Post by neokyle on 2011-01-11
when it reaches its limet this happens.

root@server:/# ./copyscript.sh
rm: cannot remove `/home/neokyle/worldbackups/world//home/neokyle/worldbackups/worldTue Jan 11 05:26:01 EST 2011:': No such file or directory

This is my script.

#!/bin/bash
c=$(ls -1 /home/neokyle/worldbackups/world* |wc -l)
if (("$c" >= 19))
then
 f=$(ls -tr /home/neokyle/worldbackups/world* |head -n 1)
 rm -r "/home/neokyle/worldbackups/world/$f"
fi
DATE=$(date)
cp -r /home/neokyle/mcoriginal/creationnation/bin/world "/home/neokyle/worldbackups/world${DATE}"

---

### Post by TeoBigusGeekus on 2011-01-11
> **neokyle said:**
> when it reaches its limet this happens.

root@server:/# ./copyscript.sh
rm: cannot remove `/home/neokyle/worldbackups/world//home/neokyle/worldbackups/worldTue Jan 11 05:26:01 EST 2011:': No such file or directory

This is my script.

#!/bin/bash
c=$(ls -1 /home/neokyle/worldbackups/world* |wc -l)
if (("$c" >= 19))
then
 f=$(ls -tr /home/neokyle/worldbackups/world* |head -n 1)
 rm -r "/home/neokyle/worldbackups/world/$f"
fi
DATE=$(date)
cp -r /home/neokyle/mcoriginal/creationnation/bin/world "/home/neokyle/worldbackups/world${DATE}"
Change this line
```
rm -r "/home/neokyle/worldbackups/world/$f"
```
to
```
rm -r "/home/neokyle/worldbackups/$f"
```

---

### Post by neokyle on 2011-01-11
rm: cannot remove `/home/neokyle/worldbackups//home/neokyle/worldbackups/worldTue Jan 11 05:26:01 EST 2011:': No such file or directory


using script

#!/bin/bash
c=$(ls -1 /home/neokyle/worldbackups/world* |wc -l)
if (("$c" >= 19))
then
 f=$(ls -tr /home/neokyle/worldbackups/world* |head -n 1)
 rm -r "/home/neokyle/worldbackups/$f"
fi
DATE=$(date)
cp -r /home/neokyle/mcoriginal/creationnation/bin/world "/home/neokyle/worldbackups/world${DATE}"

---

### Post by TeoBigusGeekus on 2011-01-11
> **neokyle said:**
> rm: cannot remove `/home/neokyle/worldbackups//home/neokyle/worldbackups/worldTue Jan 11 05:26:01 EST 2011:': No such file or directory


using script

#!/bin/bash
c=$(ls -1 /home/neokyle/worldbackups/world* |wc -l)
if (("$c" >= 19))
then
 f=$(ls -tr /home/neokyle/worldbackups/world* |head -n 1)
 rm -r "/home/neokyle/worldbackups/$f"
fi
DATE=$(date)
cp -r /home/neokyle/mcoriginal/creationnation/bin/world "/home/neokyle/worldbackups/world${DATE}"
Rechange the line
```
rm -r "/home/neokyle/worldbackups/$f"
```
to
```
rm -r "$f"
```

---

### Post by neokyle on 2011-01-11
rm: cannot remove `/home/neokyle/worldbackups/worldTue Jan 11 05:26:01 EST 2011:': No such file or directory

i changed the line, that path is correct so i dont get it

---

### Post by TeoBigusGeekus on 2011-01-11
Output of
```
ls ~/neokyle/worldbackups
```
?

---

### Post by neokyle on 2011-01-11
1world                              worldTue Jan 11 08:52:46 EST 2011
1worldTue Jan 11 08:50:49 EST 2011  worldTue Jan 11 08:58:21 EST 2011
worldTue Jan 11 04:25:44 EST 2011   worldTue Jan 11 09:00:01 EST 2011
worldTue Jan 11 05:26:01 EST 2011   worldTue Jan 11 09:00:12 EST 2011
worldTue Jan 11 05:27:01 EST 2011   worldTue Jan 11 09:07:16 EST 2011
worldTue Jan 11 05:28:01 EST 2011   worldTue Jan 11 09:07:32 EST 2011
worldTue Jan 11 05:29:01 EST 2011   worldTue Jan 11 09:11:06 EST 2011
worldTue Jan 11 05:30:01 EST 2011   worldTue Jan 11 09:14:38 EST 2011
worldTue Jan 11 05:31:01 EST 2011   worldTue Jan 11 09:15:35 EST 2011
worldTue Jan 11 05:32:01 EST 2011   worldTue Jan 11 09:17:05 EST 2011
worldTue Jan 11 05:33:01 EST 2011   worldTue Jan 11 09:18:09 EST 2011
worldTue Jan 11 06:30:01 EST 2011   worldTue Jan 11 09:23:44 EST 2011
worldTue Jan 11 07:00:01 EST 2011   worldTue Jan 11 09:30:01 EST 2011
worldTue Jan 11 07:30:01 EST 2011   worldTue Jan 11 09:57:23 EST 2011
worldTue Jan 11 08:00:01 EST 2011   worldTue Jan 11 10:00:02 EST 2011
worldTue Jan 11 08:30:01 EST 2011   worldTue Jan 11 10:06:00 EST 2011
worldTue Jan 11 08:52:08 EST 2011   worldTue Jan 11 10:30:01 EST 2011

---

### Post by TeoBigusGeekus on 2011-01-11
The folder is there, the path is correct.
Post the script you're using in its current form again.

---

### Post by neokyle on 2011-01-11
#!/bin/bash
c=$(ls -1 /home/neokyle/worldbackups/world* |wc -l)
if (("$c" >= 19))
then
 f=$(ls -tr /home/neokyle/worldbackups/world* |head -n 1)
 rm -r "$f"
fi
DATE=$(date)
cp -r /home/neokyle/mcoriginal/creationnation/bin/world "/home/neokyle/worldbackups/world${DATE}"

Exactly my thoughts

---

### Post by TeoBigusGeekus on 2011-01-11
Found it (or maybe not...)
When we introduce the world* patterns, ls started to add additional lines between entries, so the condition (and its result) are completely wrong.
The only thing you can do is
```
#!/bin/bash
c=$(ls -1 /home/teo/Desktop/backup |grep -v nameoffoldertobeexcluded |wc -l)
if (("$c" >= 19))
then
f=$(ls -tr /home/teo/Desktop/backup |grep -v nameoffoldertobeexcluded |head -n 1)
rm -r "/home/teo/Desktop/backup/$f"
fi
DATE=$(date)
cp -r /home/teo/Desktop/orig/world "/home/teo/Desktop/backup/world$DATE"
```
[COLOR="Red"]This one of course will delete any other older folder you have in /backup.
I couldn't find any other way around it (unless someone knows a way to exclude a folder in the ls command).
So, you either move the folder mentioned in post#46, or created a completely separate backup folder.[/COLOR]


EDIT: I had forgotten about grep!!!! Forget what's written in red, the above script should work...

---

### Post by Grenage on 2011-01-11
> **TeoBigusGeekus said:**
> unless someone knows a way to exclude a folder in the ls command

Is this an option?

```
ls /home/teo/Desktop/backup | grep -v DIRECTORY
```

---

### Post by TeoBigusGeekus on 2011-01-11
Grep!!! Of course...
Spot on grenage!!! :P
```
#!/bin/bash
c=$(ls -1 /home/teo/Desktop/backup |grep -v nameoffoldertobeexcluded |wc -l)
if (("$c" >= 19))
then
f=$(ls -tr /home/teo/Desktop/backup |grep -v nameoffoldertobeexcluded |head -n 1)
rm -r "/home/teo/Desktop/backup/$f"
fi
DATE=$(date)
cp -r /home/teo/Desktop/orig/world "/home/teo/Desktop/backup/world$DATE"
```

I hope that's the last version of the script.

---

### Post by TeoBigusGeekus on 2011-01-11
...the forums gone berzerk herp derp....
deleted

---

### Post by TeoBigusGeekus on 2011-01-11
deleted

---

### Post by TeoBigusGeekus on 2011-01-11
deleted

---

### Post by Grenage on 2011-01-11
Peachy. :)

Wouldn't we just sell our souls for a 'delete post' option?

---

### Post by TeoBigusGeekus on 2011-01-11
> **Grenage said:**
> Peachy. :)

Wouldn't we just sell our souls for a 'delete post' option?

I think posts are in sync with linux itself; the forums presume that you know what you're doing... :popcorn:

---

### Post by sisco311 on 2011-01-11
I was bored, so I wrote my own version :)

```
#!/usr/bin/env bash

_error1 ()
{
  echo "error: SOURCE or DEST doesn't exist or is not a directory" >&2
  echo "USAGE: $0 [ SOURCE [ DEST ] ]" >&2
  exit 1
}

_error2 ()
{
  echo "error: failed to create backup" >&2
}

DIRNAME="$1"
BACKUP="$2"

# set the default directory names if no directories are specified
DIRNAME="${DIRNAME:-/home/sisco/xtmp/foo}"
BACKUP="${BACKUP:-/home/sisco/xtmp/bar}"

# number of maximum backup directories
BNUMBER="3"

# format of the date and the pattern which matches it
DATEF='%Y-%m-%d-%H:%M:%S'
DATEP='-[123][0-9][0-9][0-9]-[01][0-9]-[0123][0-9]-[012][0-9]:[012345][0-9]:[012345][0-9]'

# if SOURCE dir doesn't exits or is not a directory, then exit
[ -d "$DIRNAME" ] || _error1

# same for DEST dir
[ -d "$BACKUP" ] || _error1

# backup the dir
DIR="${DIRNAME##*/}"
DATE=$(date +"$DATEF")

cp -r -- "$DIRNAME" "${BACKUP}/${DIR}-${DATE}" || _error2

# check number of backups and delete the old ones if needed
i=0
for file in "${BACKUP}/${DIR}"${DATEP}; do
  i=$((i+1))
done

for file in "${BACKUP}/${DIR}"${DATEP}; do
  if (( i > BNUMBER )); then
    rm -rf -- "$file"
    i=$((i-1))
  else
    break
  fi
done

```

---

### Post by neokyle on 2011-01-11
I tried to stay on to finish this up and make sure the new script works but staying up till 11am is just a little to late for me :P

I dont think i made a new backup folder or changed a path. im using the same path that the script originally backed up to and it alyways placed the folders fine, right in the worldbackups folder. 

Hopefully this new script works :P

gonna finish off my breakfast and try it out.

your script looks allot bigger and more complicated sisco :D

---

### Post by neokyle on 2011-01-11
The new script works great. no errors, it removes a folder before placing a new one once it reaches its limit.

Thanks for all the help guys :)

time to go dance like an idiot out of excitement and joy :D

---

### Post by TeoBigusGeekus on 2011-01-11
Finally... glad to hear that...:)

PS: Don't forget to mark the thread as solved.

---

