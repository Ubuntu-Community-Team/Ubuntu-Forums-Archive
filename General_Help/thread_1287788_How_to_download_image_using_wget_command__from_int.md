---
title: "How to download image using wget command  from internet every 30 min"
date: 2009-10-10
forum: General Help
---

### Post by sundar_ima on 2009-10-10
Here is my requirement. I have to download image from this link [http://imd.gov.in/section/dwr/dynamic/doppler-caz.htm]("http://imd.gov.in/section/dwr/dynamic/doppler-caz.htm") But this image is updated every 30 min. Therefore i need to download those new image every 30 min and save in the same folder (with out deleting previously downloaded image).

The problem is that i am unable to download image from above link using this command (because the link does not end with ".jpg")  ```
wget --output-document=dwr_$(date +\%Y\%m\%d\%H).htm "http://imd.gov.in/section/dwr/dynamic/doppler-caz.htm"
``` Also URL does not change even though image is updated.

If anybody know the proper command can help me. 
Is there any shell script to do this? 
If not how to write it? 

**Note :: i am not a programmer but have very basic idea of shell script**

---

### Post by The Cog on 2009-10-10
The \url of the actual image is:
[http://imd.gov.in/section/dwr/img/caz_chn.gif](http://imd.gov.in/section/dwr/img/caz_chn.gif)

Assuming the rest of the command you posted is OK, then I suggest you put it as a command into your cron (scheduler) table.

Use the command **crontab -e** (which opens an editor on your cron scheduler's configuration file) and add a line to the file like this:
```
0,30 * * * * wget --output-document=dwr_$(date +\%Y\%m\%d\%H).gif "http://imd.gov.in/section/dwr/img/caz_chn.gif"
```

---

### Post by StuartN on 2009-10-10
> **sundar_ima said:**
> I have to download image from this link

1. The image at this page has the URL [http://imd.gov.in/section/dwr/img/caz_chn.gif](http://imd.gov.in/section/dwr/img/caz_chn.gif), so that is what you should wget.

2. You will overwrite the first image each hour unless you add %M (minutes) to the date specification string.

3. Your command becomes:
```
wget --output-document=dwr_$(date +\%Y\%m\%d\%H\%M).gif http://imd.gov.in/section/dwr/img/caz_chn.gif

```

4. Run **crontab -e** to enter the cron scheduled job editor and add a line beginning **0,30 * * * * ~/my_command**, meaning 0 and 30 minute (of every hour, date, month, day, etc) run my_command. Either enter the whole wget command or save the wget command in a file, make that file executable and call it. The second is preferable because editing the script is easier than editing the crontab. (Call it something like "Save_Image" and save it in your home directory).

---

### Post by The Cog on 2009-10-10
Snap! LOL.

By the way,
first time you launch crontab -e it asks which editor to use. If you're not sure, choose nano. Vi is somewhat cryptic to use.

---

### Post by StuartN on 2009-10-10
> **The Cog said:**
> Snap! LOL.

Except my arthritic fingers take longer...

---

### Post by sundar_ima on 2009-10-11
Thanks for the reply. 

But how did you find the actual url is [http://imd.gov.in/section/dwr/img/caz_chn.gif]("http://imd.gov.in/section/dwr/img/caz_chn.gif") and not [http://imd.gov.in/section/dwr/dynamic/doppler-caz.htm]("http://imd.gov.in/section/dwr/dynamic/doppler-caz.htm")

---

### Post by blackened on 2009-10-11
Open the html page in firefox, right-click on the image, select "properties" and it will display the URL for the picture.

---

### Post by sundar_ima on 2009-10-12
Thank you man. I never thought it would be so simple to find :-)

---

### Post by sundar_ima on 2009-10-12
One more question. Is it possible to edit crontab  by using geit??? bcoze i am finding it difficult using **vi / nano**.

---

### Post by StuartN on 2009-10-12
> **sundar_ima said:**
> One more question. Is it possible to edit crontab  by using geit??? bcoze i am finding it difficult using **vi / nano**.

Yes, but I have no idea what other system commands will be affected. Fortunately the setting below will be forgotten as soon as you close the terminal session:

```
export EDITOR=gedit
crontab -e
```

---

### Post by sundar_ima on 2009-10-13
Thank you all. It woks like a charm :-)

---

### Post by sundar_ima on 2009-12-22
hi,
thank you all for your kind help. 

Now i have some other query to ask. 

**_Here is my requirement:-_**

1. Following is the url from which i have to download a picture.

[http://imd.gov.in/section/dwr/img/caz_chn.gif]("http://imd.gov.in/section/dwr/img/caz_chn.gif")

2. I have to save the downloaded file in a folder as per system date & time.

3. The above mentioned website uploads an image with the same name (irrespective of time interval)

4. Again i have to download the updated picture and save in the same folder.


Is there any script or command to that???

---

### Post by StuartN on 2009-12-22
> **sundar_ima said:**
> 2. I have to save the downloaded file in a folder as per system date & time.

I am not sure that I understand the problem - but if you mean that you want part of the date and time to become a folder, and you wish to save the image into that (possibly newly created) folder, then these two commands will work:

```
mkdir --parents images_$(date +\%Y/\%m/\%d)
wget --output-document=images_$(date +\%Y/\%m/\%d\/%Y\%m\%d\%H\%M).gif http://imd.gov.in/section/dwr/img/caz_chn.gif
```

**mkdir --parents** makes a directory, including all the path components, and ignores any errors if the directory already exists. It does not overwrite or delete if the directory exists.

The date format in the wget command, $(date +\%Y/\%m/\%d\/%Y\%m\%d\%H\%M), makes paths of the form 2009/12/22/200912220922 which creates year, month and day directory with a file using year month day hour minute. The year month day can be repeated in the format.

Obviously the path in mkdir and wget (\%Y/\%m/\%d/) must match, but you easily modify them. I repeated the year month day to create unique filenames even between directories - perhaps it is not useful, but it has zero cost.

---

### Post by sundar_ima on 2009-12-22
Thank you for the reply. 

What I meant was to download the picture and save in a folder which i already created in home directory. Name of the file should have date and time (only).

---

### Post by StuartN on 2009-12-22
> **sundar_ima said:**
> What I meant was to download the picture and save in a folder which i already created in home directory. Name of the file should have date and time (only).

The --output-document=<path/file> parameter can contain forward slash / characters. If the directory has a fixed name mydir then --output-document=mydir/$(date +....gif) will save into that directory.

The previous example (--output-document=images_$(date +\%Y/\%m/\%d\/%Y\%m\%d\%H\%M).gif) saves to a directory <year>/<month>/<day>.

In both cases, wget will generate an error if the directory does not exist, but mkdir --parents <path> will create a new directory if <path> does not exist, or do nothing if it already exists.

---

### Post by sundar_ima on 2009-12-22
Thank you StuartN.

It is working but how do i download updated image every time???

---

### Post by JoelOl75 on 2009-12-23
Plus it will need to be run as root, so start with a sudo -i unless you created a root account.

sudo -i
export EDITOR=gedit
crontab -e

---

### Post by StuartN on 2009-12-23
> **sundar_ima said:**
> It is working but how do i download updated image every time???

What part is not working? The command is now something like:

wget --output-document=mydir/$(date +\%Y\%m\%d\%H\%M).gif [http://imd.gov.in/section/dwr/img/caz_chn.gif](http://imd.gov.in/section/dwr/img/caz_chn.gif)

where the directory mydir already exists. Each time it is run, it creates a new file with the current date and time, which is a copy of whatever is on the website (so the copy may be a duplicate of the previous run). It seems to me that the time on the website changes every 15 minutes.

Possibly you need the whole path, like /home/stuart/mydir/, instead of the path from the current directory, just mydir/, to be sure of where cron places the file.

---

### Post by sundar_ima on 2009-12-24
Thank you for the reply again.

When i run the command suggested by you it creates a folder called **images_2009 --> 12 --> 23** and saves the downloaded file in **23**. I assume that 12 is month and 23 is date (bcoz i ran the command on 23rd Dec 09). This is what exactly i wanted.

Whit this 50% of the work is done. Now the problem is that the web page updates the image very often. Some time it may be every 15 min or in some  cases it may be 10 min. When ever the picture is being updated url  directing to the new image / picture will be same as mentioned earlier (same url for old and new picture). 

My requirement is to **run the command / script once** and download pictures when ever picture is being updated on the web server / web page.

Possible solution is to download the image from same url every 30 min or 15 min using **crontab -e**. But in some cases same image is downloaded again and some time few pictures are missed.

Any possible solution???

---

### Post by iMisspell on 2009-12-24
> **sundar_ima said:**
> But how did you find the actual url is [http://imd.gov.in/section/dwr/img/caz_chn.gif]("http://imd.gov.in/section/dwr/img/caz_chn.gif") and not [http://imd.gov.in/section/dwr/dynamic/doppler-caz.htm]("http://imd.gov.in/section/dwr/dynamic/doppler-caz.htm")In firefox, you can also right click on the image and "*View Image*".

> **sundar_ima said:**
> Possible solution is to download the image from same url every 30 min or 15 min using **crontab -e**. But in some cases same image is downloaded again and some time few pictures are missed.

Any possible solution???
For the first part, you might beable to compair the image size, would require alittle coding (not sure how a gif's meta tag works or if they even have them,but if so, you could check the date of the image creation). As for missing images, personaly, i dont see any way around this with out killing the server and checking it all the time, which could get you into trouble with them.

Maybe if you post what you are trying to do; exactly, someone might beable to give you another solution to this.

_

---

### Post by HighCommander540 on 2009-12-25
> **sundar_ima said:**
> Thank you for the reply again.

When i run the command suggested by you it creates a folder called **images_2009 --> 12 --> 23** and saves the downloaded file in **23**. I assume that 12 is month and 23 is date (bcoz i ran the command on 23rd Dec 09). This is what exactly i wanted.

Whit this 50% of the work is done. Now the problem is that the web page updates the image very often. Some time it may be every 15 min or in some  cases it may be 10 min. When ever the picture is being updated url  directing to the new image / picture will be same as mentioned earlier (same url for old and new picture). 

My requirement is to **run the command / script once** and download pictures when ever picture is being updated on the web server / web page.

Possible solution is to download the image from same url every 30 min or 15 min using **crontab -e**. But in some cases same image is downloaded again and some time few pictures are missed.

Any possible solution???

No, there isn't a way for wget to check if the picture has changed. The only way would be to have it get the picture every very short period of time like 5mins. The have it run MD5 on the last picture it got and the picture it just got if they are the same get rid of the last picture if they are different keep them both.

---

### Post by sundar_ima on 2009-12-25
> Maybe if you post what you are trying to do; exactly, someone might beable to give you another solution to this.

The picture which you see in the url is actually Doppler weather radar picture. This radar product is ultimate solution for most of the aviation related now-casting (short time forecast). What i am doing with this picture is "research" on thunderstorm. However to do my research work i need all the pictures uploaded on this url ([http://imd.gov.in/section/dwr/img/caz_chn.gif]("http://imd.gov.in/section/dwr/img/caz_chn.gif")). At present i have to download all the pictures manually which resulting in Omittance of some / more pictures. This is why i came here for the help.

> you might beable to compair the image size

> The have it run MD5 on the last picture it got and the picture it just got if they are the same get rid of the last picture if they are different keep them both.

After reading above two quotes it seems like there is a possible solution for my question (However 2nd quote i have not understood till now). I have checked with two different pictures and the size of both images are different. 

> would require alittle coding

This is where i am lagging. 

Any idea???

---

### Post by iMisspell on 2009-12-25
The following code is not the most elegant, but should do what you want.

In what ever folder you are saving your downloaded images to, create a file in that folder named; **watch_weather.sh** copy the code below to it and make it executable.


Your cron job will have to be changed to...
```
0,05 * * * * /path/to/watch_weather.sh
```


You will have to change the number in the '**timedelay**' variable to what ever amount of minutes you use in your cron job.
```

# edited code is four posts below

```
[http://ubuntuforums.org/showthread.php?p=8563128&posted=1#post8563128](http://ubuntuforums.org/showthread.php?p=8563128&posted=1#post8563128)

good luck...


_

---

### Post by sundar_ima on 2009-12-25
Hi iMisspell,

Thank you for the script. I ran the script and it downloaded the picture once. thats it. After that nothing has happened.

any clue???

---

### Post by iMisspell on 2009-12-25
> **sundar_ima said:**
> ..I ran the script and it downloaded the picture once. thats it. After that nothing has happened.

any clue???
I would say the problem is with the crontab, but i do not know alot about cron jobs so im no help to you there, sorry, maybe someone else can point you in the right direction with that.


Ive edited the script, put the code in a loop.
You will *have to run the script in terminal* or else it will run forever.
While the script is running in your terminal window, you can press the 'enter' key and it will exit the script.

Same as before, you need to place this script in a file in your "download" folder. With this script, *do not* use cron.
```

#!/bin/bash
 
# change that number to how ever many minutes you are checking the site.
timedelay=5; 

# URL to download from
downloadURL='http://202.54.31.8/section/dwr/img/caz_chn.gif';


# the sleep command works off of seconds, so we have to convert the 'timedelay' minutes to seconds.
sleepDelay=$((60 * $timedelay));

#print timedelay to screen...
echo "=======================================";
echo "Download image every $timedelay minutes";
echo "=======================================";
echo "Press the 'enter' key to exit";
echo "=======================================";
echo "";

#loop over the code
while [ 1 ]
do

# this will get the current date (year and month) and time (hour and minute)
CurrentTime=$(date +\%Y\%m\%d\%H\%M);

# this will subtract what ever minute vause you asign to 'timedelay' from the CurrentTime
LastTime=$(($CurrentTime - $timedelay));

# Download your image and save the file yyyymmhhmm.gif
wget --output-document=$CurrentTime.gif $downloadURL

# md5 check sum on the current file you downloaded and save results to 'test1'
test1=`md5sum $CurrentTime.gif | awk '{print $1}'`

# Check to see if old file exists, if so run check sum
if [ -s "$LastTime.gif" ]; then
	
	# md5 check sum on the last file you downloaded and save results to 'test2'
	test2=`md5sum $LastTime.gif | awk '{print $1}'`

	# compair 'test1' to 'test2', if they both have the same check sum, delete the last downloaded image
	if [ "$test1" == "$test2" ]; then
	  rm "$LastTime.gif";
	fi
fi

# pause's for a set number of seconds and checks tty to see if the 'enter' has been pressed during the pause, if so, exit loop
read -t $sleepDelay && break


#pause - another way to pause the loop
#sleep $sleepDelay;

#continue loop
done

exit


```

---

### Post by sundar_ima on 2009-12-26
> I would say the problem is with the crontab, but i do not know alot about cron jobs so im no help to you there, sorry, maybe someone else can point you in the right direction with that.

Your first script is working. After posting my previous reply i have noticed that the pictures were stored in home folder instead of the script folder. Except this (**bug ;-)**) your script works with out an error. 

> Ive edited the script, put the code in a loop.

Thank very much for the script. It is working absolutely fine. You have saved my valuable time. :) :) :)

---

### Post by iMisspell on 2009-12-26
> **sundar_ima said:**
> Thank very much for the script. It is working absolutely fine. You have saved my valuable time. :) :) :)
Your welcome.


> **sundar_ima said:**
> Your first script is working. After posting my previous reply i have noticed that the pictures were stored in home folder instead of the script folder. Except this (**bug ;-)**) your script works with out an error. 
OK, here is an edited version of the first script so you can run it as a cron-job.
You will have to edit the '**saveFolder**' variable to reflect your save folder.

Personaly i think running something like this is better in as a cron job, but thats just me.
Anyway, now you have two ways of doing it.

```

#!/bin/bash
 
# change that number to how ever many minutes you are checking the site (matching your con-job time).
timedelay=1; 

# URL to download from
downloadURL='http://202.54.31.8/section/dwr/img/caz_chn.gif';

# Path to save folder on your computer...
# Do *not* end with a foward / slash
# Example -  saveFolder='/path/to/save/dir';
saveFolder='/path/to/save/dir';




# this will get the current date (year and month) and time (hour and minute)
CurrentTime=$(date +\%Y\%m\%d\%H\%M);

# this will subtract what ever minute you asign to 'timedelay' from the CurrentTime so it can check the last file saved
LastTime=$(($CurrentTime - $timedelay));

# Download your image and save the file yyyymmhhmm.gif
wget --output-document="$saveFolder/$CurrentTime.gif" $downloadURL;

# md5 check sum on the current file you downloaded and save results to 'test1'
test1=`md5sum "$saveFolder/$CurrentTime.gif" | awk '{print $1}'`;

# Check to see if old file exists, if so run check sum
if [ -s "$saveFolder/$LastTime.gif" ]; then
	
	# md5 check sum on the last file you downloaded and save results to 'test2'
	test2=`md5sum "$saveFolder/$LastTime.gif" | awk '{print $1}'`;

	# compair 'test1' to 'test2', if they both have the same check sum, delete the last downloaded image
	if [ "$test1" == "$test2" ]; then
	  rm "$saveFolder/$LastTime.gif";
	fi
fi

exit


```

---

### Post by sundar_ima on 2010-05-11
Ok. The script is running perfectly on my system. Now i need some modification on it. I want to upload the downloaded pictures directly to my email account and delete the uploaded pictures from my system. Search in the google resulted that we can send an email directly from terminal usng mail / mailx utility. I tried that, however it resulted with an error code 1 and also i dont know how to upload a picture from terminal.

---

### Post by sundar_ima on 2010-05-11
**@ iMisspell**

I forgot to mention that your script is popular among my friends here... :)

---

### Post by StuartN on 2010-05-11
> **sundar_ima said:**
> I want to upload the downloaded pictures directly to my email account and delete the uploaded pictures from my system.

There is no command-line email installed and configured by default, and trying to use Thunderbird and other GUI mail from the command-line just does not work.

I use mutt, but you could use exim4 or sendemail (that is not a typo for sendmail). You need to choose and install one of them and use a command like:

```
mutt -s "This is the subject line" -a attachment.gif recipient@some.domain < body.txt
_or_
sendemail -u "This is the subject line" -a attachment.gif -t recipient@some.domain -m body.txt
```

As you can see, they do the same thing with very similar syntax. There is some configuration to set up, and it can be a little more complex than a GUI mail package, but not much more.

mutt manpage: [http://www.mutt.org/doc/man_page.html](http://www.mutt.org/doc/man_page.html)
sendemail manpage: [http://man.gnusquad.org/sendemail/section-1/en/](http://man.gnusquad.org/sendemail/section-1/en/)

Fully worked examples: [http://ubuntuforums.org/showthread.php?t=1284459](http://ubuntuforums.org/showthread.php?t=1284459) and [http://ubuntuforums.org/showthread.php?t=1293937](http://ubuntuforums.org/showthread.php?t=1293937)

---

