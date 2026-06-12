---
title: "Setting up a virtual directory"
date: 2010-10-31
forum: General Help
---

### Post by odror on 2010-10-31
I have video files in multiple directories. Is there a way to setup a vitrual directory that shows that content of all the video directories. Sym link is not good enough since the content of these directories changes all the time.

Thanks

---

### Post by ragtag on 2010-10-31
In Nautilus you can bookmark a search result. So if you create a search that finds all your video files, you can gather them all in one folder this way. The downside is that other programs won't see this as a virtual folder, so you'll have to open Nautilus and access them from there.

You could create symbolic links to the folders that contain the video, but then your resulting folder would contain subfolders, so all your video files wouldn't bee in one folder...if that's your goal.

Finally, a rather hacky way, would be to create a cron job that adds and remove symlinks as needed. It can run every few minutes, so when you add or remove a video file, the symlink will be updated soon after. The script wouldn't be too hard to write. :)

---

### Post by odror on 2010-10-31
This directory needs to seen by a windows computer on the local network. The option with nautilus will not work. I am surprised that there are no tools under linux to create such directory.

---

### Post by ragtag on 2010-11-01
Here is a tool I hacked together quickly.
:guitar:
When you run it the first time, it creates a sample config file for you in ~/.virtualfolders/sample.conf. You can then edit this file, and create more like it, to create your virtual folders.

```

#!/bin/sh                                                                                                                                                                                            
#                                                                                                                                                                                                    
# This is a hacky script to create virtual folders from searches.                                                                                                                                    
# Feel free to share it or improve on it.                                                                                                                                                            
settings="$HOME/.virtualfolders"

# Create the settins folder if not found.                                                                                                                                                            
if [ ! -d $settings ]
then
    mkdir $settings
    echo "# Edit this file, to set up your virtual folder.\n# Path to where you want your virtual folder\nvirtualfolder=$HOME/virtualfolder\n# A list of folders you want to look for files in (fold\
er names with spaces currently not supported).\nsourcefolders=\"$HOME/Videos $HOME/Documents\"\n# List of file extensions you want to look for\nextensions=\"ogg ogv avi\"" > $settings/sample.conf
    echo "No settings file found. I've created a sample settings file in $HOME/.virtualfolders/sample.conf. You can edit it or make copies of it for multiple virtual folders."
    exit 1
fi

# Loop through all the configuration files.  
for conf in `ls -1 $settings/*.conf`
do
    # Source the current configuration file.
    . $conf
    # Make the virtual folder if it does not exist.
    if [ ! -d $virtualfolder ]
    then
        mkdir $virtualfolder
    fi
    # Loop through the source folders and create symbolic links for all files matching extension.                             
    for d in $sourcefolders
    do
        for e in $extensions
        do
            find $d -name "*.$e" -exec ln -s "{}" "$virtualfolder/." \;
        done
    done
    # Delete any broken symlinks.                
    find $virtualfolder -type l ! -xtype f ! -xtype d -delete
done



```

It's not perfect, and there is very little error checking, but it seems to work. It quickly creates a folder full of sylminks based on the criteria you've defined in the config file.

I haven't tested this as a cron job, and I'm not 100% it works as one, as I'm not sure how cron jobs treat the $HOME variable. :)

---

