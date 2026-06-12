---
title: "Maximum number of clients reached GTK-WARNING ** Cannot open display:  :0"
date: 2012-06-18
forum: General Help
---

### Post by wendallsan on 2012-06-18
Hi everyone,

I upgraded from 11.10 to 12.04 as soon as it was out of beta, and have been plagued by a problem ever since.  After my computer has run for a few hours (maybe around 4 or so), I can't open any new programs from the Unity Launcher.  If I try to open them from the command line (in the example below, I'm attempting to open Chrome), I get the following message:

Maximum number of clients reachedMaximum number of clients reached
(chromium-browser:29820): Gtk-WARNING **: cannot open display: :0

I'm unable to open any programs unless I close a currently open program (which I assume reduces the number of 'clients') or reboot my computer.  On reboot, it runs fine for a few hours again, then starts having this problem again.  I have 2 instances of 12.04 installed on my system and they both have this problem.  I'm running the 64 bit version of the OS on an AMD Phenom II X6 system w/ 4 gigs of ram.  Happy to share any other info about my system if there's hope I can get this fixed!  Let me know if anyone has seen this before . . .

---

### Post by hwttdz on 2012-06-18
I haven't seen that message before, but it does seem to be an x11 issue.  Probably more related to not freeing resources when clients exit than from having too many clients.  This thread:
[http://askubuntu.com/questions/4499/how-can-i-diagnose-debug-maximum-number-of-clients-reached-x-errors](http://askubuntu.com/questions/4499/how-can-i-diagnose-debug-maximum-number-of-clients-reached-x-errors)

might give you some ideas of where to poke around.  It looks like there are a few programs which might be culprits (thread mentions chrome and gnome-screensaver), so you could try using xscreensaver and firefox/midori/epiphany... for a little and see if that solves anything?

---

### Post by wendallsan on 2012-06-18
Thanks for the reply.  The issue is not specific to chrome (I just happened to be trying to open it for the example in my 1st post), but will happen with any apps as long as the machine runs for a while.  I usually have Eclipse, Firefox, Banshee, Deluge, and Filezilla running, and sometimes use Chrome for testing sites out, etc.  I'm beginning to suspect Wally (the wallpaper changer), as I installed it on both instances of Ubuntu that I've got when I upgraded both to 12.04.  I've disabled Wally and will see what happens . . .  maybe Wally is not releasing resources each time it changes a wallpaper, and that eventually stacks up and bogs down my system.  I'll post back later after I see if anything has improved.  I also have the python script referenced in your post, have run that, and will keep it handy if I run into problems again to see if it helps.

thanks!

---

### Post by ***J*** on 2013-03-18
I have the same problem. I don't use chrome or screensavers. My setup:
ubuntu 12.04 lts
8 gb memory
amd fx 8120 cpu
geforce gtx 550 ti graphics card
64-bit
1.5 tb hdd space

---

### Post by ***J*** on 2013-03-19
bump

---

### Post by ***J*** on 2013-03-20
bump

---

### Post by schragge on 2013-03-20
Well, this message usually means one of two things: either you're actually running too many apps or you've run out of file descriptors.
To check for the first, try ```
xlsclients
``` For the last, try
```
sudo lsof -U +c0|(printf 'PID%3suser%6sFD%6sinode command\n';awk 'NR>1{printf"%5d %-8s%5s%10d %s\n",$2,$3,$4,$8,$1}')
```
To only check how many apps / open FDs you've got, append *|wc -l* at the end of both commands:
```

xlsclients|wc -l
sudo lsof -U|wc -l

```

---

### Post by ***J*** on 2013-03-21
Thanks. I'll try these the next time this happens.

---

### Post by ***J*** on 2013-03-23
Haven't had this happen again yet (probably because I'm being more careful with my computer's resources) but I've noticed that occasionally when I have vlc or qbittorrent open for long enough and put xlsclients in a terminal I'll see multiple instances of them open. This contrasts with top that says there is only one instance of them open. Is this normal behavior?

---

### Post by ***J*** on 2013-03-24
bump

---

### Post by ***J*** on 2013-03-25
bump

---

### Post by ***J*** on 2013-03-26
bump

---

### Post by ***J*** on 2013-03-26
This happened again today, here are the results of terminal commands:

xlsclients|wc -l
42

sudo lsof -U|wc -l
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/john/.gvfs
      Output information may be incomplete.
1229

I had to close some programs to even be able to use these commands.

---

### Post by schragge on 2013-03-27
For comparison, this is what I get on my system
```

[color=green]$[/color] xlsclients|wc -l
[color=green]4[/color]
[color=green]$[/color] sudo lsof -U|wc -l
[color=green]95[/color]

```
The four clients being the browser and three terminal windows.

---

### Post by ***J*** on 2013-03-27
Is there a maximum amount of apps or file descriptors I can have open before this starts happening?

---

### Post by schragge on 2013-03-27
The maximum amount of X clients is 256. It's a hard limit, you cannot change it without recompiling the X server. Once upon a time Ubuntu carried [a patch]("http://bazaar.launchpad.net/%7Eubuntu-branches/ubuntu/precise/xorg-server/precise-updates/view/119/debian/patches/158_raise_maxclients.patch") that raised this number to 512, but it was [dropped]("http://bazaar.launchpad.net/%7Eubuntu-branches/ubuntu/precise/xorg-server/precise-updates/revision/120/debian/changelog") because of LP#[lpbug]326344[/lpbug].

I'm not sure how applications with multiple windows/tabs are accounted for. You can count them with
```
xwininfo -root -children|grep -o '[0-9]* children'
```

How to see the system-wide and per-user/per-process limits on open file descriptors is described [here]("http://www.cyberciti.biz/faq/linux-increase-the-maximum-number-of-open-files/"). How to change them -- [here]("http://cherry.world.edoors.com/CPZKoGkpxfbQ").

On my system
```
[COLOR=green]$[/COLOR] cat /proc/sys/fs/file-max
[COLOR=green]334099
$[/COLOR] ulimit -n
[COLOR=green]1024[/COLOR]
```

---

### Post by malabarth on 2013-06-06
I have the same problem! :/
I have to reboot!

I will investigate to find which app is taking all thos ressources! :)

---

### Post by VMC on 2013-06-06
@[wendallsan]("http://ubuntuforums.org/member.php?u=37567")[COLOR=#DD4814][COLOR=#000000],
[/COLOR][/COLOR][COLOR=#000000][/COLOR]

Maybe you have stuff left over from [COLOR=#000000]11.10 that might be the issue. Have you tried creating a new user and log in to see if it crashes.[/COLOR]

---

### Post by malabarth on 2013-06-06
I'm on a 13.04 fresh install! :/

---

### Post by ***J*** on 2013-06-07
This actually happened to me again today. Sometimes it will be obvious what's causing the problem, for example I'll open the system monitor and see that something is taking up a lot of cpu and close it. Other times like today it is less obvious since nothing is taking up a lot of cpu and I have ram free. For me I think what sometimes causes this problem is vlc. A trick I learned on another forum for this is to close vlc and delete the .conf file in /home/john/.config/vlc. This sometimes temporarily fixes the problem for me for some reason even if vlc isn't taking up a lot of cpu. Aside from this I am still forced to restart the computer after a while unfortunately. If someone can find out other solutions for this feel free to post them.

---

### Post by malabarth on 2013-06-07
It happend again!
I just found what is the cause:
 - when restarting dbus service, everything is working again!

```
malabarth@malabarth:~$ sudo lsof -U|wc -l
696
malabarth@malabarth:~$ xlsclients|wc -l
39
```

---

### Post by voron-phys on 2013-08-27
Hi! I had the same error in Ubuntu 12.04. I have increased the maximum limit of opened files number by creating the following file:
```
voron@voron-desktop ~ $ cat /etc/security/limits.d/nofile-all.conf
#<domain>      <type>  <item>         <value>
*               soft    nofile        4096
*               hard    nofile        4096
root            soft    nofile        4096
root            hard    nofile        4096
```
The default value was:
```
voron@voron-desktop ~ $ ulimit -n
1024
```

After Ubuntu rebooting, I have launched a lot of apllications (couple scientific programs; Chromium, Firefox and Opera browsers with extensions; Open Office applications; some file viewers and image creators and so on) and reached this values without any errors:
```
voron@voron-desktop ~ $ sudo lsof -U | wc -l; xwininfo -root -children | wc -l; xlsclients | uniq -c | wc -l; xlsclients | wc -l
1088
322
62
94

```
So, I hope that the problem was solved, but I can not claim it for sure yet. This must be checked more durable :)

---

### Post by Gannin on 2013-09-07
I have this same problem.  I had a fresh install of Ubuntu 12.10 and after a few months of normal use including shutting down the computer every night, I started getting the maximum number of clients message.  The only way around it was to log out and log back in.

Now I'm using a clean install of Lubuntu 13.04, and I've been using it for about three days, and I just started getting the maximum number of clients message again.  On average, both in Ubuntu 12.10 and in Lubuntu 13.04 I was, and am, getting that message about five times a day, and each time I have to log out and log back in.

The only possible explination I've been able to find for this was this particular line from a bug report on Launchpad:  "However, in this case, there is a bug in the ATI drivers which causes users to hit this limit sooner due to elevated number of windows created and/or not released correctly."

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/910539](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/910539)

As I am using an AMD graphics card, and considering the lower quality of AMD software these days, it wouldn't surprise me if the AMD graphics card and graphics driver is the issue.

If it is indeed the issue, I hope the upcoming AMD graphics driver will fix the issue.

---

