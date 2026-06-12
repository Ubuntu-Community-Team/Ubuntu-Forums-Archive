---
title: "script to cut some steps out"
date: 2011-07-19
forum: General Help
---

### Post by sectshun8 on 2011-07-19
I'm looking to write a .sh script to help cut out some steps, and just make running the script do the work.

I want it to:

- ftp into a given IP and login
- go to a specific dir
- "get" the newest file
- exit ftp
- bzip2 the file

Doesn't seem like it'd be hard... but then, I just really don't know.

Anyone give some pointers on how to accomplish this?

---

### Post by sectshun8 on 2011-07-19
Just trying some stuff... I'm able to ftp in and "put" a defined file in a defined directory with this script... but how can I make it look for the most recent file?  Or at the very least list the files in the directory and allow the user to choose which to FTP?  Is there any way to bzip2 a file while in the ftp session?

EDIT:  I edited the code slightly to zip before ftp'ing.  So really... if I can just get it to choose the newest file I'd be all set here :)  Anyone?

```

#!/bin/sh
HOST='<IP ADDRESS>'
USER='<user>'
PASSWORD='<pw>'
DIR='<dir>'
FILE='<filename>'

echo "Compressing file... "
bzip2 $FILE

echo "Transferring file... "
ftp -n $HOST <<END_SCRIPT
quote USER $USER
quote PASS $PASSWORD
cd $DIR
put $FILE
bye
END SCRIPT

echo "Transfer complete."
exit 0
```

---

### Post by jhonan on 2011-07-19
Do you need to unzip the file after you've PUT it?

---

### Post by jhonan on 2011-07-19
Also, have you checked out [rsync](http://en.wikipedia.org/wiki/Rsync) or [unison](http://en.wikipedia.org/wiki/Unison_%28file_synchronizer%29) for this kind of task? (Unison has a nice front-end which lets you select various actions on different files - upload/download/delete etc.)

---

### Post by sectshun8 on 2011-07-19
No, no need to unzip it after.

Really just trying to find how to make it so this script will find and use the most recent file without being told which file it is.... then, it does everything I want :)

EDIT:  And no, I don't need any front end.  95% of my work is done in command line, so I'm keeping it that way so my other shift can just run a command and get the same results.  It's a short script that saves us a bunch of time to do other stuff while all that is going on and not having to babysit to see when we can go to the next step.

---

### Post by sectshun8 on 2011-07-19
Well.. I was able to get it to work with a user defined file.  The program will list the available files and allow you to choose which.  So I'm pretty happy with it.

Next step will be adding a fucntion a the beginning to copy say XXX.tif to another directory and rename it to XXX+1.tif... then proceed with the rest of the script.   :P

```
#!/bin/sh
#Automated .tif compression and transfer utility
#Created by XXXX
HOST='<IP>'
USER='<user>'       
PASSWORD='<PW>'
DIR='<dir>'

display_seq(){
echo " "
echo "Copy sequence and hit enter."
ls -rt 
}
read_seq(){
read FILE_NAME;
}

display_seq;
read_seq;

echo "Compressing file... "
bzip2 $FILE_NAME
echo "Compression complete."

FILE=$FILE_NAME'.bz2'

echo "Transferring file... " 
ftp -n $HOST <<END_SCRIPT
quote USER $USER
quote PASS $PASSWORD
cd $DIR
put $FILE
bye
END_SCRIPT
echo "Transfer to QC5 complete."
exit 0
```

---

### Post by sectshun8 on 2011-07-20
So my above script works great on my one machine... however due to the limitations of the version of bzip2 we have on it... I decided to move the scrip to the other machine and go the opposite way.

Unfortunately this means the script needs to be changed.

Now I need to find a way to FTP into one machine, and then the script needs to find the newest/latest file and "get" it... bring it back to itself... I can handle the bzip2 after.

But how can I ftp in and get the newest file without telling it what file it is? :confused::confused::confused:

---

### Post by dethorpe on 2011-07-20
I don't think FTP will have a way to pick a file by date ( i could be wrong) so think you'd have to do that in three stages.
 
1) An initital FTP command to do a directory listing with dates (DIR command or ls -l) and capture that output
2) Back in the bash script work out which file you want from the captured directory listing based on the date.
3) A second FTP to GET that particuler file.
 
Using perl with the net::FTP module would probably be easier than trying to do it in a bash script if that is possible for you.

---

### Post by sectshun8 on 2011-07-20
Not sure that anyone gives a damn, but I found a solution.

I wrote the script to FTP in to the remote host and then ls the contents of the directory into a file called lastfile.txt that is automatically sent back to my local host.

Then i set the file variable to equal the output of the last entry in lastfile.txt.

Then FTP back in and get it.. then compress it on my local machine.

Seemed to take forever as I didn't really find any other solutions after hours of looking online.

```
#!/bin/sh
#Automated .tif compression and transfer utility
#Created by CCCC
HOST='<IP'
NAME='<USER>'
PASSWORD='<PW>'
DIR='<DIR>'

echo "Locating file... "
ftp -n $HOST <<END_SCRIPT
quote USER $NAME
quote PASS $PASSWORD
cd $DIR
ls . lastfile.txt
bye

END_SCRIPT

FILE=`more lastfile.txt | tail -1`

echo "Transferring File... "
ftp -n $HOST <<END_SCRIPT
quote USER $NAME
quote PASS $PASSWORD
cd $DIR
get $FILE
bye

END_SCRIPT

echo "Compressing File... "
rm lastfile.txt
bzip2 $FILE

echo "Script complete."
exit 0

```

---

### Post by Bandit on 2011-07-20
This FTP flag may help:
```
**newer** file-name [local-file]
Get the file only if the modification time of the remote file is more
recent that the file on the current system.  If the file does not exist on
the current system, the remote file is considered newer.  Otherwise, this
command is identical to get.

```

Use man for more info.

---

### Post by dethorpe on 2011-07-21
> **sectshun8 said:**
> 
I wrote the script to FTP in to the remote host and then ls the contents of the directory into a file called lastfile.txt that is automatically sent back to my local host.
 
Then i set the file variable to equal the output of the last entry in lastfile.txt.
 
Then FTP back in and get it.. then compress it on my local machine.
 

 
Yup, thats the algorithum i figured you'd have to use. 
 
May be able to avoid the temporary lastfile.txt file and just capture the output of stdout from the ftp command directly using *output=$(ftp ...)* and then parse the output to get the file name you want to GET, would save the FTP transfer of the file, might speed it a bit.

---

