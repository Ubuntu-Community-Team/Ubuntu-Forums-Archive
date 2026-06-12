---
title: "Problems with cronjob"
date: 2009-08-20
forum: General Help
---

### Post by ebp on 2009-08-20
Hi

I'm running some cronjob on my sheevaplug but one of them doesn't work. My crontab is:

Code:
```


# m h  dom mon dow   command

@hourly /flexget/flexget.py -q

*/10 * * * * /flexget/watchdog.sh

@hourly gpodder -r


```

The script i have problems with is watchdog, when i run it from the commandline it works fine, but as a cronjob it doesn't work. The content of the script is: 


```


#!/bin/bash

#Watch dir, may contain spaces:
watchdir="/mnt/mybook/Torrent/torrentfiler/showrss/"

#move file to a subdirectory? if Commented out, it'll removed remove
# the torrent file.
# Note: Don't put a '/' before the path!
movesubdir="added/"

# Authentication "username:password":
tr_auth="brugernavn:kodeord"

# Transmission host "ip:port":
tr_host="127.0.0.1:9091"

# Verbose?
verbose=1


```

Hope you can help :)

---

### Post by DaithiF on 2009-08-20
Hi, I don't think thats all the script, is it?  It doesn't seem to do anything other than set some variables.

---

### Post by ajgreeny on 2009-08-20
Does the script also work when you double click on it in nautilus?  I am not sure also if you have used the full pathway to the sh file in the crontab.  If you haven't, change the pathway, eg if the sh file is in your home, it will be ```
* 10 * * * * /home/username/path/to/file.sh
```Incidentally, why the forward slash in * /10 * * * *?

---

### Post by ebp on 2009-08-21
> **DaithiF said:**
> Hi, I don't think thats all the script, is it?  It doesn't seem to do anything other than set some variables.

Oh sorry you are absolutely right this is the whole script:

```


#!/bin/bash

# Watch dir, may contain spaces:
watchdir="/mnt/mybook/Torrent/torrentfiler/showrss/"

# move file to a subdirectory? if Commented out, it'll removed remove
# the torrent file.
# Note: Don't put a '/' before the path!
movesubdir="added/"


# Authentication "username:password":
tr_auth="brugernavn:kodeord"

# Transmission host "ip:port":
tr_host="127.0.0.1:9091"

# Verbose?
verbose=1

#############################################
time=$(date "+%Y-%m-%d (%H:%M:%S)")
if [ -n "$tr_auth" ]; then
    tr_auth="--auth=$tr_auth"
fi

for file in "$watchdir"*.torrent
do
    if [ -f "$file" ]; then
        if [ -n "$verbose" ]; then echo "$time: $file added to queue."; fi

        /usr/bin/transmission-remote "$tr_host" "$tr_auth" -a "$file" > /dev/null
        # give the remote some time to process
        sleep 5

        if [ $movesubdir ]; then
            if [ -d "$watchdir$movesubdir" ]; then
                mv "$file" "$watchdir$movesubdir"
            else
                mkdir "$watchdir$movesubdir"
                mv "$file" "$watchdir$movesubdir"
            fi
        else
            rm "$file"
        fi
    else
        if [ -n "$verbose" ]; then echo "$time: No torrent in $watchdir."; fi
    fi
done

exit 0


```

---

### Post by ebp on 2009-08-21
> **ajgreeny said:**
> Does the script also work when you double click on it in nautilus?  I am not sure also if you have used the full pathway to the sh file in the crontab.  If you haven't, change the pathway, eg if the sh file is in your home, it will be ```
* 10 * * * * /home/username/path/to/file.sh
```Incidentally, why the forward slash in * /10 * * * *?

If i don't use the slash i get an error when trying to edit my crontab:

```

root@simba:~# crontab -e
crontab: installing new crontab
"/tmp/crontab.hbUCuF/crontab":4: bad command
errors in crontab file, can't install.
Do you want to retry the same edit? 

```


I run this on my sheevaplug which is a headless server so i can't double click on it in nautilus :)

---

### Post by DaithiF on 2009-08-21
regarding the '/', 
*/10 means run every 10 minutes|hours|days etc, depending on which field has the /10 attached to it.

to see whats going on with the script when run by cron, (and indeed to make sure that it is actually getting run by cron!) I would suggest adding some logging.

so capture stdout and stderr output in a file by changing the command like this
*/10 * * * * /flexget/watchdog.sh 2>&1 >> /home/yourusername/cronoutput.log

then wait and see what turns up in this file.

---

### Post by ebp on 2009-08-21
> **DaithiF said:**
> regarding the '/', 
*/10 means run every 10 minutes|hours|days etc, depending on which field has the /10 attached to it.

to see whats going on with the script when run by cron, (and indeed to make sure that it is actually getting run by cron!) I would suggest adding some logging.

so capture stdout and stderr output in a file by changing the command like this
*/10 * * * * /flexget/watchdog.sh 2>&1 >> /home/yourusername/cronoutput.log

then wait and see what turns up in this file.

I have done as you said, the file was created but there's nothing in it

---

### Post by wojox on 2009-08-21
You have to put the file in /usr/bin or /usr/local/bin or /bin.
You could also edit /etc/crontab and add the new path to you scripts directory.

---

### Post by DaithiF on 2009-08-21
ok, well at least we know that its running.

next step add some logging statements to the script to track its progress.  example here:

```
#!/bin/bash
echo "Start of script"

# Watch dir, may contain spaces:
watchdir="/mnt/mybook/Torrent/torrentfiler/showrss/"

# move file to a subdirectory? if Commented out, it'll removed remove
# the torrent file.
# Note: Don't put a '/' before the path!
movesubdir="added/"


# Authentication "username:password":
tr_auth="brugernavn:kodeord"

# Transmission host "ip:port":
tr_host="127.0.0.1:9091"

# Verbose?
verbose=1

#############################################
time=$(date "+%Y-%m-%d (%H:%M:%S)")
if [ -n "$tr_auth" ]; then
    tr_auth="--auth=$tr_auth"
fi

echo "About to look for files in '$watchdir'"
num_torrents=$(ls "$watchdir"*.torrent | wc -l)
echo "There are $num_torrents torrents in the directory"
for file in "$watchdir"*.torrent
do
    if [ -f "$file" ]; then
        if [ -n "$verbose" ]; then echo "$time: $file added to queue."; fi

        echo "About to call tranmission-remote with params $tr_host $tr_auth -a $file"
        /usr/bin/transmission-remote "$tr_host" "$tr_auth" -a "$file" > /dev/null
        # give the remote some time to process
        sleep 5

        if [ $movesubdir ]; then
            if [ -d "$watchdir$movesubdir" ]; then
                echo "About to run command: mv $file $watchdir$movesubdir"
                mv "$file" "$watchdir$movesubdir"
            else
                echo "About to run command: mkdir $watchdir$movesubdir"
                mkdir "$watchdir$movesubdir"
                echo "About to run command: mv $file $watchdir$movesubdir"
                mv "$file" "$watchdir$movesubdir"
            fi
        else
               echo "About to run command: rm $file"
            rm "$file"
        fi
    else
        if [ -n "$verbose" ]; then echo "$time: No torrent in $watchdir."; fi
    fi
done
echo "Finished loop"
exit 0
```

---

### Post by DaithiF on 2009-08-21
> **wojox said:**
> You have to put the file in /usr/bin or /usr/local/bin or /bin.


why is that?  the OP is using an absolute path to the script in their crontab.  
```
/flexget/watchdog.sh
```
If they were just giving the name of a command/script then yes, it would need to be in the path, but with an absolute path the script can be anywhere.
So while its unusual to hang a directory off root like that, as long as that directory exists there it should work.  

Although worth confirming I guess.  ebp -- where exactly is your watchdog.sh script located?  Or more to the point, where is your flexget directory?

---

### Post by ebp on 2009-08-21
I have fixed it, but i'm sorry i have wasted your time. The problem was my own fault, since i'm not terribly good at english i by mistake called the scrip whatchdog and it should have been watchdog as in the crontab.

---

### Post by xyepblra on 2009-11-15
Somebody please help me telling what buttons you have to press in order to save the crontab file edited inside the terminal window.
Besides, does ```
* 1 * * * /home/xyepblra/.custom_scripts/custom_script_1.sh
``` line added to the crontab file seem to be correct as a command invoking an hourly executed shell script to you?

---

### Post by dcstar on 2009-11-15
> **xyepblra said:**
> Somebody please help me telling what buttons you have to press in order to save the crontab file edited inside the terminal window.
.......

The crontab -e command invokes whatever editor is set with this:

```
sudo update-alternatives --config editor
```

---

### Post by DaithiF on 2009-11-16
[FONT=monospace]> * 1 * * * /home/xyepblra/.custom_scripts/custom_script_1.sh

this crontab will run every minute of the 1st hour of the day (ie. 1:00 am to 1:59am), which I don't think is what you want.

To run every hour, you could do either of these:
[/FONT]```
5 * * * * /home/xyepblra/.custom_scripts/custom_script_1.sh
runs at 5minutes past the hour, each hour.

[FONT=monospace][/FONT][CODE]
```* /1 * * * /home/xyepblra/.custom_scripts/custom_script_1.sh
[/CODE]

---

