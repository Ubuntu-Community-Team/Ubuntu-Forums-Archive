---
title: "Transmission Daemon, startup problems,"
date: 2009-10-11
forum: General Help
---

### Post by Ordes on 2009-10-11
trying to get transmission daemon to auto start, on a different user than administer. The account  just name user now. I also auto login into this account on boot


i tried: 
1) adding td to startup applications (user), didnt work 
2) writing a start script, adding script to startup applications (user), didnt work
3) tried the whole, edit rc.local -- [http://plope.com/Members/chrism/debian_rc_local_equiv](http://plope.com/Members/chrism/debian_rc_local_equiv) -- , adding --su user -c transmission client-- to local, didnt work

--> the not working refers to: that i always get unauthorized IP, when i try to connect by browser, the daemon itself loads up though.


edited: 
it actually is not only on autostart. also with no td starting at all, when i start td (after reboot)manually in user, i have the same problem.the daemon loads up, but i cannot connect because of unauthorized IP

so no matter how i start it, after reboot, i always have to:

1) start td (user)
2) stop td (admin)
3) start td (user)

after this i tried&#65306;&#12288;transmission-daemon -g ~/user/.config/transmission-daemon, but didnt really help

any clues, because i dont get it..
thanks

---

### Post by Ordes on 2009-10-11
mhm... ok getting closer...

in /etc/transmission-daemon  is also a settings.json, which seems to be the main one

i allowed my ip throught this, and td was working on the first time.

but i still cannot manage to get tb to use my /home/user/.confg.transmission-daemon/settings.json
because with the /etc/td i am not able to use my "~/user/download/", 

shoudlnt $ transmission-daemon -g /home/user/.confg/transmission-daemon/
solve this?

also tried in /init.d/local --> su server -c "transmission-daemon -g /home/user/.confg/transmission-daemon/"
but still same, gotta stop first, and than start again to get my "user" settings

clueless

---

### Post by Ordes on 2009-10-11
i finally figured it out..:guitar:

in case someone is struggling too:

root -> $ gedit /etc/init.d/transmisson-daemon

two positions have to be changed:

**Original**:
NAME=transmission-daemon

USER=debian-transmission

**Into**:
NAME=transmission-daemon -g /home/XXX/.config/transmission-daemon

USER=XXX

**than**
* edit your config file in: $ /home/XXX/.config/transmission-daemon/settings.json
   its probably best to have td started once under XXX, so the /.config/td is created, than just edit it

* for autostart its enough to add in XXXs startup applications (in gnome) 
  transmission-daemon

no need to change or create, init.d/local, scripts ,etc...

---

### Post by akmodi on 2009-11-18
Hi,

Broke my head for 2 days -- then found the problem and the solution.

Previously (jaunty) no module was created in /etc/init.d/ for autostart. one had to put a crontab entry for this.

So, transmission starts automatically, but no settings directory is defined -- so starts with pre-sets that one cannot change.

Solution:
1. kill td (sudo kill -9 `pidof transmission-daemon` >/dev/null)
2. start transmission and ask it to create its files (transmission-daemon -g /home/transmission/.config/transmission-daemon -f)
3. when transmission shows up some lines and waits -- cancel it (control + c)
4. When you have canceled this process you will see it says - amoungst other things - the following text:

Saved "/home/transmission/.config/transmission-daemon/settings.json

5.get transmission to restart properly (sudo vi /etc/init.d/transmission-daemon)

6. and then change

NAME=transmission-daemon 

NAME=transmission-daemon -g /home/transmission/.config/transmission-daemon

7. restart transmission daemon

8. should be OK now.

9. you can now edit /home/transmission/.config/transmission-daemon/settings.json for your settings and all will be well ( as TD knows to look here for its files)

---

### Post by Cadmus on 2010-01-10
I'm trying this now, when I add the '-g' part to NAME I get a message when trying to run the init script...

-g not found

What am I doing wrong?

---

### Post by redstain on 2010-01-14
> **Cadmus said:**
> I'm trying this now, when I add the '-g' part to NAME I get a message when trying to run the init script...
 
-g not found
 
What am I doing wrong?
 
I have the same issue and get the same error after implementing the change.
 
-g not found

---

### Post by wasutton3 on 2010-03-16
I can confirm the same problem on a current up to date karmic 32 bit installation.

---

### Post by medley_44 on 2010-03-21
I was having the "-g not found" problem after an update came down from the transmission PPA; I'm running Mythbuntu Jaunty. Here's how I got the daemon and web interface back up and running:

sudo /etc/init.d/transmission-daemon stop

sudo vim /etc/default/transmission-daemon

Set the CONFIG_DIR variable to point to the folder that contains your settings. e.g, :

CONFIG_DIR="/home/username/.config/transmission"

Save the file. Next, type:

sudo vim /etc/init.d/transmission-daemon

Set the USER variable to the same name as above, e.g., "username" in this example. Also, you don't need the -g option in NAME any more. The first three lines /etc/init.d/transmission-daemon should now look like this:

NAME=transmission-daemon
DAEMON=/usr/bin/$NAME
USER=username

Save your changes, then

sudo /etc/init.d/transmission-daemon start

The daemon should now be running using the settings from the directory you specified.

BTW, in my experience no entry is needed in your desktop environment's startup applications.

---

### Post by naaman on 2010-04-13
Thanks to akmodi & medley_44 - solution working for Ubuntu Server 9.10..
My issue was that transmission-daemon kept overwriting the settings in /etc/transmission-daemon/settings.json upon restarting the daemon via /etc/init.d..

1. stop transmission-daemon via: sudo /etc/init.d/transmission-daemon stop

> **akmodi said:**
> 

2. start transmission and ask it to create its files (transmission-daemon -g /home/transmission/.config/transmission-daemon -f)
3. when transmission shows up some lines and waits -- cancel it (control + c)
4. When you have canceled this process you will see it says - amoungst other things - the following text:

Saved "/home/transmission/.config/transmission-daemon/settings.json

5. edit /home/transmission/.config/transmission-daemon/settings.json for your settings and all will be well ( as TD knows to look here for its files)

> **medley_44 said:**
> 

6. sudo vim /etc/default/transmission-daemon

Set the CONFIG_DIR variable to point to the folder that contains your settings. e.g, :

CONFIG_DIR="/home/username/.config/transmission"

7. sudo vim /etc/init.d/transmission-daemon

Set the USER variable to the same name as above, e.g., "username" in this example. Also, you don't need the -g option in NAME any more. The first three lines /etc/init.d/transmission-daemon should now look like this:

NAME=transmission-daemon
DAEMON=/usr/bin/$NAME
USER=username

8. sudo /etc/init.d/transmission-daemon start

The daemon should now be running using the settings from the directory you specified.


---

