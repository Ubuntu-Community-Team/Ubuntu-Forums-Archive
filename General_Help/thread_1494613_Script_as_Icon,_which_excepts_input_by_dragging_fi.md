---
title: "Script as Icon, which excepts input by dragging file or directory"
date: 2010-05-27
forum: General Help
---

### Post by BergmanW on 2010-05-27
L.S.

I hardly dare to ask.

I havein W7 een .bat file in which I use the exiftool to change several items in  .jpg files   (copyright, owner etc)
This is put as an Icon on my desktop.
I can drag a directory or a file to this icon and it will be processed by the script with the directory or file as input.

My question, of course, is how to realize this on Ubuntu.

script  Copyright.bat looks like this :
@echo off

rem Update jpg  data in file %1, Wil Bergman (c) 2010

rem is done with use of exiftool, so must be in the PATH.



IF  [%1]==[] goto :help
:start
SET JPGFILE=%1
IF  NOT EXIST %1 SET JPGFILE=%1.jpg
IF NOT EXIST %JPGFILE% goto  :error

c:\Copyright\exiftool -@  c:\Copyright\Copyright_options.txt %JPGFILE%

shift

IF  NOT [%1]==[] goto :start

goto :end


Hope I&#7743; in the right somebody can help

:error
Echo  can not find %JPGFILE% or %JPGFILE%.jpg
goto :end

:help
echo  copyright.bat edits EXIT/IPTC of a JPEG foto with use of

echo the program exiftool (so must be in the PATH).

echo Call: Copyright_auto {filenaam}
echo Or make a icon of this script and drag a file or folder on it
echo  Wil Bergman (c) 2010

:end

@SET JPGFILE=

pause hello

---

### Post by lykeion on 2010-05-27
The equivalent of windows/DOS batch files in Ubuntu is bash scripts.

1. start up a text editor (gedit, geany or whatever)
2. create a new text file and paste this code in:
```
#!/usr/bin/env bash

# function to output usage info
usage() {
cat << EOF
Usage: `basename $0` [INPUT]

INPUT:
   Name of the jpeg file
EOF
}

# test if number of arguments is 1
if [ $# -ne 1 ]; then usage; exit 1; fi

# assign the argument to the variable INPUT
INPUT="$1"

# test if INPUT does exist AND is a file
if [ -e "$INPUT" -a -f "$INPUT" ]; then 
	echo "OK: $INPUT is an existing file."
else
	echo "Error: $INPUT does not exist or is not a file."
	usage
	exit 1
fi 

# test if INPUT is a JPEG file using the file command
IS_JPEG=$(file -b "$INPUT" | grep JPEG)

if [ -n "$IS_JPEG" ]; then 
	echo "OK: $INPUT is a JPEG file"
else
	echo "Error: $INPUT is not a JPEG file."
	usage
	exit 1
fi

# test if the exiftool is installed
EXIFTOOL=$(which exiftool)

if [ -n "$EXIFTOOL" ]; then 
	echo "OK: exiftool is installed"
else
	echo "Error: Exiftool must be installed to use this script, use this command:"
	echo "sudo apt-get install libimage-exiftool-perl"
	exit 1
fi

# make sure the file Copyright_options.txt is in your your home folder
# you might want to perfom exist and file tests for this file also 
COPYRIGHT_FILE=~/Copyright_options.txt

# perform the exiftool command on the JPEG file
$EXIFTOOL -@ $COPYRIGHT_FILE "$INPUT"

# this is needed to not let the terminal window close immediately
read -p "Press enter to continue"

exit 0

``` 

3. save this file (as copyright.sh) somewhere in your home directory

4. rightclick the file in Nautilus > Properties > Permissions tab
Tick on "Allow executing as program"

5. make sure you have the file Copyright_options.txt in your home folder (this path is hard-coded in the script)

Now you have a script file which you could execute in a terminal like this:
> /path/to/copyright.sh image_file.jpeg

To make a luncher on the panel where you can drop jpeg files to perform the script:

1. Right-click panel > Add to panel... > Custom application launcher

2. Fill in the fields:
Type: <change to Application in Terminal>
Name: <any name you like>
Command: <click Browse... and select the script file copyright.sh>
Comment (optional): <any comment you like>
Icon (optional): <click icon and browse to a suitable icon image>

Hope this helps.

PS. Writing bash scripts is not that hard (especially since you already know hot to write DOS batch files).
You can google around to find out the basics of bash scripting. This is a start:

[http://tldp.org/LDP/abs/html/dosbatch.html](http://tldp.org/LDP/abs/html/dosbatch.html)

PS2. Personally I think you shouldn't press too hard on adding (c) info (as you did in the help section of your batch file).
Scripting and coding is something you learn by sharing with others, not secluding others with copyrights and stuff.

---

### Post by BergmanW on 2010-06-19
The script is meant to put a copyright in jpeg foto's. Which I take and distribute.
Of course not for scripts.

---

