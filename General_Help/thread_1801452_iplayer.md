---
title: "iplayer"
date: 2011-07-10
forum: General Help
---

### Post by mrwolfie on 2011-07-10
hi im not that good with Ubuntu yet i just got. Im trying get iplayer to work iv alread download flashplayer and everything i just get a black screen.  but i can still watch videos on youtube how do i get iplayer working? Thanks every 1:).

---

### Post by flipper T on 2011-07-10
don't bother


get "get_iplayer" from synaptic package manager and download any bbc programme you like.

this operates from the command line but is well documented if you do some basic google searches

---

### Post by flipper T on 2011-07-11
just realized that i answered a question that you did not ask :)

the answer to the question you did ask is to run the flash aid extension from within firefox and that will fix your issue in any browser

ps im assuming that you are UK based, and that is not the issue

---

### Post by mister_p_1998 on 2011-07-11
Might be worth checking you have installed ubuntu-restricted-extras

If you want to use Get_Iplayer, its been nobbled by the BBC so you need to get the modified version here:
[http://freshmeat.net/projects/get_iplayer](http://freshmeat.net/projects/get_iplayer)

---

### Post by flipper T on 2011-07-11
i got get_iplayer from synaptic and it works fine

---

### Post by johnaaronrose on 2011-08-10
I've written a GUI for get_iplayer in Gambas. It allows selection of a program followed by downloading it. It calls get_iplayer with a --raw parameter since it doesn't work without it. Its .deb package (which includes Gambas runtime) is  downloadable from:
[http://dl.dropbox.com/u/3928731/irec...0.39-1_all.deb]("http://dl.dropbox.com/u/3928731/irecorder_0.0.39-1_all.deb")

Selecting Default mode results in a TV programmes being recorded as a .flv  file. Use Mobile Media Converter / HandBrake / VLC / WinFF if you wish  to convert to another format (e.g. to play on the iphone). 

I'd be grateful if people who try iRecorder would let me know their  experiences with it, particularly if they wish to suggest enhancements. 

I'd be happy to write similar functionality incorporated into iRecorder  of the code used in get_iplayer if anyone could document the Perl code  used by iRecorder (i.e usage of the search and get options.  Alternatively, documentation of the requests & responses from the  iPlayer archives. Similarly, for Channel 4 IOD.

---

### Post by flipper T on 2011-08-10
get_iplayer has stopped working

error loop after approx 40mb of download

know a solution ?

---

### Post by johnaaronrose on 2011-08-10
flipper,

Current version of get_iplayer is 2.79. Download it by clicking
[http://dl.dropbox.com/u/3928731/get-iplayer_2.79-1_all.deb](http://dl.dropbox.com/u/3928731/get-iplayer_2.79-1_all.deb)

As you said that you're a Ubuntu newbie, in case you don't know how to install a .deb file: double click the file in the File Browser (aka Nautilus).

I often have problems with get_iplayer and iRecorder. A typical one ran just now shows part of the log for get_iplayer in a terminal:
$ get_iplayer amy --get --raw --output /home/john
...
WARNING: Stream does not start with requested frame, ignoring data... 
60867.019 kB / 312.16 sec (13.7%)
Couldn't resume FLV file, try --skip 1

INFO: Command exit code 1 (raw code = 256)
WARNING: Retry recording for 'Amy Winehouse Tribute - Amy Winehouse Tribute (b0139h7z)'
INFO: File name prefix = Amy_Winehouse_Tribute_-_Amy_Winehouse_Tribute_b0139h7z_default                 
RTMPDump v2.3
(c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL
ERROR: RTMP_HashSWF: couldn't contact swfurl [http://www.bbc.co.uk/emp/10player.swf?revision=18269_21576](http://www.bbc.co.uk/emp/10player.swf?revision=18269_21576) (HTTP error 301)
WARNING: Ignoring SWF size, supply also the hash with --swfhash
Connecting ...
INFO: Connected...
ERROR: HandleCtrl: Ignoring SWFVerification request, use --swfVfy!
Resuming download at: 60867.019 kB / 312.160 sec (13.7%)
^CCaught signal: 2, cleaning up, just a second...
ERROR: RTMP_ReadPacket, failed to read RTMP packet header
60867.019 kB / 312.16 sec (13.7%)
Download may be incomplete (downloaded about 13.70%), try resuming

INFO: Cleaning up (signal = INT), killing PID=6629:...

I wish I knew the cause. It seems to me to be one or more of:
a. my laptop being 4 years old & being minimal spec then
b.  BBC's servers often being busy
c. get_iplayer having errors
Because of the last reason, I would like to rewrite the bits of get_iplayer that I want (i.e. that iRecorder uses) in a language that I understand (not Perl, Ruby or Python). However, I need info on the get_iplayer code and/or the BBC's internet interaction with us.

---

### Post by johnaaronrose on 2011-08-10
flipper,

Apologies, I've mislead you. The .deb file is Canonical's attempt at packaging get)iplayer 2.79 which is actually 2.78! To get get_iplayer 2.79, either run following in terminal:
sudo apt-get install git-core && \
cd ~/ && \
git clone git://git.infradead.org/get_iplayer.git && \

sudo cp ~/get_iplayer/get_iplayer /usr/bin/get_iplayer(which will put the source etc into a new directory called get_iplayer, which you can delete afterwards, as the Perl script is installed into /usr/bin)

or get the Perl script from:
[http://dl.dropbox.com/u/3928731/get_iplayer](http://dl.dropbox.com/u/3928731/get_iplayer)
and install it by:
sudo mv /home/user/Downloads/get_iplayer /usr/bin/
(assuming that user is your login id & that you have configured Firefox to download to Downloads directory, otherwise adjust appropriately) .

---

### Post by doobydave on 2011-08-13
I found I had to install rtmpdump 2.4 in order to get a successful download.

[http://ubuntuforums.org/showthread.php?t=1816737](http://ubuntuforums.org/showthread.php?t=1816737)

YMMV

---

### Post by johnaaronrose on 2012-07-09
Latest version of iRecorder is at:
[http://dl.dropbox.com/u/3928731/irecorder_0.0-1_all.deb](http://dl.dropbox.com/u/3928731/irecorder_0.0-1_all.deb)

You need to use Gambas 3 ppa by kendek, due to Benoit now having a check
that Gambas version dev = (though might be <=) Gambas version run on. It downloads from:
[https://launchpad.net/~nemh/+archive/gambas3](https://launchpad.net/~nemh/+archive/gambas3)

No need to download anything explicitly from the ppa site: after adding  the repository, just do sudo apt-get update & sudo apt-get upgrade.  Running the above .deb should cause gdebi to install the appropriate  Gambas3 modules.

---

