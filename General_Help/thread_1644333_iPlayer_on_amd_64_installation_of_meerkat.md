---
title: "iPlayer on amd 64 installation of meerkat"
date: 2010-12-13
forum: General Help
---

### Post by grey1beard on 2010-12-13
From the BBC site, if I try to download the desktop iPlayer, it tries to download Adobe Air installer, but says it "can't write the application to the hard disk", so it stops.

I've got the Flash player plugin installed, but not Flash 10, and I've tried to use the software centre to install Adobe Air from there, but it starts, runs for a couple of seconds, then stops. The same result if I try to download Flash 10.
I've restarted and checked the installed software, but zilch.
Any suggestions gratefully received by this aged newbie.:confused:

John

---

### Post by cascade9 on 2010-12-13
I dont know if it would help, but I'd try the newest version of flash. The 64bit version- 

[http://labs.adobe.com/technologies/flashplayer10/square/](http://labs.adobe.com/technologies/flashplayer10/square/)

If you dont want to manually install, try the 'flash aid' plugin. (written by "lovinglinux" who is a member here) 

[http://flash-aid-extension.blogspot.com/](http://flash-aid-extension.blogspot.com/)

---

### Post by grey1beard on 2010-12-13
Do I actually need to install Flash in order to install Adobe Air, which is what I do need  ?
On the KISS principle, I'd only do it if I have to :)
John

---

### Post by cascade9 on 2010-12-14
Updating flash is a really good idea, even if it seems pointless. The server end might be expecting flash 10+ and if you've only got 9.x that could cause problems. 

As for iplayer, I'd have a look here- 

[http://www.bbc.co.uk/iplayer/install](http://www.bbc.co.uk/iplayer/install)

Since I'm not in the UK, I'd have to do a lot of stuffing around to view the BBC iplayer content so I dont know anything more than that, really. Sorry.

---

### Post by grey1beard on 2010-12-14
Thanks Cascade. That BBC page is where my problem began :(
It's moved down the urgent list somewhat - visitors coming - but I've now only got a few days left to get it sorted.
Desperate to see the video on "Come Clog Dancing" -how sad is that !!!
John

---

### Post by nothingspecial on 2010-12-14
Hi John,

I don`t know about the iplayer on the bbc`s website.

However, I can show you how to watch Come clog dancing on your computer.

First, install the outdated version of get_iplayer (to install the dependencies)

```
sudo apt-get install get_iplayer mplayer
```The trouble is that it dosen`t work anymore. So you have to get the updated version from here.```


wget ftp://ftp.infradead.org/pub/get_iplayer/get_iplayer-2.78.tar.gz
```unpack it.

```
tar -xvf get_iplayer-2.78.tar.gz
```Remove the old one. [SIZE=4][COLOR=Red]Be really careful here. Copy and paste, a mistake could break your system. [/COLOR][/SIZE]

```
sudo rm /usr/bin/get_iplayer
```replace it with the new one

```
sudo mv get_iplayer-2.78/get_iplayer /usr/bin
```

Now search for Clog

```
get_iplayer Clog
```after a couple of minutes you should get something like this
```

Matches:
170:    Come Clog Dancing - Treasures of English Folk Dance, BBC Four, Arts Culture & the Media,Factual,Folk,Music,TV, default
```The number 170 is the important bit.

To play it```


get_iplayer --stream 170 --player="mplayer -cache 3072 -"
```The number could be different for you.

I am pretty certain that if you are a uk resident license fee payer, that this breaks no laws. I am not 100%.

I know it looks really geeky, but it`s easy really.

Cheers.

---

### Post by grey1beard on 2010-12-14
> **nothingspecial said:**
> 
....I am pretty certain that if you are a uk resident license fee payer, that this breaks no laws. I am not 100%.
.......

Yes, I think so too.
If I'm watching a programme after it was broadcast, then I am free to do so on my pc.
What is illegal is to watch in real time without a TV licence.
No TV, therefore no licence.

I'll hold on to that method if I get too close to the deadline ;)
Thanks again,
John

---

### Post by grey1beard on 2010-12-14
My terminal -
 

[B]Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package get_iplayer[/B]


I presume this is what you meant by "getting the dependencies, but it doesn't work any more."

EDIT Run into snag.

I copy/pasted the **sudo rm /usr/bin/get_iplayer** line, and it says

**rm: cannot remove `/usr/bin/get_iplayer': No such file or directory**

John

---

### Post by nothingspecial on 2010-12-14
My fault, john.

The package is get-iplayer (with a hyphen)

The command is get_iplayer with an underscore

```
sudo apt-get install get-iplayer
```

---

### Post by nothingspecial on 2010-12-14
You haven't got usr/bin/get_iplayer till the first command works

---

### Post by grey1beard on 2010-12-14
I take it that I can just start again with your line
**sudo apt-get install get-iplayer**
Then proceed as before, running the rest as originally written, and without having to undo anything ?

John

---

### Post by nothingspecial on 2010-12-14
Yes.

You won`t need to do the** wget** or** tar **lines again

---

### Post by grey1beard on 2010-12-14
Brilliant, a complete success !

One last question - the BBC site says it's available till 23 December, so I presume that when I run that last line

**get_iplayer --stream 170 --player="mplayer -cache 3072 -"**

 I've then downloaded it for playing later, or am I only able to run it at that instant ?

John

---

### Post by nothingspecial on 2010-12-14
That command only plays it.

To save it

```
get_iplayer -g 170
```

But then you are in dodgy territory.

but as long as you remember to delete it after 30 days I think you are fine.

---

### Post by grey1beard on 2010-12-14
No, that's fine. It's having it accessable ( the extra 30 days is a bonus) so that I can view it off line.
Last last question - what does

**get_iplayer -g 170**

do with it ? does it store it in the download folder ?

John

---

### Post by nothingspecial on 2010-12-14
It stores it, where ever you are in the shell.

Which would be your home folder if you open a terminal and use those commands.

You can move it though.

---

### Post by grey1beard on 2010-12-14
Many thanks for your help.
Keep well,
John

---

### Post by nothingspecial on 2010-12-14
No problem.

Just so you are sure, you don`t have to do all that wget and tar and sudo mv business anymore.

To search for tv
```

get_iplayer searchterm
```

For radio 

```
get_iplayer --type=radio searchterm

```

And for podcasts
```

get_iplayer --type=podcast searchterm
```

Then just ```
get_iplayer -g ???
```

To save, replacing the question marks with the number get_iplayer gives the program.

---

### Post by grey1beard on 2010-12-14
BONUS  :biggrin:

---

### Post by grey1beard on 2011-01-18
I've Unsolved this thread as I now have the same problem with only a slight variation.

I'm trying to install the iPlayer on my wife's laptop (a 32 bit system) and used the set of instructions *nothingspecial* gave me for my 64 bit desktop.
However, I got confused at the point I did before, trying to run the **sudo rm usr/bin/get_iplayer**,
 where the error message **/usr/bin/get_iplayer : No such file or directory** appeared.
I tried to change the instruction to **sudo rm usr/bin/get-iplayer** 
(with a hyphen instead of the underscore) but got the same result.
So I went on to the line **sudo mv get_iplayer-2.78/get_iplayer /usr/bin** .
As that produced no error message, I then used **get_iplayer Horizon**, and then the 2.78 copyright message appeared, followed by a Newer version message - 2.79
It then posted  **Could not create backup file /usr/bin/get_iplayer.old - Update aborted**.
I did the same search for the Horizon programme in my own 64 bit system with no problems, and no mention of an update.
I suspect I've removed the wrong package, so I'm not clear how to reinstate it without risking further chaos.

I'd be grateful for a bit of help here, mainly to keep my kudos re my wife ;)

John

---

### Post by grey1beard on 2011-01-18
Just used the bit of my brain still functioning, and used synaptic to download/ install 2.78 again.
So I'll see what results.
John
PS I just ran get_iplayer Horizon again, and it worked !

---

### Post by grey1beard on 2011-01-18
Duplicate

---

### Post by grey1beard on 2011-01-18
Multiple posts, sorry. No idea what is going on.

---

### Post by grey1beard on 2011-01-18
A final question now that I'm being told in Terminal that my system is too slow to play it !

As the laptop plays dvds with no problem, is it possible to download iplayer streams, save to hdd, then play it afterwards ?
Not very technically expressed perhaps, but you may see what I'm driving at.

---

### Post by grey1beard on 2011-01-18
Well, it worked as far as giving me the necessary info, but threw up an 
> ERROR : Cannot open player command

Help still required it seems.
Just looked in synaptic and discovered mplayer not installed, so that is now going in, and will reboot.
John

---

### Post by grey1beard on 2011-01-18
Duplicate, again!!!!

---

### Post by grey1beard on 2011-07-08
The method described above worked OK, but now I have run into a problem.
I'm trying to perform the same installation on a 32 bit Ubuntu 10.04 running on a different pc, and I can't reach the ftp site of infradead.org mentioned in post #6 above, to get the latest working version of get-iplayer.

Can anyone offer advice ?

John
EDIT
I've just checked, and found the version 2.66 is installed, but I don't know how to update it without access to the infradead site. Is there another way for this old newbie to get past the problem ?

---

### Post by grey1beard on 2011-07-08
> **grey1beard said:**
> .......
EDIT
I've just checked, and found the version 2.66 is installed, but I don't know how to update it without access to the infradead site. Is there another way for this old newbie to get past the problem ?

Oooooooooops, version 2.66 certainly downloads the info OK, so it looks as though I don't need a later version anyway.
If it runs, I'll post solved tomorrow.

John

---

### Post by ron999 on 2011-07-08
> **grey1beard said:**
> Oooooooooops, version 2.66
Hi
Your version of get_iplayer is well out of date.
It's v2.79 now.

This command will update it:-

```
sudo apt-get -y install get-iplayer rtmpdump mplayer ffmpeg git-core && \
git clone git://git.infradead.org/get_iplayer.git && \
sudo cp ~/get_iplayer/get_iplayer /usr/bin/get_iplayer && \
sudo rm -r ~/get_iplayer
```

Then use this command to check it:-
```
ls -lh /usr/bin | grep -i "get_iplayer"
```

> ron@ubuntu:~$ ls -lh /usr/bin | grep -i "get_iplayer"
-rwxr-xr-x 1 root   root    325K [COLOR="Red"]2011-07-09 00:19[/COLOR] get_iplayer
lrwxrwxrwx 1 root   root      11 2011-07-06 23:31 get-iplayer -> get_iplayer

---

### Post by grey1beard on 2011-07-09
> **ron999 said:**
> 
.....Your version of get_iplayer is well out of date.......


Like me, Ron :D

Many thanks for the code.

Regards

John

---

### Post by grey1beard on 2011-07-09
> [sudo] password for john: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
get-iplayer is already the newest version.
Package rtmpdump is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package rtmpdump has no installation candidate
john@frizzy:~$ ls -lh /usr/bin | grep -i "get_iplayer"
-rwxr-xr-x 1 root   root    318K 2010-05-27 21:58 get_iplayer
lrwxrwxrwx 1 root   root      11 2011-07-08 23:00 get-iplayer -> get_iplayer


Does this last line indicate that I have already had it updated ?

John

---

### Post by grey1beard on 2011-07-09
Having just started get_iplayer in a terminal, I noticed that the version is 2.66, but I'm letting it run anyway, for the moment.
John

---

### Post by ron999 on 2011-07-09
> **grey1beard said:**
> Does this last line indicate that I have already had it updated ?


No, that is the date when you installed v2.66

---

### Post by ron999 on 2011-07-09
Hey greybeard
RTMPDump isn't available for Ubuntu 10.04.

So run this command instead:-
```
cd ~/ && sudo apt-get -y install get-iplayer mplayer ffmpeg git-core && \
git clone git://git.infradead.org/get_iplayer.git && \
sudo cp ~/get_iplayer/get_iplayer /usr/bin/get_iplayer && \
sudo rm -r ~/get_iplayer
```
Then this afterwards:-
```
ls -lh /usr/bin | grep -i "get_iplayer"
```

---

### Post by grey1beard on 2011-07-09
Thanks Ron, it looks good.

> john@frizzy:~$ ls -lh /usr/bin | grep -i "get_iplayer"
-rwxr-xr-x 1 root   root    325K 2011-07-09 11:24 get_iplayer
lrwxrwxrwx 1 root   root      11 2011-07-08 23:00 get-iplayer -> get_iplayer
john@frizzy:~$ 

Regards

John

---

