---
title: "rtorrent execute script on finish"
date: 2009-12-06
forum: General Help
---

### Post by kempy1000 on 2009-12-06
Hi

I know it is possible to get rtorrent to execute a script when a torrent finishes.

However I need to be able to pass parameters to the script:
I need to execute:

/usr/local/bin/mover -b [the folder the finished download is inside of]

Is this possible? if so how?

Thanks
Chris

---

### Post by iMisspell on 2009-12-06
Some where along the lines i was using...
```
system.method.set_key = event.download.finished,move_complete,"d.set_directory=$d.get_custom2= ;execute=mv,-u,$d.get_base_path=,$d.get_custom2= ;execute=/torrents/scripts/unrar_movies.pl,$d.get_name="
```
Notice the end part **;execute=/torrents/scripts/unrar_movies.pl,$d.get_name=**
**$d.get_name** will be passed to my script.

I ended up writing a perl script to monitor the folder which rTorrent was moving files to and scrapped the above commands, the monitor script works much more consistent.


_

---

### Post by kempy1000 on 2009-12-07
Hi

Thanks for the reply.

I think using perl to monitor the folder might be a better idea!

Can I ask how would I go about doing it?

Thanks
Chris

---

### Post by iMisspell on 2009-12-08
Sure... heres a snippet of the code (i had a env variable in there which i edited out to post here)...
Im sure theres better ways to do this, im new to linux along with perl, so this was just slapped together and is a small part of a collection of scripts im using.

```

#!/usr/bin/perl
use strict; use warnings; use diagnostics;

use Linux::Inotify2;

# /include/watch.pl

my $watch_folder = "/dir/that/rTorrent/moves/stuff/to" ;

my $script_dir = "/path/to/script/which/does/the/work";


my $inotify = new Linux::Inotify2();

=p
IN_ALL_EVENTS
IN_CREATE
IN_MOVE
=cut
$inotify->watch($watch_folder, IN_ALL_EVENTS);

print "\n Watching folder = $watch_folder \n===========================================\n";

while (1) {
	
  # By default this will block until something is read
  my @events = $inotify->read();
  if (scalar(@events)==0) {
    print "read error: $!";
    last;
  }
  
  foreach (@events) {
	  
	  my $w = $_->w;
	  #my $wd = $_->wd;
	  my $name = $_->name || '';
	  my $cookie = $_->cookie;
	  my $mask = $_->mask;
	  
	  # new 1073742080
	  # 1073741952
	  # 1073741888
	  if($name ne '' && $mask eq '1073741952'){
		 print "** $name  **\n" ;
		 system("perl $script_dir/unrar_movies.pl '$name'");

	  }
	    
  }
  
}

```

Here a link with alittle info:
[http://ubuntuforums.org/showthread.php?t=1323937](http://ubuntuforums.org/showthread.php?t=1323937)

Module page for Inotify2
[http://search.cpan.org/dist/Linux-Inotify2/Inotify2.pm](http://search.cpan.org/dist/Linux-Inotify2/Inotify2.pm)
I had to install *Linux::Inotify2*, did so via cpan.

Heres the set up im using...
I have ubuntu 8.04 server installed as a virtual machine.
Running the script above (along with rTorrent) in two separate '_[screens]("http://www.gnu.org/software/screen/")_'.
To run the script above ill open a screen, **screen -R watchmovie**
Load the script, **/path/to/watch.pl**
Close the screen **^a + ^d**
 When i want to kill the "watch.pl" script i'll open the screen again **screen -R watchmovie** and then **^x** (or **^z** i forget) and it will kill the script.

^ is the ctrl key on your keyboard.

Ive read about people doing simulare but they would write something and then stuff it into a cron job.

Hope it helps.
If you have any questions about it, post back and i can try and give you more info.


[edit]
heres what i have in rTorrents config file.

```

schedule = watch_directory_2,10,10,"load_start=/torrents/movies/_torrents/*.torrent,d.set_custom2=/torrents/movies/"

system.method.set_key = event.download.finished,move_complete,"d.set_directory=$d.get_custom2= ;execute=mv,-u,$d.get_base_path=,$d.get_custom2="

```

torrent downloads are saved in rTorrents default dir, once done rTorrent moves them to the **set_custom2**, the 'set_custom2' dir is what the watch.pl script monitors.





_

---

### Post by kempy1000 on 2009-12-08
> **iMisspell said:**
> 
```

#!/usr/bin/perl
use strict; use warnings; use diagnostics;

use Linux::Inotify2;

# /include/watch.pl

my $watch_folder = "/dir/that/rTorrent/moves/stuff/to" ;

my $script_dir = "/path/to/script/which/does/the/work";


my $inotify = new Linux::Inotify2();

=p
IN_ALL_EVENTS
IN_CREATE
IN_MOVE
=cut
$inotify->watch($watch_folder, IN_ALL_EVENTS);

print "\n Watching folder = $watch_folder \n===========================================\n";

while (1) {
	
  # By default this will block until something is read
  my @events = $inotify->read();
  if (scalar(@events)==0) {
    print "read error: $!";
    last;
  }
  
  foreach (@events) {
	  
	  my $w = $_->w;
	  #my $wd = $_->wd;
	  my $name = $_->name || '';
	  my $cookie = $_->cookie;
	  my $mask = $_->mask;
	  
	  # new 1073742080
	  # 1073741952
	  # 1073741888
	  if($name ne '' && $mask eq '1073741952'){
		 print "** $name  **\n" ;
		 system("perl $script_dir/unrar_movies.pl '$name'");

	  }
	    
  }
  
}

```


Hi Thanks
I dint quite get the perl and couldnt get it working!
But thanks to the idea of screen and i bit of looking a made the script bellow that does the job for me when ran in a detached screen:

```

#!/bin/bash

MONITORFOLDER=/mediadrive/torrent/downloaded/dir1
MESSAGE="/home/rtorrent/messageonfinish.txt"
RECIPIENT=USER@EXAMPLE.NET

while [ 1 ]
do

inotifywait --monitor -q --format %f --event move --event create $MONITORFOLDER | while read NAME
do
        cd $MONITORFOLDER
        tvnamer -b "$NAME"
        rm -rf $MONITORFOLDER/"$NAME"
        echo $NAME > $MESSAGE
        echo "Sending Email"
        mail -s "rTorrent Notification" "$RECIPIENT" < $MESSAGE

done

sleep 300

done


```

> **iMisspell said:**
> 
```

schedule = watch_directory_2,10,10,"load_start=/torrents/movies/_torrents/*.torrent,d.set_custom2=/torrents/movies/"

system.method.set_key = event.download.finished,move_complete,"d.set_directory=$d.get_custom2= ;execute=mv,-u,$d.get_base_path=,$d.get_custom2="

```


This was very useful! I couldnt understand the rtorrent documentation for the life of me!

Thanks for the help

Chris

---

### Post by iMisspell on 2009-12-09
Good to hear you have it working to your needs.

> **kempy1000 said:**
> I couldnt understand the rtorrent documentation for the life of me!
:) When i first started to program (windows apps) i would write up "directions/instructions" (or lake of ;) ) simular to whats on the rTorrent wiki. Pretty much jotting down basic ideas and what not. In the beginning i would pass the program off to a friend to help me test and debug, they would always make a comment about the "howto/readme or help file". I think some devs kind of forget that the people using their scripts or programs did not make the script or progarm and take alot of things for grant.

If your just looking for an email to be sent off when the torrent finishes, there is a rTorrent command for that.

```

system.method.set_key = event.download.finished,notify_me,"execute=/torrents/scripts/unrar_movies.pl,$d.get_name="

```

scroll down alittle...
[http://wiki.archlinux.org/index.php/RTorrent#Send_Text_Message_Upon_Torrent_Completion_Using_GMail](http://wiki.archlinux.org/index.php/RTorrent#Send_Text_Message_Upon_Torrent_Completion_Using_GMail)

site is dead as of this post... but info should be found here
[http://libtorrent.rakshasa.no/wiki/RTorrentCommonTasks](http://libtorrent.rakshasa.no/wiki/RTorrentCommonTasks)

Just some extra info if you felt like playing with it.

_

---

