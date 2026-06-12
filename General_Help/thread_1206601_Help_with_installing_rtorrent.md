---
title: "Help with installing rtorrent"
date: 2009-07-07
forum: General Help
---

### Post by delubu on 2009-07-07
hey,
Will anybody please guide me on how to install libtorrent/rtorrent in ubuntu 9.04? 

I googled and forund couple of guides but they were posted in like 2007 or earlier than that. That's why i am asking here for a fresh guide to install newer version. :\

thanks
:guitar:

---

### Post by michy99 on 2009-07-07
Have you seen this guide yet?

```
http://www.crtgen.com/2009/06/29/howto-install-the-latest-version-of-rtorrent-ubuntu/
```

---

### Post by delubu on 2009-07-07
thanks [michy99]("http://ubuntuforums.org/member.php?u=811368").

but I think i am stuck at this point.  (look at the pic please)

[http://i25.tinypic.com/154dceb.png](http://i25.tinypic.com/154dceb.png)


because when i execute this command then nothing opens of anything else happen...

# touch .rtorrent.rc


am i supposed to open/create a file manually to get it done?

:/

---

### Post by rampageoberon on 2009-07-07
Hi there,

```
touch .rtorrent.rc
```

The above code only creates a new file .rtorrent.rc

If you are using ubuntu why not use the version in the repository which you can install using apt

---

### Post by delubu on 2009-07-08
^ will that install and configure the rtorrent? 

i am new to all this and still stuck at that point.
help!

---

### Post by x33a on 2009-07-08
try 
```
sudo aptitude install rtorrent
```

this will install rtorrent and dependencies. afterwards, you can configure the .rtorrent.rc according to your needs.

---

### Post by delubu on 2009-07-08
> **x33a said:**
> try 
```
sudo aptitude install rtorrent
```this will install rtorrent and dependencies. afterwards, you can configure the .rtorrent.rc according to your needs.


will this surly install rtorrent**-0.8.4** ?





[COLOR=Red]EDIT:[/COLOR]


OK so i followed that command and it installed rtorrent. but the same problem still seems to exist.

when i run this command

```
./configure && make && make install
```


then i see this message at the end,

```

checking for C++ compiler default output file name... 
configure: error: C++ compiler cannot create executables
See `config.log' for more details.


```

but still moving on when i run following command nothing seems to happen... :/ will some file open or what?

```
touch .rtorrent.rc
```

---

### Post by x33a on 2009-07-08
the command i posted installs rtorrent 0.8.2. 

any specific reason, why you want 0.8.4?

and, why are you trying to compile it when it is already installed? (through the command i posted).

---

### Post by delubu on 2009-07-08
i was just following the tutorial (link in the second post) and that tut has version 0.8.4... :/

I followed the command in there which installed that version.... and now i followed command posted by you. all i want is rtorrent be installed and running successfully. :/

...and i am still stuck

---

### Post by x33a on 2009-07-08
don't be disheartened. 

open a terminal, post the output of
```
rtorrent
```

by the way, are you new to linux?

any specific reason, why you want rtorrent. if you aren't comfortable with the commandline, then deluge and transmission are excellent torrent clients with a gui.

---

### Post by nothingspecial on 2009-07-08
When you`ve got it up and running have a look at this [[COLOR="Magenta"]excellent beginners tutorial[/COLOR]]("http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/")

---

### Post by oldos2er on 2009-07-08
If you want to compile rtorrent, you'll first need to install build-essential:
```
sudo apt-get update && sudo apt-get install build-essential
```

Then you'll need to install any dependencies rtorrent may need. See [https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

---

### Post by delubu on 2009-07-09
@[x33a]("http://ubuntuforums.org/member.php?u=750258"),
yea dude its my first time ever with linux/ubuntu. I am told that the rtorrent is 'the best' client out there so i just wanna use that. I ran 'rtorrent' command in terminal and it showed rtorrent 0.8.2 on top and couple other lines at the end. i forgot to save the lines. :( 

then i ran the command provided by [oldos2er]("http://ubuntuforums.org/member.php?u=338320") and after that i retried and got same result.

i then retried whole tutorial (link in 2nd post) and reinstalled libtorrent rtorrent and at the compiling stage with following commands i saw different results,

```

Configure, Compile & Install:
 [INDENT]# cd libtorrent-0.12.4
# ./configure && make && make install
# cd ../rtorrent-0.8.4
# ./configure && make && make install
[/INDENT]

```



for libtorrent,

```

make[3]: Leaving directory `/home/win/libtorrent-0.12.4/src'
make[2]: Leaving directory `/home/win/libtorrent-0.12.4/src'
make[2]: Entering directory `/home/win/libtorrent-0.12.4'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/home/win/libtorrent-0.12.4'
make[1]: Leaving directory `/home/win/libtorrent-0.12.4'
Making install in src
make[1]: Entering directory `/home/win/libtorrent-0.12.4/src'
Making install in torrent
make[2]: Entering directory `/home/win/libtorrent-0.12.4/src/torrent'
Making install in data
make[3]: Entering directory `/home/win/libtorrent-0.12.4/src/torrent/data'
make[4]: Entering directory `/home/win/libtorrent-0.12.4/src/torrent/data'
make[4]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/include/torrent/data" || /bin/mkdir -p "/usr/local/include/torrent/data"
/bin/mkdir: cannot create directory `/usr/local/include/torrent': Permission denied
make[4]: *** [install-libtorrentincludeHEADERS] Error 1
make[4]: Leaving directory `/home/win/libtorrent-0.12.4/src/torrent/data'
make[3]: *** [install-am] Error 2
make[3]: Leaving directory `/home/win/libtorrent-0.12.4/src/torrent/data'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/home/win/libtorrent-0.12.4/src/torrent'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/win/libtorrent-0.12.4/src'
make: *** [install-recursive] Error 1
win@win-laptop:~/libtorrent-0.12.4$ 


```



for rtorrent,


```

No package 'libtorrent' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables libtorrent_CFLAGS
and libtorrent_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


```



:(

---

### Post by Chronon on 2009-07-09
You seem to be confusing two different ways of getting rtorrent.

1) Simply install it from the repositories, as mentioned on the first page.
```
sudo aptitude install rtorrent
```
Then you can use it to open a saved .torrent
```
rtorrent saved.torrent
```

You can also just run it with no arguments and then navigate to a saved torrent once the program is running.
```
rtorrent
```

There's no reason to run a configure script or make if you use this approach.

2) Download and compile the source for libtorrent and rtorrent.  This requires running the "configure" script and "make".  It looks like your last attempt failed because it's trying to make some directories and doesn't have permissions.  Even if those are present it probably won't have permission to write to those directories unless you run "make install" as root (use sudo).


----
Personally, unless you have a compelling reason to build the source I would just use option 1.  I did this and was able to immediately boot rtorrent.

---

### Post by delubu on 2009-07-09
ok i will try that way.

isnt rtorrent supposed to look something like this?

[img]http://i31.tinypic.com/hx1y5e.png[/img]

---

### Post by nothingspecial on 2009-07-09
That's a web interface for rtorrent, never tried it. 

rtorrent itself is a command line application.

Did you look at that beginners guide I linked

---

### Post by delubu on 2009-07-09
oh i c. so can i use rtorrent in that kindda interface?

I just looked at the tutorial and thats all command based client. :/  But o well i am still gonna use it.

---

### Post by nothingspecial on 2009-07-09
I presume so. Like I said I`ve never used it.

I use rtorrent on my headless box. Command line apps are really useful for that. But I`d recommend Deluge for use on a pc or laptop.

I`ll have a look at that web interface when I have some time.

---

### Post by oldos2er on 2009-07-09
"No package 'libtorrent' found"

 libtorrent11 is in the universe repository.

---

### Post by ericab on 2009-07-09
you guys;
if you want the latest version of rtorrent (from SVN) compiled and installed (AUTOMATICALLY) all you have to do is this:

[http://ubuntuforums.org/showthread.php?t=1064377&](http://ubuntuforums.org/showthread.php?t=1064377&)

be sure to read the first post COMPLETELY, and don't miss the "Optional step" part.

once the script finishes, you will have an rtorrent that looks like this:

[http://qnas.pl/qpkg/rtorrent++/screens/wtorrent_1.jpg](http://qnas.pl/qpkg/rtorrent++/screens/wtorrent_1.jpg)

---

### Post by delubu on 2009-07-10
> **ericab said:**
> you guys;
if you want the latest version of rtorrent (from SVN) compiled and installed (AUTOMATICALLY) all you have to do is this:

[http://ubuntuforums.org/showthread.php?t=1064377&](http://ubuntuforums.org/showthread.php?t=1064377&)

be sure to read the first post COMPLETELY, and don't miss the "Optional step" part.

once the script finishes, you will have an rtorrent that looks like this:

[http://qnas.pl/qpkg/rtorrent++/screens/wtorrent_1.jpg](http://qnas.pl/qpkg/rtorrent++/screens/wtorrent_1.jpg)



why does it say wTorrent in the pic? is that just a name or something different?

---

### Post by ericab on 2009-07-10
> **delubu said:**
> why does it say wTorrent in the pic? is that just a name or something different?

wTorrent is a graphical front end for rTorrent.
arguably the nicest front end available.

---

### Post by hibliss on 2009-07-10
If you want a client with a GUI, try ktorrent, Deluge, or Transmission.

rtorrent is definitely the best in my opinion, and I do not use any kind of graphical frontend for it.

The nicest thing about rtorrent is that it is not banned on any of the trackers that I use.

Configuring the rtorrent.rc file is important, and setting up a watch directory to auto add torrents is essential.

---

### Post by delubu on 2009-07-16
you are very right hidliss.

i have used rtorent for sometime now and its working nice. i have not yet tried the wtorrent frontend thing yet tho. (i have been very busy with studies as well)


what i am wondering is that why cant i find and edit the rtorrent.rc file yet? I mean i want files to be saved in the folder of my choice rather than home folder.


also weni close rtorrent and then restart it then all (completed) torrents simply just vanish away from it. is there anyway to change that setting? I mean i wanna seed torrents for very long itme.

---

### Post by nothingspecial on 2009-07-16
nano .rtorrent.rc

[[COLOR="Magenta"]This[/COLOR]]("http://wiki.archlinux.org/index.php/RTorrent") page from the arch wiki is a good guide on editing it.

Forget all that pacman stuff about installing it at the beginning.

---

### Post by x33a on 2009-07-16
make sure to save .rtorrent.rc in the home directory.

---

### Post by delubu on 2009-07-18
so when i run this command

nano .rtorrent.rc


i see the .rtorrent.rc file (which i can also see as hidden file in home folder) i have edited the file to save newly added torrents to the torrent folder but still new torrents are downloaded in 'home folder' 

also when i close rtorrent and then reopen it then all finished/unfinished just disappear from rtorrent. :/



when unhide the files in home folder then i can see '**.rtorrent.rc**'  and '**.rtorrent.rc~**'

i am pasting whole .rtorrent.rc content here incase i have done something horibly wrong,


```


# This is an example resource file for rTorrent. Copy to
# ~/.rtorrent.rc and enable/modify the options as needed. Remember to
# uncomment the options you wish to enable.

# Maximum and minimum number of peers to connect to per torrent.
#min_peers = 40
#max_peers = 100

# Same as above but for seeding completed torrents (-1 = same as downloading)
#min_peers_seed = 10
#max_peers_seed = 50

# Maximum number of simultanious uploads per torrent.
#max_uploads = 15

# Global upload and download rate in KiB. "0" for unlimited.
#download_rate = 0
#upload_rate = 0

# Default directory to save the downloaded torrents.
#directory = /home/your-user-name/torrent

# Default session directory. Make sure you don't run multiple instance
# of rtorrent using the same session directory. Perhaps using a
# relative path?
#session = /home/your-user-name/.session

# Watch a directory for new torrents, and stop those that have been
# deleted.
#schedule = watch_directory,5,5,load_start=./watch/*.torrent
#schedule = untied_directory,5,5,stop_untied=

# Close torrents when diskspace is low.
#schedule = low_diskspace,5,60,close_low_diskspace=100M

# Stop torrents when reaching upload ratio in percent,
# when also reaching total upload in bytes, or when
# reaching final upload ratio in percent.
# example: stop at ratio 2.0 with at least 200 MB uploaded, or else ratio 20.0
#schedule = ratio,60,60,"stop_on_ratio=200,200M,2000"

# The ip address reported to the tracker.
#ip = 127.0.0.1
#ip = rakshasa.no

# The ip address the listening socket and outgoing connections is
# bound to.
#bind = 127.0.0.1
#bind = rakshasa.no

# Port range to use for listening.
#port_range = 6890-6999

# Start opening ports at a random position within the port range.
#port_random = no

# Check hash for finished torrents. Might be usefull until the bug is
# fixed that causes lack of diskspace not to be properly reported.
#check_hash = no

# Set whetever the client should try to connect to UDP trackers.
#use_udp_trackers = yes

# Alternative calls to bind and ip that should handle dynamic ip's.
#schedule = ip_tick,0,1800,ip=rakshasa
#schedule = bind_tick,0,1800,bind=rakshasa

# Encryption options, set to none (default) or any combination of the following:
# allow_incoming, try_outgoing, require, require_RC4, enable_retry, prefer_plaintext
#
# The example value allows incoming encrypted connections, starts unencrypted
# outgoing connections but retries with encryption if they fail, preferring
# plaintext to RC4 encryption after the encrypted handshake
#
# encryption = allow_incoming,enable_retry,prefer_plaintext

# Enable DHT support for trackerless torrents or when all trackers are down.
# May be set to "disable" (completely disable DHT), "off" (do not start DHT),
# "auto" (start and stop DHT as needed), or "on" (start DHT immediately).
# The default is "off". For DHT to work, a session directory must be defined.
# 
# dht = auto

# UDP port to use for DHT. 
# 
# dht_port = 6881

# Enable peer exchange (for torrents not marked private)
#
# peer_exchange = yes

#
# Do not modify the following parameters unless you know what you're doing.
#

# Hash read-ahead controls how many MB to request the kernel to read
# ahead. If the value is too low the disk may not be fully utilized,
# while if too high the kernel might not be able to keep the read
# pages in memory thus end up trashing.
#hash_read_ahead = 10

# Interval between attempts to check the hash, in milliseconds.
#hash_interval = 100

# Number of attempts to check the hash while using the mincore status,
# before forcing. Overworked systems might need lower values to get a
# decent hash checking rate.
#hash_max_tries = 10


```

---

### Post by x33a on 2009-07-18
uncomment the directory line, and give full path of the directory you want the downloads to be saved to.```
 # Default directory to save the downloaded torrents.
directory = /home/win/torrent
```uncomment, session directory. This, will let rtorrent remember the state of the torrents you quit in the previous session and no need for hash checks every time you start-up.```
# Default session directory. Make sure you don't run multiple instance
# of rtorrent using the same session directory. Perhaps using a
# relative path?
session = /home/win/.rtorrent
```another thing, you can change the default directory for individual torrents, just select the torrent, press ctrl+o, then type in the new path.

ps: not to discourage you, but if you find all this a bit daunting, please give deluge and/or transmission a try first. then gradually as you get good with config files and commandline, you could switch to rtorrent. i did the same thing :popcorn:

---

### Post by hibliss on 2009-07-18
I have that session line uncommented and rtorrent still checks the hash on all my files each time I start. Can you explain this a bit more?

edit: I figured it out. I had to add a line after the uncommented session directory that says:

```
session_save
```

Thanks for mentioning this, because I am often seeding 30+gigs in torrents and rechecking them can take some time.

---

### Post by delubu on 2009-07-19
wow thanks alot x33a. its now saving to desired location and also reloads torrents when rtorrent is restarted.

/me googles for more rtorrent commands


hey hibliss, when i restarted rtorrent it again checks the hash on torrents. you are right, it will get annoying when there will be bigger torrents. besides i have a 6 years old laptop. ;p

so tell me what exactly did you do you stop the auto hash check?


and does this mean dht is enabled?

# dht = auto


how to disable dht? 

i suppose with the comment # thing its not enabled yet...?

---

### Post by x33a on 2009-07-19
anything with a # means a comment for config files.

as for rtorrent tutorials: take a look here, i learnt everything from the clear documentation on this site and man page of rtorrent.

[http://libtorrent.rakshasa.no/wiki/RTorrentUserGuide](http://libtorrent.rakshasa.no/wiki/RTorrentUserGuide)

[http://libtorrent.rakshasa.no/wiki/RTorrentCommonTasks](http://libtorrent.rakshasa.no/wiki/RTorrentCommonTasks)

[http://libtorrent.rakshasa.no/rtorrent/rtorrent.1.html](http://libtorrent.rakshasa.no/rtorrent/rtorrent.1.html)

---

### Post by hibliss on 2009-07-19
> **delubu said:**
> wow thanks alot x33a. its now saving to desired location and also reloads torrents when rtorrent is restarted.

/me googles for more rtorrent commands


hey hibliss, when i restarted rtorrent it again checks the hash on torrents. you are right, it will get annoying when there will be bigger torrents. besides i have a 6 years old laptop. ;p

so tell me what exactly did you do you stop the auto hash check?


and does this mean dht is enabled?

# dht = auto


how to disable dht? 

i suppose with the comment # thing its not enabled yet...?

I uncommented the following and added one more line under it:

```
# Default session directory. Make sure you don't run multiple instance
# of rtorrent using the same session directory. Perhaps using a
# relative path?
session = /home/chris/.session
session_save = YES

```

Of course the .session directory has to actually exist in your home directory, or wherever you put it for this to work. If it does not exist, create it.

Also if you have not done so already, set up a watch directory, somewhere to save torrents to from your browser so rtorrent sees them and starts downloading them automatically. Here is mine (this needs to be changed in .rtorrent.rc)

```
# Watch a directory for new torrents, and stop those that have been
# deleted.
schedule = watch_directory,5,5,load_start=/home/chris/Desktop/Watch/*.torrent

```

The *.torrent is a wildcard at the end for any torrent file in that folder. This will make your rtorrent experience much easier.

And to answer your DHT question, the default is auto, which means in a public swarm where the private flag is not on the torrent, DHT will be enabled (which is to your benefit), and in a private swarm where the private flag is marked, DHT will be disabled. There is no benefit to disabling DHT.

---

### Post by delubu on 2009-07-20
hibliss,
the save session thing seems to e working well now :D

altho i made these changes


```


# Watch a directory for new torrents, and stop those that have been
# deleted.
schedule = watch_directory,5,5,load_start=/home/win/torrentwatch/*.torrent
schedule = untied_directory,5,5,stop_untied=



```


now when i moved the new .torrent file to that folder it wasnt added in rtorrent automatically... what could be wrong?

---

### Post by hibliss on 2009-07-20
Recomment the untied directory line and see if that does the trick. As long as that directory exists, the watch directory line looks right.

---

### Post by delubu on 2009-07-20
oh yea dude i mistyped the folder name. its working now. as soon as i save the file in watch folder then its automatically started in rtorrent. :D


I didnt have to recomment [FONT=monospace]stop_united line. should i leave it as it is now?


anyhoo, is everything now done? 

[/FONT]

---

### Post by hibliss on 2009-07-20
> **delubu said:**
> 
I didnt have to recomment [FONT=monospace]stop_united line. should i leave it as it is now?


anyhoo, is everything now done? 

[/FONT]

If it is working to your liking, leave it.

Now you just need to learn the commands and you will love this client.

Something that I do is run rtorrent in screen so I never accidentally close it. Screen is another thing to learn, with it's own set of commands, so I would get a grip on rtorrent first before you move in to that. I also run it in screen so I can access it via ssh.

---

### Post by delubu on 2009-07-20
k nice.

I will now read tuts of rtorrent and memorize and practice its commands. ;p

thanks alot for helping me :D


i will however post in this thread as whenever i discover any problem .

---

### Post by hibliss on 2009-07-20
> **delubu said:**
> 
I will now read tuts of rtorrent and memorize and practice its commands. ;p

I have been using it for over a year and still use the command reference sometimes. There are commands  that you will use every day, and others that you will seldom use and forget.

One handy one if you only want one file in a big pack on a torrent is to load it in the client, stop it with ctrl+d, then go to the file list and hit *, that will set all the files not to download, then you can go through hand hit spacebar to select what you do want. I use this a lot.

---

### Post by nothingspecial on 2009-07-20
You also ought to use encryption. From wikipedia

> As of January 2005, BitTorrent traffic made up more than a third of total internet traffic.[2] Some ISPs deal with this traffic by increasing their capacity whilst others use specialised systems to throttle (i.e. slow down) peer-to-peer traffic. Obfuscation and encryption make traffic harder to detect and therefore harder to throttle. These systems are not designed to provide anonymity or confidentiality.

Add this line to your .rtorrent.rc

```
encryption = allow_incoming,try_outgoing,enable_retry
```

---

### Post by delubu on 2009-07-20
hey hibliss,
thaks for the tip. there is one odd thing that i noticed that when i open rtorrent then all those .torrents that were added thru the watch directory automatically start themselves and those added earlier dont start automatically. is it normal? 


now one 'problem' came back. now each torrent performs the hash check before it starts seeding/leeching... :\  



@[nothingspecial]("http://ubuntuforums.org/member.php?u=491516"),
do you want me to add the line there?


```


# Encryption options, set to none (default) or any combination of the following:
# allow_incoming, try_outgoing, require, require_RC4, enable_retry, prefer_plaintext
#
# The example value allows incoming encrypted connections, starts unencrypted
# outgoing connections but retries with encryption if they fail, preferring
# plaintext to RC4 encryption after the encrypted handshake
#
# encryption = allow_incoming,enable_retry,prefer_plaintext
encryption = allow_incoming,try_outgoing,enable_retry


```

---

### Post by hibliss on 2009-07-20
Add all torrents to the watch directory. And that line looks fine for enabling optional encryption.

---

### Post by nothingspecial on 2009-07-20
yep

---

### Post by delubu on 2009-07-20
alright i added the line. :)


hibliss, these are the hash check lines,

```


# Default session directory. Make sure you don't run multiple instance
# of rtorrent using the same session directory. Perhaps using a
# relative path?
session = /home/win/.session
session_save = YES




```



i think it only checks the the hash when i close the rtorrent without stoping the torrents first. so i suppose that is normal...?

---

### Post by hibliss on 2009-07-20
> **delubu said:**
> alright i added the line. :)


hibliss, these are the hash check lines,

```


# Default session directory. Make sure you don't run multiple instance
# of rtorrent using the same session directory. Perhaps using a
# relative path?
session = /home/win/.session
session_save = YES




```



i think it only checks the the hash when i close the rtorrent without stoping the torrents first. so i suppose that is normal...?

If you mean close as in hit ctrl+q, that is a proper shutdown and does stop the torrents. If you mean closing the terminal session without stopping or quitting, than yes, it will recheck after that.

---

### Post by delubu on 2009-07-21
yea it checks only when i close the terminal down while rtorrent is still running.... just wanted to test how it will perform. i wanna test rtorrent from every angle. lol

---

### Post by hibliss on 2009-07-21
> **delubu said:**
> yea it checks only when i close the terminal down while rtorrent is still running.... just wanted to test how it will perform. i wanna test rtorrent from every angle. lol

Yeah, but that is an improper shutdown. It has to check after that. Any time you are going to close that window, hit ctrl+q (unless you decide to start running Screen, then you can detach the session and close it without killing rtorrent).

---

### Post by delubu on 2009-07-21
are you going to tell me about the screen now or should i just play with rtorrent for a while?

my univ semester will start on august 1 and i wont be spending much time learning ubuntu and rtorrent so i am trying to gather as much important as possible. :(

I am trying all these things on a 5 year old laptop. once ubuntu is more friendly with me then i will install it on my new laptop. ;p

---

### Post by hibliss on 2009-07-21
Once you start University, Screen is very good for downloading torrents remotely from home (if the school blocks them, which most do).

You can SSH to the machine in question and administer the torrents remotely, and since you can detach the session, you can logout with Screen/rtorrent still running.

---

### Post by nothingspecial on 2009-07-21
> **delubu said:**
> are you going to tell me about the screen now or should i just play with rtorrent for a while?

my univ semester will start on august 1 and i wont be spending much time learning ubuntu and rtorrent so i am trying to gather as much important as possible. :(

I am trying all these things on a 5 year old laptop. once ubuntu is more friendly with me then i will install it on my new laptop. ;p

```
sudo apt-get install screen
```

```
screen
```

```
rtorrent
```

Get your torrents going then press Ctrl A then Ctrl D

That will leave rtorrent running but detach the session. You can then close the terminal. Do whatever you want then when you are ready type ```
screen -r
```

rtorrent will magically reappear as though you`d never closed the terminal.

This is cool but not much use until you want to ssh into your computer from another one but have a go. Screen does tons of other stuff too, just thought I`d give you a starter.

---

### Post by delubu on 2009-07-21
awesome [nothingspecial]("http://ubuntuforums.org/member.php?u=491516"),
i got it working in first attemp. :D


when the first time i ran screen it asked what kind of environment (w/e) i wanted - plain dark etc -  and i chose 1 for plain mode and i wanna try other modes and cant seem to find that option even in 'screen --help'

:\

---

### Post by hibliss on 2009-07-21
Read the man page for Screen.

---

### Post by delubu on 2009-07-21
how to open man age?

> screen --help 


^ is that man page? i dont seem to find that thing there

---

### Post by hibliss on 2009-07-21
```
man rtorrent
```

Every installed application has a man page (manual), and it is generally worth reading, especially for a command line app. A lot of the information will be redundant to online tutorials and guidance you have read, but it is still worth your time.

---

### Post by delubu on 2009-07-22
oh yea thats really awesome manual.

but i was asking about the screen. screen showed me options when the very first time i ran it.

but i will now read 'man screen'

thanks a lot again hibliss

---

### Post by nothingspecial on 2009-07-22
Type ```
select-screen-profile
```

It should save it then.

---

### Post by nothingspecial on 2009-07-22
Also read [this]("http://news.softpedia.com/news/GNU-Screen-Tutorial-44274.shtml").

It`s a nice simple beginners guide to the basic features of screen.

I find splitting the screen useful and multiple screens (kind of like tabs in firefox).

---

### Post by The-ITu on 2009-07-22
> **delubu said:**
> hey,
Will anybody please guide me on how to install libtorrent/rtorrent in ubuntu 9.04? 

I googled and forund couple of guides but they were posted in like 2007 or earlier than that. That's why i am asking here for a fresh guide to install newer version. :\

thanks
:guitar:
here is a tip:
use [URL="http://deluge-torrent.org"]deluge
[/URL]

---

### Post by nothingspecial on 2009-07-22
> **The-ITu said:**
> here is a tip:
use [URL="http://deluge-torrent.org"]deluge
[/URL]

Read the whole thread.

The OP _wants_ to use rtorrent.

---

