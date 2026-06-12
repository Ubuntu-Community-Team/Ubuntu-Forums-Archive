---
title: "greeter crash"
date: 2006-06-18
forum: General Help
---

### Post by s_h_a_d_o_w_s on 2006-06-18
whenever I boot-up, a pop-up says: The greeter application seems to be crashing, attempting to start another one.      

How can I fix this?

---

### Post by Shampyon on 2006-07-01
Bump, because I just developed this problem.
Everything was fine until just a few minutes ago. I changed the default OS from WinXP back to Ubuntu. I'd reformatted an NTFS partition to FAT32 so I could read it from Dapper, but it refused to mount.

I tried to change the screen resolution from the max down to 1080x760, and it logged me out. I tried to log in, but the greeter kept crashing and restarting after I input my name and password. It just keeps looping like that, over and over.

---

### Post by Shampyon on 2006-07-02
I managed to get into Ubuntu through the Recovery option in GRUB. I thought that maybe the problem was a login theme I installed, but I can't get access to the login manager through the menu.
The partition I had trouble with before is now mounted and working fine (although I can't get write permission to it, for some reason, though I formatted it to ext3). I just can't log in to Ubuntu properly.

It tells me that the greeter crashed, it'll try another one. I input my name and password, and it goes to the black and white command line state. I tried changing the graphics driver (sudo dpkg-reconfigure xserver-xorg), but while I'm going through it's options the login greeter pops up again. I'll input my ame and pass again, and it returns to the command line options screen, right back where I was before it interrupted me...

This is starting to really annoy me. I'd just gotten Dapper running just they way I want it (theme, login, programs, everything) and this just comes right out of left field. Is there any trick to fixing this up? Will I have to reinstall and re-download all the programs and updates I've gotten since my first install? Is there some kind of recovery program on the install disc I can use, like the recovery option on WinXP?

Like I said, it's starting to really annoy me. Not enough to give up, though - it'll take more than a setback like this to drive me away from Ubuntu.

Edit: I just remembered that I ran the Simple Backup Config utility yesterday. Would running Simple Backup Restore fix my problem by reverting things back to the state they were yesterday (like XP's Restore Points)? Or would that just mess things up even further?

---

### Post by Shampyon on 2006-07-02
I'm getting a new error message now:

[i]The display server has been shut down about 6 times in the last 90 seconds. 
It is likely that soething bad is going on. 
Waiting for 2 minutes before trying again on display :0.[/i]

---

### Post by energed on 2006-07-02
Hi, i just thought that this information could help. I noticed that login option 'Enable accessible login' causes this error in my setup. I just disabled that option and it started to work without crashing.

---

### Post by Shampyon on 2006-07-02
Do you know how to do that from the command line? Because I can only use a GUI in recovery mode, and the login menu item isn't available through it.

*Edit: *I've tried using the Simple Backup Restore option. No dice. It gave me back the default login page, and that's it. I was able to get into my system for a very short while at a lower resolution (I still don't know how I did it), but haven't been able to get back in since. It looks like I'll have to reinstall everything from scratch. Is there anyone with any clue to what I can do to fix this, so I don't have to go through the process of downloading all those updates and programs again?

---

### Post by energed on 2006-07-06
Sorry Shampyon i just made my first ubuntu installation 3 days ago. So i really dont know.

---

### Post by Shampyon on 2006-07-06
Don't sweat it. I reinstalled and made sure not to enable the accesible login, and everything's been running smoothly. Even got me a bunch of new themes and wallpapers to make it all extra pretty :)

---

### Post by tehnad on 2006-07-13
I am still siting here in amazement about the simple solution to the gnome greeter issue.  What I did last night was go to System->Administration->Login Window and selected another login window.  The options I went through all came from Ubuntu with no outside stuff from myself.  I selected a new login window and rebooted bringing me to the issue of the greeter crashing and it reloading another one.  I went back in and set everything back to default.  This did not resolve the situation.  I was getting pretty worried for a minute and decided to come here for a solution.  Turning off "Enable accessible login" worked like a champ.  How in the world did you discover that?
     Tell you what though, I give to you a gold smiley star :KS Thanks for your post.  I am really glad I did not need to spend the next several hours trying to figure it all out.

---

### Post by cikic on 2008-01-21
Since I have the same problem and no graphical front end I am wondering where (in which config-file) the "Enable accessible login" setting is set?

Thanks
Christian

---

### Post by punkybouy on 2008-02-16
You might have to edit the /etc/gdm/gdm.conf-custom file.  Below is the part of mine that does the work, see how yours compares.

[daemon]

[security]

[xdmcp]

[gui]

[greeter]
GraphicalThemedColor=#657d3b
GraphicalTheme=morning
DefaultWelcome=false
Welcome=Welcome to %n

[chooser]

[debug]

[servers]

---

### Post by punkybouy on 2008-02-16
I installed a login theme last night that hosed this file and produced the same greeter message.  Since I did not get a GUI I had to do a ctrl+alt+F1 and log in to a prompt and edit this file manually.

---

### Post by AvengingAngel718 on 2008-03-09
i need to know how you fixed this. i just installed a new login window the other day and i havent been able to log in since. this is the only change i made to my login options, what exactly do you have to do to fix this from the command line, and can it be fixed from the live cd?

---

### Post by almostdvs on 2008-04-03
> **cikic said:**
> Since I have the same problem and no graphical front end I am wondering where (in which config-file) the "Enable accessible login" setting is set?[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/211241]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/211241")

Thanks
Christian

i had same problem, after recieving help on irc that fixed i submitted crash to launchpad which showed me this.

[link]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/211241")


so press ctl+alt+f1 to switch to terminal, login  and then run

sudo /etc/init.d/gdm stop

startx

This is just a workaround that will let you get to your desktop as to further prevent it im not positive.

---

### Post by overdog_001 on 2008-06-12
I know it's been a long time since this was posted, but there never was a satisfactory answer.

So I decided to post my answer, so when some other poor soul searches for the greeter crash, they can see this and not have to wait 2 years for an answer.

Here is what worked for me, when my greeter crashed:

1.  Work through the recovery mode, letting the greeter crash, until you can get to a command line login prompt for tty.  Tip:  If you can't get the crash to stop, try using Ctrl-Alt-Backspace to kill the X server.  After several times, you'll get a message that complains that the display crashed too many times, and it'll drop to a command prompt.

2.  From your command line, edit the gdm configuration file with nano, an easy command line editor.  (No quips about VI here, nano is easier for newbies.)

    cd /etc/gdm
    sudo nano gdm.conf

3.  Scroll down to find the greeter selection section.  It'll look like this:

    # The greeter for attached (non-xdmcp) logins.  Change gdmlogin
    # to gdmgreeter to get the new graphical greeter.
    Greeter=/usr/lib/gdm/gdmgreeter

4.  Comment out that last line by prefixing it with a "#".  Then make a new line right below it, like this:

    Greeter=/usr/lib/gdm/gdmlogin

5.  Save changes and reboot.

When it reboots, you will see gnome using the old, default resolution and a different looking login screen.  If you do, it's because the "recovery" mode overwrote the other conf with default settings.  Once you're logged in again, you can change it back to whatever you want.

---

### Post by sbUdUbU on 2008-07-01
Hi everybody, 
I'm becoming mad, i have all my thesis stuff on my ubuntu partition but thank to this "greeter crash" i cannot access to that. :confused:
Everything began when "greeter crash ...bla bla" appeared, just because the previous day i put a different login window theme: i read all about that, i tryed to change /etc/gdm/gdm.comf file, to reconfigure xserver-xorg and moreover i cannot access my desktop to change "enable accessible login" option...
nothing! now all i can see is my screen changing colour continously, but, a very strange thing happens: i can hear the typical ubuntu startup sound and if i put my user name, wait a couple of seconds, and then i put my password i can hear also the other longer song, like i could access the system normally..... so, no more greeter crash, but just a crazy screen changing colour and a "blind" desktop... 
How can i fix that?? 
please, my thesis dipends on that...

---

### Post by macroshaft on 2008-07-03
That sounds to me like you've fixed the problem but for some reason your graphics settings have gone screwy. Use the above advice in the previous posts to get to a prompt and try typing

sudo dpkg-reconfigure -phigh xserver-xorg

it'll step you through a few basics steps to set up your graphics again and may well kick the system back on it's proverbial rails!

---

### Post by sbUdUbU on 2008-07-13
> **macroshaft said:**
> Use the above advice in the previous posts to get to a prompt and try typing

sudo dpkg-reconfigure -phigh xserver-xorg

it'll step you through a few basics steps to set up your graphics again and may well kick the system back on it's proverbial rails!

Neither this worked... I think it's something about my graphical card: since the very first time ubuntu told me that the graphical drivers are not freeware and there can be some problems.

---

### Post by sbUdUbU on 2008-07-24
Just wanted to let you know that I fixed the problem by myself, finally...
The solution was to edit the file /etc/X11/xorg.conf and put the correct informations about my graphical card in the proper Section "Device": with the first reboot I entered the low graphic modality (don't remember the real name) but it was enough to change, correct and update everything I needed, and now it works like always!! :)
thanks to everyone anyway

---

