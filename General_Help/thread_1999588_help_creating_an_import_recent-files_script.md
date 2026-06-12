---
title: "help creating an import recent-files script"
date: 2012-06-08
forum: General Help
---

### Post by swizzla on 2012-06-08
Hello all,

I had an idea to create a script that will auto-run on startup to import the recent files list from winDOZE into Ubuntu's unity recent-files list. My mom was using windoze on her laptop which is dual-booting, but she wanted to be able to see files that she was working on when she goes back over to unity. I dont know anything about how unity stores that information for its recent files but i do know that in winDOZE, the recent files info is stored in a folder called Recent as a bunch of .lnk files with the names of the files used.

what I would like to do is create a script or maybe later on a small program with a gui for selecting the winDOZE recent directory for the desired user account. It will be run on startup so things get a bit more seamless for dual-boot computers.

Any ideas, tips? 
thanks guys

---

### Post by hakermania on 2012-06-11
Hello swizzla, I am willing to make something that will work like this, because I am also interested. I have bookmarked this thread and I will work on it when I find the time.

---

### Post by swizzla on 2012-06-12
Thats great news man,:smile:
what's the first step though?

---

### Post by hakermania on 2012-06-12
> **swizzla said:**
> Thats great news man,:smile:
what's the first step though?
I guess that the 1st step will be to fully understand how Ubuntu and Windows store their recent-files. Then, the script will possibly ask for the mounted location of windows and search there for the proper files. 
Providing that the recent files will be on the mounted drive, the path will be different so as to call them from inside your Ubuntu OS, rather than from inside your Windows OS.

Taking all these into consideration, it should take some time searching for the creation of something like this :)

---

### Post by hakermania on 2012-07-29
I had some free time today, and the 1st step is to automatically mount the windows partition on boot. This is not so hard to be done. The script will mount the windows partition at /media/ (preferably by reading from a configuration file or specified at the header of the script as variable).

The next point is to extract the recent-files data from a specific user on the windows partition (user-defined at a config file or at the top of the script as variable) and then to append the recent-files at the Zeitgeist database, located at ~/.local/share/zeitgeist/activity.sqlite.

I haven't searched yet how to extract these data from windows, but I just wanted to let you know that I'm still interested in doing this.

---

### Post by hakermania on 2012-07-29
Ok, I also did the first 2 steps:
(1) <-> Mount the windows partition
(2) <-> Get the recent files path list and write them to a temp file
```

#!/bin/bash
#Script written by the internet. Seriously.
#Please specify the below variables so as to much your needs:

### VARIABLES START ###

#Where is the windows partition? [Required! Run 'sudo fdisk -l' to see where it is]
windows_location="/dev/sda2"
#Where is the windows partition mounted at when you do it manually? [Very Optional! If you leave this blank, an attempt will be made so as to get the mount position with the 'udisks --mount $windows_location' command]
mount_location=""
#specify from which user to take the recent files... [Required!]
windows_user="alex"
#Set this at 0 if you don't want debugging info (on what the script is doing) to be shown
show_info=1

###  VARIABLES END  ###

### (1) Mounting the windows ###

#Checking if $windows_location has been declared
if [ -z "$windows_location" ]; then
   echo "Please specify the windows_location variable! You can see where your windows partition is located by running the command 'sudo fdisk -l'! (example location: /dev/sda2)"
   exit 1;
fi

#checking if $windows_location points to a correct file
if ! file "$windows_location" 2>&1 > /dev/null; then
   echo "The file $windows_location does not point to the correct file... Edit the corresponding variable 'windows_location' on the head of this script."
   exit 1;
fi

#checking if $mount_location is already mounted
is_mounted=$(udisks --show-info "$windows_location" | grep "is mounted" | awk '{print $3}')

if [[ "$is_mounted" == "0" ]]; then #we have to mount the windows partition
   if [ -z "$mount_location" ]; then #$mount_location has not been specified, take it manually
      if [ $show_info -eq 1 ]; then
         echo "'mount_location' has not been specified, attempting to get it...."
      fi
      mount_location=$(udisks --mount "$windows_location" | awk '{print $4}')
   else
      udisks --mount "$windows_location" 2>&1 > /dev/null
   fi
else #windows partition is already mounted, get the mount location, if not specified
   if [ -z "$mount_location" ]; then
      if [ $show_info -eq 1 ]; then
         echo "'mount_location' has not been specified, attempting to get it...."
      fi
      mount_location=$( udisks --show-info "$windows_location" | grep "mount path" | awk '{print $3}');
   fi
fi

#if the script has reached this point, then it has mounted the windows partition successfully and it has its mount point

if [ $show_info -eq 1 ]; then
   if [[ "$is_mounted" == "0" ]]; then
      echo "The partition wasn't mounted, but I mounted it."
   else
      echo "The partition was already mounted"
   fi
   echo "The mount location is at $mount_location"
fi


### (2) Get the recent files ###

#Checking whether the recent files directory exists
if ! [ -d "$mount_location"/Users/"$windows_user"/AppData/Roaming/Microsoft/Windows/Recent ]; then
   echo "The recent directory has not been found... If you have specified manually the 'mount_location' variable, be sure it is correct. If you are not sure about the 'mount_location', then leave it blank (mount_location=\"\") and I will try to take care of it. Also, be sure that the 'windows_user' variable is set correctly."
   exit 1
fi

if [ $show_info -eq 1 ]; then
   echo "Heading to the windows recents directory..."
fi

cd "$mount_location"/Users/"$windows_user"/AppData/Roaming/Microsoft/Windows/Recent/

#loop between the .lnk files:

if [ $show_info -eq 1 ]; then
   echo "Creating some temporary files..."
fi

temp_file=$(mktemp)
links_file=$(mktemp)

if [ $show_info -eq 1 ]; then
   echo "Looping between the recent files at windows..."
fi

for windows_shortcut in *.lnk; do
   if strings "$windows_shortcut" 2> /dev/null | grep ':' > $temp_file; then
      #getting the largest line of $temp_file and storing it to $links_file
      awk '{ if (length($0) > max) {max = length($0); maxline = $0} } END { print maxline }' $temp_file >> $links_file
   fi
done

rm -f $temp_file
echo "Entries written at "$links_file""

```
You should just run the above script, **BUT** you have to edit the variables that are at the top of the script so as to much your needs!

PS: Tested on Ubuntu 12.04 with Windows 7 target!

PS2:
What is to follow: A new variable will exist on the top of the above script requesting the windows' drive letter (which in most cases (99% probably) it is 'C'), so as to convert any of these links that point to C:\ converted into /media/windows/ path so as to be accessible through Ubuntu with one click, if the windows partition is mounted. Also, we have to see what we will do with recent files that have to do with other disks, like G:, F: etc, that may refer to external devices, but I guess that we have to just ignore them (don't include them, after all). After these conversions, the links will finally be written to the Zeitgeist database and will be available and accessible through Ubuntu's recent files system. Also, there should be a way so as not to give duplicate entries to Zeitgeist (you told me that you are planning to have this script run at startup, and, if, for example you are logged in into ubuntu and you restart your pc and you login again at ubuntu, then exactly the same recent files will be found by my script and we wouldn't like giving duplicate entries to Zeitgeist).

There are some problems that have to be solved (and I don't know how to work the databases, but it's a good chance to learn!) but we will fix all of them, at the end, I think :)

Please tell me if the above script works fine for you, **after** specifying the corresponding values at the top of the script.

---

