---
title: "Downgrade to 9.04"
date: 2010-02-05
forum: General Help
---

### Post by Dunchillin on 2010-02-05
Soooo...having problems with 9.10 (first and foremost it won't boot properly, opens in low graphics mode only) and wishing I'd stuck with 9.04!

Have been trawling for help but can only find threads that didn't get answered or closed threads (including one about 'partial upgrades', which I did after booting in low graphics mode the first time.  I am new to, or at least pretty green about Ubuntu and pretty much always install any updates offered - don't shoot me)

Anyhow, I am hoping to avoid a full re-installation, but is there any way of going back...downgrading...to 9.04?

---

### Post by tom.swartz07 on 2010-02-05
> **Dunchillin said:**
> Soooo...having problems with 9.10 (first and foremost it won't boot properly, opens in low graphics mode only) and wishing I'd stuck with 9.04!

Have been trawling for help but can only find threads that didn't get answered or closed threads (including one about 'partial upgrades', which I did after booting in low graphics mode the first time.  I am new to, or at least pretty green about Ubuntu and pretty much always install any updates offered - don't shoot me)

Anyhow, I am hoping to avoid a full re-installation, but is there any way of going back...downgrading...to 9.04?

Unfortunately, there is no safe way to downgrade your system. Although it is possible, it would most likely make your computer very unstable.


Perhaps you could post here with your problems, and we could sort them out? 

Describe your system, Manufacturer, model, cpu type (386 or x64), video cards you have, etc.
Then tell us, specifically, what your problems are- the more detail the better- just keep it organized and concise (some of the posters here are lazy and dont like to read a novel-sized post every time :P)


Hope to hear from you soon!

---

### Post by switch10 on 2010-02-05
The only good way to do this, is backup and do a clean reinstall.

---

### Post by Dunchillin on 2010-02-05
Thanks tom.swartz07

My biggest problem is exactly this one:

[http://ubuntuforums.org/showthread.php?t=1376738]("http://ubuntuforums.org/showthread.php?t=1376738")

Actually my biggest problem is being Ubuntually inept, but I love it still!

---

### Post by tom.swartz07 on 2010-02-05
> **Dunchillin said:**
> Thanks tom.swartz07

My biggest problem is exactly this one:

[http://ubuntuforums.org/showthread.php?t=1376738]("http://ubuntuforums.org/showthread.php?t=1376738")

Actually my biggest problem is being Ubuntually inept, but I love it still!

As far as learning Ubuntu; try this guide: [http://books.google.com/books?id=kHLlJzI6L20C&printsec=frontcover#v=onepage&q=&f=false](http://books.google.com/books?id=kHLlJzI6L20C&printsec=frontcover#v=onepage&q=&f=false)

At any rate, I agree with switch- before you try anything- back up your data- even if you just dump your /home folder on a USB drive, and get a markings list from synaptic.
Your /home folder should be a priority- that has all of your files and program config settings in it; you save that, you have your entire system with you (all you need to do is install the programs again and youre set)




This thread mentions that they used an Alternate CD installer- is that the case for you?

---

### Post by Dunchillin on 2010-02-05
No, sorry I'd missed that. I upgraded from 8. something (that my friend installed for me a couple of years ago) through to 9.10 via update manager over the last few days, finally arriving at low graphics mode about 7 hours ago!

Thanks for the user guide, and also the advice (saving home folder to external now ;))

---

### Post by tom.swartz07 on 2010-02-05
> **Dunchillin said:**
> No, sorry I'd missed that. I upgraded from 8. something (that my friend installed for me a couple of years ago) through to 9.10 via update manager over the last few days, finally arriving at low graphics mode about 7 hours ago!

Thanks for the user guide, and also the advice (saving home folder to external now ;))

Sure! Hope you will enjoy it!



Okay- Im sorry if im mincing words here, but Im trying to diagnose what may have caused the errors. When you say you updated over the past few days- did you cancel the updates at any point?


If thats the case try running

```
sudo apt-get update
```
and
```
sudo apt-get dist-upgrade
```
from the terminal

---

### Post by Dunchillin on 2010-02-05
No I didn't cancel the updates at any time

> **tom.swartz07 said:**
> 
```
sudo apt-get update
```


That caused a fair amount of activity in terminal


> **tom.swartz07 said:**
> 
```
sudo apt-get dist-upgrade
```


and that didn't

But restarting the comp to see if there was any effect I still had to open in low graphics mode.

I tried to copy the error message generated at startup but couldn't, but basically it says I have no "EE" (possibly it says "no EE device"?)

Any ideas? Thanks again

---

### Post by Dunchillin on 2010-02-05
The error message I'm getting at start up says "Ubuntu running in low graphics mode.  You may need to update your configuration to solve this. (EE) No devices detected"

---

### Post by Dunchillin on 2010-02-06
Hi. Sorry to bump up this thread again even though no-one has replied to the last couple of posts, but I'm really hoping to find a way to solve this 'low graphics mode' issue. Big Thanks to tom.swartz07 for your help so far :)

Has no-one else had this happen after upgrading to 9.10?

Thanks to anyone that can help!

---

### Post by Amrobadr on 2010-02-06
> **switch10 said:**
> The only good way to do this, is backup and do a clean reinstall.

would you tell me how can I backup system files !!
bcuz, I'm facing many problems & I'm planning to install a fresh copy of uBuntu 9.10

---

### Post by tom.swartz07 on 2010-02-06
> **Dunchillin said:**
> Hi. Sorry to bump up this thread again even though no-one has replied to the last couple of posts, but I'm really hoping to find a way to solve this 'low graphics mode' issue. Big Thanks to tom.swartz07 for your help so far :)

Has no-one else had this happen after upgrading to 9.10?

Thanks to anyone that can help!


Im not so sure about how to fix it outright. Like some others suggested, perhaps it would be best to just simply clean install.

> **Amrobadr said:**
> would you tell me how can I backup system files !!
bcuz, I'm facing many problems & I'm planning to install a fresh copy of uBuntu 9.10

In order to help you both back up your stuff to do a clean install, ill just simply outline how you could back things up for when you get your new install put back on.

I would definitely recommend using either an external hard drive (will hold almost everything, but can be a tad expensive), a large capacity USB key (easy to use, cheap, but not a permanent solution), or an online storage service like Dropbox (accessible from anywhere on internet and safe, but limited capacity for no charge).

If you only have a few files you could use Dropbox or a USB key- but in the long run, it is best to get an external drive for backing up. You could get Dropbox right now (2GB free) by clicking the link in my signature.

**Installed Programs**
In order to get installed programs, you need 2 separate, but very important files. Your package sources list, and your Synaptic markings.

The list of repositories, or places that you can receive program updates from, is located in a text file here:
```
/etc/apt/sources.list
```
This command will copy it to your desktop; simply copy it to a safe place:
```
sudo cp /etc/apt/sources.list ~/Desktop
```
Once on your new computer, simply copy the file back to the original location; /etc/apt/sources.list


Now we will get the Synaptic markings, or a list of every program you have so that you could easily re-install them all. Open Synaptic Package manager from the System>Administration menu and then click File>Save Markings as...

Navigate to your desktop or backup location and save the file.
NOTE: the default 'desktop' location that synaptic points you to is ROOT's. You will need to get to your own desktop from /home/USERNAME/Desktop
After you get to the new computer, you could then open Synaptic the same way, then select File>Read Markings (then select the file) to get the entire list of programs you had installed. Just click apply and it will take care of the rest.


**Your settings and system files**
Next you need to back up your /home folder. 99.9% of your settings are stored here, such as; your background images, panel configurations, visual effects settings, documents, videos, downloads, among many other things.
This will definitely be the most data that you will need to copy. 
On my computer, my /home folder can easily fit on a 4GB USB key. Personally, Ive found that the hands-down easiest way to copy my files to the usb key is using this script:
```
#!/bin/sh
####################################
#
# Backup to external USB drive
#
####################################

# What to backup. *EDITABLE*
backup_files="/home/tom"

# Where to backup to. *EDITABLE*
dest="/media/backup"

# Temporary storage for file as its being processed. *EDITABLE*
temp="/media/Data"

# -----DO NOT EDIT BELOW THIS LINE----- #
# Create archive filename.
#day=$(date +%a)
#time=$(date +%R)
hostname=$(hostname -s)
#archive_file="$hostname-$day-$time.tgz"
archive_file="$hostname.tgz"
# Print start status message.
echo "Backing up $backup_files to $dest/$archive_file"
date
echo

# Backup the files using tar.
tar czf $temp/$archive_file $backup_files
#compress to save space.
gzip -9 $temp/$archive_file
#Remove previous file and copy new version
rm $dest/$archive_file
mv $temp/$archive_file $dest
# Print end status message.
echo
echo "Backup finished"
date

# Long listing of files in $dest to check file sizes.
ls -lh $dest
```
You will need to change three lines for your specific computer: the location of your home folder, the location of the temporary storage, and the location of the final backup. You could simply change the last two to your desktop and copy the file however you would like. 

Simply copy the code to gEdit Text Editor and save it as backup.sh then run it.

If you cant get that to run, or have problems- you could just simply copy the folder to a drive and save it that way. The only thing that this script does more, is that it compresses the file too.

Other than that, you should have all of your stuff all taken care of, and ready for when you reinstall!

---

