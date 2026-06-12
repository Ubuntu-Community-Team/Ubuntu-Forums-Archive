---
title: "Adept problems in Kubuntu"
date: 2006-05-10
forum: General Help
---

### Post by jude254 on 2006-05-10
Hi everyone,
Im new to Kubuntu, have been using it now for about 3 weeks, and need to solve a few things.
I have a problem with adept, that doesnt let me find all the packages I want. I guess I have to update all the repositories. What I have done is enable all the repositories in the manage repositories dialog, and  then do sudo apt-get upate from the terminal.

First of all is here what I get in the manage repositories dialog:


[B]deb    cdrom: [KUBUNTU 5.10 _BREEZY BADGER_ -Release 1386 (20051012)]/                breezy             main restricted
(separator)
(separator)
comment             #Uncomment the following two lines to fetch updated software from the network
deb              [http://it.archive.uubntu.com/ubuntu](http://it.archive.uubntu.com/ubuntu)                                                                  breezy updates     main restricted
deb-src        [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu)                                                                  breezy updates     main restricted
(separator)
comment    ##Uncomment the following two lines to add software from the universe repository
comment    ##NB software from this repository is entirely unsupported by the ubuntu team
comment    ## and may not be under a free license. Please satisfy yourself as your rights to use the software. Also please note the software in universe will not receive any review or updates from the Ubuntu security team
deb      [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu)                                                                          breezy                    universe multiverse
deb src  [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu)                                                                        breezy                     universe multiverse
(separator)
comment ## Uncomment the following two lines to add software from the backports repository
comment   ## NB software from this repository may not have been tested as extensively as that contained in the main release. Although it includes newer versions of some apps which may provide useful features. 
comment   ## also please note that software in backports will not receive any review or updates from the kubuntu security team
deb             [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu)                                                                 breezy backports       main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)                                                                          breezy backports         main restricted universe multiverse
(separator)
deb      [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu)                                                                            breezy security                 main restricted
deb-src   [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu)                                                                         breezy security                  main restricted
(separator)
deb                [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu)                                                                  breezy security                 universe multiverse
DEB-SRC     [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu)                                                                   breezy security                universe multiverse
(separator)[/B]


I dont know why I have all those comments.  It doesnt look normal to me.
Secondly, when I do fetch updates, nothing changes. If I do sudo apt-get update it gives me this script:(check end of script for italian translation)



[B]Err [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy Release.gpg
  risoluzione di 'it.archive.ubuntu.com' temporaneamete fallita
Err [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates Release.gpg
  risoluzione di 'it.archive.ubuntu.com' temporaneamete fallita
Err [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports Release.gpg
  risoluzione di 'it.archive.ubuntu.com' temporaneamete fallita
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg
  risoluzione di 'security.ubuntu.com' temporaneamete fallita
Impossibile ottenere [http://it.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg](http://it.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg)  risoluzione di 'it.archive.ubuntu.com' temporaneamete fallita
Impossibile ottenere [http://it.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg](http://it.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg)  risoluzione di 'it.archive.ubuntu.com' temporaneamete fallita
Impossibile ottenere [http://it.archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg](http://it.archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg)  risoluzione di 'it.archive.ubuntu.com' temporaneamete fallita
Impossibile ottenere [http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg)  risoluzione di 'security.ubuntu.com' temporaneamete fallita
Lettura della lista dei pacchetti in corso... Fatto
W: Impossibile controllare la lista dei pacchetti sorgente [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/it.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Impossibile controllare la lista dei pacchetti sorgente [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/it.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Impossibile controllare la lista dei pacchetti sorgente [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/it.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Impossibile controllare la lista dei pacchetti sorgente [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/it.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Impossibile controllare la lista dei pacchetti sorgente [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/it.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Impossibile controllare la lista dei pacchetti sorgente [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/it.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Impossibile controllare la lista dei pacchetti sorgente [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/it.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Impossibile controllare la lista dei pacchetti sorgente [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/it.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Impossibile controllare la lista dei pacchetti sorgente [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/it.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Impossibile controllare la lista dei pacchetti sorgente [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/it.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Impossibile controllare la lista dei pacchetti sorgente [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Impossibile controllare la lista dei pacchetti sorgente [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Impossibile controllare la lista dei pacchetti sorgente [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Impossibile controllare la lista dei pacchetti sorgente [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: È consigliabile eseguire apt-get update per correggere questi problemi
E: Impossibile scaricare alcune file di indice, essi verranno ignorati, oppure si useranno quelli precedenti.[/B]


The lines in italian mean:
1) risoluzione fallita= failed resolution
2) impossibile ottenere= impossible to obtain
3)lettura della lista pacchetti in corso...fatto=reading the list of packages....done
4)W: impossible to control the list of packages (source list)
5)E: impossible to downlaod any file of index (index file?), they will be ingored or previous packages will be used


 I dont get why I get the above script when attempting to update the repositories. I get errors even trying to install things from the terminal eg apt-get install ...Any suggestions?

Thanks
Elisa

---

### Post by jonnymccullagh on 2006-05-10
Have you tried manually editing sources.list rather than using Adept (I don't use Adept so I don't know how it works)
Instructions: [http://ubuntuguide.org/#extrarepositories]("http://ubuntuguide.org/#extrarepositories")

You can make your own sources.list by visiting:
[http://www.ubuntulinux.nl/source-o-matic]("http://www.ubuntulinux.nl/source-o-matic")

Also I use Automatix to get a lot of propriety stuff and it seems to add it's own sources.list so you could possibly try using it?
[PHP]wget http://beerorkid.com/automatix/automatix_5.7-3_i386.deb
sudo dpkg -i automatix_5.7-3_i386.deb
[/PHP]

Also I prefer Synaptic to Adept (probably because I haven't tried Adept) so you could maybe give it a go?

I am a new user myself but I hope some of this might help,
jonny

---

### Post by jude254 on 2006-05-10
Thanks but I dont think the first link you gave me works, as Im using Kubuntu 5.10 breezy badger. Anyway, I have edited my source list, and its still not working. I dont know why. I have tried to do
 wget [http://beerorkid.com/automatix/automatix_5.7-3_i386.deb](http://beerorkid.com/automatix/automatix_5.7-3_i386.deb) in konsole and this is what I got:

--17:53:09--  [http://beerorkid.com/automatix/automatix_5.7-3_i386.deb](http://beerorkid.com/automatix/automatix_5.7-3_i386.deb)
           => `automatix_5.7-3_i386.deb'
Resolving beerorkid.com... failed: Temporary failure in name resolution.

I dont know how to get synaptic because I cant find it thru adept, and I dont know any other way to install it.

I am thinking my problems may be due to the proxy connection.

I dont know

Thanks anyway for your help

Im quite disappointed by the fact that I cannot solve these issues, I thought it was gonna be easier....

cheers
Elisa

---

### Post by mjm115 on 2006-05-10
Alternatively, you can have a sources.list generated for you [here]("www.ubuntulinux.nl/source-o-matic").  The default sources.list doesn't even come with every source enabled.

---

### Post by aysiu on 2006-05-10
> I am thinking my problems may be due to the proxy connection. I think so, too. There's no way the Italian mirror, the main Ubuntu site, and beerorkid are all down at the same time.

---

### Post by jonnymccullagh on 2006-05-10
Elisa,
Stick with it - I had problems like this for a week or two but the help here in the forums got me through it and I'm happy now.

Also the Ubuntu Guide link above is a great resource but try to use kwrite in place of gedit in any of the code as Kubuntu does not include the gedit program by default.

Try to set your http proxy by doing this in a Console:
```
HTTP_PROXY=http://userid:password@ip.addr:port#/
```

then
```

export HTTP_PROXY
```

check that it has worked by doing:
```
env
```

Then try the automatix stuff again. You may get stuck with a zenity dependency problem but if you get that far then reply here.

This should set up linux with your proxy details (most of them anyway).

If you are on a WAN you may also experience problems with the holding of your gateway address, if so see:
[http://www.ubuntuforums.org/showthread.php?t=160065]("http://www.ubuntuforums.org/showthread.php?t=160065")

---

### Post by jude254 on 2006-05-10
[QUOTE=jonnymccullagh]


Try to set your http proxy by doing this in a Console:
```
HTTP_PROXY=http://userid:password@ip.addr:port#/
```
[/QUOTE]
so with the info being

user id: elisa
password : my passwd
ip address: 192.168.1.2
port #: 6588

I would have [http://elisa:pswd@192.168.1.2:6588](http://elisa:pswd@192.168.1.2:6588) right?

---

### Post by jonnymccullagh on 2006-05-10
Yeh mine is a little different at work but I think this should work for you:

```
HTTP_PROXY=http://elisa:mypasswd@192.168.1.2:6588/
```

I don't have username and password for my proxy so mine is a little simper i.e.
 ```
HTTP_PROXY=http://192.168.1.2:8080/
```

---

### Post by jude254 on 2006-05-11
I dont have username and password for my proxy either. SO here is what I have done:

 HTTP_PROXY=http://192.168.1.2:6588/ (enter)
then
export HTTP_PROXY (enter)
then
env (enter)

This is what I got:
KDE_MULTIHEAD=false
SSH_AGENT_PID=6997
DM_CONTROL=/var/run/xdmctl
TERM=xterm
SHELL=/bin/bash
XDM_MANAGED=/var/run/xdmctl/xdmctl-:0,maysd,mayfn,sched,rsvd,method=classic
GTK2_RC_FILES=/etc/gtk-2.0/gtkrc:/home/elisa/.gtkrc-2.0:/home/elisa/.kde/share/config/gtkrc-2.0
GTK_RC_FILES=/etc/gtk/gtkrc:/home/elisa/.gtkrc:/home/elisa/.kde/share/config/gtkrc
GS_LIB=/home/elisa/.fonts
WINDOWID=37748741
KDE_FULL_SESSION=true
USER=elisa
LS_COLORS=no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.gz=01;31:*.bz2=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.ogg=01;35:*.mp3=01;35:*.wav=01;35:
SSH_AUTH_SOCK=/tmp/ssh-NYFTWp6965/agent.6965
SESSION_MANAGER=unix/kubuntuElisa:/tmp/.ICE-unix/7046
KONSOLE_DCOP=DCOPRef(konsole-7264,konsole)
DESKTOP_SESSION=default
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games
KONSOLE_DCOP_SESSION=DCOPRef(konsole-7264,session-1)
PWD=/home/elisa
LANG=it_IT.UTF-8
SHLVL=2
HOME=/home/elisa
LANGUAGE=it_IT
XCURSOR_THEME=default
HTTP_PROXY=http://192.168.1.2:6588/
LOGNAME=elisa
LESSOPEN=| /usr/bin/lesspipe %s
DISPLAY=:0.0
LESSCLOSE=/usr/bin/lesspipe %s %s
COLORTERM=
_=/usr/bin/env

 then I tried that automatix thing again, but got that same error script 

wget [http://beerorkid.com/automatix/automatix_5.7-3_i386.deb](http://beerorkid.com/automatix/automatix_5.7-3_i386.deb)
--12:16:00--  [http://beerorkid.com/automatix/automatix_5.7-3_i386.deb](http://beerorkid.com/automatix/automatix_5.7-3_i386.deb)
           => `automatix_5.7-3_i386.deb'
Resolving beerorkid.com... failed: Temporary failure in name resolution

I dont know if I made any mistake in configuring the proxy?

Any suggestion?

---

### Post by jude254 on 2006-05-11
I think I have solved my problem

This is what I have done:

"set an environment variable in your root terminal window prior to running apt-get. Here's the syntax:
[B]
export http_proxy=http://my.proxy.server:port/[/B]

I have done and I have updated adept that way. NOw I can find any package I want!!

I wonder if I have to do it everytime I want to update though?

Elisa

---

### Post by beerorkid on 2006-05-11
automatix has been updated by arnieboy.  it is now version 5.8.3

so the wget you are using is wrong (out dated)

refer to the automatix thread: [http://ubuntuforums.org/showthread.php?t=138405&highlight=automatix](http://ubuntuforums.org/showthread.php?t=138405&highlight=automatix)

and in the first post there will be the current code to install automatix.

no reason to have older versions on the server ;)

---

### Post by jonnymccullagh on 2006-05-12
You could try:
adding:
export http_proxy="http://192.123.123.123:8080/"

to 3 different files:
/etc/environment
/etc/profile
/etc/bash.bashrc

I did that at one point a few weeks ago and seem to be OK now.
jonny

---

### Post by jude254 on 2006-05-17
thanks I will try that!!

thanks for your help

---

### Post by jude254 on 2006-05-17
I have tried adding those lines but to no results.
I have added:

export http_proxy=http://192.168.1.2:6588/

is that right? or should it be:


export http_proxy="http://192.168.1.2:6588/" 

?

I still cannot get apt, not adept to work.

I dont get what the problem is

---

### Post by Brutalix on 2006-05-19
Does anyone know where I should set the proxy setting so it would work globally, since only the webbrowser manage to find the one set in the system setting.

Edit, I managed to get wget to work, by editing wgetrc and putting the proxy adress in there and to turn on proxy usage. 
I found a similar to apt and adept, if in apt directory in ect/apt you create apt.conf and into 
it write ACQUIRE {http::proxy "http://your_proxy:port/"} //remember that smileyface is : and p


Kind regards 

B.

---

### Post by jude254 on 2006-05-19
[QUOTE=Brutalix] 
I found a similar to apt and adept, if in apt directory in ect/apt you create apt.conf and into 
it write ACQUIRE {http::proxy "http://your_proxy:port/"} //remember that smileyface is : and p

[/QUOTE]

What type of file should apt-conf be? text file?
let me know

---

### Post by Al3xanR0 on 2006-05-19
[QUOTE=jude254]What type of file should apt-conf be? text file?
let me know[/QUOTE]

Go [here]("http://www.ubuntuforums.org/showthread.php?t=179244") for an example of how to edit the apt.conf file for proxy use.

---

### Post by Brutalix on 2006-05-20
Well you open Kate and write in the following: [noparse]ACQUIRE {http::proxy "http://your_proxy:port/"}[/noparse]
and save as apt.conf and thats it... 

Edit, thanks Steveire.. quiet helpfull tip.


B.

---

### Post by Steveire on 2006-05-20
Remember you can use [noparse][noparse][/noparse] tags on vb:

```
[[noparse]n[/noparse]oparse]proxy:port[/noparse]
``` will give you a much more readable way to tell people these things.

---

### Post by jude254 on 2006-05-23
OK I have done what you told me and created a new apt.conf file in the direcftory etc/apt. This is what I put:

ACQUIRE {http::proxy "http://192.168.1.2:6588"}

But apt-get is still not working .

If I do sudo apt-get update this is what I get (with translation from ITA)

root@kubuntuElisa:/home/elisa# sudo apt-get update
Err [ftp://cipherfunk.org](ftp://cipherfunk.org) breezy Release.gpg
  risoluzione di 'cipherfunk.org' temporaneamete fallita (resolution temp. failed)
Get:1 [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) breezy-seveas Release.gpg [309B]
Get:2 [http://kubuntu.org](http://kubuntu.org) breezy Release.gpg [191B]
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release.gpg
Ign [http://deb.opera.com](http://deb.opera.com) etch Release.gpg
Hit [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) breezy-seveas Release
Get:3 [http://kubuntu.org](http://kubuntu.org) breezy Release.gpg [189B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:5 [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release.gpg [307B]
Get:6 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy Release.gpg [189B]
Ign [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Release.gpg
Ign [http://deb.opera.com](http://deb.opera.com) etch Release
Ign [http://kubuntu.org](http://kubuntu.org) breezy Release.gpg
Ign [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) breezy-seveas Release
Hit [http://kubuntu.org](http://kubuntu.org) breezy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Get:7 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Ign [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages
Ign [http://pkg-boinc.alioth.debian.org](http://pkg-boinc.alioth.debian.org) breezy Release.gpg
Hit [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) breezy-seveas/all Packages
Hit [http://kubuntu.org](http://kubuntu.org) breezy Release
Get:8 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports Release.gpg [189B]
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy Release
Hit [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages
Ign [http://kubuntu.org](http://kubuntu.org) breezy Release
Ign [http://kubuntu.org](http://kubuntu.org) breezy Release
Ign [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Release
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates Release
Hit [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release
Ign [http://kubuntu.org](http://kubuntu.org) breezy Release
Hit [http://pkg-boinc.alioth.debian.org](http://pkg-boinc.alioth.debian.org) breezy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports Release
Hit [http://kubuntu.org](http://kubuntu.org) breezy/main Packages
Hit [http://kubuntu.org](http://kubuntu.org) breezy/main Sources
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Ign [http://pkg-boinc.alioth.debian.org](http://pkg-boinc.alioth.debian.org) breezy/universe Packages
Get:9 [http://mirror3.ubuntulinux.nl](http://mirror3.ubuntulinux.nl) breezy-seveas Release.gpg [309B]
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/main Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/restricted Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/main Sources
Ign [http://kubuntu.org](http://kubuntu.org) breezy/main Packages
Ign [http://kubuntu.org](http://kubuntu.org) breezy/main Sources
Hit [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Sources
Ign [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages
Ign [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/restricted Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/universe Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/multiverse Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/universe Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/multiverse Sources
Hit [http://kubuntu.org](http://kubuntu.org) breezy/main Packages
Hit [http://kubuntu.org](http://kubuntu.org) breezy/main Sources
Err [http://kubuntu.org](http://kubuntu.org) breezy/main Packages
  404 Not Found
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates/main Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates/main Sources
Ign [http://pkg-boinc.alioth.debian.org](http://pkg-boinc.alioth.debian.org) breezy/universe Sources
Err [http://kubuntu.org](http://kubuntu.org) breezy/main Sources
  404 Not Found
Hit [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates/restricted Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates/universe Packages
Hit [http://people.ubuntu.com](http://people.ubuntu.com) ./ Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates/multiverse Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates/universe Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates/multiverse Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/main Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/restricted Packages
Err [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages
  404 Not Found
Hit [http://pkg-boinc.alioth.debian.org](http://pkg-boinc.alioth.debian.org) breezy/universe Packages
Hit [http://mirror3.ubuntulinux.nl](http://mirror3.ubuntulinux.nl) breezy-seveas Release
Ign [http://mirror3.ubuntulinux.nl](http://mirror3.ubuntulinux.nl) breezy-seveas Release
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/universe Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/multiverse Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/main Sources
Hit [http://pkg-boinc.alioth.debian.org](http://pkg-boinc.alioth.debian.org) breezy/universe Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/restricted Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/universe Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/multiverse Sources
Err [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Sources
  404 Not Found
Hit [http://mirror3.ubuntulinux.nl](http://mirror3.ubuntulinux.nl) breezy-seveas/all Sources
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Release.gpg
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) source/ Release.gpg
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Release
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) source/ Release
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) source/ Sources
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) source/ Sources
Scaricato 1309B in 31s (41B/s) (downloaded 1309B in 31s)
Impossibile ottenere (impossible to obtain) [ftp://cipherfunk.org/pub/packages/ubuntu/dists/breezy/Release.gpg](ftp://cipherfunk.org/pub/packages/ubuntu/dists/breezy/Release.gpg)  risoluzione di 'cipherfunk.org' temporaneamete fallita (resolution temp. failed)
Impossibile ottenere [http://kubuntu.org/packages/amarok-latest/dists/breezy/main/binary-i386/Packages.gz](http://kubuntu.org/packages/amarok-latest/dists/breezy/main/binary-i386/Packages.gz)  404 Not Found
Impossibile ottenere [http://kubuntu.org/packages/amarok-latest/dists/breezy/main/source/Sources.gz](http://kubuntu.org/packages/amarok-latest/dists/breezy/main/source/Sources.gz)  404 Not Found
Impossibile ottenere [http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz)  404 Not Found
Impossibile ottenere [http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz)  404 Not Found
Lettura della lista dei pacchetti in corso... Fatto (reading list of packages...done)
W: GPG error: [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) breezy-seveas Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49A120FD1135D466
W: GPG error: [http://kubuntu.org](http://kubuntu.org) breezy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A506E6D4DD4D5088
W: GPG error: [http://kubuntu.org](http://kubuntu.org) breezy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A506E6D4DD4D5088
W: GPG error: [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B0B7481B1F44842D
W: GPG error: [http://mirror3.ubuntulinux.nl](http://mirror3.ubuntulinux.nl) breezy-seveas Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49A120FD1135D466
W: Impossibile controllare la lista dei pacchetti sorgente [ftp://cipherfunk.org](ftp://cipherfunk.org) breezy/main Packages (/var/lib/apt/lists/cipherfunk.org_pub_packages_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Impossibile controllare la lista dei pacchetti sorgente [http://kubuntu.org](http://kubuntu.org) breezy/main Packages (/var/lib/apt/lists/kubuntu.org_packages_amarok-latest_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Impossibile controllare la lista dei pacchetti sorgente [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages (/var/lib/apt/lists/koti.mbnet.fi_%7eots_ubuntu_breezy_Packages) - stat (2 No such file or directory)
W: È consigliabile eseguire apt-get update per correggere questi problemi
E: Impossibile scaricare alcune file di indice, essi verranno ignorati, oppure si useranno quelli precedenti. (W: suggested to do apt-get update to solve these problems) (E:impossible to downlaod some  index files, they will be ignored or previous ones will be used)

Please can you help me on this? If I dont get apt-get to work, I cant do anything
Any help is appreciated

thanks
Elisa

](*,)

---

### Post by jude254 on 2006-05-30
Guys please help!!!Im stuck here:(

[QUOTE=jude254]OK I have done what you told me and created a new apt.conf file in the direcftory etc/apt. This is what I put:

ACQUIRE {http::proxy "http://192.168.1.2:6588"}

But apt-get is still not working .

If I do sudo apt-get update this is what I get (with translation from ITA)

root@kubuntuElisa:/home/elisa# sudo apt-get update
Err [ftp://cipherfunk.org](ftp://cipherfunk.org) breezy Release.gpg
  risoluzione di 'cipherfunk.org' temporaneamete fallita (resolution temp. failed)
Get:1 [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) breezy-seveas Release.gpg [309B]
Get:2 [http://kubuntu.org](http://kubuntu.org) breezy Release.gpg [191B]
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release.gpg
Ign [http://deb.opera.com](http://deb.opera.com) etch Release.gpg
Hit [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) breezy-seveas Release
Get:3 [http://kubuntu.org](http://kubuntu.org) breezy Release.gpg [189B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:5 [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release.gpg [307B]
Get:6 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy Release.gpg [189B]
Ign [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Release.gpg
Ign [http://deb.opera.com](http://deb.opera.com) etch Release
Ign [http://kubuntu.org](http://kubuntu.org) breezy Release.gpg
Ign [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) breezy-seveas Release
Hit [http://kubuntu.org](http://kubuntu.org) breezy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Get:7 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Ign [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages
Ign [http://pkg-boinc.alioth.debian.org](http://pkg-boinc.alioth.debian.org) breezy Release.gpg
Hit [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) breezy-seveas/all Packages
Hit [http://kubuntu.org](http://kubuntu.org) breezy Release
Get:8 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports Release.gpg [189B]
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy Release
Hit [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages
Ign [http://kubuntu.org](http://kubuntu.org) breezy Release
Ign [http://kubuntu.org](http://kubuntu.org) breezy Release
Ign [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Release
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates Release
Hit [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release
Ign [http://kubuntu.org](http://kubuntu.org) breezy Release
Hit [http://pkg-boinc.alioth.debian.org](http://pkg-boinc.alioth.debian.org) breezy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports Release
Hit [http://kubuntu.org](http://kubuntu.org) breezy/main Packages
Hit [http://kubuntu.org](http://kubuntu.org) breezy/main Sources
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Ign [http://pkg-boinc.alioth.debian.org](http://pkg-boinc.alioth.debian.org) breezy/universe Packages
Get:9 [http://mirror3.ubuntulinux.nl](http://mirror3.ubuntulinux.nl) breezy-seveas Release.gpg [309B]
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/main Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/restricted Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/main Sources
Ign [http://kubuntu.org](http://kubuntu.org) breezy/main Packages
Ign [http://kubuntu.org](http://kubuntu.org) breezy/main Sources
Hit [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Sources
Ign [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages
Ign [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/restricted Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/universe Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/multiverse Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/universe Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/multiverse Sources
Hit [http://kubuntu.org](http://kubuntu.org) breezy/main Packages
Hit [http://kubuntu.org](http://kubuntu.org) breezy/main Sources
Err [http://kubuntu.org](http://kubuntu.org) breezy/main Packages
  404 Not Found
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates/main Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates/main Sources
Ign [http://pkg-boinc.alioth.debian.org](http://pkg-boinc.alioth.debian.org) breezy/universe Sources
Err [http://kubuntu.org](http://kubuntu.org) breezy/main Sources
  404 Not Found
Hit [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates/restricted Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates/universe Packages
Hit [http://people.ubuntu.com](http://people.ubuntu.com) ./ Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates/multiverse Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates/universe Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates/multiverse Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/main Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/restricted Packages
Err [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages
  404 Not Found
Hit [http://pkg-boinc.alioth.debian.org](http://pkg-boinc.alioth.debian.org) breezy/universe Packages
Hit [http://mirror3.ubuntulinux.nl](http://mirror3.ubuntulinux.nl) breezy-seveas Release
Ign [http://mirror3.ubuntulinux.nl](http://mirror3.ubuntulinux.nl) breezy-seveas Release
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/universe Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/multiverse Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/main Sources
Hit [http://pkg-boinc.alioth.debian.org](http://pkg-boinc.alioth.debian.org) breezy/universe Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/restricted Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/universe Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/multiverse Sources
Err [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Sources
  404 Not Found
Hit [http://mirror3.ubuntulinux.nl](http://mirror3.ubuntulinux.nl) breezy-seveas/all Sources
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Release.gpg
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) source/ Release.gpg
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Release
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) source/ Release
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) source/ Sources
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) source/ Sources
Scaricato 1309B in 31s (41B/s) (downloaded 1309B in 31s)
Impossibile ottenere (impossible to obtain) [ftp://cipherfunk.org/pub/packages/ubuntu/dists/breezy/Release.gpg](ftp://cipherfunk.org/pub/packages/ubuntu/dists/breezy/Release.gpg)  risoluzione di 'cipherfunk.org' temporaneamete fallita (resolution temp. failed)
Impossibile ottenere [http://kubuntu.org/packages/amarok-latest/dists/breezy/main/binary-i386/Packages.gz](http://kubuntu.org/packages/amarok-latest/dists/breezy/main/binary-i386/Packages.gz)  404 Not Found
Impossibile ottenere [http://kubuntu.org/packages/amarok-latest/dists/breezy/main/source/Sources.gz](http://kubuntu.org/packages/amarok-latest/dists/breezy/main/source/Sources.gz)  404 Not Found
Impossibile ottenere [http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz)  404 Not Found
Impossibile ottenere [http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz)  404 Not Found
Lettura della lista dei pacchetti in corso... Fatto (reading list of packages...done)
W: GPG error: [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) breezy-seveas Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49A120FD1135D466
W: GPG error: [http://kubuntu.org](http://kubuntu.org) breezy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A506E6D4DD4D5088
W: GPG error: [http://kubuntu.org](http://kubuntu.org) breezy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A506E6D4DD4D5088
W: GPG error: [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B0B7481B1F44842D
W: GPG error: [http://mirror3.ubuntulinux.nl](http://mirror3.ubuntulinux.nl) breezy-seveas Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49A120FD1135D466
W: Impossibile controllare la lista dei pacchetti sorgente [ftp://cipherfunk.org](ftp://cipherfunk.org) breezy/main Packages (/var/lib/apt/lists/cipherfunk.org_pub_packages_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Impossibile controllare la lista dei pacchetti sorgente [http://kubuntu.org](http://kubuntu.org) breezy/main Packages (/var/lib/apt/lists/kubuntu.org_packages_amarok-latest_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Impossibile controllare la lista dei pacchetti sorgente [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages (/var/lib/apt/lists/koti.mbnet.fi_%7eots_ubuntu_breezy_Packages) - stat (2 No such file or directory)
W: È consigliabile eseguire apt-get update per correggere questi problemi
E: Impossibile scaricare alcune file di indice, essi verranno ignorati, oppure si useranno quelli precedenti. (W: suggested to do apt-get update to solve these problems) (E:impossible to downlaod some  index files, they will be ignored or previous ones will be used)

Please can you help me on this? If I dont get apt-get to work, I cant do anything
Any help is appreciated

thanks
Elisa

](*,)[/QUOTE]

---

