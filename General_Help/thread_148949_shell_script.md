---
title: "shell script"
date: 2006-03-23
forum: General Help
---

### Post by chocolatetoothpaste on 2006-03-23
Hello again.  I have a question about shell scripts.  My digital camera does not work with gphoto, so I want to create a shell script that will just copy the folder from my camera a directory in my home folder.  the location of the camera is /media/usbdisk/DCIM/100_FUJI   I want to copy this whole folder to my home directory, but here is the catch, is there anyway I can rename the folder to the current date?  I guess I am fine with any date format, since I may not have an option.  If there is a way to alter the date format that would be great.  I really would like to learn about shell scripting, so if anyone knows of a good guide that would be great.  But please help me with this script if you can.  I think I have part of it figured out.  for the copy-to part, I would use $USER for the directory, right? that way, whoever was logged on would get the pictures copied to their home folder.  Any help you could give would be great.  Thanks

---

### Post by IYY on 2006-03-23
> Hello again. I have a question about shell scripts. My digital camera does not work with gphoto, so I want to create a shell script that will just copy the folder from my camera a directory in my home folder. the location of the camera is /media/usbdisk/DCIM/100_FUJI I want to copy this whole folder to my home directory, but here is the catch, is there anyway I can rename the folder to the current date? I guess I am fine with any date format, since I may not have an option. Any help you could give would be great. Thanks

No problem: 

[B]#!/bin/sh
foldername=`date +%F`
mkdir "~/somefolder/$foldername"
cp -r /media/usbdisk/DCIM/100_FUJI/* "~/somefolder/$foldername"[/B]

Assuming that you have a folder called somefolder in your home folder, it will create a folder from the output of the "date" command and copy your files to it. However, you don't have to settle for this format. Read the manpage for the date command for various formatting options. You'll be able to make this date look like anything you like.

The formatting **date +%F** which I wrote above will give you a date in the format 2006-03-23, which is nice because it has no spaces in it.

---

### Post by nanotube on 2006-03-23
here is your script:
```

#!/bin/bash
mkdir ~/`date -Idate`
cp /media/usbdisk/DCIM/100_FUJI/* ~/`date -Idate`/
```

first line makes a directory, in form YYYY-MM-DD, second line copies all your stuff from the camera to that folder. save that file, chmod it to executable, and you are all set. :)

---

### Post by chocolatetoothpaste on 2006-03-23
IYY-
  I am sorry I am a bit confused by your post.  How do I format the date then?  I would like this script to be automatic so all I have to do is type in ```
photos
``` or something and have it automagically get the date and create the dir.  This script will do that?  Also, in order to create this script, do I just create a file called "whatever.sh" and run that?  Thank you very much for your quick response.

Thanks nanotube.  I will try it out.  Do you know where I can find more date format codes, to see what my options are?

---

### Post by IYY on 2006-03-23
Copy the script I wrote (or nanotube's, it's pretty much the same thing) into a blank text file. Call it, say, photos. Save this file in /usr/bin or any other folder in your execute path (to see which directories are in your path, run **echo $PATH**). Then do **chmod +x /usr/bin/photos** to make it executable (assuming that you chose to save it in /usr/bin). 

To see the codes, type in the terminal: **man date** to get the manual page for the date command.

For example, **date +%Y** will print out the year. **date +%m** will print out the month. **Date +%Ystuff%m** will print out the year and the month, seperated by the word "stuff". You can read the rest of the codes in the manual page.

---

### Post by chocolatetoothpaste on 2006-03-23
Ok, IYY, I got it working now.  Thank you very much for your help.  I had to change one thing in the script you wrote.  I had to change ```

#!/bin/sh
foldername=`date +%F`
mkdir "~/somefolder/$foldername"
cp -r /media/usbdisk/DCIM/100_FUJI/* "~/somefolder/$foldername"

```
to
```

#!/bin/sh
foldername=`date +%b\ %d\ %Y`
mkdir ~/"fuji/$foldername"
cp -r /media/usbdisk/DCIM/100_FUJI/* ~/"fuji/$foldername"

```

I am by no means complaining; again thank you very much.  I just wanted to point that out in case you missed it, but also for anyone who might find this post in the future with a similar question.   One last question.  In the script, how do I write an if/else statement to see if the fuji folder exists, and create it before the date folder?  Like in psuedo:
```

if(!exists(fuji)){
mkdir(fuji)
mkdir ~/"fuji/$foldername"
cp -r /media/usbdisk/DCIM/100_FUJI/* ~/"fuji/$foldername"
}else{
mkdir ~/"fuji/$foldername"
cp -r /media/usbdisk/DCIM/100_FUJI/* ~/"fuji/$foldername"
}

```
something like that.  Thanks again.

---

### Post by IYY on 2006-03-23
This is what your code translates to:

> 
#!/bin/sh
foldername=`date +%b\ %d\ %Y`
if [ -e fuji ]
then
mkdir ~/"fuji/$foldername"
cp -r /media/usbdisk/DCIM/100_FUJI/* ~/"fuji/$foldername"
else
mkdir fuji
mkdir ~/"fuji/$foldername"
cp -r /media/usbdisk/DCIM/100_FUJI/* ~/"fuji/$foldername"
fi

But even better would be:
> 
#!/bin/sh
foldername=`date +%b\ %d\ %Y`
if [ ! -e fuji ]
then
mkdir fuji
fi
mkdir ~/"fuji/$foldername"
cp -r /media/usbdisk/DCIM/100_FUJI/* ~/"fuji/$foldername"
fi

This is better because you're not repeating the code twice.

And you could also use another method, which would be a bit like cheating:

> 
#!/bin/sh
foldername=`date +%b\ %d\ %Y`
mkdir fuji 2>> /dev/null
mkdir ~/"fuji/$foldername"
cp -r /media/usbdisk/DCIM/100_FUJI/* ~/"fuji/$foldername"
fi

This just tries to make a directory fuji every time. If it fails, it tries to print the output "file exists", but this output is redirected to /dev/null where it is forever lost. ;)

Edit:

Sorry man, I just thought of another way that's even simpler:

> 
#!/bin/sh
foldername=`date +%b\ %d\ %Y`
mkdir -p ~/"fuji/$foldername"
cp -r /media/usbdisk/DCIM/100_FUJI/* ~/"fuji/$foldername"
fi

All we do is just add **-p** to your mkdir command.

---

### Post by chocolatetoothpaste on 2006-03-23
For anyone who may search and find this post in the future, this is the final code that I used to quickly transfer pictures from my camera.  What I was impressed with was how super fast it transfered my pictures, compared to the GUI.  Command line is awesome.
```

#!/bin/sh

pictures=`date +%m-%d-%y`
camera='fuji'
if [ ! -e "$camera" ]
then
mkdir "$camera"
fi

if [ ! -e ~/"$camera/$pictures" ]
then
mkdir ~/"$camera/$pictures"
fi
cp -r /media/usbdisk/DCIM/100_FUJI/* ~/"$camera/$pictures"

```
This way, if the camera directory does not exist it creates it.  Also, if a folder already exists with the same date, it simply copies the new pictures to the existing folder.  Thanks for everyone who helped.  This forum is just one reason why UBUNTU IS THE BEST EVER!

---

### Post by chocolatetoothpaste on 2006-03-23
Hello, all.  I am just posting an update to my original post.  The script has become a little more mature, with the option of arguments.  This is what I have so far:
```

#!/bin/sh

picdir=`date +%m-%d-%y`
usage="Options: [-c camere name] [-d delete source pictures]"

while getopts ":c:d" options; do
  case $options in
    c ) newcam=$OPTARG;;
    d ) delsrc=$OPTIND;;
    h ) echo $usage;;
    \? ) echo $usage

         exit 1;;
    * ) echo $usage
          exit 1;;
  esac
done

if [ $newcam ]; then
camdir=$newcam
else
camdir='fuji-a303'
fi

mkdir -p "$camdir"
mkdir -p ~/"$camdir/$picdir"
cp -r /media/usbdisk/DCIM/100_FUJI/* ~/"$camdir/$picdir"

if [ $delsrc ]; then
rm /media/usbdisk/DCIM/100_FUJI/*
fi

```
Now if you plug in a different camera, instead of going to the "fuji-a303" folder you can specify a new camera model with the -c argument and it will create whatever folder you tell it to.  It also handles wrong args.  Also, with -d it will delete the source pictures.
Now I have another question to pose.  The pictures are stored on the camera in the following format:
DSCF0001.jpg
DSCF0002.jpg
etc.
Now, what if, in the morning I go out and take some pictures, come home, download them, go out and take more pictures, then come home to download them.  Well, on the camera it starts back at DSCF0001.jpg.  This is bad because it will overwrite the picture I took this morning.  So here is the quesion, how could I check to see if the file exists, and if it does, rename the to-be-imported picture to continue where the other pictures left off?  IE  the last picture I took this morning is DSCF0023.jpg.  How do I make the script start copying at DSCF0024.jpg?

---

### Post by chocolatetoothpaste on 2006-03-23
I came up with this, which at least sees all of the .JPG's in the folder.  But how can I start importing pics from where the last round left off.  Also, how can I switch the extension to lowercase while the pics are importing?  I need this for compatability/convenience.

---

### Post by krismatth3 on 2006-03-24
To lowercase-ize the filenames as they're copied, you can do something like:

```

# arg 1: source directory arg 2: destination
function copyFiles()
    SRCDIR=$1
    DESTDIR=$2
    for FILE in "$SRCDIR/"*; do
        NEWFN=`echo $FILE | tr [A-Z] [a-z]`
        if [ "$FILE" != "$NEWFN" ]; then
            cp "$SRCDIR/$FILE" "$DESDIR/$NEWFN"
        fi
    done
}

```

instead of the 'cp -r' your script is currently using. As for checking if a file exists:

```

if [ -f "/path/to/file" ]; then
   # file exists
else
   # doesn't exist
fi 

```

('man test' will list the various options for that if syntax). If you come up with something nice for continuing the numbering where the previous session ended, please post, I'm curious. :)

---

### Post by IYY on 2006-03-24
Here's a solution:

> 
#!/bin/sh

lastNum=`for x in *.jpg
do
        echo $x | cut -dF -f2 | cut -d\. -f1
done | sort | tail -n1`

lastNum=DSCF`expr $lastNum + 1`.jpg
echo $lastNum

For each file you copy, you could check if it exists or not. If it exists, you could run this script.

This will strip DSCF and .jpg from each filename ending with .jpg, then sort them (just in case), then get the last line (the largest number). 
To this last number it will add a 1, then add the DSCF and .jpg and print it out. This is not a perfect solution: one major problem with it is that while adding 1, all leading zeros are cut off (this is easy to fix, but the solution I have in mind is very manual and tedious, using the expr length command; I hope somebody can suggest a one liner for this).

---

### Post by chocolatetoothpaste on 2006-03-24
Thanks for that bit of code IYY.  I took it and this is what I came up with:
```

#!/bin/sh

lastNum=`for x in *.txt
do
echo $x | cut -dF -f2 | cut -d\. -f1
done | sort | tail -n1`

if [ $lastNum \< 10 ];then
lastNum=DSCF000`expr $lastNum + 1`.txt
elif [ $lastNum \< 100 ];then
lastNum=DSCF00`expr $lastNum + 1`.txt
elif [ $lastNum \<1000 ];then
lastNum=DSCF0`expr $lastNum + 1`.txt
else
lastNum=DSCF`expr $lastNum + 1`.txt
fi

echo $lastNum

```
However, this does not seem to work.](*,)  When I had files DSCF0001.txt, DSCF0002.txt, DSCF0004.txt, the next would be DSCF0005.txt (the .txt is just for testing.)  But when I created DSCF0011.txt, the next file would be DSCF00012.txt.  It was resolving true on the first statement!  What is wrong with my conditions?  How is 12 less than 10?!?!:confused:

Edit:  I figured out what my problem is.  I will update the code, test it out, and then post the final product tonight.  Thanks to everyone who helped!

---

### Post by chocolatetoothpaste on 2006-03-26
Well, after many attempts, I must say I cannot get the auto renaming part to work.  As a work around, I set it so that if a directory exists with an identical date, it creates one and includes the time.  That way, unless you can take and import photos twice in less than a minute, this script should serve it's purpose.  When I get better at shell scripting, maye I will take this up again and polish it off. Thanks to all who helped.  Here is the final code.  I hope this will be a benefit to some others. 
PS - if you don't know what I mean by renaming, I mean this.  If you take pictures in the morning, transfer them, then take some later, when you go to transfer them, you will have 2 pictures with the same name, and the one you took later will overwrite the one you took earlier.  So there needs to be a way to find the largest picture name, and then continue copying from there.  IE  the last picture you took in the morning was DSCF0017.JPG.  The script should detect this, and rename the files as they transfer from your camera, starting with DSCF0018.JPG.  Thanks to IYY, who figured out the part to add one to the highest number, I just can't get the transfer part to work.
Anyway, here is the code:
```

#!/bin/sh

picdir=`date +%m.%d.%y`
altdir=`date +%m.%d.%y-%H:%M%P`
usage="Options: [-c camera name] [-d delete source pictures]"

function copyFiles() {
    SRCDIR=$1
    DESTDIR=$2
cd "$SRCDIR/"
    for FILE in *; do
        NEWFN=`echo $FILE | tr [A-Z] [a-z]`
        if [ "$FILE" != "$NEWFN" ]; then
            cp "$FILE" "$DESTDIR/$NEWFN"
        fi
    done
}

while getopts ":c:d" options; do
  case $options in
    c ) newcam=$OPTARG;;
    d ) delsrc=$OPTIND;;
    h ) echo $usage;;
    \? ) echo $usage

         exit 1;;
    * ) echo $usage
          exit 1;;
  esac
done

if [ $newcam ]; then
camdir=$newcam
else
camdir='fuji-a303'
fi

#mkdir -p "$camdir"
if [ -e ~/"$camdir/$picdir" ];then
mkdir -p ~/"$camdir/$altdir"
copyFiles /media/usbdisk/DCIM/100_FUJI ~/"$camdir/$altdir"
echo "Directory exist with matching date.  Creating alternate directory."
else
mkdir -p ~/"$camdir/$picdir"
copyFiles /media/usbdisk/DCIM/100_FUJI ~/"$camdir/$picdir"
fi



if [ $delsrc ]; then
rm /media/usbdisk/DCIM/100_FUJI/*
fi

```

---

### Post by nanotube on 2006-03-26
hey choco
your comparisons did not work because you use incorrect syntax. use "-gt" for greater than, and "-lt" for less than. using "\<" does not do it. so, for example, you would do:

```
if [ $lastNum -lt 10 ];then
lastNum=DSCF000`expr $lastNum + 1`.txt
elif [ $lastNum -lt 100 ];then
lastNum=DSCF00`expr $lastNum + 1`.txt
elif [ $lastNum -lt 1000 ];then
lastNum=DSCF0`expr $lastNum + 1`.txt
else
lastNum=DSCF`expr $lastNum + 1`.txt
fi
```

that should be just about right to get your renaming to work. :)

if you really want to use "\<", then you have to put it through "expr". but why, when -lt does the trick just fine? :)
btw, "man test" for more details.

---

### Post by chocolatetoothpaste on 2006-04-02
Alas, I have reached my goal for this project.  This script will transfer pictures from my camera, and if there is already a directory with todays date, it will look to see if it has files already.  If it does, it dynamically renames pictures to avoid overwriting pics with the same name.  So without further delay, here is the script:
```

#!/bin/bash
#A script for transfering pictures from a digital camera.
#Ross Paskett - 2006.
#This code may be used, abused and redistributed in anyway, as long as due credit is given
#Thanks to IYY, member of ubuntuforums.org, for the filename spliting code.

picdir=`date +%m.%d.%y`
usage="Options: [-c camera name] [-d delete source pictures]"
camsrc=/media/usbdisk/DCIM/100_FUJI

while getopts ":c:d" options; do
  case $options in
    c ) newcam=$OPTARG;;
    d ) delsrc=$OPTIND;;
    h ) echo $usage;;
    \? ) echo $usage

         exit 1;;
    * ) echo $usage
          exit 1;;
  esac
done

if [ $newcam ]; then
    camdir=$newcam
else
    camdir='fuji-a303'
fi

dst=~/$camdir/$picdir

mkdir -p ~/"$camdir/$picdir"
    if [ ! -e "$camsrc" ];then
        echo "Camera is not attached or incorrect path:"
        echo "$camsrc"
        exit 1
    fi

  for exstnc in $camsrc/*;do
    if [ ! -e $exstnc ];then
     echo "No pictures on camera!"
     exit 1
    fi
  done

clear

echo "Transfering pictures:"
  cd $camsrc
    for fl in *;
    do

    campic=`echo $fl | cut -dF -f2 | cut -d\. -f1`

    extn=`echo $fl | cut -d\. -f2 | tr [A-Z] [a-z]`

    if [ "X$extn" = "Xjpg" ];then
      pref="pic"
    else
      pref="mov"
    fi

    firstNum="$pref$campic"."$extn"

    cd $dst
    if [ -f "$firstNum" ];then
      cd $dst

      if [ "X$extn" = "Xjpg" ];then
        lastNum=`for x in *."$extn"
        do
        echo $x | cut -dc -f2 | cut -d\. -f1
        done | sort | tail -n1`
      else
        lastNum=`for x in *."$extn"
        do
        echo $x | cut -dv -f2 | cut -d\. -f1
        done | sort | tail -n1`
       fi


      if [ $lastNum -lt 9 ];then
        lastNum="$pref"000`expr $lastNum + 1`."$extn"
      elif [ $lastNum -lt 99 ];then
        lastNum="$pref"00`expr $lastNum + 1`."$extn"
      elif [ $lastNum -lt 999 ];then
        lastNum="$pref"0`expr $lastNum + 1`."$extn"
      else
        lastNum="$pref"`expr $lastNum + 1`."$extn"
      fi
      echo "$dst/$lastNum"
      cp "$camsrc/$fl" "$dst/$lastNum"

    else
      cd $camsrc
      echo "$dst/$firstNum"
      cp $fl "$dst/$firstNum"

    fi
  done

if [ $delsrc ]; then
  echo " "
  for DEL in $camsrc/*; do
  echo "Deleting: $DEL"
    rm -f "$DEL"
  done
fi

echo "Transfer complete!"
echo " "

```Thanks to all who have contributed.  I have had substantial help along the way, and I hope that this script will help others.  By the way, if you have any comments about this script, like if something can be done better, please by all means, fire away!

Edit:
Updated code again, so now it will also get the file extension dynamically, and retain.  I added this because my camera also takes video, and I don't want those renamed to jpg's!

---

