---
title: "HellaNZB killing whole system."
date: 2009-07-12
forum: General Help
---

### Post by Dad1985 on 2009-07-12
I have been a long time user of HellaNZB for Usenet downloads.  My computer is pretty much top of the line and I run Ubuntu 9.04 64bit.  

My problem occurs when I use HellaNZB, it takes over the entire system.  All other running processes on the system come to a standstill and I cannot really do anything else when HellaNZB is working.  It is worse when the application is actually doing the downloading, but it is still bad even when doing par checks and extracting.  

I have tried to screw around with nice priorities and such, but even if I set hellaNZB to the lowest priority it still takes over the entire system.

Any ideas on how to fix this?  Thank you.

---

### Post by Frugoo Scape on 2009-07-12
What do you mean, "it takes over the entire system"?

---

### Post by Dad1985 on 2009-07-12
I mean that I cant do anything else.  As the context switching occurs it seems that I can get little bits of work in, but once hellanzb is switched back in(which is very frequent) my system is brought to a stand still.

I could be listening to a song in Rythmbox and the system could be basically stalled due to hellanzb.  The song will keep playing, but when the song that was already playing is done, the next one will not load until hellanzb is switched out.

Browsing, typing, etc all all impossible.  Those media applications don't seem to be effected to bad, as long as they were started up before hellanzb.

---

### Post by mistakenidentity on 2009-07-12
I use LottaNZB and this program is the best, IMHO. Try it out!

---

### Post by darco on 2009-07-12
> **Dad1985 said:**
> I have been a long time user of HellaNZB for Usenet downloads.  My computer is pretty much top of the line and I run Ubuntu 9.04 64bit.  

My problem occurs when I use HellaNZB, it takes over the entire system.  All other running processes on the system come to a standstill and I cannot really do anything else when HellaNZB is working.  It is worse when the application is actually doing the downloading, but it is still bad even when doing par checks and extracting.  

I have tried to screw around with nice priorities and such, but even if I set hellaNZB to the lowest priority it still takes over the entire system.

Any ideas on how to fix this?  Thank you.

post your hellanzb.conf file...maybe we can spot something....

darco

---

### Post by ericab on 2009-07-12
> **mistakenidentity said:**
> I use LottaNZB and this program is the best, IMHO. Try it out!

SABnzbdplus for life dawg!

---

### Post by Dad1985 on 2009-07-12
> **darco said:**
> post your hellanzb.conf file...maybe we can spot something....

darco

The only changes to it are my added usenet account details.  Its Generic.



As for the other alternatives, I dont like to use a interface, I just like to run the program and it works like hellanzb.

---

### Post by darco on 2009-07-12
> **Dad1985 said:**
> The only changes to it are my added usenet account details.  Its Generic.



As for the other alternatives, I dont like to use a interface, I just like to run the program and it works like hellanzb.

Really thats all you changed? I remember having to specify the download dir, uncomment the rar, par2 and other changes...
oh well..good luck

darco

---

### Post by Dad1985 on 2009-07-12
> **darco said:**
> Really thats all you changed? I remember having to specify the download dir, uncomment the rar, par2 and other changes...
oh well..good luck

darco

Your right, im sorry.  Here is the conf





> 

# 
# hellanzb.conf - sample hellanzb configuration file
#
# To quickly get started, change the default defineServer() call and the
# Hellanzb.PREFIX_DIR directory
#
# This is actually interpreted python code: strings must be surrounded by
# quotes, numbers and the 'None' keyword should not
# 
# $Id: hellanzb.conf.sample 1057 2007-03-27 04:13:53Z pjenvey $

# Log output to this file, set to None (no single quotes) for no logging
Hellanzb.LOG_FILE = '/var/tmp/hellanzb.log'

# Uncomment this line to log DEBUG messages to the specified file
#Hellanzb.DEBUG_MODE = '/var/tmp/hellanzb-debug.log'

# Automatically roll over both log files when they reach LOG_FILE_MAX_BYTES
# size
Hellanzb.LOG_FILE_MAX_BYTES = 0

# Save LOG_FILE_BACKUP_COUNT of those rolled over log files
Hellanzb.LOG_FILE_BACKUP_COUNT = 0


# Define server connections. Servers can have multiple hosts, hellanzb will
# persist the number of connections to each specified server. There may be
# multiple defineServer lines.

# Set both the username and password to 'None' (without the quotes) if your
# usenet server does not require authorization
defineServer(id = 'changeme',
             hosts = [ 'news.usenetserver.com:119' ],
             #hosts = [ 'news.changeme.com', 'morenews.changeme.com:8000' ],


             username = 'name',
             password = 'pass',
             #username = None,           # no auth
             #password = None,

             connections = 10,
             antiIdle = 4.5 * 60,        # 4 minutes, 30 seconds, 0 to disable
             #bindTo = '204.31.33.7',    # connect FROM this ip address
             #enabled = False,           # disable this server
             #skipGroupCmd = False,      # skip sending nntp GROUP commands
             #fillserver = 0,            # defaults to 0 (a main server).
                                         # fillservers must have values > 0
                                         # (priority)
             ssl = False
             )

# Uncomment this line to limit all server connections to the specified KB/s
# bandwidth
#Hellanzb.MAX_RATE = 150 # limit to 150kB/s


# Important locations
Hellanzb.PREFIX_DIR = '/home/name/'

# Where to put queued .nzb files
Hellanzb.QUEUE_DIR = Hellanzb.PREFIX_DIR + 'nzb/Queue/'

# Where the fully processed archives go
Hellanzb.DEST_DIR = Hellanzb.PREFIX_DIR + 'nzb/Complete/'

# The .nzb currently being downloaded is stored here
Hellanzb.CURRENT_DIR = Hellanzb.PREFIX_DIR + 'nzb/daemon.current/'

# The archive currently being downloaded is stored here
Hellanzb.WORKING_DIR = Hellanzb.PREFIX_DIR + 'nzb/daemon.working/'

# Archives interrupted in the middle of downloading are stored here temporarily
Hellanzb.POSTPONED_DIR = Hellanzb.PREFIX_DIR + 'nzb/daemon.postponed/'

# Archives currently being processed. May contains archive directories, or
# symbolic links to archive directories
Hellanzb.PROCESSING_DIR = Hellanzb.PREFIX_DIR + 'nzb/daemon.processing/'

# Temp storage
Hellanzb.TEMP_DIR = Hellanzb.PREFIX_DIR + 'nzb/daemon.temp/'

# Filename to store hellanzb state in between CTRL-Cs. The state (includes the
# order of the queue, and smart par recovery information) is intermittently
# written out as XML to this file
Hellanzb.STATE_XML_FILE = Hellanzb.PREFIX_DIR + 'nzb/hellanzbState.xml'


# _Sub directory within the nzb archive dir_ to move processed files to
Hellanzb.PROCESSED_SUBDIR = 'processed'

# Remove the PROCESSED_SUBDIR if the archive was successfully post processed. 
# Warning: The normal Hellanzb.LOG_FILE should be enabled with this option --
# for a record of what hellanzb deletes
Hellanzb.DELETE_PROCESSED = True


# Maximum amount of memory used to cache encoded Article data segments.
# hellanzb will write article data to disk when this cache is exceeded
# Available settings:
# -1: Unlimited size
#  0: Disable cache (only cache to disk)
# >0: Limit cache to this size, in bytes, KB, MB, e.g.:
#     1024 '1024KB' '100MB' '1GB'
#Hellanzb.CACHE_LIMIT = 0


# Save archives into a sub directory of DEST_DIR named after their newzbin.com
# category (when queued using the enqueuenewzbin XMLRPC call); e.g. Apps,
# Movies, Music
Hellanzb.CATEGORIZE_DEST = True

# Disable SMART_PAR (download all PAR files)
#Hellanzb.SMART_PAR = False

# Supply a path to the (un)rar command
#Hellanzb.UNRAR_CMD = None

# Supply a path to the par2 command
#Hellanzb.PAR2_CMD = None

# Skip unraring during post processing
#Hellanzb.SKIP_UNRAR = False

# Supply a path to the optional macbinconv command (for converting MacBinary
# files)
#Hellanzb.MACBINCONV_CMD = None

# hellanzb inherits the umask from the current user's environment (unless it's
# running in daemon mode). The umask can be forced with this option
#Hellanzb.UMASK = 0022


# Supported music types (case insensitive) and optionally their decompression
# executables
# and the file type that executable will decompress to (case insensitive). The
# exes must be in the PATH.
#
# <FILE> will be replaced with the name of music file
# optional <DESTFILE> is <FILE> with the specified extension
#
# None means these files don't need to be decompressed
defineMusicType('wav', None, None)
defineMusicType('mp3', None, None)
#defineMusicType('ape', 'mac <FILE> <DESTFILE> -d', 'wav')
#defineMusicType('flac', 'flac -d -- <FILE>', 'wav')
#defineMusicType('shn', 'shorten -x < <FILE> > <DESTFILE>', 'wav')

# Max files we should decompress at the same time
Hellanzb.MAX_DECOMPRESSION_THREADS = 2


# Enable Mac OS X Growl notifications
Hellanzb.GROWL_NOTIFY = False

# The growl notification server, in the format 'hostname'
Hellanzb.GROWL_SERVER = 'IP'

# The growl password
Hellanzb.GROWL_PASSWORD = 'password'


# Enable libNotify Daemon notifications
Hellanzb.LIBNOTIFY_NOTIFY = False


# Disable ANSI color codes in the main screen (preserves the in place scroller)
#Hellanzb.DISABLE_COLORS = False

# Disable ALL ANSI color codes in the main screen (for terminals that don't
# support ANY ANSI codes
#Hellanzb.DISABLE_ANSI = False


# Hostname for the XMLRPC client to connect to. By default, localhost
Hellanzb.XMLRPC_SERVER = 'localhost'

# Port number the XML RPC server will listen on, and the client will connect to.
# Set to 'None' (without the quotes!) for no XML RPC server
Hellanzb.XMLRPC_PORT = 8760

# Password for the XML RPC server. You might probably never use this, but the
# command line XML RPC calls do -- it should definitely be changed from its
# default value. The XML RPC username is hardcoded as 'hellanzb' -- E.g. URL:
# [http://hellanzb:changeme@localhost:8760](http://hellanzb:changeme@localhost:8760)
Hellanzb.XMLRPC_PASSWORD = 'changeme'


# Username/Password to [http://www.newzbin.com](http://www.newzbin.com) for automatic NZB downloading
Hellanzb.NEWZBIN_USERNAME = None
Hellanzb.NEWZBIN_PASSWORD = None


# If any of the following file types are missing from the archive and cannot be
# repaired, continue processing because they're unimportant (case insensitive)
Hellanzb.NOT_REQUIRED_FILE_TYPES = [ 'log', 'm3u', 'nfo', 'nzb', 'sfv', 'txt' ]

# Don't get rid of (move into the PROCESSED dir) the following file types when
# finished post processing (case insensitive)
#Hellanzb.KEEP_FILE_TYPES = [ 'log', 'm3u', 'nfo', 'nzb', 'sfv', 'txt' ]
Hellanzb.KEEP_FILE_TYPES = [ 'nfo', 'txt' ]


# List of alternative file extensions matched as NZB files in the QUEUE_DIR.
# The 'nzb' file extension is always matched
#Hellanzb.OTHER_NZB_FILE_TYPES = [ 'xml' ]

# Support extracting NZBs from ZIP files with this suffix (case insensitive) in
# QUEUE_DIR. Defaults to '.nzb.zip'. Set to False to disable.
#Hellanzb.NZB_ZIPS = '.nzb.zip'

# Support extracting NZBs from GZIP files with this suffix (case insensitive)
# in QUEUE_DIR. Defaults to '.nzb.gz'. Set to False to disable.
#Hellanzb.NZB_GZIPS = '.nzb.gz'

# Delay enqueueing new, recently modified NZB files added to the QUEUE_DIR until
# this many seconds have passed since the NZB's last modification time (defaults
# to 10 seconds)
#Hellanzb.NZBQUEUE_MDELAY = 10

# Optional external handler script. hellanzb will run this script after post
# processing an archive, with the following arguments:
#
# handler_script type archiveName destDir elapsedTime parMessage
#
# type: post processing result, either 'SUCCESS' or 'ERROR'
# archiveName: name of the archive, e.g. 'Usenet_Post5'
# destDir: where the archive ended up, e.g. '/ext2/usenet/Usenet_Post5'
# elapsedTime: a pretty string showing how long post processing took, e.g.
#              '10m 37s'
# parMessage: optional post processing message. e.g. '(No Pars)'
#Hellanzb.EXTERNAL_HANDLER_SCRIPT = '~/bin/post_hellanzb.sh'






---

### Post by darco on 2009-07-12
I didnt see a whole lot of difference except for what I have posted...also try either reinstalling a fresh hellanzb.conf as it worked for me or like the other poster mentioned, lottanzb is great...when you download a .nzb it automatically opens and processes the file whereas w/hella you have to d/l it to your queue folder...

```
# Supply a path to the (un)rar command
Hellanzb.UNRAR_CMD = '/usr/bin/unrar'

# Supply a path to the par2 command
Hellanzb.PAR2_CMD = '/usr/bin/par2'

# Skip unraring during post processing
Hellanzb.SKIP_UNRAR = True 
# IP address on which the XMLRPC Server will be binded to.
# Type '0.0.0.0' for any interfaces, '127.0.0.1' will disable remote access
Hellanzb.XMLRPC_SERVER_BIND = '127.0.0.1'

```

good luck

darco

---

### Post by Dad1985 on 2009-07-12
I tried the sabnzbd and while it is not as bad as the hellanzb, while processing nsb files I get much of the same.  The system seems to freeze when its doing a clot of work on these files.  

Ive reinstalled the os a few times and tried different ways of installing hella and using it, all the same result.  Maybe its because my download is very fast at around 10-11MB/s.  But that's not even that fast.

---

### Post by darco on 2009-07-12
This worked for me

[http://ubuntuforums.org/showpost.php?p=2510539&postcount=152](http://ubuntuforums.org/showpost.php?p=2510539&postcount=152)

darco

p.s.  i have a 16mb dl so its not that

---

### Post by ericab on 2009-07-12
> **darco said:**
> This worked for me

[http://ubuntuforums.org/showpost.php?p=2510539&postcount=152](http://ubuntuforums.org/showpost.php?p=2510539&postcount=152)

darco

p.s.  i have a 16mb dl so its not that

1 believe he means a 100mbit inet connection hence 10-11MB/s

chance are good your cpu cant handle it.

are you using SSL ?
if so, *try* it without SSL ie port 119.

---

### Post by Dad1985 on 2009-07-15
> **ericab said:**
> 1 believe he means a 100mbit inet connection hence 10-11MB/s

chance are good your cpu cant handle it.

are you using SSL ?
if so, *try* it without SSL ie port 119.

No I am not using ssl, but do have ssl with my news and maybe I should try it to slow down the connection.  You are right that I do have a 100bit university connection and do download ~10MB/s.  Ive tried hellanzb as well as sabnzbd and have pretty similar results with it literally. incapacitating my desktop.  

My cpu is a Intel Q6600 with 4GB of Memory.  So while its not top of the line, its close.  

In windows xp when using a program like newsleecher, I really dont see these problems as I do in Ubuntu.  Though windows does not download as fast, possibly due to the lack of twisted.


So far I do like the Sabnzbd interface, but find it to fail many extractions where hellanzb doesn't.  So far I am liking HellaNZB a bit better.  

I will try LottaNZB next, though any other suggestions are welcome.  I personally think its a priority problem in the OS rather than a hardware limitation.  Network interfaces as well as servers around the net are a lot less powerful than my desktop and process a lot more than 100mbit connections.

---

### Post by Dad1985 on 2009-07-15
I guess I didnt realize Lottanzb was just a frontend of hellanzb.

---

### Post by madman100 on 2009-08-05
Hi m8 try using SABnzbd just download and extract the cd in to the folder the type ./SABnzbd.py 

that will open a web interface [http://localhost:8080/sabnzbd/](http://localhost:8080/sabnzbd/) 
i find it a lot better that hellanzb and with no problems with it 
but you will have to install python-cheetah most of these should have been installed when you installed hellanzb

[http://www.sabnzbd.org/download/](http://www.sabnzbd.org/download/)

---

