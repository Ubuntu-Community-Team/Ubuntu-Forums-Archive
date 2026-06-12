---
title: "rtorrent -- auto-unrar and delete data on completed."
date: 2009-11-12
forum: General Help
---

### Post by IamHungry on 2009-11-12
I have recently upgraded to 9.10 ubuntu with 0.8.5 rtorrent. 

I use flexget to filter and download torrents from Rss feeds.  The torrents are put in a specific directory watched by rtorrent.  The torrent is loaded, the file downloaded into the incoming directory, and moved to another specific directory.  Rtorrent continues to dowload until ratio is met, then deletes the torrent file.

This process is working well for me now, but I would like to make a few changes.  I want rotorrent to unrar the files on completion, keep seeding until ratio is met, then delete the RAR files when it deletes the torrent file.  

I believe i used something like this in the older version of rtorrent:
on_finished = unrar_on_completion,"execute=unrar,e,$d.get_base_path=,*"

And the new version would be something like this:
system.method.set_key = event.download.finished,unrar_on_completion,"execute=unrar,e,$d.get_base_path=,*"

Does that sound right?

I am not sure how to make rtorrent delete the RAR files when it deletes the torrents.  Would something like this be correct:

system.method.set_key = event.download.finished,delete_data,"execute=rm,$d.get_name="

Or am I going about this all wrong?

Any advice would be appreciated.

---

### Post by gymmarn on 2010-02-05
Hi

I can give you my script of unraring the files when the whole torrent is downloaded. It also manages .zip and .001 files.

I haven't found a solution on deleting the .rar/.001/.zip files when the ratio is met however.

Here goes:

In .rtorrent.rc add this to invoke the script:
```

system.method.set_key = event.download.finished,unpack_rar,"execute=~/unrar_files.sh,$d.get_base_path="
```

Then make the script in the home folder of the user which runs rtorrent (you can specify searchpath if you want aswell but I won't add this in my example).

vim unrar_files.sh

Cut-n-paste this:
Note you need to change "nedladdat/torrents" to the folder your rtorrent download files to. And "/home/viktor" to the folder the user your using.
These two checks are there for rtorrent freaks out if the script takes too long to complete.
```

#!/bin/bash
#Skapat av Gymmarn 2010-02-11
#Variabel $1 is the folder sent
#Start to check if we're in the right folder (rTorrent seems to bug sometimes)
if [ "$(ls -d $1 | grep -F nedladdat/torrents/)" ]; then
        #Create only 1 instance of this script to avoid rTorrent crashing
        if [ ! "$(ls /home/viktor/ | fgrep -i pidfile)" ]; then
                yes no | nice -n 15 touch /home/viktor/pidfile
                #Find and repeat for all folders and subfolders
                for directory in $(find $1 -type d); do
                        #Check for .rar files and unpack them if found
                        if [ "$(ls $directory | fgrep -i .rar)" ]; then
                                rarFile=`ls $directory | fgrep -i .rar`;
                                searchPath="$directory/$rarFile"
                                yes no | nice -n 15 unrar x -o+ $searchPath $directory
                        #Check for .001 files and unpack them if found
                        elif [ "$(ls $directory | fgrep -i .001)" ]; then
                                rarFile=`ls $directory | fgrep -i .001`;
                                searchPath="$directory/$rarFile"
                                yes no | nice -n 15 unrar x -o+ $searchPath $directory
                        #Check for .zip files and unpack them if found
                        elif [ "$(ls $directory | fgrep -i .zip)" ]; then
                                for zipFiles in `ls $directory | fgrep -i .zip`; do
                                        searchPath="$directory/$zipFiles"
                                        yes no | nice -n 15 unzip -n $searchPath -d $directory
                                done
                                #When there is .zip files there is often .rar/.001 in them. Check and unpack if so
                                if [ "$(ls $directory | fgrep -i .rar)" ]; then
                                rarFile=`ls $directory | fgrep -i .rar`;
                                searchPath="$directory/$rarFile"
                                yes no | nice -n 15 unrar x -o+ $searchPath $directory
                                #Check for .001 files and unpack them if found
                                elif [ "$(ls $directory | fgrep -i .001)" ]; then
                                rarFile=`ls $directory | fgrep -i .001`;
                                searchPath="$directory/$rarFile"
                                yes no | nice -n 15 unrar x -o+ $searchPath $directory
                                fi
                        fi
                done
                yes no | nice -n 15 rm -f /home/viktor/pidfile
        fi
fi

```


I'm no programmer and things could probably be made nicer, but here it is in all it's glory :)

---

### Post by Loginbug on 2010-03-04
Does not work for me.

I have added this in .rtorrent.rc file.

> system.method.set_key = event.download.finished,unpack_rar,"execute=/root/unrar_files.sh,$d.get_base_path="
Then i have saved your script as is in /root/unrar_files.sh
Then chmod +x unrar_files.sh
Then program restart

When a download is finisched it does not happen anything.

Please help.
:?:

---

### Post by gymmarn on 2010-03-04
> **Loginbug said:**
> Does not work for me.

I have added this in .rtorrent.rc file.


Then i have saved your script as is in /root/unrar_files.sh
Then chmod +x unrar_files.sh
Then program restart

When a download is finisched it does not happen anything.

Please help.
:?:

I added my newest version of the script in my previous post.

Have you tried running the command manually, ie:
./unpack_files.sh /folder/where/the/files/are

You need to have unrar and unzip installed.

---

### Post by Loginbug on 2010-03-05
Very Thanks, i will try. I'm the [owner of italian wtorrent mod]("http://code.google.com/p/wtorrent/"). ;)

---

### Post by Loginbug on 2010-03-06
it works, but i have a small problem. I'm using the sub-directory future with wTorrent and my download directory contains other directories such as **user1**, **user2**, ..

How can i edit this line?

```
if [ "$(ls -d $1 | grep -F /downloads/ ??? )" ]; then
```

---

### Post by Loginbug on 2010-03-07
Found a solution: repeat the script for any user dir.

The script works, but not with rtorrent. I think it sends wrong path to script. Any ideas? :)

---

### Post by Ahmedmb on 2010-05-15
u can use 'event.download.erased' & 'event.download.finished' events

---

### Post by kroem on 2010-10-08
Gymmarn! I've been using your scrip for a couple of months and love it, thank you!

...however...from today it just stopped working, have no idea why. hehe

E: got is working, was something with the pid...thingy.

---

### Post by toinou on 2010-11-06
Hi
I'd like to thank you for this script.
I've used it as part as a complex script that rsyncs with my seedbox, expands files, rename them if necessary sends those files to flexget, which will move them to the appropriate folders.
Today I'm facing a slight glitch : if one of the folder includes a space followed by a - (e.g "... -CLA..."), ls would interpret it as a parameter and fail.
I have yet to find a way to preserve folders path between quotes. I'm scratching my head right now.

*** EDIT ***

Turns out it wasn't a ls issue.
It is a "for loop" issue ; the "for / do / if / elif" loop considers spaces as delimiters. A folder with a space in its name will be splitted and interpreted as two paths.
This issue can be solved by modifying the IFS variable.
More info here
[http://www.cyberciti.biz/tips/handling-filenames-with-spaces-in-bash.html](http://www.cyberciti.biz/tips/handling-filenames-with-spaces-in-bash.html)

Regards,

     Toinou

---

### Post by toinou on 2011-03-28
gymmarn's amazing script led me to write my own script that could do a bit more than just expanding rar archives.
One thing led to another, my script is now a ginormous 60kb shell script that I'd like to share with you.
[http://code.google.com/p/torrentexpander/](http://code.google.com/p/torrentexpander/)

I hope you enjoy it

      Toinou

---

### Post by Thyrael31 on 2011-04-12
Hello,

i found this Thread on Google, i'm searching for a Script that extract my finished Torrents but i dont have the ability to install 'unrar' on my [IPFire](http://www.ipfire.org/). Is there a possibility to use gymmarns Script with 7zip?

I tried this so far:
```
#!/bin/bash
#Skapat av Gymmarn 2010-02-11
#Variabel $1 is the folder sent
#Start to check if we're in the right folder (rTorrent seems to bug sometimes)
if [ "$(ls -d $1 | grep -F var/ipfire/samba/rtorrent/download/)" ]; then
        #Create only 1 instance of this script to avoid rTorrent crashing
        if [ ! "$(ls /var/ipfire/samba/rtorrent/ | fgrep -i pidfile)" ]; then
                yes no | nice -n 15 touch /var/ipfire/samba/rtorrent/pidfile
                #Find and repeat for all folders and subfolders
                for directory in $(find $1 -type d); do
                        #Check for .rar files and unpack them if found
                        if [ "$(ls $directory | fgrep -i .rar)" ]; then
                                rarFile=`ls $directory | fgrep -i .rar`;
                                searchPath="$directory/$rarFile"
                                yes no | nice -n 15 7z x -o+ $searchPath $directory
                        #Check for .001 files and unpack them if found
                        elif [ "$(ls $directory | fgrep -i .001)" ]; then
                                rarFile=`ls $directory | fgrep -i .001`;
                                searchPath="$directory/$rarFile"
                                yes no | nice -n 15 7z x -o+ $searchPath $directory
                        #Check for .zip files and unpack them if found
                        elif [ "$(ls $directory | fgrep -i .zip)" ]; then
                                for zipFiles in `ls $directory | fgrep -i .zip`; do
                                        searchPath="$directory/$zipFiles"
                                        yes no | nice -n 15 7z x $searchPath -d $directory
                                done
                                #When there is .zip files there is often .rar/.001 in them. Check and unpack if so
                                if [ "$(ls $directory | fgrep -i .rar)" ]; then
                                rarFile=`ls $directory | fgrep -i .rar`;
                                searchPath="$directory/$rarFile"
                                yes no | nice -n 15 7z x -o+ $searchPath $directory
                                #Check for .001 files and unpack them if found
                                elif [ "$(ls $directory | fgrep -i .001)" ]; then
                                rarFile=`ls $directory | fgrep -i .001`;
                                searchPath="$directory/$rarFile"
                                yes no | nice -n 15 7z x -o+ $searchPath $directory
                                fi
                        fi
                done
                yes no | nice -n 15 rm -f ~/pidfile
        fi
fi
```

but if i start the Script manually, i become this Errormessage:

```
7-Zip 4.65  Copyright (c) 1999-2009 Igor Pavlov  2009-02-03
p7zip Version 4.65 (locale=en_US.utf8,Utf16=on,HugeFiles=on,2 CPUs)


Error:
Cannot use absolute pathnames for this command
```

---

### Post by toinou on 2011-04-14
Hi Thyrael31
I never tried 7z and I don't have it installed, but you may want to read the [7z man]("http://pwet.fr/man/linux/commandes/7z") in order to adapt gymmarn's script.
From what I read, the command should look a bit like this :
nice -n 15 7z x -o "$directory" "$searchPath"

I have yet to find a way to make sure 7z won't get stuck if an item from the archive already exists in $directory (-o+ in the unrar commandline stands for overwrite)

      Toitoinou

---

### Post by Thyrael31 on 2011-04-14
Thank you for your Replay toinou. i tried your suggestions but unfortunately, it didn't work, it shows a "Incorrect Command Line" Error. I read the 7z Manual, the Option for extract a File to a specified Location is the -o Switch, but i dont know how to make the Script work because my knowledge about scripting is very limited. :oops:

---

### Post by toinou on 2011-04-14
Hi Thyrael31
Try this
nice -n 15 7z x -y "$searchPath" -o"$directory"
(make sure there is no space between the -o and "$directory")
This command line is kinda weird but it should work

If you face issues with files that have a space in them, see this post
[http://ubuntuforums.org/showpost.php?p=10080257&postcount=10](http://ubuntuforums.org/showpost.php?p=10080257&postcount=10)

     Toinou

---

### Post by Thyrael31 on 2011-04-14
Thank you again toinou, the Script is working now! :D But only when i'm using it manually with: *./unpack_files.sh /folder/where/the/files/are*

When rTorrent (Version is 0.8.6) finished a download, nothing happens. :-s The Folders dont have a space in its Name.

Edit:
It works now, but only when rTorrent run as root. Oo

---

### Post by toinou on 2011-04-15
Hi Thyrael31
Running a torrent client on root level is probably not a great idea.
Have you made sure the regular rTorrent user has execution rights for running 7z and the unrar script (aka: -rwxr-xr-x permissions on those two files) 

      Toinou

---

### Post by Thyrael31 on 2011-04-15
Thats the weird Part, for testing, i set both Files to 777 but no effect. If i log in with the rtorrent User and execute the Script manually it works fine.

Edit:

It works now!! Because someone from the IPFire Forums told me i should try to set the complete Path to 7z in the Script and that was the last bit, now rtorrent run as a User and it unpacks the torrents that finished downloading. :D Thank you toinou for your Time and Help!

That is the complete Script now:


```
#!/bin/bash
#Skapat av Gymmarn 2010-02-11
#Variabel $1 is the folder sent
#Start to check if we're in the right folder (rTorrent seems to bug sometimes)
if [ "$(ls -d $1 | grep -F var/ipfire/samba/rtorrent/download/)" ]; then
        #Create only 1 instance of this script to avoid rTorrent crashing
        if [ ! "$(ls /var/ipfire/samba/rtorrent/ | fgrep -i pidfile)" ]; then
                yes no | nice -n 15 touch /var/ipfire/samba/rtorrent/pidfile
                #Find and repeat for all folders and subfolders
                for directory in $(find $1 -type d); do
                        #Check for .rar files and unpack them if found
                        if [ "$(ls $directory | fgrep -i .rar)" ]; then
                                rarFile=`ls $directory | fgrep -i .rar`;
                                searchPath="$directory/$rarFile"
                                yes no | nice -n 15 /usr/local/bin/7z x -y "$searchPath" -o"$directory"
                        #Check for .001 files and unpack them if found
                        elif [ "$(ls $directory | fgrep -i .001)" ]; then
                                rarFile=`ls $directory | fgrep -i .001`;
                                searchPath="$directory/$rarFile"
                                yes no | nice -n 15 /usr/local/bin/7z x -y "$searchPath" -o"$directory"
                        #Check for .zip files and unpack them if found
                        elif [ "$(ls $directory | fgrep -i .zip)" ]; then
                                for zipFiles in `ls $directory | fgrep -i .zip`; do
                                        searchPath="$directory/$zipFiles"
                                        yes no | nice -n 15 /usr/local/bin/7z x -y "$searchPath" -o"$directory"
                                done
                                #When there is .zip files there is often .rar/.001 in them. Check and unpack if so
                                if [ "$(ls $directory | fgrep -i .rar)" ]; then
                                rarFile=`ls $directory | fgrep -i .rar`;
                                searchPath="$directory/$rarFile"
                                yes no | nice -n 15 /usr/local/bin/7z x -y "$searchPath" -o"$directory"
                                #Check for .001 files and unpack them if found
                                elif [ "$(ls $directory | fgrep -i .001)" ]; then
                                rarFile=`ls $directory | fgrep -i .001`;
                                searchPath="$directory/$rarFile"
                                yes no | nice -n 15 /usr/local/bin/7z x -y "$searchPath" -o"$directory"
                                fi
                        fi
                done
                yes no | nice -n 15 rm -f /var/ipfire/samba/rtorrent/pidfile
        fi
fi
```

---

### Post by toinou on 2011-04-15
Hi Thyrael31

Unix language tends to be difficult to tame.
Being a beginner myself, I learnt all I know today by writing my own script. After countless hours of pulling my hair, I published this neat little script.
[http://code.google.com/p/torrentexpander/source/browse/trunk/torrentexpander.sh](http://code.google.com/p/torrentexpander/source/browse/trunk/torrentexpander.sh)

Sometimes you face fonctions that work only on selected platforms, sometimes you struggle with buggy functions, sometimes some fonctions are not aliased, and sometimes they are aliased to a function with a parameter specified...
If there's something I'm sure of now it is that the more you learn about UNIX, the less you know. But being able to overcome a challenging line of code is always fulfilling.

I'll implement 7z in a future update of my script in order to improve its compatibility. I'll keep the line we came up with for future reference.

       Toinou

---

### Post by arrrghhh on 2011-11-04
> **toinou said:**
> gymmarn's amazing script led me to write my own script that could do a bit more than just expanding rar archives.
One thing led to another, my script is now a ginormous 60kb shell script that I'd like to share with you.
[http://code.google.com/p/torrentexpander/](http://code.google.com/p/torrentexpander/)

I hope you enjoy it

      Toinou

Hopefully this thread isn't too old.

I have rTorrent + flexget configured, and I was hoping to find a way to extract RAR files automatically after a download finishes.

It seems torrentexpander is a great solution, but perhaps it's too powerful for my tiny brain to understand!

I have configured the ini file as simply as possible - I added a destination folder, and set everything else to 'no'.  When I run it manually, it asks for an ID of the torrent source.  So I point it to my complete download directory.  Then it asks for a destination folder, which is just a folder I created in my complete folder called "undone".

It runs... and runs... and runs?  It seems to be in some sort of a loop.  It creates a temp directory and copies seemingly all my files from my complete folder - even a pdf?  Its not renaming any files, however it did unrar at least one.  Which is great - but why is it copying all these other files?  Also, once its done... it seems to start over again, and recopies all of the files again in a folder one deeper?  I'm not sure what I've done wrong.

I think eventually I'd like to look into the renaming/cleaning abilities of this script - but for now I'd just like to get it to unrar automatically & remove the rar files (and possibly folders?) when the download is complete.  It seems I can put a hook in flexget or better yet in rtorrent when the download is complete, run your script.  But if I can't get it to run manually, I worry about setting it up to run automatically.  Thanks!

---

### Post by toinou on 2011-11-12
Hi arrrghhh

The best option is to configure torrentexpander to be launched by Flexget (that's what I've been doing for months now)
[http://code.google.com/p/torrentexpander/wiki/How_to_setup_this_script_with_Flexget](http://code.google.com/p/torrentexpander/wiki/How_to_setup_this_script_with_Flexget)

Another way to run torrentexpander is to have rTorrent trigger it. A torrentexpander user contributed this page to my project :
[http://code.google.com/p/torrentexpander/issues/detail?id=15](http://code.google.com/p/torrentexpander/issues/detail?id=15)

     Toitoinou

---

### Post by arrrghhh on 2011-11-13
> **toinou said:**
> Hi arrrghhh

The best option is to configure torrentexpander to be launched by Flexget (that's what I've been doing for months now)
[http://code.google.com/p/torrentexpander/wiki/How_to_setup_this_script_with_Flexget](http://code.google.com/p/torrentexpander/wiki/How_to_setup_this_script_with_Flexget)

Another way to run torrentexpander is to have rTorrent trigger it. A torrentexpander user contributed this page to my project :
[http://code.google.com/p/torrentexpander/issues/detail?id=15](http://code.google.com/p/torrentexpander/issues/detail?id=15)

     Toitoinou

Yes, thank you for those tips.

But I'm having trouble manually running the script - it seems to copies a lot of files, when all I want it to do is extract any .rar/.zip files and delete the compressed files on a successful decompression.

Is this possible?  Can I use torrentexpander to simply extract files?  How do I achieve this?

Thanks!

---

### Post by toinou on 2011-11-13
Hi
The whole idea behind my script is to be able to manage most filetypes
If you have it launched by flexget, only files identified by flexget will be handled by my script
If you only need an unrar/unzip script, you should maybe use the script by gymmarn

       Toitoinou

---

### Post by arrrghhh on 2011-11-13
> **toinou said:**
> Hi
The whole idea behind my script is to be able to manage most filetypes
If you have it launched by flexget, only files identified by flexget will be handled by my script
If you only need an unrar/unzip script, you should maybe use the script by gymmarn

       Toitoinou

Hrm.  Perhaps I missed the point of your script then.  I do want it to trigger on stuff from Flexget, but I fear if I cannot run it manually, then I will not be able to run it from Flexget.

Thanks, I'll look at gymarn's script.

---

### Post by toinou on 2011-11-16
You should definitely try to run my script manually.
There is a basic GUI included that will enable you to choose the directory you want to unzip/unrar and where you want to unrar it.
By default, my script will try to use the torrent directory to rename the resulting file, so you should only run it with one torrent at a time.

      Toitoinou

---

### Post by pyroscope on 2011-11-16
Unrar stuff, with or without deleting the RARs: [https://pastee.org/rzms4](https://pastee.org/rzms4)

Delete the original RARs only after some ratio and/or whatever other condition (older than x days) is met: [http://code.google.com/p/pyroscope/wiki/RtControlExamples#Ratio_Management](http://code.google.com/p/pyroscope/wiki/RtControlExamples#Ratio_Management)

---

### Post by arrrghhh on 2011-11-17
> **toinou said:**
> You should definitely try to run my script manually.
There is a basic GUI included that will enable you to choose the directory you want to unzip/unrar and where you want to unrar it.
By default, my script will try to use the torrent directory to rename the resulting file, so you should only run it with one torrent at a time.

      Toitoinou

I thought I explained that I did try to run it manually, and the script failed miserably.  I'm sure it's user-error, and I'm usually pretty good at figuring this stuff out... but your script stumps me.  I can't get it to do what I want, at all.

> **pyroscope said:**
> Unrar stuff, with or without deleting the RARs: [https://pastee.org/rzms4](https://pastee.org/rzms4)

Delete the original RARs only after some ratio and/or whatever other condition (older than x days) is met: [http://code.google.com/p/pyroscope/wiki/RtControlExamples#Ratio_Management](http://code.google.com/p/pyroscope/wiki/RtControlExamples#Ratio_Management)

I'll check these out, thanks!

---

### Post by toinou on 2011-11-22
Hi
pyroscope's suggestions are probably the most appropriate option.
What I meant by running torrentexpander manually was only run /path/to/torrentexpander.sh
This should enable you to select source torrent and destination through a basic "GUI".
This way, the script should display issues in configuration.

I'm currently testing torrentexpander on Debian 6, Ubuntu 9.04, Ubuntu 11.10, Mac OS 10.7 and NetworkedMediaTank and default options seem to run smoothly.
What platform have you tried to run torrentexpander on ?

Thanks

---

### Post by arrrghhh on 2011-11-24
> **toinou said:**
> Hi
pyroscope's suggestions are probably the most appropriate option.
What I meant by running torrentexpander manually was only run /path/to/torrentexpander.sh
This should enable you to select source torrent and destination through a basic "GUI".
This way, the script should display issues in configuration.

I'm currently testing torrentexpander on Debian 6, Ubuntu 9.04, Ubuntu 11.10, Mac OS 10.7 and NetworkedMediaTank and default options seem to run smoothly.
What platform have you tried to run torrentexpander on ?

Thanks

I have been running it manually, I thought I made that clear.

I keep my server on LTS releases, so it's currently on 10.04.  I have a feeling I just misunderstand the purpose/goal of the script... It seemed to aggressively copy files, even ones that aren't in .rar/.zip.  Additionally, it didn't extract any files that were compressed, it merely copied them.  I either am missing the point of the script, or simply using it wrong.  Let me know if I can help test, perhaps we can coordinate on IRC or some messenger service... Thanks!

---

### Post by toinou on 2011-12-08
Hi arrrghhh

Torrentexpander was initially just an unrar / unzip script.
Now this script's goal is to automate various tasks that many users have to do manually.
Not all torrents are made of compressed archives, so uncompressed torrents are also managed by the script.

You can view here the list of tasks executed by the script :
[http://code.google.com/p/torrentexpander/wiki/What_is_torrentexpander](http://code.google.com/p/torrentexpander/wiki/What_is_torrentexpander)

If you still wanna try it out once again, I suggest you start with the latest SVN. Many users encountered issues while running this script because the user running their torrent client does not have write access to some essential directories or execute access to essential binaries. This build now executes many verifications and outputs a "debug" file.
[http://code.google.com/p/torrentexpander/source/browse/trunk/torrentexpander.sh](http://code.google.com/p/torrentexpander/source/browse/trunk/torrentexpander.sh)

If you run into errors, I suggest you delete torrentexpander_settings.ini and run the script manually once again, using the default values.

Don't hesitate to PM me if you have any question.

        Toitoinou

---

