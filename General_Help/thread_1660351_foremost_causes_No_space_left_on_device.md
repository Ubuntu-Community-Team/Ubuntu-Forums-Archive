---
title: "foremost causes No space left on device"
date: 2011-01-05
forum: General Help
---

### Post by jvanwijnendaele on 2011-01-05
hi all,

I used foremost to recover some files on my hd. I made the mistake of not mounting a location first and then executing the recovery process.

This mistake resulted in filling up my free space on my partition my root is on.
[INDENT]administrator@Linpha:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            480688980 480675496         0 100% /
udev                   2025608       224   2025384   1% /dev
none                   2025608       256   2025352   1% /dev/shm
none                   2025608      4948   2020660   1% /var/run
none                   2025608         0   2025608   0% /var/lock
none                   2025608         0   2025608   0% /lib/init/rw
/dev/sdb1            480688980 249182988 207088400  55% /1
/dev/sdc1            480688980 227500536 228770852  50% /2
[/INDENT]i see that /dev/sda1 mounted on / is 100% full... then where is my data that is worth half a terrabyte?

when I do a du -hc --max-depth=1 this is generated: 
[INDENT]280K    ./.gstreamer-0.10
116K    ./.gnome2
528K    ./.gconf
24K    ./.evolution
144K    ./.pulse
4.0K    ./Music
48K    ./.cache
4.0K    ./.update-notifier
4.0K    ./linpha
12K    ./.update-manager-core
4.0K    ./.nautilus
1.8M    ./.openoffice.org
2.9M    ./Downloads
44K    ./.config
56M    ./.mozilla376G    ./.local
4.0K    ./Videos
4.0K    ./Desktop
4.0K    ./Templates
80K    ./.gconfd
8.0K    ./.tsclient
9.3M    ./.thumbnails
4.0K    ./Public
4.0K    ./Pictures
4.0K    ./.gnome2_private
20K    ./.gnupg
4.0K    ./.ssh
12K    ./.dbus
6.2M    ./Documents
376G    .
376G    total
[/INDENT]any tips or tricks please?

I use this ubuntu server as my web server. Because of this 'no free space left' problem, php can no longer create session files and users can no longer log in.

---

### Post by sohlinux on 2011-01-05
the files must be hiding somewhere

try
```
du / -h | less
```

---

### Post by seawolf167 on 2011-01-05
df also has a -h flag you can use to read it easier

```
df -h
```does this show any missing files (you prob will get permission errors without the sudo)

```
sudo du / -hac --max-depth=1
```

---

### Post by sohlinux on 2011-01-05
looking again at your du output maybe the 376G file is called .

---

### Post by seawolf167 on 2011-01-05
> **sohlinux said:**
> looking again at your du output maybe the 376G file is called .

The . in this case could mean current folder? since the previous du entries all have ./directory_name, so the last entry would then be ~

My output from any of my machines don't have that leading period

```

...
70G     /home
16K     /lost+found
4.0K    /mnt
868M    /var
77G     /
77G     total
```edit: I'm stupid, I used the root directory, when preformed on the home directory they do have the period

```

...
4.0K    ./Public
4.0K    ./Videos
45G     .
45G     total

```So the . is just the current folder size is my guess

---

### Post by jvanwijnendaele on 2011-01-06
fist off, thank you for the replies but I haven't had the change to try out your commands.

After logging out I can no longer log in.:confused:(also after restart)

In the login console i get the folowing error message after trying to log in: [INDENT]install problem. the configuration defaults for GNOME power manager have not been installed correctly.[/INDENT]

When I select an account to login a drop down menu in the lower bar appears where I can select failsafe GNOME, GNOME or xterm.

The shared folders and the webserver are also no longer accessable. (ping sends a time out...)

I use ubuntu server 9.10 64bit

I think all this is still caused by /dev/sda1 = 100% used.
while logging in, ubuntu tries to write something to a file I guess, fails on disk usage and problems occure. 

any suggestions?

---

### Post by sohlinux on 2011-01-06
> **jvanwijnendaele said:**
> fist off, thank you for the replies but I haven't had the change to try out your commands.

After logging out I can no longer log in.:confused:(also after restart)

In the login console i get the folowing error message after trying to log in: [INDENT]install problem. the configuration defaults for GNOME power manager have not been installed correctly.[/INDENT]

When I select an account to login a drop down menu in the lower bar appears where I can select failsafe GNOME, GNOME or xterm.

The shared folders and the webserver are also no longer accessable. (ping sends a time out...)

I use ubuntu server 9.10 64bit

I think all this is still caused by /dev/sda1 = 100% used.
while logging in, ubuntu tries to write something to a file I guess, fails on disk usage and problems occure. 

any suggestions?


use xterm to delete some files from sda1

---

### Post by jvanwijnendaele on 2011-01-10
> **sohlinux said:**
> use xterm to delete some files from sda1

I tried to login with xterm, GNOME and GNOME failsafe.

I can't get past the login screen.
/edit: in failsafe I get a black screen and my mousecursor. yeey.

When I do ctrl-alt-f1 i get asked for login and password but  I can't get to login either

either way, how can i reach my sda1 to delete some files?

/edit: got the hd out of the server. accessed it as data disc. deleted the hidden files using sohlinux's command. everything works again.

---

### Post by Daedal007 on 2011-03-27
:)

---

### Post by nottoobright on 2011-03-27
Hi. I have accidentally deleted all of our pictures (approximately 3000 images) and ran foremost to try to find them. I ran...

foremost -v -T -t jpg -i /dev/sda1

After about two hours of recovering some 200,000 jpgs, it said there was an error writing files and that my disk space was all used up.  From here, I am completely lost. All I need is my pictures back. Anyone have any ideas on what i can do now?

---

