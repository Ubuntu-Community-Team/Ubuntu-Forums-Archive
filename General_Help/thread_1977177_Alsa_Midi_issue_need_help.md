---
title: "Alsa Midi issue need help"
date: 2012-05-09
forum: General Help
---

### Post by AceKinslayer on 2012-05-09
Ok so I'm a little new to ubuntu but I have this alsa midi installation  that pops up run by timidity. So is there any commands to bypass this installation? I've tried everything and looked everywhere but can't find anything hoping I don't have to reformat entirely to fix the problem. Also if anyone knows the command for the [y]es [n]one [a]ll thing that'd be greatly appreciated can't seem to just hit yes and replace a jpeg for sandbox for awhile so it won't fully install thanks in advance......ME

---

### Post by jadtech on 2012-05-09
go to the software center type in the search box alas midi choose click to un-install  that should take care of it .. 

if you are saying it is popping jup in boot up and you want that to stop go to the top bar  click the far right  icon looks like a gear on the menu click start-up applications  and remove alas midi from the list ...

just a side note if you are  using wubi in technicality you have nothing to format  since wubi is not on it own partition  though it is ubuntu it is running as a windows program

---

### Post by AceKinslayer on 2012-05-09
Wish I could but it pops up log before I can log into the gui side and runs I can't get to a software center to stop it. I have to have command codes for this I think

---

### Post by cariboo on 2012-05-10
You will have to stop the timidity-daemon before you can completely remove it.

Open a terminal and type:

```
ps ax | grep timidity
```

I don't have it installed here, but the output should look something like this:

```
ps ax | grep cupsd
  974 ?        Ss     0:00 /usr/sbin/cupsd -F
```

Note the number at the beginning o the line, that is call the ***pid*** or program id, you need to know the pid in order to stop the daemon. Of course it will be different for timidity. Once you have found the pid, in the terminal type:

```
sudo kill <pid>
```

this should stop timidity. the next thing to do is to completely remove the package:

```
sudo apt-get --purge timidity-daemon
```

The next time you reboot, you shouldn't see timidity starting. 

To find out more about the optional parametrs of the commands I gave you have a look at:

[LIST]
[*]man ps
[*]man apt-get
[/LIST]

Man pages can be your friend when you can't remember all of the options. It will probably take a bit to get your head around the way man pages are written, but once you do, they can be very helpful.

---

### Post by AceKinslayer on 2012-05-10
Thanks ok to expand on this you all know when ubuntu loads up it goes to the pre-menu part and it says click to go to ubuntu login, recovery ubuntu whatever and go to previous versions right after that before your sign in screen where the gear next to your name typically is it does that thing freezes up and just kind of dies there. To the person that said the terminal commands guess my question is gonna have to be does the recovery mode work for a terminal if not is there a way to tell it not to load alsa and let me in main til I can better resolve it. I've tried making myself super user and trying to kill the process but it's not running at that time so that's useless and I checked everywhere for a command to tell it to suspend its actions until a more favorable time. Lol I love linux os' but man when it has problems reversing it has to be just about the biggest pain in the world.:lolflag:

---

### Post by AceKinslayer on 2012-05-10
oh ya that's another problem that I'm having because for whatever reason when installed sandbox it wants to replace a jpeg it has in it's folders and I can't tell it yes no or inbetween I've tried yes, y, [y] [y]es and sudo all three on every option it asked for and for some reason none of them are acceptable so using sudo apt is useless til I find a way to make that part finally go through and finish. Which is aggrevating I don't even know what this option dialogue is called to look up how your supposed to tell it replace the file already

---

