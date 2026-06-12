---
title: "Youtube nightmare"
date: 2012-04-06
forum: General Help
---

### Post by tunnafish on 2012-04-06
Help anyone , I use Ubuntu 10.04 , everything has been fine 
until I downloaded the latest updates, now my youtube video or video sound
no longer works, 

                   any ideas  greatfully accepted

                                  regards tony

---

### Post by wildmanne39 on 2012-04-06
Hi, I would open firefox go to tools>addons then install flashaid and let it do its magic with flash and see if that fixes your issue.
Thanks

---

### Post by tunnafish on 2012-04-06
Thanks  for you quick reply , but tried that ,but it didnt work sadly ,


                          regards tunnafish

---

### Post by dragonfly41 on 2012-04-06
run command

[COLOR=Blue]locate libflashplayer.so[/COLOR]

to find flash plugins

---

### Post by tunnafish on 2012-04-06
Thanks again but it didnt work , just have to keep trying

                     but thank you,

                             regards tony

---

### Post by 0011235813 on 2012-04-06
OK so you say YouTube doesn't work? The thing that comes to mind is a Flash error. Have you tried using any other Flash based websites? If flash is the error, first uninstall anything that tries to play Flash in USC. That includes Gnash or Lightspark. Then install the Flash that you're supposed to be using;
```
sudo apt-get install flashplugin-installer 
```
and restart your browser. Also, you're using 12.04, you do realize it's beta right?

---

### Post by tunnafish on 2012-04-07
Once again much appreciate you taking the time to try to help me , but 
unfortunately that didnt work either,

                 but thank you

---

### Post by Hungry Man on 2012-04-07
Is Flash just not launching or is it giving an error when it launches or perhaps a blue/green screen where videos are?

Is it only on youtube or on other sites as well?

Do you know which GPU you have in your computer?

---

### Post by tunnafish on 2012-04-08
HI its a Athlon AMD 3200, but the occasional youtube video will play ,

say one in fifty or so , but it has only happened since down loading

Ubuntu updates a couple of days ago, up till then its been faultless,

I have tried turning on and off various packages in the synaptic 

package manager , but cannot  find the right combination to get 

youtube to work again, I just get a black screen where normally the 

video would be , 

             thanks for taking the time to help,

---

### Post by na5h on 2012-04-08
I'm assuming there is some kind of problem with the flash. Could you post the output of the following command:
```
lsb_release -a; uname -a; dpkg -l | egrep 'flash|gnash|swf|spark'
```

In the meantime, you could try to view the youtube videos in HTML5-mode (go to [http://www.youtube.com/html5]("http://www.youtube.com/html5") and click on "Join the HTML5 trial". Not all videos are available without flash, but it's still a pretty convenient alternative.

---

### Post by 0011235813 on 2012-04-08
> **na5h said:**
> I'm assuming there is some kind of problem with the flash. Could you post the output of the following command:
```
lsb_release -a; uname -a; dpkg -l | egrep 'flash|gnash|swf|spark'
```

**In the meantime, you could try to view the youtube videos in HTML5-mode** (go to [http://www.youtube.com/html5]("http://www.youtube.com/html5") and click on "Join the HTML5 trial". Not all videos are available without flash, but it's still a pretty convenient alternative.

+1 Good riddance to Flash! 
@OP Are you sure your drivers are working properly? If they are, then it's a Flash error. Also, can you post the output you got from my previous command?

---

### Post by dragonfly41 on 2012-04-08
The clue is that this command "didn't work" for OP .. post #4

[COLOR=Blue]locate libflashplayer.so

[COLOR=Black]so it appears that there is no flash plugin .. anywhere?[/COLOR]
[/COLOR]

---

### Post by tunnafish on 2012-04-09
ailed to fetch [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.


This is what I keep getting ,

                   thanks again

---

### Post by tunnafish on 2012-04-09
Hi all this is what I get when trying to install adobe flash player,

 Failed to fetch [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by tunnafish on 2012-04-11
thanks everyone for trying to help , now----- out IT man helped me

he had to reinstall firefox , as one of the latest updates seems

was not compatible  with the version of Firefox I had , well that worked,

but now I have another problem ,----email , when I try to send a email this 

is what I keep getting ,       An error occurred sending mail: The mail server sent an incorrect greeting:  #4.4.5 Too many connections to this listener..


:confused:   please anyone help

                                  tunnafish

---

### Post by 0011235813 on 2012-04-11
> **tunnafish said:**
> thanks everyone for trying to help , now----- out IT man helped me

he had to reinstall firefox , as one of the latest updates seems

was not compatible  with the version of Firefox I had , well that worked,

but now I have another problem ,----email , when I try to send a email this 

is what I keep getting ,       An error occurred sending mail: The mail server sent an incorrect greeting:  #4.4.5 Too many connections to this listener..


:confused:   please anyone help

                                  tunnafish

What client are you using? Thunderbird? Anyway, it sounds like you have another client connected or maybe your viewing it in the browser?

---

