---
title: "Terminal- File Moving?"
date: 2010-01-24
forum: General Help
---

### Post by Tourdog on 2010-01-24
I've downloaded this file from the "nightly builds" updates for going 64 bit on FireFox 3.6 from Mozilla:

"firefox-3.6.1pre.en-US.linux-x86_64.tar.bz2"

It took 18 seconds to auto download into a subdirectory (firefox) that is attached to my (Downloads) directory.  I've now spent 18 hours researching how to move it to my (home) directory but all attempts have failed.  No where before the download did I find how to "re-direct" the file to my (home) directory.

I've tried "mv" and even "sudo mv" but somehow my multitudes of "Path" or "hierarchy" have been all thwarted..................

It shows up now as "firefox firefox-3.6.1pre.en-US.linux-x86_64.tar.bz2"    It appears to be one that I can use but I'm not even sure of that now!

TIA for your HELP!  :(

---

### Post by howefield on 2010-01-24
What is it you want to do, move the file from /home/user/Downloads to /home ?

Open a terminal and type

```
cd Downloads
```

then type

```
sudo mv firefox-3.6.1pre.en-US.linux-x86_64.tar.bz2 /home
```

Or you can open nautilus with elevated rights and move it "graphically"

```
gksudo nautilus
```

---

### Post by lidex on 2010-01-24
> It shows up now as "firefox firefox-3.6.1pre.en-US.linux-x86_64.tar.bz2"

It looks like you may have renamed it in your move attempt. The download directory was "/home/user/Downloads/firefox/", correct? I'd follow howefield's advice on gksudo nautilus and navigate to that folder.

BTW, I would suggest this thread for best way to install firefox:
[http://ubuntuforums.org/showthread.php?t=1193567]("http://ubuntuforums.org/showthread.php?t=1193567")

---

### Post by Tourdog on 2010-01-24
Howefield,
Thanks for replying!

Here is what I have so far:

/
tourdog@PJK3:/$ cd ~/Downloads
tourdog@PJK3:~/Downloads$ sudo mv firefox-3.6.1pre.en-US.linux-x86_64.tar.bz2 /home
[sudo] password for tourdog:

tourdog@PJK3:~/Downloads$ cp -R ~/.mozilla ~/.mozilla.backup
tourdog@PJK3:~/Downloads$ sudo tar -jxvf firefox-*.tar.bz2 -C /opt
tar: firefox-*.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors
tourdog@PJK3:~/Downloads$ 

That is what's been happening.......................  the "cp-R ........................backup" and the next "sudo tar -jxvf....................................................../opt" are the 1st & 2nd lines from a set of 6 lines posted on the "Optimization and Trouble Shooting Thread on "Tutorials and Tips.by author "LovingLinux"  

The "tar" is there in subdirectory Firefox below Downloads but I can't get it moved to "home" ???  :(

What do you think?  TIA!

---

### Post by lidex on 2010-01-24
In a terminal:
```
cd ~/Downloads
ls
```

Post output.

---

### Post by steveneddy on 2010-01-24
Just install the ppa - simple - easy - and it updates automatically

linky:

[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)

no muss - no fuss - and no dirty .tar.gz cluttering up the floor.

---

### Post by lidex on 2010-01-24
> **steveneddy said:**
> Just install the ppa - simple - easy - and it updates automatically

linky:

[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)

no muss - no fuss - and no dirty .tar.gz cluttering up the floor.

Stop making sense! Nicely done.

---

### Post by Tourdog on 2010-01-24
Steveneddy,
lidex,


tourdog@PJK3:~/Downloads$ cd ~/Downloads
tourdog@PJK3:~/Downloads$ 
tourdog@PJK3:~/Downloads$ ls
firefox
tourdog@PJK3:~/Downloads$ 



[FONT=monospace]The ppa doesn't indicate 64 bit or did I miss that?   It seems the AMD64 all have red X on them.

Whatzup with that?


[/FONT]

---

### Post by lidex on 2010-01-24
> **Tourdog said:**
> Steveneddy,
lidex,


tourdog@PJK3:~/Downloads$ cd ~/Downloads
tourdog@PJK3:~/Downloads$ 
tourdog@PJK3:~/Downloads$ ls
firefox
tourdog@PJK3:~/Downloads$ 



[FONT=monospace]The ppa doesn't indicate 64 bit or did I miss that?   It seems the AMD64 all have red X on them.

Whatzup with that?


[/FONT]

Not sure, let me look into that. Do you currently have 32bit installed? I'm on AMD_64 with Firefox 3.6.1pre (Namoroka)x64 installed from that very PPA. Where are you seeing those red X's, synaptic?


Edit: Now that I think about it, they may all be x32, just packaged for x64

---

### Post by Tourdog on 2010-01-24
Lidex, I finally got the subject "tar" moved to "home" and completed the 6 lines of code given by author "LovingLinux". 4 pages of data ran but nothing happened so I extracted the "tar" right there in "home". Now I need to know which file to point to in a script that can run at "startup" pretty much as I do for avoiding the Nvidia Resolution problem.

 I fixed that with a startup script... Hopefully this will be similar. Any ideas on this since the ball has been moved down the court to this point !!! Guessing: /home/firefox/???.exe???bin...??? What do you think??? Sure appreciate ya following this saga!

What is an easy way to keep FF 3.56 from running..........  script or ?   Solved this line already.  3.6 64 bit Namoroka is up and running.........................looking good and maybe faster with less "hang" time on web site changes.  Whoohoo!

Script for "Startup Applications" and I'll be set.

---

### Post by lidex on 2010-01-25
Are you saying you need a launcher for firefox? Not running it at system startup, right?

---

### Post by lidex on 2010-01-25
> What is an easy way to keep FF 3.56 from running

Uninstall it.

---

### Post by lidex on 2010-01-25
Generally you want to install optional progams into the /opt directory however you may have installed it in your home folder -- if I follow, which I'm not sure I do.

You can usually run the .bin file to start but if there's a .sh script of the same name use that. To see a list of directories which may give you a clue use this:
```
ls | less
``` press "Q" to quit

---

### Post by Tourdog on 2010-01-25
Lidex,

Yes, I did (out of frustration) install Namoroka in my "home" directory but it is fine since it all works!  
Tomorrow I'll work on a script which will be ok for the short term.  Having both 3.56 and 3.61 available (one at a time) will permit seeing the diff's I think.

I'll use the "ls | less" tomorrow.

Sure thank you for sticking with these problems.  My Ubuntu 9.10 Karmic works pretty smoothly and it is do to all you Guru's putting out so much time for us new guys!  :)

---

### Post by steveneddy on 2010-01-25
Actually, installing the ppa is as simple as opening up a file:

```
sudo gedit /etc/apt/sources.list
```

and entering the two lines of code at the bottom:

```
deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu **[COLOR="Red"]karmic[/COLOR]** main 
deb-src http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu **[COLOR="red"]karmic[/COLOR]** main 
```

of course, if you aren't using karmic, change it to the version of Ubuntu you are using - jaunty - hardy - intrepid

now install the key

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 247510BE
```

```
sudo apt-get update
```

then 

```
sudo apt-get upgrade

```

then finally

```
sudo apt-get install firefox-3.6
```

This is the easiest way of installing software because you never have to touch it again. It will update when new packages are available with the regular system updates.

See? easy peasy. :)

---

