---
title: "compiz cube-atlantis"
date: 2010-07-14
forum: General Help
---

### Post by johnsky on 2010-07-14
Running Ubuntu 10.4 LTS

In CompizConfig Settings Manager I don't have Cube-Atlantis present.
Latest Compiz-Fusion-Plugins-Main and Compiz-Fusion-Plugins-Extra packages have been installed.

Upon looking online, all instructions I have found as to how to install cube-atlantis are for 8.04, 9.10, and don't seem to work on 10.4, as the packages they instruct you to install don't seem to contain cube-atlantis anymore.

Found a little information regarding something called "git", and a suggestion that I need to install cube-atlantis using "git", but no real instructions as to how to use this "git" to install cube-atlantis.

Has the community simply abandoned cube-atlantis all-together?
I remember it used to be pretty neat.

---

### Post by WorMzy on 2010-07-14
It hasn't been present in default installations of Compiz for at least a couple of years now. There's no way of installing it from the repos, so I think the git method is the best you can hope for at present. Here's an adapted (from [here]("http://ubuntuforums.org/showthread.php?t=601957")), and untested by myself, way of obtaining the plugin:

```
cd /tmp && wget -O 'atlantis.tar.gz' 'http://gitweb.compiz.org/?p=inactive/fusion/atlantis;a=snapshot;h=d3e913e8fd1da7ad77beedc364cdea582a6f730e'
cd ~/ && mkdir compiz
cd ~/compiz
tar -xvf '/tmp/atlantis.tar.gz' && cd 'atlantis'
make clean
make
sudo make install
```

Don't run 'sudo make install' if something goes wrong during either of the previous 'make' commands.

It's not just the Ubuntu community that's abandoned this plugin, as you can see from the git url, the Compiz team has set it's status to an inactive plugin. What this means to me and you, I don't know, it may not even be compatible with the most recent versions of Compiz. Still, the instructions are there if you want to try it.

---

### Post by johnsky on 2010-07-14
Awesome, thanks for the reply.
I'll give this a try, wont keep my fingers crossed from the sounds of how compiz is abandoning it.

Makes one wonder why though.
Odd that they would just drop it from all the repos, and nothing else has taken its place... kind of a back-step if you ask me. I noticed even the unsupported repo no longer exists.

Thanks again for the response, off to give this a try.

---

### Post by johnsky on 2010-07-14
Alright!

Now we're cooking with fish!

Only one setback, the options within CompizConfig Setting Manager for cube-atlantis don't affect the actual cube-Atlantis itself (number of fish, water height etc)... just turns cube-Atlantis on or off.

But at this point, I'm just happy I can turn it on and off.
Figuring out why the settings don't work can wait, the default settings will do for me for now!

Thanks again for your help!!! If I lived anywhere nearby I'd buy you a pint!
Sadly, England is a bit of a swim from Canada.

---

### Post by WorMzy on 2010-07-14
Ahaha, I intend to move to Canada one day, so if you ever bump into me in the future feel free to buy me as many pints as you like! :p

I don't know where the plugin reads it's config from, but you could check gconf-editor under /apps/config/plugins, or have a poke around your /etc directory for anything that looks like it may be tied to it. I recommend that you make a note of the original settings or a backup of the config file if you find it before you start modifying them/it, just in case something goes wrong and breaks the plugin.

Anyway, glad it worked for you, even if it's only partially.

---

### Post by johnsky on 2010-07-14
That's what I had in mind; hunting down the config file and figuring it out manually. But that's for another day!

Oh, and if you do move to Canada, try Southern Ontario or British Columbia (if you can afford British Columbia)... the other provinces climates will be a living nightmare for you.

Highest paying jobs seem to be in the most uninhabitable parts of this country though... so it depends on what you're after.

---

### Post by WorMzy on 2010-07-14
BC's my intended destination, since I have friends living there. But I'm just a poor just-out-of-uni ex-student looking for a job at the moment, so it'll probably be a few years before I get enough money scraped together to realistically consider moving. For now, it's just a dream keeping me (and my very understanding parents!) looking forward. :)

I've just got a couple of other pointers to make: you may need to switch your compiz back-end to the GConf backend, or to the Flat-file backend; the plugin may not be compatible with one or the other. The Gconf settings I mentioned above, the flat-file settings are saved to ~/.config/compiz/compizconfig. Hopefully you can find a way to get it to work. Good luck.

Oh, almost forgot to mention that you can change the backend that Compiz uses in the settings manager (ccsm).

---

### Post by johnsky on 2010-07-14
Well, am I ever red...

I neglected to restart compiz before trying to change settings for cube-atlantis.

Turns out the settings work just fine.
Provided I restart to let the install take effect.

So... (looking sheepishly around) if anyone else out there wants to install Cube-Atlantis on 10.4 Ubuntu... follow WorMzy's instructions... and don't forget to restart before assuming anything.

Can't believe I didn't restart immediately... used to do tech support... biggest pet peeve was people who would call up without restarting first... and here I am guilty of it myself.

---

### Post by fabjoa on 2010-07-24
Hey

After make clean, i get the following error


Makefile:48: *** [ERROR] Compiz not installed.  Stop.

Yet, Compiz is installed, I am rotating the cube right now. Any idea?

---

### Post by realzippy on 2010-07-24
Maybe the development packages are missed... install
*compiz-fusion-bcop compiz-dev*

```
sudo apt-get install compiz-fusion-bcop compiz-dev
```

and try again...

---

### Post by WorMzy on 2010-07-24
Check Synaptic for a compiz-dev or a libcompiz package, or something similar. I'm not on Ubuntu at the moment, so I can't check. If there's nothing like that, then try re-installing the main compiz packages

---

### Post by fabjoa on 2010-07-24
Thank you realzippy, you is a genius ):P

---

### Post by umps1988 on 2010-08-04
[B]compiling : water.c -> build/water.lo/bin/sh: libtool: not found
make: *** [build/water.lo] Error 127
[/B]
how to solved?

---

### Post by WorMzy on 2010-08-04
Try running ```
sudo apt-get install libtool
``` then re-run make.

---

### Post by umps1988 on 2010-08-14
thanks man..pretty cool..my pc wet..haha:P

---

### Post by Banick on 2010-11-15
craig@ubuntu:~$ sudo apt-get install libtool
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


That is the problem I get when doing this command

---

### Post by WorMzy on 2010-11-15
Do you have another terminal with apt-get running? Or do you have Synaptic Package Manager or Ubuntu Software Centre open? I'm not sure if the Software Centre can cause that error, but Synaptic sure can. If you're not running another apt-get command, and don't have either Synaptic or Software Centre open, then try restarting your PC. If that's not an option or doesn't help, then as a last resort, run (in a terminal):
```
sudo rm /var/lib/dpkg/lock
```

---

### Post by omonemo on 2011-03-10
after the second make command i got the following, what is the issue with the whale? can i go on?


point-nemo@blue2:~/compiz/atlantis$ make
convert   : atlantis.xml.in -> build/atlantis.xml
bcop'ing  : build/atlantis.xml -> build/atlantis_options.h
bcop'ing  : build/atlantis.xml -> build/atlantis_options.c
schema    : build/atlantis.xml -> build/compiz-atlantis.schema
compiling : whale.c -> build/whale.lo/bin/sh: libtool: not found
make: *** [build/whale.lo] Error 127
point-nemo@blue2:~/compiz/atlantis$ ^C

---

### Post by WorMzy on 2011-03-10
That error looks similar to post #13's. Did you try installing libtool?

---

### Post by MiThRaZoR on 2011-04-23
After typing in 'make'. It gives me this.

"....
build/.libs/shark.o: In function `DrawShark':
/home/kudafi/compiz/atlantis/shark.c:1258: multiple definition of `DrawShark'
build/atlantis/.libs/shark.o:/home/kudafi/compiz/atlantis/atlantis/shark.c:1258: first defined here
[i]collect2: ld returned 1 exit status
make: *** [build/libatlantis.la] Error 1[/i]"

---

### Post by HolyDonut on 2011-09-19
I'm having the same problem as *omonemo* and I installed libtools.

make 
convert   : atlantis.xml.in -> build/atlantis.xml
bcop'ing  : build/atlantis.xml -> build/atlantis_options.h
bcop'ing  : build/atlantis.xml -> build/atlantis_options.c
**make: *** No rule to make target `build/whale.lo', needed by `c-build-objs'.  Stop.**

Any other ideas for fixing this?

I'm in 11.04 Natty Narwhal.

---

### Post by thetruckinglife on 2011-11-27
thank you WorMzy followed your instructions and it works!
i already had Compiz intstalled just ran these 2 commands prior to yours for Cube Atlantis to install properly.
sudo apt-get install compiz-fusion-bcop compiz-dev
sudo apt-get install libtool
now i have an aquarium installed in my rotating cube!
cheers to you!
[img]http://pics.3ezy.net/var/resizes/abyss/Random-Pictures/cube%20atlantis.jpg?m=1322426966[/img]

---

