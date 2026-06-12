---
title: "Right click to copy to specific folder"
date: 2010-03-21
forum: General Help
---

### Post by lv9862 on 2010-03-21
I have my mother in law running ubuntu and everything is going great.  She is not good at computers and takes her sd card to wal-mart to print pictures.  She takes tons of pictures.  I want her to go through them at the house and move all the ones she wants to a folder.  I have created the folder.  I want her to be able to rightclick on a picture and click copy to that folder.

How do I do this?

---

### Post by kaibob on 2010-03-21
There are a number of options. The first is Nautilus Actions, which is in the repo's:

[http://www.grumz.net/index.php?q=taxonomy/term/2/9](http://www.grumz.net/index.php?q=taxonomy/term/2/9)

A Nautilus script is another option:

[http://g-scripts.sourceforge.net/faq.php](http://g-scripts.sourceforge.net/faq.php)

A third option is to create a shell script as shown below and to define it as a custom command in the JPG open-with dialog. Then, if the script name is say copy, when she right clicks in Nautilus on a JPG file, the second item in the context menu will be "open with copy". If there are more than three open-with options, they will appear in a submenu of the right-click context menu, which would make things a bit cumbersome. 

```
#!/bin/sh

cp "$@" /home/username/photos
```

BTW, seems like the easiest is to control-drag with the mouse, but I guess you have ruled that out.

---

### Post by PC_load_letter on 2010-03-22
Awesome reply from kaibob, I was about to link to a shell script from Ubuntu's help, it's the "copy to" script on the the following page: 
[https://help.ubuntu.com/community/Nautilus_Scripts](https://help.ubuntu.com/community/Nautilus_Scripts)

I produce the script here for convenience, you'll have to put the script in the /home/USER/./gnome2/nautilus-scripts and make it executable.
```
# To copy selected files to a location

LOCATION=$(zenity --file-selection --directory --title="Select a directory") || exit

IFS=$'\n'
for FILENAME in $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS
do
    if [ -e "$LOCATION"/"$(basename $FILENAME)" ];then
       zenity --question --title="Conflict While Copying" --text="File ""$LOCATION"/"$(basename $FILENAME)"" already exists. Would you like to replace it?"
       case "$?" in
          1  )  exit 1 ;;
          0  )  cp -a -- "$FILENAME" "$LOCATION" ;;
       esac
    else
       cp -a -- "$FILENAME" "$LOCATION"
    fi
done
```

---

