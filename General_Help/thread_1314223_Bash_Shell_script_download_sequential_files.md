---
title: "Bash Shell script download sequential files"
date: 2009-11-04
forum: General Help
---

### Post by geekynerdz on 2009-11-04
Hi Folks ...1st time poster 

I am semi new to Linux but very new to shell programing ...so here is what I am trying to do

Here is what I am trying to do ... I have a shell script that downloads a bunch of files each day (these files can number all the way from 4 to over 100)  Each file is sequentially named ...so 0065892.PDF  then the next one would be 0065893.PDF all the way to how ever number of files there are there on the server. Each day (monday - friday) new files are added... At current I do a mget for the file name  and then upload them to a diffrent server via a diffrent script... here is what it looks like

PROG_DIR=/usr/myuser/test
BATCH_DIR=/usr/myuser/test

START_TIME=`date`
echo "START " $START_TIME
cd $BATCH_DIR

FILENAME='006'
FNAME=$FILENAME

echo $FNAME

HOST='IP_address of server to connect to'
USER='the user name for the server'
PASSWD='Password for the server'
TPATH='request'
FILE=$FNAME'*.PDF'
ftp -n -i $HOST  <<END_SCRIPT
quote USER $USER
quote PASS $PASSWD
cd $TPATH
bin
mget $FILE
bye
END_SCRIPT
rt1="$?"


This downloads all the files  but also downloads the files that have already been downloaded. so that is the 1st problem


The next is a different script that does the upload

Of those files downloaded  I need to upload those to a different FTP address so I do an mput  but again it copies all the previously downloaded files ...here is what the script looks like

PROG_DIR=/usr/myuser/test
BATCH_DIR=/usr/myuser/test


START_TIME=`date`
echo "START " $START_TIME

cd $BATCH_DIR


FILENAME='006*.PDF'
FNAME=$FILENAME

echo $FNAME

echo "this is the Fname"


HOST='IP of other server to upload to'
USER='usename of ftp'
PASSWD='password for ftp server'
TPATH='/data/SHAREDIR/data/test/pdfs
FILE=$FNAME
ftp -n $HOST <<END_SCRIPT
quote USER $USER
quote PASS $PASSWD
cd $TPATH
bin
verbose
prompt
mput $FILE
quit
END_SCRIPT
rt1="$?"

END_TIME=`date`
echo "END " $END_TIME


Now this will work for all files that start with 006  but once we get to 007  it wont and the script would have to be modified every few weeks/months.

So I guess it comes down to is ...is there a way to download only those new files (there are other files on the server that I do not need)  and upload only those new files

I am on ubuntu 9.04  while the server I download from is unknown (window/unix/linux) and the server I upload to is unknown as well. some research on my part indicated useing rsync  but for that I need to have ssh on all the server (which I do not have access to)  Both these scripts for downloading and uploading run via cron job each night.


So if any one can help it would be greatly appreciated.

Sorry if something like this has been posted before I looked and could not find the exact problem I am in ...  I am a noob !

So quote a very famous line

Help me Obi Wan Kenobi ....your my only hope

---

### Post by tuwe on 2009-11-04
You could use curl to transfer files to or from a server. The -z switch enables you to down-/upload files based on a time condition.

---

### Post by geekynerdz on 2009-11-18
Sorry for the late reply ...

and feel free to bash me for asking this really stupid question .... I looked @ the man curl and how would I implement that in my script to have the date parameter ?

---

