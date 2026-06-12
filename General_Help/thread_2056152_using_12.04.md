---
title: "using 12.04"
date: 2012-09-10
forum: General Help
---

### Post by kelpie_canada on 2012-09-10
I upgraded my 4 year old vostro 1400 with ubuntu 12.04. I followed all the instructions and restarted my computer. When it came back it told me it wasnÈt compatible with the network I was using which is cogeco cable. So I thought that I would turn it off and back on when I did and I entered the password that I have been using for 4 years it would not accept my password and opened the terminal window.

How do I get back into my computer and why wonèt it accept the netÉ

---

### Post by opensshd on 2012-09-10
How did you install? From cd/dvd/usb?

Do you see the Ubuntu login screen, and that is where you enter the password it is not accepting?

---

### Post by kelpie_canada on 2012-09-10
> **opensshd said:**
> How did you install? From cd/dvd/usb?

Do you see the Ubuntu login screen, and that is where you enter the password it is not accepting?

my system had upgrades and it was at the top of the upgrades.

yes it came up with the loginscreen with the background I had put in and it will not accept my password

---

### Post by opensshd on 2012-09-10
Ok, so you installed a distribution upgrade from a previous version of Ubuntu?

Can you log in to the terminal session with either your user account or the root user account?

---

### Post by kelpie_canada on 2012-09-10
> **opensshd said:**
> Ok, so you installed a distribution upgrade from a previous version of Ubuntu?

Can you log in to the terminal session with either your user account or the root user account?

I have had ubuntu in this computer since I got it and have always upgraded from the update manager with no problem. 

the terminal shows katielaptop but it will not take my password. I do not know what the root user account is

---

### Post by opensshd on 2012-09-10
Is it a command prompt (/$) or login prompt (login: ) you see?

---

### Post by kelpie_canada on 2012-09-10
> **opensshd said:**
> Is it a command prompt (/$) or login prompt (login: ) you see?

it shows in the terminal (kpringle@katie-laptop:È$) and acurser
but I do not know what to type in if I put in just the password it says command not found

---

### Post by opensshd on 2012-09-10
Yeah, you are at the command prompt. The system accepted your login and password and when it tried to load the window manager, crashed. At least this is my theory :)

So you can try entering the command "startx" to try and start the window manager again... it will likely fail again, but it may show you output in that terminal window that can help diagnose the problem.

---

### Post by kelpie_canada on 2012-09-10
> **opensshd said:**
> Yeah, you are at the command prompt. The system accepted your login and password and when it tried to load the window manager, crashed. At least this is my theory :)

So you can try entering the command "startx" to try and start the window manager again... it will likely fail again, but it may show you output in that terminal window that can help diagnose the problem.

it says X:user not authorized to run the X server, aborting
X IO:fatal IO error 11 on X server(resource temporarily unavailable)on X server then quote :0 quote
after 7 requests (7 known processed) with 0 events remaining
then back to original kpringle@katie-laptop

---

### Post by opensshd on 2012-09-10
try this:

sudo /etc/init.d/lightdm start

---

### Post by kelpie_canada on 2012-09-10
> **opensshd said:**
> try this:

sudo /etc/init.d/lightdm start

Ityped that in and got back [sudo] password for kpringle:

but when I typed in my password I got
sudo: /etc/init.d/lightdm: command not found

---

### Post by newb85 on 2012-09-10
In case it really is a problem with your password, follow [psychocat's tutorial on resetting passwords]("http://www.psychocats.net/ubuntu/resetpassword").

---

### Post by opensshd on 2012-09-10
Ok, what window manager are you using?

It's not a password issue.

---

### Post by kelpie_canada on 2012-09-10
> **opensshd said:**
> Ok, what window manager are you using?

It's not a password issue.

I have no idea what a window manager is. I bought the computer from Dell and took it to a man in town who fixes and sells ubuntu and he installed ubuntu for me.

---

### Post by opensshd on 2012-09-10
Ok... I'd try the following steps.

Reboot the machine - see if it works as normal. Sometimes the extra reboot after kernel upgrades are surprisingly helpful :)

If you wind up in the same spot, you might consider trying to update your machine:

sudo apt-get update

sudo apt-get upgrade

then you could try installing gnome-shell, alongside whatever window manager that is presently not working by doing this:

sudo apt-get install gnome-shell

and try starting it by:

sudo /etc/init.d/lightdm start

If that doesn't work, then we have a good idea of where to look next. You can remove gnome-shell later by the following command:

sudo apt-get purge gnome-shell

sudo apt-get autoremove

sudo apt-get clean

I have to step out for a while but will check and see how you're making out when I return. Good luck.

---

### Post by kelpie_canada on 2012-09-12
[COLOR="Red"][/COLOR]> **opensshd said:**
> Ok... I'd try the following steps.

Reboot the machine - see if it works as normal. Sometimes the extra reboot after kernel upgrades are surprisingly helpful :)

If you wind up in the same spot, you might consider trying to update your machine:  [COLOR="red"]this did
n't work[/COLOR]
sudo apt-get update   [COLOR="red"]error message[/COLOR]

sudo apt-get upgrade  [COLOR="red"]error message[/COLOR]

then you could try installing gnome-shell, alongside whatever window manager that is presently not working by doing this:

sudo apt-get install gnome-shell [COLOR="red"]this gave me the suggestion to try apt-get --fix-missing which I did and that gave me 2 lists of options but I don't know which option I need to use. The last line is "See the apt-get(eight), sources.list(5) and apt.conf(5)manual pages for more information and options,[/COLOR]


and try starting it by:[COLOR="red"]I have not tried to start it again yet[/COLOR]
sudo /etc/init.d/lightdm start

If that doesn't work, then we have a good idea of where to look next. You can remove gnome-shell later by the following command:

sudo apt-get purge gnome-shell

sudo apt-get autoremove

sudo apt-get clean

I have to step out for a while but will check and see how you're making out when I return. Good luck.

I had to wait to get the use of a laptop sorry for the delay in response

---

### Post by opensshd on 2012-09-12
hmmm... weird...

what does this do:

sudo apt-get dist-upgrade 

can you post the exact error message this gives you?

What are the two options you are given after apt-get --fix-missing?

---

### Post by kelpie_canada on 2012-09-12
[COLOR="Red"][/COLOR]> **opensshd said:**
> hmmm... weird...

what does this do:

sudo apt-get dist-upgrade 

can you post the exact error message this gives you? [COLOR="Red"]it  asked for my password
gave me this message: reading package lists... Done
                      Building dependency tree
                      Reading state information... Done
                      Calculating upgrade... Done
                      0 upgraded, 0 installed, 0 to remove and 0 not upgraded[/COLOR]

What are the two options you are given after apt-get --fix-missing? [COLOR="Red"]it wasn't 2 options it was 2 sets of options with as many as 9 choices in each set [/COLOR]
this is what I got

---

### Post by opensshd on 2012-09-12
Ok... dis upgrade works...

can you paste the output of these two commands you said gave you an error please?

sudo apt-get update 

sudo apt-get upgrade

---

### Post by kelpie_canada on 2012-09-12
> **opensshd said:**
> Ok... dis upgrade works...

can you paste the output of these two commands you said gave you an error please?

sudo apt-get update [COLOR="Red"] I can't paste I am on a different laptop The error meesage is so long and went by so fast that all I can give you are the last few lines:
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/precise/InRelease](http://archive.canonical.com/ubuntu/dists/precise/InRelease)
W:Failed to  fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/InRelease](http://security.ubuntu.com/ubuntu/dists/precise-security/InRelease)
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/precise/Release.9P9](http://archive.canonical.com/ubuntu/dists/precise/Release.9P9)
Could not resolve 'archive.canonical.com'
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/Release.9P9](http://security.ubuntu.com/ubuntu/dists/precise-security/Release.9P9)
Could not resolve 'security.ubuntu.com'
W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/precise/Release.9P9](http://ca.archive.ubuntu.com/ubuntu/dists/precise/Release.9P9)
Could not resolve 'ca.archive.ubuntu.com'
W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.9P9](http://ca.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.9P9)
Could not resolve 'ca.archive.ubuntu.com'
W: some index files failed to download. They have been ignored or old ones used insted.
W: Duplicate sourdes.list entry [http://archive.canonical.com/ubuntu/precise/partner](http://archive.canonical.com/ubuntu/precise/partner) i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary_i386_Packages)[/COLOR]
sudo apt-get upgrade

This is what I could copy from the first cammand I will try the second

---

### Post by opensshd on 2012-09-12
Ok, do you have an internet connection when you try these commands?

ifconfig -a

that command will show you network interfaces.

---

### Post by kelpie_canada on 2012-09-12
> **opensshd said:**
> Ok... dis upgrade works...

can you paste the output of these two commands you said gave you an error please?

sudo apt-get update 

sudo apt-get upgrade

it gave me the same message as before: reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 installed, 0 to remove and 0 not upgraded

---

### Post by opensshd on 2012-09-12
Ok, you have a problem with your /etc/apt/sources.list file, I think.

This is what my sources.list file looks like:

```

#deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/main/binary-i386/

#deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
#deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ precise universe
deb http://ca.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ca.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main

```

You can view yours by entering the command:

cat /etc/apt/sources.list|more

And you can edit it with:

sudo vim.tiny /etc/apt/sources.list

or:

sudo vi /etc/apt/sources.list

You can read up on how to use the command line text editor by typing:

man vi

Do you see any differences between my sources.list and yours?

---

### Post by kelpie_canada on 2012-09-12
> **opensshd said:**
> Ok, do you have an internet connection when you try these commands?

ifconfig -a

that command will show you network interfaces.

my computer will not recognize my wireless modem

this is what I got typing in the above command

eth0 Link encap:Ethernet HWaddr 00:1e:c9:03:bf:60
BROADCAST MULTICAST MTU:1500 Metric:1
RX Packets:0 errors:0 dropped:0 overruns:0 frame:0
TX Packets:0 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interupt:17

Io Link Encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX Packets:356 errors:0 dropped:0 overruns:0 frame:0
TX Packets:356 0 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:0
RX bytes:28480 (28.4 KB) TX bytes:28480 (28.4 KB)

it took a while to type but here it is

---

### Post by opensshd on 2012-09-12
Ok, can you use a wired network connection? If you can plug in an ethernet cable to your modem/router then type:

sudo ifconfig eth0 up

and

sudo dhclient eth0 

You should get internet connectivity with that so when you run apt-get commands, it can speak to the repository server.

If you get no problems getting an ip address with dhclient, then try rerunning the command:

sudo apt-get update

See if anything starts working then :)

---

### Post by kelpie_canada on 2012-09-12
> **opensshd said:**
> Ok, you have a problem with your /etc/apt/sources.list file, I think.

This is what my sources.list file looks like:

```

#deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/main/binary-i386/

#deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
#deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ precise universe
deb http://ca.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ca.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main

```

You can view yours by entering the command:

cat /etc/apt/sources.list|more  [COLOR="Red"]this told me no such file exists[/COLOR]

And you can edit it with:

sudo vim.tiny /etc/apt/sources.list [COLOR="Red"]this gave me a blank window with "/etc/pt/sources.list" [New DIRECTORY][/COLOR]

or:

sudo vi /etc/apt/sources.list

You can read up on how to use the command line text editor by typing:

man vi

Do you see any differences between my sources.list and yours?

Now what do I do?

---

### Post by opensshd on 2012-09-12
First try running 

sudo apt-get update

after you get your network running.

check and see if you have an ip address after running:

sudo dhclient eth0 

by typing,

ifconfig -a

you'll probably see a 192.168.xxx.xxx number in there somewhere if it worked.

If you are still having problems reaching the repositories, then we'll inspect your sources.list file for problems. It should look much like mine, with the possible exception of the backports - you are 64bit right?

cat /etc/apt/sources.list | more

that will display your list.

---

### Post by kelpie_canada on 2012-09-12
> **opensshd said:**
> Ok, can you use a wired network connection? If you can plug in an ethernet cable to your modem/router then type:

sudo ifconfig eth0 up [COLOR="Red"]i got no response with this command[/COLOR]



sudo dhclient eth0 [COLOR="Red"]and this one sent back Rather than invoking init scripts through /etc/init.d, use the service(eight) utility, e.g. service smbd reload
Since the script you are attempting to invoke has been converted to an  Upstart job, you may also use the reload (eight) utility, e.g. reload smbd[/COLOR]

You should get internet connectivity with that so when you run apt-get commands, it can speak to the repository server.

If you get no problems getting an ip address with dhclient, then try rerunning the command:

sudo apt-get update

See if anything starts working then :)

I am now back to the same line asking for input

---

### Post by opensshd on 2012-09-12
try this:

sudo /etc/init.d/networking restart

or

sudo start networking

^ I think that is proper now ><

---

### Post by kelpie_canada on 2012-09-12
> **opensshd said:**
> try this:

sudo /etc/init.d/networking restart

or

sudo start networking

^ I think that is proper now ><

bash: no such file or directory

---

### Post by kelpie_canada on 2012-09-12
> **opensshd said:**
> try this:

sudo /etc/init.d/networking restart

or

sudo start networking

^ I think that is proper now ><

the second one says networking stop/waiting and then the input line again

---

### Post by opensshd on 2012-09-12
> **kelpie_canada said:**
> the second one says networking stop/waiting and then the input line again

Ok good, linux only complains when stuff doesn't work, when it's quiet it's good :) try this:

ifconfig -a

Do you have an IP address now?

---

### Post by kelpie_canada on 2012-09-12
> **opensshd said:**
> Ok good, linux only complains when stuff doesn't work, when it's quiet it's good :) try this:

ifconfig -a

Do you have an IP address now?

this is what it gave me
eth0 Link encap:Ethernet HWaddr 00:1e:c9:03:bf:60
inet addr:192.168.2.12 Bcast:192.168.2.255 Mask:255.255.255.0
inet6 addr: fe80::21e:c9ff:fe03:bf60/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX Packet:2799 error:0 dropped:0 overruns:0 frame:0
TX Packets:104 error:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:1000
RX bytes:446071 (446.0 KB) TX bytes:14527 (14.5 KB)

Io Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:host
UP LOOPBACK RUNNING MTU:16436 Metric:1
Rx packets:20 errors:0 dropped:0 overruns:0 frame:0
Tx packets:20 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:0
RX bytes:1456 (1.4 KB) TX bytes:1456 (1.4 KB)

---

### Post by opensshd on 2012-09-12
Yes good. the number beginning in 192.168 is your local IP address. So you should have internet access now.

try a 

sudo apt-get update 

and see if it works for you now or gives you the same output :) If it's working, go ahead and try

sudo apt-get upgrade

---

### Post by kelpie_canada on 2012-09-12
> **opensshd said:**
> Yes good. the number beginning in 192.168 is your local IP address. So you should have internet access now.

try a 

sudo apt-get update 

and see if it works for you now or gives you the same output :) If it's working, go ahead and try

sudo apt-get upgrade

it ran through a long list of something and the last line says You may want to run apt-get update to correct these problems
Should I still try the second command

---

### Post by opensshd on 2012-09-12
oh sorry what?!

you ran sudo apt-get update and it said to run the same command? Or did it say to run upgrade?

---

### Post by opensshd on 2012-09-12
In that long line of stuff, was it saying 'hit' at the beginning of every line or something else?

---

### Post by kelpie_canada on 2012-09-12
> **opensshd said:**
> In that long line of stuff, was it saying 'hit' at the beginning of every line or something else?

some lines say get and some line say hit

it wanted me to run apt-get update to correct some problems

---

### Post by opensshd on 2012-09-12
Give me a minute... it's either a keyring issue or a sources.list duplicate issue i think.

If you could do this:

cat /etc/apt/sources.list | more

and tell me if you see any duplicate entries that are not commented out

(commented out means: there isn't a # sign starting the line, those lines 
are disregarded)

---

### Post by kelpie_canada on 2012-09-13
> **opensshd said:**
> Give me a minute... it's either a keyring issue or a sources.list duplicate issue i think.

If you could do this:

cat /etc/apt/sources.list | more

and tell me if you see any duplicate entries that are not commented out

(commented out means: there isn't a # sign starting the line, those lines 
are disregarded)

i ran sudo apt-get upgrade and it listed a bunch of stuff told me what would be added and what would be removed and  asked me if I wanted to continue so I said yes and it is  now doing what ever it does the lines are saying unpacking something followed by preparing to replace the same thing

---

### Post by kelpie_canada on 2012-09-13
there is now a list of setting up things followed by Processing triggers for libc-bin...
Idconfig deferred proccessing now taking place and then the input line

---

### Post by opensshd on 2012-09-13
Ok.. lets go with that then :) seems to be working eh?

try:

sudo apt-get dist-upgrade

---

### Post by kelpie_canada on 2012-09-13
> **opensshd said:**
> Ok.. lets go with that then :) seems to be working eh?

try:

sudo apt-get dist-upgrade

it says
reading package list: done
building dependency tree
reading state information: done
calculating upgrade: done
The following NEW packages will be installed:linux headers and a few more linux
The following packages will be upgraded:more linux header and generic linux
4 upgraded, 4 newly installed 0 to remove and 0 not upgraded
Need to get 51.6 MB of archives
After this operation 191 MB of additional disk space will be used 
Do you want to continue
I said yes

---

### Post by opensshd on 2012-09-13
Very good ^ ^

If it completes without errors, you'll need to reboot the machine. See if you can login to it normally.

If it falls back to the same command line, restart your network with:

sudo start networking

And we'll go from there ;)

oh, and you can reboot with the command:

sudo reboot

=]

---

### Post by kelpie_canada on 2012-09-13
it says A new version of /boot/grub/menu.list is available, but the version installed currently has been locally modified.
What would you like to do about menu.list?
install the package maintainer's version
[COLOR="Red"]keep the local version currently installed[/COLOR]
show the difference between the versions
show a side-by-side difference between the versions
show a three-way difference between available versions
do a 3-way merge between vailable versions (experimental)
start a new shell to examine the situation
the red one is highlighted on the screen so I guess that is the one I should choose right

---

### Post by opensshd on 2012-09-13
I would choose package maintainers version if you aren't multibooting, meaning, more than one operating system on that machine.

---

### Post by kelpie_canada on 2012-09-13
> **opensshd said:**
> I would choose package maintainers version if you aren't multibooting, meaning, more than one operating system on that machine.

the computer wouldn't let me change my choice all I could do was type in ok and hit enter
Now it found what it was looking for and has updated /boot/grub/menu.list
it set up the linux generic headers and other linux  and now it is waiting for a command should I reboot now?

---

### Post by opensshd on 2012-09-13
Yah, if you're back to the prompt, no errors?

type

sudo reboot 

=] *cross my fingers* hehehe

---

### Post by kelpie_canada on 2012-09-13
> **opensshd said:**
> Yah, if you're back to the prompt, no errors?

type

sudo reboot 

=] *cross my fingers* hehehe

well we are right back to the terminal window again

Now what

---

### Post by opensshd on 2012-09-13
k, lets try some things here...

start networking:

sudo start networking

Then, lets just see if we can get an intermediate/alternate desktop running by:

sudo apt-get install gnome-shell lightdm

if that completes successfully, give this a try:

sudo /etc/init.d/lightdm start

If you get to a login screen, before you login with your username and password just check for a button that will let you choose what window manager it loads - we want gnome, then login.

---

### Post by kelpie_canada on 2012-09-13
> **opensshd said:**
> k, lets try some things here...

start networking:

sudo start networking[COLOR="Red"]this came back with waiting[/COLOR]

Then, lets just see if we can get an intermediate/alternate desktop running by:

sudo apt-get install gnome-shell[COLOR="Red"]ran this a lot of stuff went by ending with failed to fetch some things and I may want to run apt-get update to correct these problems and 
E: unable to fetch some archives, try running apt-get update or apt-get --fix-missing[/COLOR]

if that completes successfully, give this a try:

sudo /etc/init.d/lightdm start

If you get to a login screen, you can login with your username and password, but just check for a button that will let you choose what window manager it loads - we want gnome

so there we are at the begining again.

---

### Post by opensshd on 2012-09-13
Not really at the beginning, I am pretty sure you have a duplicate entry in your sources.list and/or a keyring issue happening. We are diagnosing the problem a bit at a time :)

Do you have an install disk for ubuntu 12.04? could you download and burn a ubuntu 12.04 start disk? That would be helpful!

There are several rememdies to these problems, just trying to find the one that will be easiest for you to execute with limited command line experience... it can be tricky if you have never worked on the command line before ;)

If we can create an install disk, we have better options. If we are still working from the command line, I need to come up with a wget command to restore your sources.list file or something...

---

### Post by opensshd on 2012-09-13
Also, can you tell me the output of (need to know arch - 32 or 64 bit)

uname -a

And can you type in

startx

and see if you get to a desktop or any error messages?

---

### Post by kelpie_canada on 2012-09-13
> **opensshd said:**
> Not really at the beginning, I am pretty sure you have a duplicate entry in your sources.list and/or a keyring issue happening. We are diagnosing the problem a bit at a time :)

Do you have an install disk for ubuntu 12.04? could you download and burn a ubuntu 12.04 start disk? That would be helpful!

There are several rememdies to these problems, just trying to find the one that will be easiest for you to execute with limited command line experience... it can be tricky if you have never worked on the command line before ;)

If we can create an install disk, we have better options. If we are still working from the command line, I need to come up with a wget command to restore your sources.list file or something...

 I don't have a disk and I can't burn one but it is after 1 AM here and my eyes are starting to blur so I appreciate your help. Maybe if you sleep on the problem we can try again tommorow but for now I have to get some sleep.

---

### Post by opensshd on 2012-09-13
Sure no problem.

Also you could try 

sudo apt-get --fix-broken
and
sudo apt-get --fix-missing

and let me know what it says there too, whenever you come back to it is just fine ;)

---

