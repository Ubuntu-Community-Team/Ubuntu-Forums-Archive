---
title: "Opening .lnk files (Help with Script)"
date: 2010-12-14
forum: General Help
---

### Post by tg3793 on 2010-12-14
At first I was looking for something that would allow me to open up .lnk  files in GNOME. Ran across a dozen people with the same problem but no  solutions.

But then after several hours over the course of a few days I had an  idea. "[COLOR=Blue]**What about a script that converts .lnk  files to symlinks?**[/COLOR]"

I've seen many people with this problem but no Gnome users with a  solution yet. Here is a script that 'almost' does the job. It's about  two years old:

```
#!/bin/bash


######################################################################
#                                                                    #
# lnk2symlink by jesus.guerrero.botella at gmail dot com,            #
# search for windows .lnk files on a given directory, and creates    #
# symlinks according to the info contained on those files            #
#                                                                    #
# This script is provided without any kind of implicit or explicit   #
# guarantee, and is licensed under the GNU General Public License v3 #
# or later if available. More about licenses on the following URL:   #
#                                                                    #
# http://www.gnu.org/licenses/licenses.html                          #
#                                                                    #
######################################################################

VERSION=20080728
PROGRAM_NAME=$(basename $0)
DELETE_LNK=0

die() {
    case $1 in
        non_linkable_fs)
            echo "The target filesystem doesn't support symlinks."
            exit 11
            ;;
        ln_error)
            echo "Undefined error while symlinking."
            exit 10
            ;;
        *)
            echo "Undefined error."
            exit 20
            ;;
    esac
}

show_help() {
        echo "$PROGRAM_NAME v$VERSION"
        echo "Search for windows .lnk files and creates linux symlinks  according"
        echo "to the info within those .lnk files."
        echo
        echo "Usage: "
        echo "    $PROGRAM_NAME [-d|--do] [directory]"
        echo
        echo "Where the optional parameter [directory] is a directory  where to look"
        echo "for .lnk files, and -d|--do is a parameter to actually do  the work."
        echo "By default, $PROGRAM_NAME will not do anything, but just  output WHAT"
        echo "would be done if -d|--do is used."
        echo 
        echo "Parameters:"
        echo "  -d, --do"
        echo "    Do the real work."
        echo "  -h, --help"
        echo "    Show this help text."
        echo "  -e, --erase, --del, --delete"
        echo "    Delete de .lnk files after doing the work. These imply  --do."
        echo
}

case $1 in
    -h|--help|"")
        show_help
        exit 0
        ;;
    -d|--do)
        DO_WORK=1
        DIR="$2"
        ;;
    -e|--erase|--del|--delete)
        DELETE_LNK=1
        DO_WORK=1
        DIR="$2"
        ;;
    *)
        DO_WORK=0
        DIR="$1"
        ;;
esac

TEST_FILE="$DIR/test-$RANDOM$RANDOM$RANDOM$RANDOM"
ln -s "$HOME" "$TEST_FILE" > /dev/null 2>&1 || die  non_linkable_fs
rm -f "$TEST_FILE"

echo "Specified directory: $DIR"
echo "Finding files, this may take a while..."
find "$DIR" -iname '*.lnk' | while read LNK_FILE
do
    echo
    echo "Processing file: $LNK_FILE"
    echo  "================================================================================"
    CANDIDATE_STRING=$(strings "$LNK_FILE" | grep ':\\')
    LINUX_PATH="$(echo $CANDIDATE_STRING | \
        sed -e 's#.*\:\\#'"$HOME"'\/.wine\/drive_c\/#' | \
        sed -e 's#\\#\/#g')"
    SYMLINK_NAME="${LNK_FILE/.lnk/}"
    if [ ! -L "$SYMLINK_NAME" ]
    then
        if [ -r "$SYMLINK_NAME" ]
        then
            echo "File with the same name detected, but it's not a  symlink."
            echo "I will add a RANDOM suffix to the symlink name."
            SYMLINK_NAME="${SYMLINK_NAME}-${RANDOM}"
        fi
        if [ $DO_WORK -eq "1" ]
        then
            echo "Running: ln -s $LINUX_PATH $SYMLINK_NAME"
            ln -s "$LINUX_PATH" "$SYMLINK_NAME" || die
        else
            echo "This is what WOULD be done:"
            echo "ln -s $LINUX_PATH $SYMLINK_NAME"
        fi
    else
        echo "$SYMLINK_NAME do exist, and it's a symlink, skipping."
    fi
    if [ $DELETE_LNK -eq "1" ]
    then
        rm -f "$LNK_FILE"
    fi
done
```Full credit to **the author jesus.guerrero.botella** for the promise  that this script holds. However there is a problem with the script and  wondering if someone can help me with it. _Any time I run it on a .lnk  file it creates a shortcut to "[COLOR=SeaGreen]/.wine/drive_c/[/COLOR]"  and the problem is that the .lnk file I'm trying to create a symlink to  is on an external drive._

Another tip to consider is the external drive is named "SignatureMini"  which had previously been the "G:\" drive in my previous WindowsXP  environment.

Any help with this is appreciated.

---

