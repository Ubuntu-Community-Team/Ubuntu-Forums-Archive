---
title: "mocp (music on console player) init.d script doesn't work unless i cd to /etc/init.d"
date: 2012-06-01
forum: General Help
---

### Post by thebestofall007 on 2012-06-01
hello. i was wondering what would cause an init.d script to not load unless the user cd'd to the /etc/init.d directory it was located manually? i am using mocp under an ubuntu 12.04 minimal console (no x, no de, or wm) and am trying to make a music jukebox (i have already tried xbmc and geexbox but i want a dedicated mp3 playback setup with basic ff/rw, skip, stop, pause, etc - nothing else). i would like mocp to start at boot from a console and i don't have x installed (don't need it). mocp itself runs superb even after resuming from suspend, but when i type:

```
sudo /etc/init.d/mocp start
```

and enter my password i get:

```
/etc/init.d/mocp: 64: /etc/init.d/mocp: Syntax error: unexpected end of file (expecting ";;")
```

but when i manually cd to the directory typing:

```
cd /etc/init.d
```
 
to go to the directory the mocp init script is in and then type:

```
sudo mocp start 
```

to run it, it starts.

what is going on here? i wonder what part of the script is having the snafoo (if there really is a syntax error, where does the ";;" bash was expecting go?)?

here is the script if anyone wants to have a look: [http://pastebin.com/gPXfRq56]("http://pastebin.com/gPXfRq56")

thanks a bunch!

---

### Post by matt_symes on 2012-06-02
Hi

First things first. There is a problem with the script. Add the three lines highlighted in bold to the bottom of it. I've left three of the original lines for reference as well

```
*)
        echo "Usage: $0 {start|stop|restart|status}"
        exit 1
[B];;

esac

exit 0;[/B]
```

EDIT: In the case of this script, i'm not sure the last exit 0; need to be there but.. meh.

Kind regards

---

### Post by matt_symes on 2012-06-02
Hi

Sorry for the delay. I had to pop out to the supermarket.

> to go to the directory the mocp init script is in and then type:

```
sudo mocp start
```

to run it, it starts.

Before making the changes in my last post, what happens when you navigate to the /etc/init.d directory and type

```
sudo ./mocp start
```

;)

EDIT: Hint. Bear in mind that mocp is mostly likely going to be in your list of paths.

Kind regards

---

### Post by thebestofall007 on 2012-06-02
> **matt_symes said:**
> Hi

First things first. There is a problem with the script. Add the three lines highlighted in bold to the bottom of it. I've left three of the original lines for reference as well

```
*)
        echo "Usage: $0 {start|stop|restart|status}"
        exit 1
[B];;

esac

exit 0;[/B]
```

EDIT: In the case of this script, i'm not sure the last exit 0; need to be there but.. meh.

Kind regards

made the changes you noted plus changed "USER" references to my account name (like in "export HOME=/home/USER") , but now i am getting a ```
start-stop-daemon: need at least one of --exec, --pidfile, --user, or --name try 'start-stop-daemon --help' for more  information
```

---

### Post by thebestofall007 on 2012-06-02
> **matt_symes said:**
> Hi

Sorry for the delay. I had to pop out to the supermarket.



Before making the changes in my last post, what happens when you navigate to the /etc/init.d directory and type: 
```
sudo ./mocp start
```

;)

EDIT: Hint. Bear in mind that mocp is mostly likely going to be in your list of paths.

Kind regards
it outputs a command not found if done from the default home directory. but cd'ing to the /etc/init.d directory and typing sudo mocp start starts it. but typing sudo ./mocp start after cd'ing outputs:```
start-stop-daemon: need at least one of --exec, --pidfile, --user, or --name try 'start-stop-daemon --help' for more  information
```

---

### Post by matt_symes on 2012-06-02
Hi

> **thebestofall007 said:**
> made the changes you noted plus changed "USER" references to my account name (like in "export HOME=/home/USER") , but now i am getting a ```
start-stop-daemon: need at least one of --exec, --pidfile, --user, or --name try 'start-stop-daemon --help' for more  information
```

That is a different error so that means the script is running now even if it is not working correctly.

A couple of questions as i do not have mocp installed in my system.

1. What version and what release of *buntu are you using ?

2. How did you install mocp ? From a ppa, sofware center, compiled from source etc.... Please post the exact commands you used.

3. Did you have any errors when you installed the script ?

I am really surprised there were errors in the init script in the first place and i would like to see where you got it from.

I may also then set up a VM and install your setup and the install mocp the way you did and see what happens.

Kind regards

---

### Post by thebestofall007 on 2012-06-02
1. i'm running ubuntu 12.04 minimal from an iso i downloaded from  [http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/mini.iso]("http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/mini.iso") and didn't install ANY packages in the install.

2. i installed mocp using ```
sudo apt-get install moc
``` It is in the repo's. the program is called moc, and it is started by typing "mocp".

3. nope. i didn't have any errors when i installed it. i renamed the script to mocp and moved it into the /etc/init.d directory, cd'd to the directory, typed:```
sudo update-rc.d mocp defaults
```. 

to update the startup. before i did this, i had to install dos2unix by typing ```
sudo apt-get install dos2unix
``` and run it on the mocp script to make it unix compatible as it will be dos encoded, then typed ```
chmod a+x mocp
``` to make it executable, then ran it manually by typing: ```
sudo mocp start
``` it ran as explained earlier.

the site i got the script is here:[http://moc.daper.net/node/744]("http://moc.daper.net/node/744")

please let me know what comes up. thanks.

---

### Post by matt_symes on 2012-06-02
Hi

Another fan of minimal installs. Nice :)

I will install it on Quantal and see what it does.

Not to disparage the writer of that script, however it does not seem to work.

Give me an hour or two to eat first though.

Kind regards

---

### Post by matt_symes on 2012-06-02
Hi

I've had a look at the script and only really found a few issues. This is the ammended script.

I cannot test this until tomorrow so i am posting this at risk but if there are any problems then we can look at them tomorrow.

I think i have fixed the issues (but like i said i cant test this tonight) and i modified the code slightly.

Change USER=matthew to your user name.

Uncomment out any of the lines below where i have said uncomment below, for that functionality...

```
#!/bin/sh
### BEGIN INIT INFO
# Provides:             MOCP Application Instance
# Required-Start:       $all
# Required-Stop:
# Default-Start:        2 3 4 5
# Default-Stop:         0 1 6
# Short-Description:    starts instance of mocp
# Description:          starts instance of mocp using start-stop-daemon
### END INIT INFO

# Change the user here as required
[COLOR="Red"]USER=matthew[/COLOR]

is_running()
{
	# Start the daemon
        if ! pidof -o  %PPID mocp > /dev/null; then
        	return 1;
	else
		return 0;
        fi
}

start_mocd()
{
	if ! is_running; then

		echo "Starting MOCP...";

                # Start the daemon
                start-stop-daemon --start --chuid "$USER" --exec /usr/bin/mocp -- -S;

		# Give time for the daemon to start
		sleep 2;

		[COLOR="red"]# Uncomment below for full volume
                #/usr/bin/mocp --volume 100 --play;

		# Uncomment below for shuffle
                #/usr/bin/mocp --on shuffle;

		# Uncomment below for auto next
                #/usr/bin/mocp --on autonext;

		# Uncomment below for auto repeat
		#/usr/bin/mocp --on repeat;[/COLOR]

		echo "Starting MOCP...";
	else
                echo "MOCP Already Running...";
        fi
}

stop_mocd()
{
	if is_running; then
		# Stop the daemon
		start-stop-daemon --stop --exec /usr/bin/mocp -- -x;
	else
		echo "MOCP is not running";
	fi
}

case "$1" in
	start)
		# Start moc as a daemon.
		start_mocd;
	;;

	stop)
        	stop_mocd;
	;;

	restart)
		# Stop mocd
		stop_mocd;

		# Give time for the daemon to stop.
		sleep 1;

		# Restart the daemon
		start_mocd;
	;;

	status)

		if is_running; then
			echo "Running";
			exit 0;
		else
			echo "Not running";
			exit 1;
		fi
	;;

	*)
        	echo "Usage: $0 {start|stop|restart|status}"
        	exit 0;
	;;
esac
```

---

### Post by thebestofall007 on 2012-06-02
> **matt_symes said:**
> Hi

I've had a look at the script and only really found a few issues. This is the ammended script.

I cannot test this until tomorrow so i am posting this at risk but if there are any problems then we can look at them tomorrow.

I think i have fixed the issues (but like i said i cant test this tonight) and i modified the code slightly.

Change USER=matthew to your user name.

Uncomment out any of the lines below where i have said uncomment below, for that functionality...

```
#!/bin/sh
### BEGIN INIT INFO
# Provides:             MOCP Application Instance
# Required-Start:       $all
# Required-Stop:
# Default-Start:        2 3 4 5
# Default-Stop:         0 1 6
# Short-Description:    starts instance of mocp
# Description:          starts instance of mocp using start-stop-daemon
### END INIT INFO

# Change the user here as required
[COLOR="Red"]USER=matthew[/COLOR]

is_running()
{
	# Start the daemon
        if ! pidof -o  %PPID mocp > /dev/null; then
        	return 1;
	else
		return 0;
        fi
}

start_mocd()
{
	if ! is_running; then

		echo "Starting MOCP...";

                # Start the daemon
                start-stop-daemon --start --chuid "$USER" --exec /usr/bin/mocp -- -S;

		# Give time for the daemon to start
		sleep 2;

		[COLOR="red"]# Uncomment below for full volume
                #/usr/bin/mocp --volume 100 --play;

		# Uncomment below for shuffle
                #/usr/bin/mocp --on shuffle;

		# Uncomment below for auto next
                #/usr/bin/mocp --on autonext;

		# Uncomment below for auto repeat
		#/usr/bin/mocp --on repeat;[/COLOR]

		echo "Starting MOCP...";
	else
                echo "MOCP Already Running...";
        fi
}

stop_mocd()
{
	if is_running; then
		# Stop the daemon
		start-stop-daemon --stop --exec /usr/bin/mocp -- -x;
	else
		echo "MOCP is not running";
	fi
}

case "$1" in
	start)
		# Start moc as a daemon.
		start_mocd;
	;;

	stop)
        	stop_mocd;
	;;

	restart)
		# Stop mocd
		stop_mocd;

		# Give time for the daemon to stop.
		sleep 1;

		# Restart the daemon
		start_mocd;
	;;

	status)

		if is_running; then
			echo "Running";
			exit 0;
		else
			echo "Not running";
			exit 1;
		fi
	;;

	*)
        	echo "Usage: $0 {start|stop|restart|status}"
        	exit 0;
	;;
esac
```

this split the log wide open, but i have one question: how do you i get the player to start up @ boot with the default blue ncurses interface that is invoked when a user types "mocp" in the terminal/console when running the binary? the script loads mocp as a daemon, but i get no player/interface.

again, THANKS A BUNCH!!

---

### Post by matt_symes on 2012-06-02
Hi

> **thebestofall007 said:**
> this split the log wide open,

Eh ? I have no idea what you mean. Did the script work for you or not ? Please explain... :P

**EDIT:**

> again, THANKS A BUNCH!!

Maybe it did. I'm on my fourth glass of wine so...

> but i have one question: how do you i get the player to start up @ boot with the default blue ncurses interface that is invoked when a user types "mocp" in the terminal/console when running the binary? the script loads mocp as a daemon, but i get no player/interface.

How is your system set up ? Are you booting into a frame buffer ? Do you want this to start up when you boot into a console; a terminal ?

Can you explain a bit more please. Explain your current set up.

Kind regards

---

### Post by thebestofall007 on 2012-06-02
the script starts with no errors and outputs:

```
starting MOCP
running the server
trying JACK
trying ALSA
starting MOCP
```

to verify it is working (which is a great sign ;)), but the ncurses interface that appears after someone manually starts mocp in a terminal or the console doesn't appear at boot and mocp runs in the background. i wonder if it is possible to have the interface appear at boot so navigation to the music folders can be possible? i'm running mocp in the basic console that first appears at boot up (i have no desktop environment, no x server, no window manager, etc installed) and would like the mocp interface to start up when the system boots in that console.

very sorry about the misunderstanding.

---

### Post by matt_symes on 2012-06-02
Hi

No problem. I will have to look into this tomorrow, though, for you.

*Bump* this thread please, so i will not have to search for it.

Kind regards

---

### Post by thebestofall007 on 2012-06-02
> **matt_symes said:**
> Hi

No problem. I will have to look into this tomorrow, though, for you.

*Bump* this thread please, so i will not have to search for it.

Kind regards

i also didn't realize it was later where you live (based on your location below your avatar). i live in the U.S. (central time).

---

### Post by thebestofall007 on 2012-06-02
bump.

---

### Post by thebestofall007 on 2012-06-02
*Bump*

---

### Post by thebestofall007 on 2012-06-03
bump.

---

### Post by matt_symes on 2012-06-03
Hi

@thebestofall007.

No worries. I have seen your bumps :) Thanks for doing that. 

It keeps this thread in my susbscribed threads folder, but you only need to do it once every 2 days to keep it there :P.

I am off out for dinner with friends in a moment and i expect to be back in 4 to 5 hours time. (If i'm a bit late then i apologise but i will respond).

We can continue this thread then if you fancy.

Kind regards

---

### Post by thebestofall007 on 2012-06-03
> **matt_symes said:**
> Hi

@thebestofall007.

No worries. I have seen your bumps :) Thanks for doing that. 

It keeps this thread in my susbscribed threads folder, but you only need to do it once every 2 days to keep it there :P.

I am off out for dinner with friends in a moment and i expect to be back in 4 to 5 hours time. (If i'm a bit late then i apologise but i will respond).

We can continue this thread then if you fancy.

Kind regards

no problem. we all have our schedules and i'll respect yours. you sound like you know your stuff on scripting, WAY better than me (i hope someday to write my own though).

---

### Post by matt_symes on 2012-06-03
Hi

> but the ncurses interface that appears after someone manually starts mocp in a terminal or the console doesn't appear at boot and mocp runs in the background. i wonder if it is possible to have the interface appear at boot so navigation to the music folders can be possible? i'm running mocp in the basic console that first appears at boot up (i have no desktop environment, no x server, no window manager, etc installed) and would like the mocp interface to start up when the system boots in that console.

I have been looking at MOC for the last 10 minutes or so. 

It looks like quite a nifty little program. I may start using it myself.

The script just starts the MOC server as it uses the -S switch.

```
start-stop-daemon --start --chuid "$USER" --exec /usr/bin/mocp -- **-S**;
```

From ```
man moc
```

> -S, --server
              Run only the server and exit.

As it's just starts the server it will have no user interface.

There are a number of ways to control it.

From the terminal you can type

```
mocp
```

This will start the client, and as the server is already running, just connect to it and not restart it. You can the hit small q to quit the client and leave the server playing music.

Another method to control the sever is to send commands from the command line.

These are the commands line moc options.

From ```
man moc
```

> -m, --music-dir
              Start in MusicDir (set in the configuration file).  This can be also set in the configuration file as StartInMusicDir.

       -a, --append
              Append files, directories (recursively) and playlists given after command line options to the playlist.  Don't start the interface.

       -c, --clear
              Clear the playlist.

       -p, --play
              Start playing from the first item on the playlist.

       -f, --next
              Request playing the next song from the server's playlist.

       -r, --previous
              Request playing the previous song from the server's playlist.

       -s, --stop
              Request the server to stop playing.

       -x, --exit
              Bring down the server.

       -P, --pause
              Request the server to pause playing.

       -U, --unpause
              Request the server to resume playing when paused.

       -G, --toggle-pause
              Toggle between play and pause.

These translate into these commands that you can type at the command line (and a couple of others)

```
/usr/bin/mocp --play
/usr/bin/mocp --toggle-pause 
/usr/bin/mocp --next
/usr/bin/mocp --previous
/usr/bin/mocp --start
/usr/bin/mocp --stop
/usr/bin/mocp --exit
/usr/bin/mocp --append
```

There is also ```
/usr/bin/mocp --playit <filename>
```  to play a list of files that are not on the current play list. You can use it as such

```
/usr/bin/mocp --playit ~/my_storage/my_music/0*.mp3
```

The thing a like about this is you can use globbing and wildcards on the filenames as i have above.

Typing these is a bit unwieldly each time you want to do something with MOC, s i would suggest creating a number of aliases.

```
alias moctp='/usr/bin/mocp --toggle-pause'
alias mocne='/usr/bin/mocp --next'
alias mocpr='/usr/bin/mocp --previous'
alias mocst='/usr/bin/mocp --start'
alias mocsp='/usr/bin/mocp --stop'
alias mocex='/usr/bin/mocp --exit'
alias mocap='/usr/bin/mocp --append'
alias mocpi='/usr/bin/mocp --playit'
```

You would then only have to type in the alias to perform the intended operation. You can, of course, call the aliases whatever you want.

You can add the aliases to the file ```
~/.bashrc
``` but i prefer to create the file ```
~/.bash_aliases
``` and keep all my aliases in there. It gets sourced by the file *~/.bashrc* anyway if it exists.

Hopefully one of the two methods for controlling the MOC server will suffice for you.

I am a bit confused as why you needed the script in the first place though. The server seems to continue running even when you stop the ncurses interface.

The only reason i can think of is to have the server start when you boot up your PC.

Kind regards

---

### Post by thebestofall007 on 2012-06-03
> **matt_symes said:**
> 

I am a bit confused as why you needed the script in the first place though. The server seems to continue running even when you stop the ncurses interface.

The only reason i can think of is to have the server start when you boot up your PC.

Kind regards

the script was so the server starts at boot like you mentioned, so you wouldn't have to type it in manually to start the server, so you are correct.

i looked at the amended script and changed

```
 # Start the daemon
                start-stop-daemon --start --chuid "$USER" --exec /usr/bin/mocp -- -S
```

to

```
# Start the daemon
                start-stop-daemon --start --chuid "$USER" --exec /usr/bin/mocp
```

and the program started with the interface at boot like i wanted. the original script was messed up and i send my many thanks for your time for cleaning it up (it wasn't wasted. if i could donate something, i would) and fixing the problem. if there is anything wrong changing this, please let me know.

i like moc because in addition to what you said it takes VERY FEW resources to run and runs very stable and doesn't lock up after resuming from suspend or hibernate, and sounds smooth. i have an old pentium II machine that works beautifully and has a great sound card on it, but it just doesn't quite have the muscle to run geexbox or xbmcbuntu properly (mplayer, xbmcbuntu, and geexbox all crashed when i suspended them while the music was playing on a newer core 2 duo machine). 

i am in the process of giving that old pentium II machine a new life by converting it into a simple media player with no point/click or touchscreen nonsense - just simple next song, previous song, ff, rw, up, down, left, right, stop, play, pause, and volume controls. i like to be able to customize the player, from its hardware to the look/feel to the sound quality - you name it, just like i do to ubuntu. that is why i don't just want a normal mp3 player.

again,
thanks a lot for your time.

---

### Post by matt_symes on 2012-06-03
Hi

Nice little project. It should be fine with out the -S switch. It will still start the MOC server.

Pentium 2 eh ? I love really old boxes like that. 

A box like that would also make a great torrent box using rtorrent...

Kind regards

---

### Post by thebestofall007 on 2012-06-03
from what i read in the documentation for moc, you can also theme it to your liking and change the keymaps, lcdproc for lcd/vfd displays, and equalization (maybe someone can code a graphic equalizer, fm tuner card support, and maybe a fade/balance/crossover control using multiple sound cards - to use in a car media player perhaps?). just thinking...

---

### Post by matt_symes on 2012-06-03
Hi

> maybe someone can code a graphic equalizer

alsamixer has a graphic equalizer plugin called alsaequal. 

It looks like mocp uses alsa. I assume you're not using pulse.

[https://launchpad.net/ubuntu/+source/alsaequal](https://launchpad.net/ubuntu/+source/alsaequal)

As it's a plugin, you have to hook it into your alsa configuration file.

Kind regards

---

### Post by thebestofall007 on 2012-06-03
> **matt_symes said:**
> Hi



alsamixer has a graphic equalizer plugin called alsaequal. 

It looks like mocp uses alsa. I assume you're not using pulse.

[https://launchpad.net/ubuntu/+source/alsaequal](https://launchpad.net/ubuntu/+source/alsaequal)

As it's a plugin, you have to hook it into your alsa configuration file.

Kind regards

oh. i'm using alsa.

---

### Post by thebestofall007 on 2012-06-03
ok, i just ran into a problem. i am having an issue with the interface outputting a "FATAL_ERROR: wgetch() failed!" message after i press a button. the interface appears after the boot sequence finishes, but displays the error the moment i press a key, then the interface disappears and the system drops to the console. 

i think that this *might* be related to getch based on a manpage as shown here: [http://linux.die.net/man/3/wgetch]().

i have a /var/log/boot.log paste of the instance. there is a lot gibberish mojibake that was outputted before the error happened:

[http://pastebin.com/miGsVYSu]("http://pastebin.com/miGsVYSu") 

 ](*,)

---

### Post by matt_symes on 2012-06-03
Hi

Run some quick tests.

1.

Now it's crashed, open a terminal and type.

```
ps aux | grep /usr/bin/mocp
```

Do you still see an instance of mocp running (not the one with grep in it). If not then post this info back. If so then type

```
mocp
```

to start the ncurses client. It should connect to the running server. Hit a key. Does it crash ?

2.

Put the -S switch back into the script. Reboot the PC. Get to the console and type

```
ps aux | grep /usr/bin/mocp
```

to ensure the server is running. Look for the -S switch.

Then type

```
mocp
```

to start the client. Hit a key.

Do you still get the crash ?

Kind regards

---

### Post by thebestofall007 on 2012-06-03
1. yes, there is an instance of mocp and i am able to type mocp and the interface starts, and i can press a key without it crashing.


2. i reinserted the -S in the script, rebooted, ran the command, and the -S switch is present in the output. typing mocp in the console starts the client with no crashing upon any button press.

---

### Post by matt_symes on 2012-06-03
Hi

> **thebestofall007 said:**
> 1. yes, there is an instance of mocp and i am able to type mocp and the interface starts, and i can press a key without it crashing.


2. i reinserted the -S in the script, rebooted, ran the command, and the -S switch is present in the output. typing mocp in the console starts the client with no crashing upon any button press.

That's good then. 

So the problem is starting the client during bootup.

Let me think for 10 mins.

Kind regards

---

### Post by matt_symes on 2012-06-03
Hi

From

```
man wgetch
```

> wgetch
returns an error if the window pointer is null, or if its timeout expires without having any data.

It maybe this first error that is causing the problem. I would need to strace or look at the source and that is a job for tomorrow. It's late here now.

Have you set it up so it automatically logs into the console ?

Kind regards

---

### Post by thebestofall007 on 2012-06-03
> Have you set it up so it automatically logs into the console ?

yes, i have it set up where i automatically log in to the console as my username, so i don't have to enter my username and password every time i have to reboot.



> It maybe this first error that is causing the problem. I would need to strace or look at the source and that is a job for tomorrow. It's late here now.

if it's late there, i'll respect that.  have a good rest, and again, thanks for your time.

---

### Post by thebestofall007 on 2012-06-04
bump.

---

### Post by matt_symes on 2012-06-04
Hi

It seems that running the mocp client from the system V init.d run levels will not work.

Maybe we could edit

```
/etc/init/tty1.conf
```

and get it to start the mocp client as opposed to the login program.

This is my tty1.conf file

```
cat /etc/init/tty1.conf
# tty1 - getty
#
# This service maintains a getty on tty1 from the point the system is
# started until it is shut down again.

start on stopped rc RUNLEVEL=[2345] and (
            not-container or
            container CONTAINER=lxc or
            container CONTAINER=lxc-libvirt)

stop on runlevel [!2345]

respawn
exec /sbin/getty -8 38400 tty1
```

We could try to change /sbin/getty -8 38400 to /usr/bin/mocp and see where that takes us.

Incidentally, i have not tried this so it will be interesting to see if it works.

Kind regards

---

### Post by thebestofall007 on 2012-06-04
> **matt_symes said:**
> 
We could try to change /sbin/getty -8 38400 to /usr/bin/mocp and see where that takes us.

Incidentally, i have not tried this so it will be interesting to see if it works.

Kind regards

here is my tty1.conf:

> # tty1 - getty
#
# This service maintains a getty on tty1 from the point the system is
# started until it is shut down again.

start on stopped rc RUNLEVEL=[2345] and (
            not-container or
            container CONTAINER=lxc or
            container CONTAINER=lxc-libvirt)

stop on runlevel [!2345]

respawn
# exec /sbin/getty -8 38400 tty1
# exec /usr/bin/mocp
**exec /bin/login -f lou < /dev/tty1 > /dev/tty1 2>&1**

the bold section is the part that allows me to login automatically as my username (whereas if i uncommented the "exec /sbin/getty -8 38400 tty1" part, i would be prompted for my username/password). 

i tried to comment the "exec /bin/login -f lou < /dev/tty1 > /dev/tty1 2>&1" part out and uncomment "/usr/bin/mocp" and the client started like before, but i had the same symptoms/error as described earlier.

---

### Post by matt_symes on 2012-06-04
Hi

Try this. It runs on my system and i am listening to it now. Obviously change the user name to lou and change your paths as appropriate.

tty1.conf

```
matthew@matthew-Aspire-7540 ~ % cat /etc/init/tty1.conf
## tty1 - getty
#
# This service maintains a getty on tty1 from the point the system is
# started until it is shut down again.

start on stopped rc RUNLEVEL=[2345] and (
            not-container or
            container CONTAINER=lxc or
            container CONTAINER=lxc-libvirt)

stop on runlevel [!2345]

respawn
exec /sbin/getty -i -l /home/matthew/test.sh -n -8 38400 tty1
matthew@matthew-Aspire-7540 ~ %
```

```
matthew@matthew-Aspire-7540 ~ % cat test.sh 
#!/bin/dash

exec su matthew -c /usr/bin/mocp
matthew@matthew-Aspire-7540 ~ %
```

Remember to chmod the script. You can also place it where you want.

```
chmod 755 test.sh
```

A couple of points to note. It's running three instances of mocp.

```
matthew@matthew-Aspire-7540 ~ % ps aux | grep mocp
matthew   3702  0.0  0.0  54852  1560 tty1     Ss+  02:58   0:00 su matthew -c /usr/bin/mocp
matthew   3716  0.0  0.2 192924  7548 tty1     S+   02:58   0:00 /usr/bin/mocp
matthew   3717  0.7  0.2 728548  6740 ?        Ssl  02:58   0:07 /usr/bin/mocp
matthew   4364  0.0  0.0   9384   880 pts/0    R+   03:15   0:00 grep mocp
matthew@matthew-Aspire-7540 ~ %
```

I'm not sure why this is and i need to run some tests tomorrow to find out exactly what is happening. This is not a job for tonight though.

It also seems to take a while to start.

EDIT: You could get it to start screen with split view and have mocp in one view and alsamixer in another. I'm not sure how you envisage this.

Kind regards

---

### Post by thebestofall007 on 2012-06-04
i am also playing it now as i type and have the three instances like you describe. 

tell me something though: 

1. did you have the interface load, then flicker back to console upon pressing a button, and then flicker back to the interface on its own (but with the buttons working without errors afterward)? 

hmm, maybe the flicker is triggered when the multiple instances start.

2. are you able to press "q" to get back to the console to enter commands (but still have the server playing the music), like if when mocp was typed manually in the console to start it? i can press q and it starts the navigation of the interface over at the root of the system's partition (at /).

just some observations...

> EDIT: You could get it to start screen with split view and have mocp in one view and alsamixer in another. I'm not sure how you envisage this.

that's a great idea! that can be a different project for a later time as i learn more on how to program. it is nice however to be able to start the player at boot-up for once (and we both learned something ;)).

once again, i respect that it's late over there. have a good rest. thanks.

---

### Post by matt_symes on 2012-06-04
Hi

It's now 4.45am so these are just quick comments. We can continue this tomorrow if you like. Once again bump this thread please.

> **thebestofall007 said:**
> i am also playing it now as i type and have the three instances like you describe.

Good :)

> 
tell me something though: 

1. did you have the interface load, then flicker back to console upon pressing a button, and then flicker back to the interface on its own (but with the buttons working without errors afterward)? 

hmm, maybe the flicker is triggered when the multiple instances start.

I am running it on desktop installation and i only get moc to appear on the console after i log into the desktop session and switch back to the console.

Tommorrow i will create a chrooted debootstrap minimal install, set that up and see if i see what you are getting.

The flashing may well be due to the three instances of moc running. I would just expect two. 

It may also be because the initial instance of moc is crashing and then respawning.

We will see tomorrow though.

> 
2. are you able to press "q" to get back to the console to enter commands (but still have the server playing the music), like if when mocp was typed manually in the console to start it? i can press q and it starts the navigation of the interface over at the root of the system's partition (at /).

This is due to the respawn option in tty1.conf.

> that's a great idea! that can be a different project for a later time as i learn more on how to program. it is nice however to be able to start the player at boot-up for once (and we both learned something ;)).

once again, i respect that it's late over there. have a good rest. thanks.

I really like this project and i am glad to help out. I'm glad you brought moc to my attention.

Kind regards

---

### Post by thebestofall007 on 2012-06-05
bump.

---

### Post by matt_symes on 2012-06-06
Hi

I will take a look tonight. Last night i had other priorities ;)

Kind regards

---

### Post by thebestofall007 on 2012-06-06
> **matt_symes said:**
> Hi

I will take a look tonight. Last night i had other priorities ;)

Kind regards

that's ok, we all have them.

---

### Post by thebestofall007 on 2012-06-07
bump.

---

### Post by thebestofall007 on 2012-06-08
bump.

---

### Post by matt_symes on 2012-06-09
Hi

@thebestofall007. Where were we ?

I have just remove the mocp script from the /etc/init.d directory and removed the symlinks

```
sudo update-rc.d -f mocp remove
```

```
matthew@matthew-Aspire-7540 ~ % ls /etc/rc?.d/*moc*    
zsh: no matches found: /etc/rc?.d/*moc*
matthew@matthew-Aspire-7540 ~ %
```

Now the only way it's being called is from /etc/init/tty1.conf.

It is working fine here. I am getting two instances of mocp and the su command to change the user to run mocp as me. D'oh :p

```
matthew@matthew-Aspire-7540 ~ % ps aux | grep mocp
matthew   4698  1.5  0.2 728156  7060 ?        Ssl  02:02   0:01 /usr/bin/mocp
matthew   4767  0.0  0.0  54852  1560 tty1     Ss+  02:03   0:00 su matthew -c /usr/bin/mocp
matthew   4779  4.0  0.2 192920  7556 tty1     S+   02:03   0:00 /usr/bin/mocp
```

Are you having any issues ? Is this what you wanted ? Do you need any more help ?

Kind regards

---

### Post by thebestofall007 on 2012-06-10
it's working great and i am listening to southbound fearing - irresistable as i type. the interface starts right up one time with no crashing or flashing upon button presses, AND IT STARTS FASTER ;).


this is pretty much what i wanted. i'll probably wind up making the alsaeq plugin start alongside mocp in the future like you mentioned in an earlier post (great idea), among any other things that suit my fancy like using lcdproc to output title/artist info to a usb lcd/vfd display (i have a perl script i downloaded from the mocp homepage that does that). i don't have an lcd to play with right now, though, so i have to use the bulky CRT that came with the machine (for now).

the tty method totally slipped my mind and i didn't realize that it would be a lot simpler in this case! 

i usually see the init scripts edited instead of /etc/init/tty*.conf in most tutorials to start programs up at boot (what are the main differences between the two methods anyway?). i totally overlooked it. 

one question though: were are you able to get back to the console/command line to enter commands if needed? if so, how?

---

### Post by matt_symes on 2012-06-10
Hi

I'm glad it's working.

> i usually see the init scripts edited instead of /etc/init/tty*.conf in most tutorials to start programs up at boot (what are the main differences between the two methods anyway?). i totally overlooked it. 

The main difference is running mocp by editing tty1.con the way we did will take over that tty and will only run mocp in the console. It will not run an interactive bash shell.

The original configuration runs getty and when you login it starts an interactive bash shell. We configured just to run mocp.

From man getty > DESCRIPTION
       agetty opens a tty port, prompts for a login name and invokes the /bin/login command. It is normally invoked by init(8).

Running commands using system V (update-rc.d to create the symlinks) or upstart generally starts running daemons.

> one question though: were are you able to get back to the console/command line to enter commands if needed? if so, how?

You can switch consoles or you could consider using tmux or screen and run that from tty1. 

You can configure them to split the screen and in each split run mocp  and other command line apps like alsamixer or an interactive bash shell.

The way we set it up, it will respawn mocp if you try to kill it. If you remove the respawn command from tty1.conf then when killing mocp (by pressing a capital Q) you will not have an interactive bash prompt.

You could try getting tty1 to run an interactive bash (or other) shell and get that shell to run mocp. This would need investigation to get this working though as i have never tried it.

Kind regards

---

### Post by thebestofall007 on 2012-06-10
i found i can switch to another console by hitting ctrl alt f2 (or f3, f4, and so on to coorespond to tty2-6) to login to the tty2, 3, 4 and up to about tty6 (tty1 is mocp) to be able to enter commands also, and then switch back to tty1 to go back to the mocp interface. this works quite well in this case.

---

### Post by matt_symes on 2012-06-10
Hi

> **thebestofall007 said:**
> i found i can switch to another console by hitting ctrl alt f2 to login to the tty2 (tty1 is mocp) to be able to enter commands also, and then switch back to tty1 to go back to the mocp interface. this works quite well in this case.

Yes; that's what i mean by changing the console. 

You can put alsamixer on a different console and run commands on a different console again.

If you want to mark this thread as solved then we can wrap this up.

If you have any more questions in the future then you can start another thread and PM me the link.

If you have more questions now then we can keep this thread open and work through them.

Kind regards

---

### Post by thebestofall007 on 2012-06-10
> If you want to mark this thread as solved then we can wrap this up.

THANKS A BUNCH. Will do.

---

