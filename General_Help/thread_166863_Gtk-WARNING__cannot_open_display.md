---
title: "Gtk-WARNING **: cannot open display:"
date: 2006-04-27
forum: General Help
---

### Post by yanik on 2006-04-27
I have a little application here that tries to open a browser, it fails giving this output:
```

(mozilla-bin:19072): Gtk-WARNING **: cannot open display:
find: /home/yanik/.mozilla: Permission denied
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified
```

Any ideas?  I'd really like this to work. 

Thanks

Yanik

---

### Post by tokez on 2006-04-27
Stupid answer - sorry .

Did you possibly try 'sudo' before the command?

---

### Post by yanik on 2006-04-27
yep, I tried sudo, sudo -s and even made a real root user and tried it with su.

Still the same thing.

Thanks for trying :)

---

### Post by douga on 2006-04-27
Try: "xhost +LOCAL:" (without the quotes of course) and then try the program. This command will give all non-network connections access to the display. I'm assuming you're running this from a terminal, though.

---

### Post by yanik on 2006-04-27
still doesn't work

```
root@s00016:~# xhost +LOCAL:
non-network local connections being added to access control list
```

And I still get:
```
(mozilla-bin:22306): Gtk-WARNING **: cannot open display: 0.0
```

Yes, I'm running it from the cli.

Thanks

---

### Post by douga on 2006-04-27
Sounds like it could be running as root? Anyway, after the xhost command, try:

export DISPLAY=:0.0

and try your command again.

---

### Post by CarsomyrXIII on 2006-05-11
I'm getting the same error just by trying to open applications that employ GUIs in terminal, logged in with su.

Again, the error:
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(synaptic:23691): Gtk-WARNING **: cannot open display:
or
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(firefox-bin:9061): Gtk-WARNING **: cannot open display:
or
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(xchat:9098): Gtk-WARNING **: cannot open display:

for a few examples.
I tried what was posted here but to no avail. I still seek an answer.

---

### Post by DirtDart on 2006-06-28
I had the same problem (I actually got to this post via a Google search).

As your normal user:

[I]sudo xhost +localhost

su - root[/I] 

and once you're root:

[i]export DISPLAY=0:0

mozilla-firefox& [/i]


That should work, as it worked for me.

---

### Post by CarsomyrXIII on 2006-06-28
Oh. I found out another fix for this.

Use su to log in as root, then add yourself to the sudoers list with visudo command. Add your username at the bottom right after root, and copy what is put after root. Now, sudo will be enabled for your pw in the terminal. Now, just open whatever you need to open that was giving you the error before only with sudo.

Hope this helps.

---

### Post by Iesos on 2006-07-11
Doesn't work for me. I get 
```
xhost:  unable to open display "0:0"
```
when running 
```
$ sudo xhost +localhost
```
and the following message is the problem:
```
$ xterm
wxterm Xt error: Can't open display: 0:0
```
or
```
$ xscreensaver
xscreensaver: Can't open display: 0:0
xscreensaver: running as johan/johan (1000/1000)
```

---

### Post by Nikos_M on 2006-08-21
Ok maybe the sollution is a bit long but bear with me....so lets start.
Lets determine that we are dealing with the same problem  :
1. open a console and login as ROOT : su
2. see who can launch an "X program" : xauth list

if you get an error or the list is empty(you dont get anything) then continue to read on-probably this is you solution.

3. open a console and as USER see who is authorized to open the X programs : xauth list
This should give you something like this :
desktop/unix:0  MIT-MAGIC-COOKIE-1  395a5228d995d958a0cc59a5afe9d521
193.5.93.21:0  MIT-MAGIC-COOKIE-1  45891337dd1f30ea26f45bb6b70449b0
desktop:0  MIT-MAGIC-COOKIE-1  370116e6e873fc798aa4f1429f536219

4. now as ROOT add the ones (hostnames) you want to be able to launch X programs on your DISPLAY :
xauth add desktop/unix:0 . 395a5228d995d958a0cc59a5afe9d521

Do the same for the other entries as well(if you want to be able to launch from other hosts too-try adding all if you dont know which one is the correct one).Notice that the long numbers at the end are the same with the users before!ALSO NOTICE THE DOT "." between the "desktop/unix:0" and the number.

Now you should be ok.Try to launch the program as ROOT
Should work

---

### Post by wondergod on 2006-08-28
omg thank you Nikos_M I've been searching all over for a fix for that error..!!

---

### Post by Nikos_M on 2006-09-18
Actually there is a faster solution to this(but has a potential disadvantage).

You just need to copy the .Xauthority file from the home directory of the user you have logged in to the root's homefolder.

As root do:
cp /home/username/.Xauthority /root/

Note that this allows the root to launch x-programs from all the machines that the user is allowed(something you might not want to do).

Since xdm creates a new mit-magick-cookie the Xauthority every time it is launched this should be done every time you restart X (or reboot).

---

### Post by lmo on 2006-12-19
Run visudo

Add 

```
env_keep+="DISPLAY XAUTHORITY"
```

to the Defaults line so it may look like:

```
Defaults !lecture,tty_tickets,!fqdn,env_keep+="DISPLAY XAUTHORITY"
```

Then sudo and gksudo won't mess up with 'Gtk-WARNING **: cannot open display:'

Finally, I can launch sudo/gksudo gnome-ppp ...

---

### Post by purpleD on 2007-04-10
> **lmo said:**
> Run visudo

Add 

```
env_keep+="DISPLAY XAUTHORITY"
```

to the Defaults line so it may look like:

```
Defaults !lecture,tty_tickets,!fqdn,env_keep+="DISPLAY XAUTHORITY"
```

Then sudo and gksudo won't mess up with 'Gtk-WARNING **: cannot open display:'

Finally, I can launch sudo/gksudo gnome-ppp ...

Wow thanks a lot! this worked for me while everything else I ran into failed.  I can gksudo firefox now and get updates.  Before my "check for updates" tab was greyed out.

---

### Post by gssharma16 on 2007-12-01
> **douga said:**
> Sounds like it could be running as root? Anyway, after the xhost command, try:

export DISPLAY=:0.0

and try your command again.




Thanks A lot Man it really helped me to much

---

### Post by venkog on 2008-02-15
> **Nikos_M said:**
> Ok maybe the sollution is a bit long but bear with me....so lets start.
Lets determine that we are dealing with the same problem  :
1. open a console and login as ROOT : su
2. see who can launch an "X program" : xauth list

if you get an error or the list is empty(you dont get anything) then continue to read on-probably this is you solution.

3. open a console and as USER see who is authorized to open the X programs : xauth list
This should give you something like this :
desktop/unix:0  MIT-MAGIC-COOKIE-1  395a5228d995d958a0cc59a5afe9d521
193.5.93.21:0  MIT-MAGIC-COOKIE-1  45891337dd1f30ea26f45bb6b70449b0
desktop:0  MIT-MAGIC-COOKIE-1  370116e6e873fc798aa4f1429f536219

4. now as ROOT add the ones (hostnames) you want to be able to launch X programs on your DISPLAY :
xauth add desktop/unix:0 . 395a5228d995d958a0cc59a5afe9d521

Do the same for the other entries as well(if you want to be able to launch from other hosts too-try adding all if you dont know which one is the correct one).Notice that the long numbers at the end are the same with the users before!ALSO NOTICE THE DOT "." between the "desktop/unix:0" and the number.

Now you should be ok.Try to launch the program as ROOT
Should work
Hi, I did: xauth list as root and  didnt get anything, I logged as a user and did : xauth list
and I have this message: 
xauth: creating new authority file /home/user/.Xauthority
and x-terminal is not working. Can you please  help ?

---

### Post by Nikos_M on 2008-02-15
There seems to be an easier way to bypass all this trouble.

1.install sux 
"sudo apt-get install sux"

2. instead of su do sux every time you want to have su priviliges and the X authorization.
"sux"

3.I would do an alias of su that would point to sux (I even have it in my /home/user/.bashrc file) so that every time you do su you ll get automatically X authorization (it is more handy than doing all the rest)
"alias su=sux"




Sux is just a wrapper for su and it only copies all the settings and authorization of the user to the root account the moment you log in.

---

### Post by anystupidname on 2008-04-23
I realize this thread is kind of old but I just found a different solution for the same error. My situation was a little different:

Debian 4 on a server running DHCPD gadmin-dhcpd, no xserver (just the xserver-utils package) and I was trying to access the gadmin-dhcpd interface through ssh from another Debian 4 box but kept getting the "Gtk-WARNING **: cannot open display : 0.0" error. I tried the xhost and xauth related suggestions to no avail. It turns out the problem was I was using yakuake for my terminal client side. When I opened an independant konsole window and re-established the ssh connection, I no longer had this problem. Hope this helps somebody.

---

