---
title: "My experiece with Ubuntu so far + Misc. questions"
date: 2010-04-02
forum: General Help
---

### Post by aCsbD6N5xj on 2010-04-02
Hello world.

I did a full install of Ubuntu 9.10 on my laptop 2  days ago, via unetbootin, and i can say that i've been really impressed  so far. The install time & ease, the boot time, the shutdown time;  everything is so much faster than XP... i hate it! jk :).

My  experience so far has nothing to do with my last year's dual boot  fiasco. What could be considered as bloat on Windows, like compiz, still  does not hit on my laptop overall performance and trust me, that POS is  kinda slow thx to faulty hardware and some mistakes i made on Windows,  like Norton.

But I still have a few things that i'd like to  clarify + "complaints". Let's start with the questions.

- How do I  uninstall software? I've got Songbird which doesn't work quite well.  But it does not even appear in the Installed Software list from the  Software Centre.

- Is amarok better than rhythmbox? What i miss  from Windows are global hotkeys for play/pause/stop and i don't know  which media player can do that on linux. I also need MSC support.

-  How do I update firefox? I upgraded from 3.5.8 to 3.6.2 yesterday using  the Mozilla Build. Now I have 2 ffx 'executables' in my menu, though  they fortunately both use my profile. Plus, both of them won't let me  update to 3.6.3 which was released yesterday :S. I don't wanna be left  with 3 'exes'.

- I use ssh to connect to school from home.  Instead of launching terminal and typing 'ssh username.at.hostname', i want to have some sort of shorcut that  will already type this for me when i launch this copy of the terminal  and just ask me for my password. I tried going into properties and type  it but when i launch it only asks me for my password, then nothing. And  when i change the name from 'Terminal' to something else, it won't  launch at all.

- Is a software firewall on linux necessary? There's already a router/firewall at my home's shared connection. But i was still using ZoneAlarm on Windows though.

Now the 'complaints'

- My laptop becomes  laggy whenever i plug in my Sansa Fuze and start browsing it.

-  Sometimes ubuntu  randomly freezes & crashes :S. But at least it just logs off  and still perform fast after that.

So,  in a nutshell, I can;t wait to have a new laptop, install ubuntu and  start afresh. And if now i could also install MS Office via wine (that  didn't work last year), everything would be perfect, full circle :D

Thx  for reading my long post and replying :D

PS. To all Canadians,  is there any place where i could possibly buy OS-free laptops or at  least get the pretty ones from the stores (coz i love aesthetics too,  sue me!!!) and ask for a discount & no Windows (all w/o buying  online) ?

---

### Post by Sin@Sin-Sacrifice on 2010-04-02
Questions:

You can uninstall software by typing ```
sudo apt-get remove --purge package-name
``` into a terminal or by going into Synaptic and marking package-name for complete removal.

Most of the media players support hot keys. You just have to either enable the plugin or make the PC recognize the hardware (for stop, play, pause, etc... buttons) I would start with the plugins. I'm guessing you can find them in the media player's properties. Whether amarok or rhythmbox is better is completely subjective. They're free... try them out. I like rhythmbox and audatious.

Firefox will update on its own just like in windows. You'll get a popup saying there is an update and you select whether or not to install. It might not update on it's own if you havn't done system updates though... not sure on that one. I always get all the updates first off (usually bug fixes).

Not sure about the ssh thing. I guess you could make a script or a Desktop launcher...

Double the protection is better than half. If you have it then use it. Probably not completely necessary but it doesn't hurt. I use both.

Complaints:

Updates might fix that... and there's tons of diagnostic tools built into Ubuntu.

---

### Post by aCsbD6N5xj on 2010-04-02
> **Sin@Sin-Sacrifice said:**
> Questions:

You can uninstall software by typing ```
sudo apt-get remove --purge package-name
``` into a terminal or by going into Synaptic and marking package-name for complete removal.

Most of the media players support hot keys. You just have to either enable the plugin or make the PC recognize the hardware (for stop, play, pause, etc... buttons) I would start with the plugins. I'm guessing you can find them in the media player's properties. Whether amarok or rhythmbox is better is completely subjective. They're free... try them out. I like rhythmbox and audatious.

Firefox will update on its own just like in windows. You'll get a popup saying there is an update and you select whether or not to install. It might not update on it's own if you havn't done system updates though... not sure on that one. I always get all the updates first off (usually bug fixes).

Not sure about the ssh thing. I guess you could make a script or a Desktop launcher...

Double the protection is better than half. If you have it then use it. Probably not completely necessary but it doesn't hurt. I use both.

Complaints:

Updates might fix that... and there's tons of diagnostic tools built into Ubuntu.

Thx for the answer.
 
 - Silly me forgot that I've got a media/internet keyboard with the  play/pause etc.. buttons already there. I was so used with the custom  shortcuts in Winamp i completely forgot about those.
 
 - When i typed songbird in search, it gave me a lot of stuff. I removed  songbird and it's no more in the App menu and search doesn't return  anything.  But in terminal before uninstalling, it told me only 119kb  disk space would be  freed. Weird...
 
 - Concerning ffx updates, it tells me the updates are available but that  i don't have permissions to apply them.
 
 - Sometimes CPU usage reaches 100% and that's when ubuntu crashes. But  it reaches that value randomly, whether i have programs like firefox or  amsn, open or not. What diagnostic tool should i use?
 
 - I did a sh script with the ssh command as the only line. Running it from the desktop opens gedit  :(
 
 - And what software firewall do you use on linux then?

---

### Post by nem75 on 2010-04-02
> **BucketBob said:**
> 
- Is amarok better than rhythmbox? What i miss  from Windows are global hotkeys for play/pause/stop and i don't know  which media player can do that on linux. I also need MSC support.

As was pointed out, what's "better" largely depends on what you need. Global hot keys in one form or other should be available for pretty much every major media player.

Amarok 1.4.x was great, the reception of Amarok 2 has been quite mixed. Still lots of great stuff in it though, but still some missing (equalizer for one) or not working right (importing old music collections from version 1.4, but of course that's of no concern to you).

Also keep in mind that Amarok is a KDE application and as such will bring lots of KDE/Qt dependencies into your system. No problem in itself, but mixing apps from different desktop environments might slow your system down (depends on the hardware too, of course).

> - Is a software firewall on linux necessary? There's already a router/firewall at my home's shared connection. But i was still using ZoneAlarm on Windows though.

Since Windows is still much more widespread than Linux desktops you will have a very hard time finding any viruses, trojans etc. that even run on Linux. So if you're behind a home router you shouldn't need any additional firewall at all.

If you often receive dubios e-mails and forward them you might want to consider installing a virus scanner so you don't spread Windows viruses. ;)

> Now the 'complaints'

- My laptop becomes  laggy whenever i plug in my Sansa Fuze and start browsing it.

-  Sometimes ubuntu  randomly freezes & crashes :S. But at least it just logs off  and still perform fast after that.

If you'd describe those problems a bit more in detail, maybe someone would even be able to help you solve them.

---

### Post by aCsbD6N5xj on 2010-04-02
> **nem75 said:**
> As was pointed out, what's "better" largely depends on what you need. Global hot keys in one form or other should be available for pretty much every major media player.

Amarok 1.4.x was great, the reception of Amarok 2 has been quite mixed. Still lots of great stuff in it though, but still some missing (equalizer for one) or not working right (importing old music collections from version 1.4, but of course that's of no concern to you).

Also keep in mind that Amarok is a KDE application and as such will bring lots of KDE/Qt dependencies into your system. No problem in itself, but mixing apps from different desktop environments might slow your system down (depends on the hardware too, of course).



Since Windows is still much more widespread than Linux desktops you will have a very hard time finding any viruses, trojans etc. that even run on Linux. So if you're behind a home router you shouldn't need any additional firewall at all.

If you often receive dubios e-mails and forward them you might want to consider installing a virus scanner so you don't spread Windows viruses. ;)



If you'd describe those problems a bit more in detail, maybe someone would even be able to help you solve them.


Concerning the crashes, it's too random for me to point out the culprit. It just reaches 100% CPU Usage, mostly when heavy apps are open, like firefox or amsn. I thought rhythmbox and songbird were the culprits as they were playing songs like a broken record whenever the crashes occured.

Concerning my Sansa Fuze, when i plug it to charge itself it's ok. But when i browse through the files using 'Explorer' the system becomes laggy. Rhythmbox does not seem to detect my mp3 player, even with the 'Open with Rhythmbox option'.

And for the firewall, I was only worried about intrusions, not viruses. Nobody else but me will be using my laptop anyways. And my password is still needed for system changes and there are no software KeyLoggers for linux right? So i guess the router/firewall will be enough in my case *relieved*

---

### Post by aCsbD6N5xj on 2010-04-02
i forgot to mention that i already have media keys on my keyboard. i didn't need global hotkeys in the first place except for winamp in XP. i won't install amarok then, at least not on my current laptop. too bad for msc suport :(

---

### Post by burton247 on 2010-04-02
I prefer rhythm box tbh, but thats just my opinion, I'm not a fan of having the KDE style themes on my desktop, I don't like them.

As for the small space freed: uninstalling something will only remove that app, not the dependencies it brings with it. in the terminal run:

```
sudo apt-get autoremove
```

This looks for unused dependencies and will uninstall them for you

---

### Post by aCsbD6N5xj on 2010-04-02
thx for the tip and command. I'll just keep things 'simple'. I'm still having MSC issues in Rhythmbox though

---

### Post by akakingess on 2010-04-02
> **BucketBob said:**
> Concerning the crashes, it's too random for me to point out the culprit. It just reaches 100% CPU Usage, mostly when heavy apps are open, like firefox or amsn. I thought rhythmbox and songbird were the culprits as they were playing songs like a broken record whenever the crashes occured.

Is it possible for you to have 'top' or 'htop' running in the background and see what happens in there when the computer freezes, it may help narrow things down a bit. Both need to be installed, but you can just choose one of them as they are basically the same thing (htop just has colors), and they are basically like 'Task Manager' within Windows in that those programs are watching all apps, daemons, etc. and the resources that they are using up. Hope this helps, if not, I would rather let you know then never tell you about them. Good luck to you.

---

### Post by kokkus on 2010-04-02
Winamp is still the best media player in my book and it works just as good in ubuntu (under Wine). Rhythmbox is a great software if you use to listen to radio and podcasts since you can simply add the stream or rss link into the program.
You can change the hotkeys for play/pause/stop etc. in Keyboard Shortkuts (system>pref>keyboard shortcuts).
All software supported by Ubuntu will be updated automatically in the Update Manager.

---

### Post by nem75 on 2010-04-02
> **akakingess said:**
> Is it possible for you to have 'top' or 'htop' running in the background and see what happens in there when the computer freezes, it may help narrow things down a bit. Both need to be installed,

top actually does not need to be installed manually, it comes with the basic setup.

---

### Post by whitethorn on 2010-04-02
If you want to connect to a ssh computer I would suggest setting up a shortcut in places in Nautilus.  To do that open nautilus then in the top type in your address.  

ssh://username@whatever.com

It should then ask you for the password, you can then add a bookmark (in nautilus) and now you have a direct connection to it from places and from nautilus.

---

### Post by aCsbD6N5xj on 2010-04-02
> **kokkus said:**
> Winamp is still the best media player in my book and it works just as good in ubuntu (under Wine). Rhythmbox is a great software if you use to listen to radio and podcasts since you can simply add the stream or rss link into the program.
You can change the hotkeys for play/pause/stop etc. in Keyboard Shortkuts (system>pref>keyboard shortcuts).
All software supported by Ubuntu will be updated automatically in the Update Manager.

Thx for the tip on the shortcuts. Right now i won't concentrate on Wine, because of the crashes. I forgot to mention from my first post that i already have media buttons on my keyboards. No need for global shortcuts :)

---

### Post by aCsbD6N5xj on 2010-04-02
> **whitethorn said:**
> If you want to connect to a ssh computer I would suggest setting up a shortcut in places in Nautilus.  To do that open nautilus then in the top type in your address.  

ssh://username@whatever.com

It should then ask you for the password, you can then add a bookmark (in nautilus) and now you have a direct connection to it from places and from nautilus.

thx i'll try that too. i also did a one-line script which works just fine.

---

### Post by aCsbD6N5xj on 2010-04-02
> **nem75 said:**
> top actually does not need to be installed manually, it comes with the basic setup.

hmmm i have system monitor on my top panel and i don't see top nor htop in the processes list. Where do i get that?

---

### Post by nem75 on 2010-04-02
Well, you will have to actually launch top to see top itself in any process list. :)

To do that, hit Alt+F2, enter
```
top
```
and check the "run in terminal" checkbox before executing the command. You should then see a terminal window with a running instance of "top".

---

### Post by aCsbD6N5xj on 2010-04-02
> **nem75 said:**
> Well, you will have to actually launch top to see top itself in any process list. :)

To do that, hit Alt+F2, enter
```
top
```and check the "run in terminal" checkbox before executing the command. You should then see a terminal window with a running instance of "top".

Ok. I've got it. How do i use it now? If my laptop crashes my cursor will be frozen anyways :confused: So far my laptop hasn't crashed yet. FFx is the only 'heavy app' running right now,

---

### Post by nem75 on 2010-04-03
I guess what akakingess was suggesting is: let "top" run (arguably you don't need "top" at all, you could just run Gnome's System Monitor with the Process tab open, rows sorted descending by "% CPU") and when your laptop freezes up, check which processes were using the most resources at the time.

---

### Post by drifter2502 on 2010-04-03
You could try downloading songbird from here..[http://skyzim.com/songbird-1-2-0-installer/](http://skyzim.com/songbird-1-2-0-installer/)
I had problems too when installing from a package manager.

---

### Post by The Cog on 2010-04-03
Re updating firefox:

The firefox that comes with Ubuntu has to be updated by loading an update from the Ubuntu repositories. This will happen in the fullness of time.

The firefox that you downloaded direct from mozilla will need updating by yourself. If you installed it into your home folder then I excpect that help/check for updates should work. If (like me) you installed it outside your home folder (mine is in /opt) then you can't update it from the help menu because as a user you don't have rights to write outside your home folder. I update mine by closing all firefox windows, then launching **gksu firefox** to launch firefox as root. Then use help/check for updates, restart firefox (which installs the downloaded update) then quit before restarting firefox as a normal user again.
**NEVER** go browsing the internet with a root firefox - it's a big security no-no.

---

### Post by nothingspecial on 2010-04-03
I don`t know if you are aware of them or not but have a look into aliases. I connect to multiple machine through ssh. And have an alias for each.

So in my .bashrc I add a line

```
alias server='ssh -X -C -c blowfish user@address'
```

or

```
alias office='ssh -X user@address'
```

then restart bash
```

bash
```

Now if I want to connect to the server I just type server 

And if I want to connect to my office, I just type office

You can put loads of them in there for all sorts of simple operations.

---

### Post by aCsbD6N5xj on 2010-04-03
Thx everyone for your replies. I'm closing this thread now and creating a new one for the crashing problem.

---

