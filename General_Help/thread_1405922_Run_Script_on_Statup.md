---
title: "Run Script on Statup"
date: 2010-02-13
forum: General Help
---

### Post by NertSkull on 2010-02-13
So I'm trying to automatically mount a truecrypt volume when I start my computer up.  I've written a real simple script, placed it in the init.d folder and run the update-rc.d stuff.

This is the script 

```
#!/bin/sh
### BEGIN INIT INFO
# Provides:          
# Required-Start:    truecrypt
# Required-Stop:     
# Default-Start:     S
# Default-Stop:      
# Short-Description: Load encrypted volume
# Description:       Mount the Data drive.
### END INIT INFO

. /lib/lsb/init-functions

set -e

case "$1" in
  start)
    truecrypt --password='my_pass_phrase' /dev/sda4 /media/Data
    ;;
  stop)
    truecrypt -d
    ;;
  restart|force-reload)
    $0 stop
    $0 start
    ;;
esac

exit 0
```I've tried running this in all combinations of run levels.  S, 2,3,5, etc.  But it never will load my truecrypt volume.  

If I run from the command prompt once running it works fine by typing 

```
sudo /etc/init.d/myscript start
```The drive loads and I'm happy.

What am I doing wrong?  I'm thinking it has to be something with the required-start part.  I've tried "truecrypt" I've tried "$all" "$remote_fs" and a whole bunch of other combinations.

I also usually put it in with the NN as 99 (so its S99myscriptname after update-rc.d).

Any help for what I'm misunderstanding about this??  Thanks all

p.s. I know I'm storing the encryption passphrase in this, which I'm not too concerned about for various reasons that are too long to explain here.

---

### Post by giammy on 2010-02-13
> **NertSkull said:**
> So I'm trying to automatically mount a truecrypt volume when I start my computer up.  I've written a real simple script, placed it in the init.d folder and run the update-rc.d stuff.

...

case "$1" in
  start)
    truecrypt --password='my_pass_phrase' /dev/sda4 /media/Data
    ;;

p.s. I know I'm storing the encryption passphrase in this, which I'm not too concerned about for various reasons that are too long to explain here.

Hi,

for the init script, I think it could be a problem of environment (PATH not set,
so truecrypt command is not found)

Try to put

/usr/bin/truecrypt --password ...

p.s: you are right: i was commenting the password fact ... I hope you know what you are doing :-)

P.s2: another way to mount it could be using PAM (I use it with encfs in [http://cloudusb.net](http://cloudusb.net) but
I think it can work with  truecrypt too)

bye
giammy

---

### Post by NertSkull on 2010-02-13
So I changed my script to look like this, to take account for the path of truecrypt.  But I still don't get any mounted drives on boot up.

```
#!/bin/sh
### BEGIN INIT INFO
# Provides:          
# Required-Start:    $all $local_fs $remote_fs
# Required-Stop:     
# Default-Start:     
# Default-Stop:      
# Short-Description: Load encrypted volume
# Description:       Mount the Data drive.
### END INIT INFO

. /lib/lsb/init-functions

set -e

case "$1" in
  start)
    /usr/bin/truecrypt --password='my_pass_phrase' /dev/sda4 /media/Data
    ;;
  stop)
    truecrypt -d
    ;;
  restart|force-reload)
    $0 stop
    $0 start
    ;;
esac

exit 0
```

Any other ideas as to why this won't auto mount my drive??  thanks??

oh, and i've played around with it loading at run level S, or levels 2,3,4,5 and the such, and I can't find any of them making a difference.  at least not with this.

p.s. this is the first script i've ever tried writing, so I'm sure i'm missing or not doing thousands of things I should be.  I've just been reading all day on how this stuff works, and taking things from other scripts i've found.

---

### Post by giammy on 2010-02-13
Hi,

I said /usr/bin/truecrypt as in my system it's located there: in your system truecrypt is in /usr/bin?
(you can see with "which truectypt")
By the way, you have to change the stop too.

If truecrypt is there, are you sure the init.d script is called?
You can verify with an ls -la /etc/rcX.d (X is  the runlevel)
There should be a link to your script in /etc/init.d

bye
giammy

---

### Post by ubername on 2010-02-13
Could you just put the script in your startup applications? Or maybe you need it before anyone logs on?

---

### Post by NertSkull on 2010-02-13
Yeah I checked to make sure truecrypt is in /usr/bin/truecrypt on my system and it is.

I just correct the stop part as well, don't know how I forgot that.

And I've checked each time to make sure the symbolic link gets updated when I run update-rc.d and it does.

I have a listing for "S98truecrypt_automnt" under rc.5.d, rc.4.d, etc (and I've had it under rcS as well, as i've tried a bunch of different options).

And I do kind of need this to run before people log on ideally.  Although I have gotten it to work by placing a different script, but same truecrypt mounting options, in the system >> preferences >> start up applications.  The problem with that is it needs root access to run the script, which I didn't want to pass my root password through the script.

So ideally I would like to find a way to get it installed through the update-rc.d

But you're right.  It seems like somehow truecrypt can't be called for that early, so the script won't load the drive because it can't find truecrypt.

Any other thoughts.

Thanks again for the help

---

