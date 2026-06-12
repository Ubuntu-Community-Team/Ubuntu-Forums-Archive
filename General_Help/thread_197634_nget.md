---
title: "nget"
date: 2006-06-16
forum: General Help
---

### Post by mikeym on 2006-06-16
Could someone please tell me hot to use nget newsgroup downloader efectively. I have managed to download some files and see lists of newsgroups and files in the newsgroups that I am interested in and download some files, but I cant see how you can browse the available files without getting lost.

Hopefully someone knows how this is done - thanks for your help.

---

### Post by mikeym on 2006-06-16
I thought I could get things rolling and describe what I have found out about using and installing nget.
[B]
Installaction[/B]

Install the *nget* package from your favourite package program or the console by typing the following:

```

sudo apt-get install nget

```
Then type in your administration password.

You can do the same to install *par2* - for re-building binary archives with missing or incoplete files - and *unrar* - for extrating windows RAR archive files that are commonly used. 

```

sudo apt-get install par2
sudo apt-get install unrar

```

**Setup**

To set up nget you need to create a directory in your home directory for it to work from, copy in an example configuration file and enter your newsgroup's details.

You can do this from the terminal as follows:

```

mkdir $HOME/.nget5 
cp /usr/share/doc/nget/examples/ .ngetrc $HOME/.nget5/
gedit $HOME/.nget5/ .ngetrc 

```

Edit the config file as follows to contain your host newsgroup server's address and port number - you can setup other connection options here too:

> 
//hostname aliases
{halias
 {mychoosenhostname
  addr=news.my.address.com:theportno
  id=1
#optional host config settings:
#  user=<name>
#  pass=<password>
#  fullxover=1
#  shortname=<y>
#  maxstreaming=64
#  idletimeout=300
#  linelenience=0
 }

Save the configuation file.

**Use**

To get a complete list of available servers type the following:

```

nget -aTr ""

```
This is not recomended as you will have a verry long list of groups, better to narrow it down with something like:

```

nget -aTr "alt\..*movies"

```
This will give you a list of all the *'alt'* newsgroups with the word movies in their title. nget uses regular expressions in the same manner as grep to see about these go to the grep man page [here]("http://www.doc.ic.ac.uk/lab/labman/lookup-man.cgi?grep(1)#sect4"). It also uses expretrieve expressions to see about their syntax go to [here]("http://nget.sourceforge.net/nget.1.html#EXPRETRIEVE%20EXPRESSIONS").

This is what the FAQ has to say on regular expressions made easy:

> 
2. Whats a regexp? I'm too lazy to read the man pages.

Simple description: take your glob expression, replace:
. with \.
? with .
* with .*

See the manpages for more complicated stuff ;)


To get a comlpete list of all the files in a group type the following:

```

nget -g alt.my.group -DTr ""

```
This will produce a verry large and difficult to read list. You can narrow this down by using a regular expression to search for the files you want.

***If anyone has any suggestions as to how to get a better list for browsing available files using nget please post.***

To download all the archive files relating to a file type:

```

nget -g alt.my.group -r "expression\.matching\.my\.file"

```
This will download the files to the current directory.

Once this is downloaded, depending on what you have selected, you should have a set of files ending in RAR or R## where ## is a sequence of numbers and a bunch of files ending in PAR2. 

To repair the archive list using the *par2* program type the following:

```

par2 r my.file.cd1.PAR2

```
Any of the par2 files can be used here.

To once the archive is complete you can extract it by typing the following:

```

unrar e my.file.cd1.r00

```
This will extract the file into the current directory.

---

### Post by TuxCrafter on 2006-09-24
can i download nzb file with nget?

---

### Post by mikeym on 2006-09-30
> **TuxCrafter said:**
> can i download nzb file with nget?

I would recomend [NZBPerl]("http://noisybox.net/computers/nzbperl/") for downloading nzb's.

Here are some files you may find usefull:

par2extract.sh - to automaticaly repair and extract par 2 files / rars.
```

#!/bin/bash

# Repair par2 sets then extract any rar files and copy anything else to
# a destination directory. If all of this is successfull then delete the
# parent directory.

# TO DO:
# * If not using own folder, remove only the files that have been successfully
#   repaired and extracted.

PAR2REPAIR=par2repair
UNRAR=unrar
OUTPUTDIR=/mp3/dvd
OWNFOLDER=`cat "$HOME/.nzbperlrc" | sed -n -e '/^[[:blank:]]*#/d' -e '/dlcreate/p'`
STATUSLOG=$HOME/.status.log
DATEFORMAT="%F %T"
LOGFILE=/var/log/postnzb.log

# Check that we have a valid source directory.

if [ ! -d "$1" ]; then
        echo "Invalid source directory '$1'!"
        exit 1
fi

# Store the current folder and change to the archive folder

CURRENTFOLDER=`pwd`
cd "$1"

# Get rid of any conflicting logs.

rm "repair.log" 2>> /dev/null
rm "extract.log" 2>> /dev/null

# Get a list of all the '.par2' files including volumes.

PARLIST=$(ls *.* 2> /dev/null | sed -n -e '/\.VOL[[:digit:]]\++[[:digit:]]\+\.PAR2$/Ip' -e '/\.par2$/Ip' -e '/\.[[:digit:]]\+$/Ip')

# Get a list of all the sets by stripping the extension from the
# par2 files.

IFS=""
SETLIST=$(echo $PARLIST | sed -e 's/\.[[:digit:]]\+$//I' -e 's/\.VOL[[:digit:]]\++[[:digit:]]\+\.PAR2$//I' -e 's/\.par2$//I' | sort | uniq)
IFS="
"

# For each par2 set get the first available 'par2' file and run
# par2repair to repair it. Get Par2repair to check all the possible files
# in the set.

ERRORS=0

for SET in $SETLIST; do

        IFS=""
        FIRSTPAR=$(echo $PARLIST | grep -i "$SET\.par2")
        if [ -z $FIRSTPAR ]; then
                FIRSTPAR=$(echo $PARLIST | grep -i "$SET\.VOL[[:digit:]]\++[[:digit:]]\+\.PAR2$" | sort | sed -n "1p")
                if [ -z $FIRSTPAR ]; then
                        FIRSTPAR=$(echo $PARLIST | grep -i "$SET\.[[:digit:]]\+$" | sort | sed -n "1p")
                fi
        fi
        IFS="
"

        date +"$DATEFORMAT Repairing: '$FIRSTPAR'" >> $LOGFILE
        echo "Repairing: '$FIRSTPAR'" > $STATUSLOG
        $PAR2REPAIR -q "$FIRSTPAR" "$SET*" > tmp.log 2>> /dev/null
        RESULT=$?
        cat tmp.log >> repair.log
        if [ $RESULT != 0 ]; then
                ERRORS=$((ERRORS+1))
                date +"$DATEFORMAT Error repairing file '$FIRSTPAR'." >> $LOGFILE
                echo "Error repairing file '$FIRSTPAR'."
                continue
        fi

        # Read the repair log to find the files that have been used to repair

        REPAIRED=`cat tmp.log 2>> /dev/null | awk 'BEGIN { FS="\"" } /Loading/ { print $2 }'`
        IFS=""
        TOTRASH=$(echo "$TOTRASH" && echo "$REPAIRED" | uniq)
        IFS="
"
done


# Get the list of 'rar's and the names of the unique sets of 'rar's

RARLIST=$(ls *.* 2> /dev/null | grep -i '\.rar$\|\.r[[:digit:]]\+$\|\.part[[:digit:]]\+\.rar$\|\.[[:digit:]]\+$')

IFS=""
RARSETS=$(echo $RARLIST | sed -e 's/\.part[[:digit:]]\+\.rar$//I' -e 's/\.rar$//I' -e 's/\.r[[:digit:]]\+$//I' -e 's/\.[[:digit:]]\+$//I' | sort | uniq)
IFS="
"

# For each 'rar' set find the first 'rar' file and repair it.

for RARSET in $RARSETS; do

        # Search for a '.rar' file, failing that try for a '.part##.rar' file,
        # and failing that take the first alphabetical listing.

        IFS=""
        FIRSTRAR=$(echo $RARLIST | grep -i "$RARSET\.rar")
        if [ -z $FIRSTRAR ]; then
                FIRSTRAR=$(echo $RARLIST | grep -i "$RARSET\.part[[:digit:]]\+\.rar$" | sort | sed -n "1p")
                if [ -z $FIRSTRAR ]; then
                        FIRSTRAR=$(echo $RARLIST | grep -i "$RARSET" | sort | sed -n "1p")
                fi
        fi
        IFS="
"

        date +"$DATEFORMAT Extracting: '$FIRSTRAR'" >> $LOGFILE
        echo "Extracting: '$FIRSTRAR'" > $STATUSLOG
        $UNRAR x -y "$FIRSTRAR" "$OUTPUTDIR" > tmp.log 2>> /dev/null
        RESULT=$?
        cat tmp.log >> extract.log
        if [ $RESULT != 0 ]; then
                ERRORS=$((ERRORS+1))
                date +"$DATEFORMAT Error extracting file '$FIRSTRAR' to '$OUTPUTDIR'." >> $LOGFILE
                echo "Error Unraring file '$FIRSTRAR' to '$OUTPUTDIR'."
                continue
        fi

        # Read the extract log to find the files that have been used to extract.
        EXTRACTED=`cat tmp.log 2>> /dev/null | sed -n -e "/^Extracting from /Ip" | sed -e "s/^Extracting from //I"`
        IFS=""
        TOTRASH=$(echo "$TOTRASH" && echo "$EXTRACTED" | uniq)
        IFS="
"
done

# Remove the temporary log file

rm tmp.log 2>> /dev/null

# Find any remaining files in the folder that don't relate to an archive
# set and copy them to the output folder.

OTHERFILES=$(ls *.* 2> /dev/null | grep -vi '\.par2\|\.rar$\|\.r[[:digit:]]\+$\|\.[[:digit:]]\+$')

for FILE in $OTHERFILES; do
        date +"$DATEFORMAT Moving: '$FILE' to '$OUTPUTDIR'" >> $LOGFILE
        echo "Moving: '$FILE'" > $STATUSLOG
        mv -f "$FILE" "$OUTPUTDIR"
        if [ $? != 0 ]; then
                ERRORS=$((ERRORS+1))
                echo "Error moving file '$FILE' to '$OUTPUTDIR'."
                continue
        fi
done

# Delete any processed files.

date +"$DATEFORMAT Deleting files." >> $LOGFILE
echo "Deleting Files" > $STATUSLOG
trash $TOTRASH
RESULT=$?
ERRORS=$((ERRORS+RESULT))

# Move back to the calling directory.

cd "$CURRENTFOLDER"

# Remove the directory as required.

if [ ! -z "$OWNFOLDER" ]; then
        date +"$DATEFORMAT Deleting: '$1'" >> $LOGFILE
        echo "Deleting: '$1'" > $STATUSLOG
        rmdir "$1" 2>> /dev/null
        if [ $? != 0 ]; then
                date +"$DATEFORMAT Unable to delete '$1'." >> $LOGFILE
        fi
fi

# Tidy up the status log
rm $STATUSLOG 2>> /dev/null

exit $ERRORS

```

and for that you need:

trash - a bit of a hack for the trash applet.
```

#!/bin/bash
# move files or directories to wastebasket
# M. Alford, Jan 2001 - modified for bash by mikey July 06

WASTEBASKET=$HOME/.Trash


function ValidName {
        # Return a valid version of a name

        NAME="$WASTEBASKET/$1"
        if [ -e "$NAME" ]; then
                if [ -e "$NAME (copy)" ]; then
                        if [ -e "$NAME (another copy)" ]; then
                                if [ -e "$NAME (3rd copy)" ]; then
                                        COUNT=4
                                        while [ -e "$NAME (${COUNT}th copy)" ]; do
                                                COUNT=$((COUNT+1))
                                        done
                                        RETURN="$NAME (${COUNT}th copy)"
                                else
                                        RETURN="$NAME (3rd copy)"
                                fi
                        else
                                RETURN="$NAME (another copy)"
                        fi
                else
                        RETURN="$NAME (copy)"
                fi
        else
                RETURN="$NAME"
        fi
}

if [ ! -d $WASTEBASKET ]; then
        mkdir "$WASTEBASKET"
        if [ $? != 0 ]; then
                echo "Failed to create wastebasket dir '$WASTEBASKET'"
                exit 1
        fi
fi

# force automounter to remount the partition where wastebasket lives,
# in case this is necessary:
# ls $WASTEBASKET >& /dev/null

# Do we tar directories?

TAR=0
if [ "$1" == "-tar" ]; then
        TAR=1
        shift
fi

EXITCODE=0
IFS="
"
for FILE in $*; do
        if [ -d $FILE ] && [ $TAR == 1 ]; then

                # it is a dir. First strip any number of trailing "/":

                DIRNAME=`echo $FILE | sed -e s%/\*\$%%`
                MANGLEDNAME=`echo $FILE | sed -e s%/%+%g | sed -e s:\^\\.\*::`

                # and tar it to wastebasket, turning all "/" to "+" and
                # stripping any number of initial "." characters from name

                MANGLEDNAME=$(echo $DIRNAME | sed -e s%/%+%g | sed -e s:\^\\.\*::)
                ValidName "${MANGLEDNAME}.tgz"
                tar -zcf "$RETURN" "$DIRNAME" >> /dev/null 2>> /dev/null
                if [ $? == 0 ]; then
                        rm -rf "$DIRNAME"
                else
                        echo "Failed for dir '$DIRNAME'"
                        EXITCODE=2
                fi
        elif [ -e $FILE ]; then

                # it is a file---move it to wastebasket

                ValidName `basename $FILE`
                mv -f "$FILE" "$RETURN" >> /dev/null 2>> /dev/null
                if [ $? != 0 ]; then
                        echo "Failed for file '$FILE'"
                        EXITCODE=3
                fi
        else
                echo "There is no file or directory called '$FILE'"
                EXITCODE=4
        fi
done
exit $EXITCODE

```

postnzb.sh - the file to be run as part of NZBPerl's post nzb function. 
```

#!/bin/sh
NZBDIR=/mp3/dvd/nzb
NZBDONEDIR=/mp3/dvd/nzb/done

# Run the postnzbpl script for decoding the downloaded 'nzb' file
# on the download directory.
# postnzb.pl "$NZBP_DECODEDIR"
par2extract.sh "$NZBP_DECODEDIR" >> /var/log/postnzb.log

# Move the completed 'nzb' file to the 'done' directory.
date +"%F %T Moving file '$NZBDIR/$NZBP_NZBFILE' to '$NZBDONEDIR/'." >> /var/log/callpostnzb.log
mv "$NZBDIR/$NZBP_NZBFILE" $NZBDONEDIR/

# We are done here!
date +"%F %T Complete." >> /var/log/callpostnzb.log

```


In the $Home/.nzbperlrc file set

```
postnzb='whateveryourpathis/postnzb.sh'
```

I also have a couple of files for running nzbperl cron jobs with a little zenity display in the taskbar but these pose a little security risk as they use a file for shutting down without root permissions.

---

### Post by TuxCrafter on 2006-09-30
I have tested nzbperl but the decoder is realy realy tooo slow. Hellanzb is far faster with the yenc C decoder. zo nzbperl has indeed nice features but hellanzb does the job better.

---

### Post by ahaslam on 2007-12-10
Nice guide, thank you. & +1 for hellanzb ;)

---

