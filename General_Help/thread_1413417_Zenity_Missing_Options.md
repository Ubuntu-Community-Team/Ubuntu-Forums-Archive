---
title: "Zenity Missing Options"
date: 2010-02-22
forum: General Help
---

### Post by chiques on 2010-02-22
Hello Fellow Ubuntu Peers,

I am experimenting with scripts (I know, scary) and I ran into the document [https://help.ubuntu.com/community/Nautilus_Scripts]("https://help.ubuntu.com/community/Nautilus_Scripts"). It seems fairly straight forward except when I check Zenity, there are a couple of options which are not there.

The script I'm using is:

> 
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




The options in quesion are:

> 
zenity --file-selection --directory


When I run 'zenity --help' I get:


> 
user@user-desktop:~$ zenity --help
Usage:
  zenity [OPTION...]
Help Options:
  -h, --help                                     Show help options
  --help-all                                     Show all help options
  --help-general                                 Show general options
  --help-calendar                                Show calendar options
  --help-entry                                   Show text entry options
  --help-error                                   Show error options
  --help-info                                    Show info options
  --help-file-selection                          Show file selection options
  --help-list                                    Show list options
  --help-notification                            Show notification icon options
  --help-progress                                Show progress options
  --help-question                                Show question options
  --help-warning                                 Show warning options
  --help-scale                                   Show scale options
  --help-text-info                               Show text information options
  --help-misc                                    Show miscellaneous options
  --help-gtk                                     Show GTK+ Options

Application Options:
  --calendar                                     Display calendar dialog
  --entry                                        Display text entry dialog
  --error                                        Display error dialog
  --info                                         Display info dialog
  --file-selection                               Display file selection dialog
  --list                                         Display list dialog
  --notification                                 Display notification
  --progress                                     Display progress indication dialog
  --question                                     Display question dialog
  --warning                                      Display warning dialog
  --scale                                        Display scale dialog
  --text-info                                    Display text information dialog
  --display=DISPLAY                              X display to use
log
  --question                                     Display question dialog
  --warning                                      Display warning dialog
  --scale                                        Display scale dialog
  --text-info                                    Display text information dialog
  --display=DISPLAY                              X display to use





Is there an add on to Zenity which I can download so I can have the --directory option?

---

### Post by chiques on 2010-02-22
Nevermind, I found it.



> 


user@user-desktop:~/Desktop/standards_datasheets$ zenity --help-file-selection
Usage:
  zenity [OPTION...]

File selection options
  --file-selection                               Display file selection dialog
  --filename=FILENAME                            Set the filename
  --multiple                                     Allow multiple files to be selected
  --directory                                    Activate directory-only selection
  --save                                         Activate save mode
  --separator=SEPARATOR                          Set output separator character
  --confirm-overwrite                            Confirm file selection if filename already exists
  --file-filter=NAME | PATTERN1 PATTERN2 ...     Sets a filename filter

user@user-desktop:~/Desktop/standards_datasheets$ 



---

### Post by josephj on 2010-10-31
How do I specify a --file-selection for any file that does *not* start with a dot (.)?

It's the *not* part that's got me stumped.

'--file-filter=[^\.].*' doesn't work with or without the backslash.

TIA

Joe

---

