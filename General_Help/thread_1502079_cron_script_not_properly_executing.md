---
title: "cron script not properly executing"
date: 2010-06-05
forum: General Help
---

### Post by capitales7 on 2010-06-05
First of all, so sorry about this seemingly silly cron question. I know a lot are asked, and are usually just environment related.

Anyway, I wrote a very simple PHP script to mount my external drive to a specific location as soon as it's switched on.
The script works great when run.
What's strange, is that it runs in cron and generates a log file, but for someone reason doesn't mount the drive when cron runs it.

I added in the full path to EVERYTHING in the script, and I'm calling it with the full path from crontab, but it doesn't mount my drive when run from cron.

I've tried running the individual commands on the cmd, and it all works. Starting to annoy me now... anyone have an idea?

---

### Post by dtfinch on 2010-06-05
Last I checked, cron (or rather run-parts) had problems with anything with a dot in the filename, like files ending in ".sh".

edit: related bug report [https://bugs.launchpad.net/ubuntu/+source/debianutils/+bug/38022](https://bugs.launchpad.net/ubuntu/+source/debianutils/+bug/38022)

---

### Post by capitales7 on 2010-06-05
> **dtfinch said:**
> Last I checked, cron (or rather run-parts) had problems with anything with a dot in the filename, like files ending in ".sh".

edit: related bug report [https://bugs.launchpad.net/ubuntu/+source/debianutils/+bug/38022](https://bugs.launchpad.net/ubuntu/+source/debianutils/+bug/38022)

never had a problem with that, but I removed the .php from my script and still nothing.
Thanks for the quick reply btw.

---

### Post by capitales7 on 2010-06-05
Could this be because cron isn't allowed to mount drives? I am using sudo in the script, but would that try to do sudo as the cron user? Obviously that would fail.
Perhaps a more correct question would be: is cron running as my user or it's own user?

---

### Post by dtfinch on 2010-06-05
Cron runs scripts as root. You don't need sudo in it. And I've had no trouble mounting drives from cron scripts.

Do you have any logging to determine whether the php script is running at all?

Did you add the full php command line to run it to your cron tab, or did you put the script in one of the existing cron folders (like cron.daily)? If the latter, the script would have to be marked as executable, and the first line of the script would have to specify the php command to run it, "#!/usr/bin/php -q".

---

### Post by thebigob on 2010-06-05
Cron scripts should run as the user that the cron entry is for. NOT always as root as has been suggested.

EG as user run
```

crontab -l

```then do 
```

sudo crontab -l

```You should see they are different.

EG here is mine 

```

callum@callumlap:~$ crontab -l
no crontab for callum
callum@callumlap:~$ sudo crontab -l
[sudo] password for callum: 
no crontab for root
callum@callumlap:~$ 

```

If you want to be sure you are running it as root (like your script requires) be sure to put your script in roots crontab and not your users.

---

### Post by mike2357 on 2010-06-05
There are often subtle differences between running things with cron versus the command line.  For instance, cron generally runs with a very limited PATH, so sometimes a command that otherwise runs fine is invisible to cron.

Have you tried sending the output of cron to an output file?  Example:

```
0 20 * * *  /home/user/script_to_be_run.sh > /home/user/OUT_FILE 2>&1
```

Then after cron runs the next time, you can check the output and hopefully get a better idea of what went wrong.  BTW, the "2>&1" means, "send both regular script output and error messages to the same file", which in this case is OUT_FILE.

---

### Post by capitales7 on 2010-06-05
I've added absolute paths in cron as well as in the script (e.g. /usr/bin/cut). So that's covered.
I also tried outputting to a file, which gets updated at the cron run time, so the script is being called for sure. 

I also just added it to roots crontab, yet nothing! I never had this problem before. Is ubuntu 10 to blame???

---

### Post by mike2357 on 2010-06-05
Could you post the output of "crontab -l" please?  Also, are you sure the cron command is not working?  In other words, is the mount working but then something is later unmounting the drive?  You could add something to your script to check to see of the mount worked, such as "ls -l /mnt/mydrive/something".

I don't think 10.04 is to blame.  All of my cron commands are running fine, although I don't have one which mounts drives.

---

### Post by capitales7 on 2010-06-05
* * * * * /usr/bin/php /home/sia/check_ext
That's crontab.
Nothing is unmounting the drive. If I mount it or rn the script manually, it remains mounted.

I added another command to ls -l /media/External RIGHT after the actual mount command, and told that command to output to mnt.log. mnt.log was created, and said "total 0".

This proves that the script run by cron can't mount... which is strange.

---

### Post by mike2357 on 2010-06-05
Gee whiz, I'm really sorry, but I'm out of ideas.  If I think of anything over the next few days, I'll post back.

Three thoughts come to mind:
1.  Does running the script through cron work if you happen to be logged in when cron fires?
2.  Is the device you are trying to mount actually connected (i.e. via a USB port) or is a device on a wireless network?
3.  Are there any commands in your script that do any window manipulation?

I'm probably grasping for straws.

---

### Post by capitales7 on 2010-06-06
> **mike2357 said:**
> Gee whiz, I'm really sorry, but I'm out of ideas.  If I think of anything over the next few days, I'll post back.

Three thoughts come to mind:
1.  Does running the script through cron work if you happen to be logged in when cron fires?
2.  Is the device you are trying to mount actually connected (i.e. via a USB port) or is a device on a wireless network?
3.  Are there any commands in your script that do any window manipulation?

I'm probably grasping for straws.

1) nope :(
2) USB, my script actually looks for the disk/by-id/ to mount it
3) nope...

thanks. let me know if you think anything.

---

### Post by bodhi.zazen on 2010-06-06
Post your script

---

### Post by capitales7 on 2010-06-06
[PHP]
<?

$command = "/bin/ls -l /dev/disk/by-id | /bin/grep SAMSUNG_HD103UJ_131801975FFF-0:0-part1 | /usr/bin/cut -d' ' -f10";
exec($command, $drive);
$loc = substr($drive[0], -4);

if(!empty($drive))
{
        $command = "/bin/ls -l /media/External | /bin/grep total | /usr/bin/cut -d' ' -f2";
        exec($command, $mount);
        if($mount[0] == 0)
        {
                $command = "/bin/mount /dev/$loc /media/External";
                exec($command);
        }
}

?>
[/PHP]

Pretty simple script. Basically checks for the ID of the drive. If it's there, it will do an ls on the mount point to see if it returns 0 or not (i.e. if it's mounted already). If not, it mounts it.
I removed the sudo bit because I now run it in root's crontab.
It works when I run at as root manually still.

---

### Post by mike2357 on 2010-06-06
There appears to be some differences in the way the "ls -l" command behaves when root runs it from cron.  When I ran "sudo ls -l <directory>" from the command line, the date was given for files like this:
2010-06-06 18:15
But when run from cron, it looked like this:
Jun  6 18:15

That would make the number of fields different, which would make your cut -f command not work as you expected.

You can run "man ls" and look at the time-syle option, but it looks like
ls -l --time-style=long-iso <directory>
might do the trick for you.

---

### Post by capitales7 on 2010-06-06
u little genius you! :)
How odd though, that cron runs ls -l differently! Or maybe not... can't see why it would though!

Thanks dude. Now time to add a media server restart to the script and my wife can't simply switch on the drive, and voila, media is ready for streaming :D

---

