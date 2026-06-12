---
title: "BASH shell scripting question"
date: 2009-09-17
forum: General Help
---

### Post by Kayone on 2009-09-17
I am trying to create a script that utilizes rsync to update a folder on another computer. 

I am placing the output of rsync's -v option into a log file so I can make another script run against updated files. These computers are separated and one of the computers/networks (used to process data) isn't connected to the internet except when syncing the files.

$sensor.pl is the pearl script that I have that processes data after it is rsync'd over. this script needs to run against "new" files only

So.. here is what I have so far but I am stumped..

dlpath=/location/location/location/location/
procpath=/location/location/location/location/
datadates='grep [0-9][0-9][0-9][0-9]/[0-9][0-9]/[0-9][0-9]\/$ /tmp/$sensor'

for sensor in sensor1 sensor2 sensor3 sensor4 
    do
        echo "Downloading $sensor"
        rsync -rvte "ssh -i location" /$dlpath/$sensor/ /$procpath/$sensor/location/ > /tmp/$sensor
        echo "Processing $sensor"
        $sensor.pl -r /$procpath/$sensor/raw_data/$datadates/
        echo "Done with $sensor"
    done


Here is the issue:

I need to basically take the output of the /tmp/$sensor log file and make it run in a loop (I think).  I need each of the times in the log file to run with the $sensor.pl script. 

The log file has various outputs. 2009/09/09/ (yyyy/mm/dd/) is what I am trying to search for. I want "each" new date in the log file to run though. 

I cant seem to think of a good way to do this. It makes it a little bit more difficult because, in that log file, I see other dates from the rsync output that look like 2009/09/09/120001 and 
2009/09/09/000101_01. (lists the individual directories AND files being updated). 

I was thinking that a global variable would work if I could get grep to work inside of it (backtick) but then I came to the realization that 1.) I don't have my sensor variable defined yet 2.) I can't use the log file until I have downloaded it.

Ehh... any ideas?

I kinda "need" to cerate a second loop because I want to do the downloads first and then process the data later.

btw.. srry for the name... I wasn't thinking when I created it. For those of you that saw the CurrentlyUnqualifiedNavalTrainee video (Halo), you will probably find it amusing. It's the new name for noob :)

Thank you in advance for your help.

---

### Post by sedawk on 2009-09-17
The find command has a few nice features you might not be
aware of, so you do not have to care about rsync's log file:

find /foo/bar/zoo -type f -newer ref.file -print
will show you all files in /foo/bar/zoo that
are newer then reference file ref.file.
You only have to remember to "touch ref.file" after
running the tool(s).

Or simpler without a ref file:

find /foo/bar/zoo -type f -mmin -60 -print 
will show all files in /foo/bar/zoo younger than
60 minutes (+60 will show files older than 60 minutes).
(-mtime will do the same for "days" instead of "minutes").


And some more comments that come to my mind:
* When I do "rsync -av" I do not see timestamps, I only see the
  "new" files that are transfered. Isn't that what you need?
* I'm not sure why you use rsync -e "ssh -i location" and not
  rsync <source_dir> location:<target_dir> or
  rsync location:<target_dir> <source_dir>
  which also use ssh as transfer protocol and are slighty
  more readable (IMHO).

---

### Post by Kayone on 2009-09-17
Delete

---

### Post by Kayone on 2009-09-17
haha... I went retarded. I just nested another for loop and set the variable to the output of grep. Allowed me to input the newly populated directories for the script to run against inside if the variable. I confused myself.

I am rsync'ing remote -> local btw.. I just tried to remove some unneeded text from the script before I posted it. 

I really appreciate all of your help.. 
I ended up doing this:

dlpath=/location/location/location/location/
procpath=/location/location/location/location/

for sensor in sensor1 sensor2 sensor3 

    do
[INDENT]        echo "Downloading $sensor"
[/INDENT] [INDENT]        rsync -rvte "ssh -i key" notroot@servername:/$dlpath/$sensor/ /$procpath/$sensor/raw-data/ > /tmp/$sensor
[/INDENT] [INDENT]         echo "Done downloading $sensor"
[/INDENT]      done

for sensor in sensor1 sensor2 sensor3 

    do
[INDENT]         echo "Processing $sensor"
[/INDENT]         [INDENT][INDENT]         for eachdate in `grep [0-9][0-9][0-9][0-9]/[0-9][0-9]/[0-9][0-9]\/$ /tmp/$sensor`
[/INDENT][/INDENT] [INDENT][INDENT]do
[/INDENT][/INDENT]             [INDENT][INDENT][INDENT]                       $sensor.pl -r /$procpath/$sensor/raw_data/$eachdate/
[/INDENT][/INDENT][/INDENT]             [INDENT][INDENT]done
[/INDENT][/INDENT] [INDENT]          echo "Done processing $sensor"
[/INDENT]          done

---

