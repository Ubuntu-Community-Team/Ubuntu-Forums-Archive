---
title: "BASH:execute next command until another command succeed"
date: 2010-03-19
forum: General Help
---

### Post by yu xintian on 2010-03-19
Hi,comrades here ![IMG]http://forums.fedoraforum.org//forum/images/smilies/smile.gif[/IMG] I have a big bash script ,its goal is to download movie one by one . But I often get into a problem: if this script is executed in cron,it often does not completely download the movie.I often find the movies it downloaded are several KB while the movie is actually 20MB.So I think it is because it did not wait for finishing one task ,and jump to download another.So I want to know ,is there a way to force the bash script to wait until one movie downloaded completely and then start to download another movie ? Please give me a hint ,thank you ![IMG]http://forums.fedoraforum.org//forum/images/smilies/smile.gif[/IMG]

---

### Post by prodigy_ on 2010-03-19
Try to add ```
wait
``` command after every d/l command.

---

### Post by lavinog on 2010-03-19
what are you using to download? Wget?

---

### Post by asmoore82 on 2010-03-19
> **lavinog said:**
> what are you using to download? Wget?

[size="4"]+1[/size]

---

### Post by amauk on 2010-03-19
It's a little unclear exactly what the issue is

Are you saying that the cron jobs run over each other?
(Ie. next run starts before last run finishes)

If so, then use a simple check like this

```
#!/bin/sh

RUN_CHK="/tmp/my_prog"

if [ -f "$RUN_CHK ]; then
	exit 1
fi

/usr/bin/touch "$RUN_CHK"
# rest of program
/bin/rm -f "$RUN_CHK"
```

However, if you mean that your program (for some reason) falls over when run as cron
check that you are using absolute paths for any external commands (as shown in the above)
Cron runs with a minimal environment (for efficiency) and some common dirs are not included in the PATH variable
Always use absolute paths to be sure

You can also try splitting the script up
have one script for downloading a file (path / url passed as cmdline arg)
and another program for producing a list of paths / urls which then loops, calling your download script with appropriate args


As others have said,
also look into the "wait" bash command
You can pause a parent script while a child script is executing

The bash internal variable $! returns the PID of the last backgrounded process
the wait command halts further execution until a specific PID has exited,
so you can do this

```
#!/bin/sh

# compile list of urls for wget

for URL in $URLS; do
	/path/to/download_script.sh $URL &
	wait $!
done
```

---

### Post by dcstar on 2010-03-19
> **yu xintian said:**
> Hi,comrades here ![IMG]http://forums.fedoraforum.org//forum/images/smilies/smile.gif[/IMG] I have a big bash script ,its goal is to download movie one by one . But I often get into a problem: if this script is executed in cron,it often does not completely download the movie.I often find the movies it downloaded are several KB while the movie is actually 20MB.So I think it is because it did not wait for finishing one task ,and jump to download another.So I want to know ,is there a way to force the bash script to wait until one movie downloaded completely and then start to download another movie ? Please give me a hint ,thank you ![IMG]http://forums.fedoraforum.org//forum/images/smilies/smile.gif[/IMG]

command2 will only run if command1 exits with Status 0 (successful):
```
command1 && command2
```

---

### Post by yu xintian on 2010-03-19
Hi,amauk ! Thank you for your reply,I think my codes here will show you my idea.I put it in a cron job.But sometimes I get that problem when I want to download some  package(contains movies).This script will get order from a web page and download the movie listed in another web page.

>  #!/bin/sh

#==THIS IS THE FUNCTION I THINK HAS A BUG ==
getmovies(){
u="http://my_site/getSchedule.do?id=100001&&type=playlist"
wget   $u -P /home/me/Documents/
movie_list="/home/me/Documents/getSchedule.do?id=100001&&type=playlist"

#===DOWNLOAD MOVIES IN NEED==========

touch /home/me/Videos/all
echo "" > /home/me/Videos/all
for file in /home/me/Music/*
do
cat $file >> /home/me/Videos/all
done
#====DELETE  MOVIES I ALREADY HAVE BUT NOT IN THE LIST==========
all=/home/me/Videos/all

for movies in /home/me/Download/* 
do
exec < /home/me/Videos/all 
flag=0
while read REPLY
do
echo "I want"  $REPLY
if [ "/home/me/Download/$REPLY" == "$movies"  ]
then
flag=1
echo " mached !"
break
fi
done

if [ $flag == 0 ]
then
rm -rf $movies
echo "deleting $movies !"
fi
done    

#=======DOWNLOAD MOVIES I WANT=========== 
exec < /home/me/Videos/all
while read newnm
do
if [ -e /home/me/Download/$newnm ]
then
echo " $newnm exists"
else
echo "need to download $newnm"
/usr/bin/wget     http://my_site/files/$newnm -P /home/me/Download/  
fi

sleep 1
done
rm -f $all
rm -f $movie_list

}



processLine() {
line="$@"
if [ "$line" == "download_this" ]
then
echo "get movies "
getmovies          
fi
unpackage
}


unpackage() {
for package in /home/me/Download/*
do
package=`echo $package | cut -d'/' -f5`
extend_name=`echo $package|cut -d '.' -f2`
name=`echo $package|cut -d '.' -f1`
if [ $extend_name == "tar" ] ||  [ $extend_name == "zip" ]
then
tar -xf /home/me/Download/$package -C  /home/me/Download/
unzip /home/me/Download/$package
rm -f $package
fi
done
}


#=============MAIN PROCESS=========
wget  [http://my_site/order.do?id=100001](http://my_site/order.do?id=100001)  --timeout=50 -P /home/me/Documents

order=/home/me/Documents/order.do?id=100001

   if [ ! -f $order ]; then
        echo "$order : does not exists"
        exit 1
   elif [ ! -r $order ]; then
        echo "$order: can not read"
        exit 2
   fi  

FL=`head -n 1 $order`
sed -i 1d $order
processLine $FL 
rm -f $order
exit 0Anybody please feel free to tell me if you feel this script ugly or wrong,thank you !

---

### Post by DaithiF on 2010-03-19
It may be this bug: [https://bugs.launchpad.net/ubuntu/+source/cron/+bug/151231](https://bugs.launchpad.net/ubuntu/+source/cron/+bug/151231)
Redirect output of the cron entry to /dev/null or set MAILTO as described in the workarounds.

---

### Post by yu xintian on 2010-03-23
Hi,people ! This problem solved ! The problem lies in another script which create movie list for Mplayer ( My idea is download movies and play it with mplayer ). And also I should make the script executes in */3 instead of  */1.This makes sense. Thank you for all your ideas;)

---

