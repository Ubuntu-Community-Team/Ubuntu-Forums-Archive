---
title: "rapidshare, kget, download movies"
date: 2009-10-29
forum: General Help
---

### Post by eneth80 on 2009-10-29
Hi,
Simple question: Could anybody be so kind to explain me how a download manager works? I missed this revolution in peer-to-peer downloading and I cannot find some basic explanations of how it works. 
If I go here: 

to download a movie, I select all download all those links, e.g. 
[HTML]http://rapidshare.com/files/6203441/Seven_Samurai_H.264_AVC_ENG_Sub_-_CD1.part01.rar
http://rapidshare.com/files/6207764/Seven_Samurai_H.264_AVC_ENG_Sub_-_CD1.part02.rar
...[/HTML] 
with FlashGot and it puts them in kget. Then kget asks me for each link if I have to overwrite:
```
Destination file 
file:///home/myname/Seven_Samurai_H.264_AVC_ENG_Sub_-_CD1.part02.rar
already exists.
Do you want to overwrite it?
```
and if I say 'Yes' it overwrites deletes all these small 26.9 KB .rar files (eg. Seven_Samurai_H.264_AVC_ENG_Sub_-_CD1.part01.rar ) except for the last. So what do I have to do? At a certain point I'll have to merge the files together?

I also installed aria2, but Alt+f2 > aria2c does nothing.
Is it conveninent to do this "download manager" job or is it already an obsolete trick? 
Thanks.

---

### Post by Bonster on 2009-10-29
I dont use any of that but for rapidshare ..etc, I use Freerapid to download

---

### Post by nikhilbhardwaj on 2009-10-29
try torrents
rapidshare is good too if you have a premium account

---

### Post by NFblaze on 2009-10-29
Okay, this is a hunch, but basically a download manager works like this, you add files via its links and it will add em to a queue and download however many it can concurrently usually, and with multiple connections.

I dont really use any download manager in Ubuntu besides DownThemAll, but I use IDM (Internet Download Manager, the best manager I've ever seen) and jDownloader in Windows.

jDownloader is written in Java (so its a bit slow/hungry at least in XP) but its available in linux. So you can download that. Jdownloader is made especially for DDL (Direct Download Links)...aka rapidshare,hotfile,uploading,etc...

So, basically what I'm assuming is you are having those small 29KB files because you dont have a premium access account. This means you can only download 1 file per certain of minutes, and only using one connection, and not concurrently. I'm pretty sure those files you are downloading are actually html, files. try and open them up with Mozilla and read them and see what they say.

What you can do is either buy a premium acct, and find if somewhere in the settings you can add you premium acct username and password. That way you will be able to bypass all those limitations listed above.

I know jDownloader has a username and password list holder, so it will automatically use it and bypass, if not jDownloader also has free mode that will download 1 file per the time limit and then automatically connect to download the rest of the files.

Also, the  ThisisaFile.part01.rar, ThisisaFile.part02.rar, ThisisaFile.part03.rar. You dont need to combine them you just need to make sure you have all the parts and unrar from the main rar which is usually part01.rar

Though, if you do downoload a file like ThisisaFile.avi.001, ThisisaFile.avi.002, ThisisaFile.avi.003 those are the ones you need to join together with a program like HJSplit (or Peazip has this built-in)

In short, basically you might just need to get a premium account.

---

### Post by RealG187 on 2009-10-29
> **nikhilbhardwaj said:**
> try torrents
rapidshare is good too if you have a premium accountThat's what I am trying to say [here]("http://ubuntuforums.org/showthread.php?t=1293348"), but all I get are immature people saying why would I use rapidshare, HELLO CUZ I HAVE PREMIUM!

---

### Post by 80aless on 2009-10-31
ok, i ll use the torrents cause i am not going to buy something. a friend of mine uses that method but windows, without having a premium account. i ll ask him .
thanks
ps i m the same user that started the thread.

---

### Post by Primefalcon on 2009-10-31
> **80aless said:**
> ok, i ll use the torrents cause i am not going to buy something. a friend of mine uses that method but windows, without having a premium account. i ll ask him .
thanks
ps i m the same user that started the thread.

```
#!/bin/bash

################################################
#Purpose: Automate the downloading of files from rapidshare using the free account 
#using simple unix tools.
#Date: 14-7-2008
#Authors: Slith, Tune
#Improvements: Please email them to jwhatson@gmail.com
#Post Feedback and comments to http://emkay.unpointless.com/Blog/?p=63
#Notes: To use curl instead of wget use 'curl -s' and 'curl -s -d'
#Version: 1.2 - Rapidshare has added a wait time in between file downloads. On top of your download
#to start. This has been fixed.
#Added a 'kill time' feature. Specify killTime as an hour of the day and if the time is greater than this. 
#the script will end. Useful for using cron to start script at offpeak time and killing it when off speak ends. 
################################################

mirror=dt.rapidshare.com;

## possible mirrors
# cg.rapidshare.com
# l34.rapidshare.com
# tg.rapidshare.com
# gc2.rapidshare.com
# dt.rapidshare.com
# tl2.rapidshare.com
# l32.rapidshare.com
# l3.rapidshare.com
# gc.rapidshare.com
# l33.rapidshare.com
# tl.rapidshare.com
# cg2.rapidshare.com

killTimeEnable=0
killTime=9

function getOutputFromFreeUserSubmit(){
        URL=$(wget -q -O - $line | grep "<form id=\"ff\" action=\"" | grep -o 'http://[^"]*');
        output=$(wget -q -O - --post-data "dl.start=Free" "$URL");
}

while read line
do

	if [[ $killTimeEnable -eq 1 && $(date +%H) -gt $killTime ]]; then exit; fi;

	getOutputFromFreeUserSubmit output; #call getOutputFromFreeUserSubmit, result is stored in $output
	posibleWaitTime=$(echo "$output" | grep "try again in about" | grep -o "[0-9]\{1,3\}");
	
	if [ -z "$posibleWaitTime" ]; then #check for zero lenght string
		echo "No wait time, likely to be the first file you have downloaded in a while";
	else
		echo "Waiting $[ $posibleWaitTime+1] minutes (in between file download wait)";
		sleep $[ $posibleWaitTime+1]m;
		getOutputFromFreeUserSubmit output; #Now we have waited we will try again...
	fi
	
	time=$(echo "$output" | grep "var c=[0-9]*;" | grep -o "[0-9]\{1,3\}");
	ourfile=$(echo "$output" | grep "document.dlf.action=" | grep -o "http://[^\"]*$mirror[^\\]*");
	echo "Waiting $time secs for download of $ourfile";
	sleep $time;


if [ "$2" -ge "1" ]; then #speed limit download
	wget --limit-rate="$2"k $ourfile;
else
	wget $ourfile;
fi


done < input.txt
```

---

### Post by RealG187 on 2009-11-02
> **80aless said:**
> ok, i ll use the torrents cause i am not going to buy something. a friend of mine uses that method but windows, without having a premium account. i ll ask him .
thanks
ps i m the same user that started the thread.I use a program called JDownloader. It's written it java so it's crossplatform. I have tried in in Ubuntu 9.04 and Windows 2000 Server, and Windows Server 2003...

---

### Post by ardit121 on 2009-11-06
This is a great website to  download movies, and the best thing is you can watch them too:


[http://www.freemoviestheatre.com](http://www.freemoviestheatre.com)


Ive been using it for more than a year and I'm very pleased with the service.
The best thing that it's completely virus free (not like the warez downloads) and it has almost everything that your looking for.

Hope this helps. (just give it a try)

---

### Post by GSF on 2009-11-06
i didn't want to open a new topic so i replied here.. ! what i need is to make flashgot in firefox to open many instances of wget for many files. so far if i select 10 files and click flashgot with wget, it will download them one by one... can someone help? thanks

---

### Post by 80aless on 2009-11-07
Primefalcon, how do I use your script? 

NFblaze, IDM is for windows only? 
Thanks everybody, I am trying JDownloader and it seems to work.

I do not like [http://www.freemoviestheatre.com](http://www.freemoviestheatre.com) , it looks like a site full of American trash.

---

### Post by NFblaze on 2009-11-07
> **80aless said:**
> Primefalcon, how do I use your script? 

[B]NFblaze, IDM is for windows only? 
Thanks everybody, I am trying JDownloader and it seems to work.

I do not like [http://www.freemoviestheatre.com](http://www.freemoviestheatre.com) , it looks like a site full of American trash.[/B]

Yes, IDM is Windows only. I wish it had a Linux port, but it doesn't. I dont use Wine so I dont know how well it works under that environment

I dont know what you mean by "American trash", but that's a harsh comment, and nearly makes you sound like an ***. Though, have you tried [http://ninjavideo.net](http://ninjavideo.net)

---

### Post by bln102 on 2010-04-11
I'm using Aria2. I want rename duplicate filename to: **[filename].[1....9999].[ext]**, but Aria2 only support: **[filename].[ext].[1...9999]**

Help me to solve it. Thank you very much.

---

### Post by JUSTINBEAIRD on 2010-04-11
i use tucan download manager for rapidshare and others like it

---

