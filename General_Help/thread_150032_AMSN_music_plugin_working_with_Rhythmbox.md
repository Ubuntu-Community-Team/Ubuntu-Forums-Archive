---
title: "AMSN music plugin working with Rhythmbox"
date: 2006-03-25
forum: General Help
---

### Post by xiaoxin on 2006-03-25
Hi all

For those that are interested, I modified the music plugin for amsn so it will work with rhythmbox.
I have tested it for a while and it seems to work alright.

So enjoy.

---

### Post by rowanparker on 2006-05-09
Good one man!

---

### Post by xiaoxin on 2006-05-10
Thanks :)

---

### Post by bored2k on 2006-05-10
Can we have a screenshot of how it looks? When I tried it, it actually inserted the song _in_ the nickname rather than the away msg, like it should (kopete does this).

---

### Post by xiaoxin on 2006-05-18
Who says how it should work?
It puts the artist - title in the personal message space.
Just like it works in the windows msn.

---

### Post by xiaoxin on 2006-05-18
in fact if i remember correctly the kopete away message is the same as the msn/amsn personal message.

---

### Post by rowanparker on 2006-06-13
Sorry to get going an old topic but i can't get this to work.

I put the plugin in the correct folder, it loads, I configure it. Still it doesn't work, it just doesn't change the PM. Any ideas?

Thanks, Rowan.

---

### Post by Zaggy on 2006-10-10
I get the 'show in nickname' part working, but the actual slashcommand /sendsong or /showsong won't work :<  This needs a better readme, or I'm missing something

<edit>
Got it working!
Feel free to mail me using this forum about the plugin.
</edit>

---

### Post by Juan_VCS on 2006-11-04
[COLOR="DimGray"]How is this configured exactly? Instead of the song showing, I get a message that says "unknown option --print-playing"[/COLOR]

EDIT: Actually that was because the command to obtain the current song wasn't *rhythmbox --print-playing*, it was *rhythmbox-client --print-playing*. I modified that line on the plugin, but the song isn't showing on amsn. Any suggestions?

---

### Post by nightangelnp on 2006-11-04
I get the same error and the song isnt showing in personal message

instead it shows the error

EDIT-

I did what Juan_CVS told, and also changed to "SONG" in config.

---

### Post by Juan_VCS on 2006-11-05
Got it working too, and I don't need to choose "song" in config (doesn't change anything for me anyway).

This is what my *inforhythmbox* file says now:

```
#! /bin/sh
if [ -z "$(pidof rhythmbox)" ]; then
	echo 0
else 
	echo ""
	rhythmbox-client --print-playing
fi
exit 0
```

---

### Post by xiaoxin on 2006-11-07
yes i guess displaying the songinfo was changed in rhythmbox.
I also found out it is rhythmbox-client now.

I updated the file. and is working again.
It can be downloaded in the first post.

---

### Post by silvio on 2006-11-08
thank you verymuch. finally the plugins works even with RB :D

---

### Post by nicoladimaria on 2006-11-17
it works.
do not upgrade your plugin (amsn will eventually ask) because it won't work anymore. By the way this plugins sucks, we need a better one

---

### Post by qrm on 2006-12-12
thank you so much for this :) finally got it working

---

### Post by alimnios72 on 2007-01-10
Hi, i'm a newbie, what exactly i have to do? I read i need to send some file into some folder or something like that, then what?
I hope someone could help me, and sorry if my question sounds really stupid.

Keep rocking guys

---

### Post by Juan_VCS on 2007-01-10
Just get the file in the first post and uncompress it to ~/.amsn/plugins (~ stands for your user's home directory, as in /home/username, and the amsn folder is hidden in case you don't see it at first - press control+h); or if you want all of the users to use it, copy it to /usr/share/amsn/plugins.

Then just go to the plugins selector in amsn and you're all done.

---

### Post by Platonov on 2007-02-09
works great - thx! :grin:

---

### Post by eowang on 2007-07-29
Hi. My name is Giorgio. I'm italian.
Nice work :)

---

### Post by blackdalek on 2007-08-12
Something very odd was just happening with this plug-in.
I quit Rhythmbox while aMSN was running and a few seconds later Rhythmbox restarted all by itself when aMSN wanted to update the song playing info. Weird...
And so I quit RB again, and this time I quit aMSN too.
Now I restarted aMSN and zappp! - it launched Rhythmbox again.
I quit both again, and restarted aMSN - again Rhythmbox launched after a few seconds.

I don't know what was causing it, but now I can't get it to happen again and Rhythmbox is staying quit when I quit it.

Any ideas on what was causing this freak occurrence? Is it normal for an aMSN to be able to start another app like that?

---

### Post by biebel on 2007-09-11
Works like a charm. Thanks!

---

### Post by Onomzio on 2007-09-17
Thank u guys!!! 
it works fine with my linux distribution (mandriva)  :)

---

### Post by simon2626 on 2007-09-26
After using this plugin for a while [ it's great thanks ] I decided I wanted to fix it a bit ;)

The attached version now correctly respects the properties to select which part of song to display, and updates album art.

It is also less prone to a race condition mentioned earlier that makes a new instance of rhythmbox start :>

---

### Post by SolitaryShell on 2007-10-18
Thank you...

Sara : )

---

### Post by magnus0 on 2008-02-24
Where do I put the file to use it?

---

### Post by Juan_VCS on 2008-02-24
[http://ubuntuforums.org/showpost.php?p=1992158&postcount=17](http://ubuntuforums.org/showpost.php?p=1992158&postcount=17)

---

### Post by uniCORE on 2008-02-27
> **simon2626 said:**
> After using this plugin for a while [ it's great thanks ] I decided I wanted to fix it a bit ;)

The attached version now correctly respects the properties to select which part of song to display, and updates album art.

It is also less prone to a race condition mentioned earlier that makes a new instance of rhythmbox start :>

hi , i'm new with ubuntu and i'm sitil learning stuf everyday ,
but i have no idea how to install the amsn music plugin 
i tried to add the file in synaptic but nothing happend 
got some advice?  thanks anyway

---

### Post by Eniak on 2008-03-12
thanx man, I love rb and didn't want to change player just cuz ofthe da amsn plugin :)

anyone tested the another version posted after? For now I'm not having any problems with the original one

---

### Post by Dacarlson on 2008-03-16
> **Juan_VCS said:**
> Just get the file in the first post and uncompress it to ~/.amsn/plugins (~ stands for your user's home directory, as in /home/username, and the amsn folder is hidden in case you don't see it at first - press control+h); or if you want all of the users to use it, copy it to /usr/share/amsn/plugins.

Then just go to the plugins selector in amsn and you're all done.

Error while copying to "/usr/share/amsn/plugins".
You do not have permissions to access this folder

That's the error I get. I'm new to ubuntu, but not new to operating systems. I don't quite understand how i don't have permission. I'm the only user. 

Thanks in advance.

---

### Post by Juan_VCS on 2008-03-16
[This]("https://wiki.ubuntu.com/RootSudo") should be a good read for you.

---

### Post by Dacarlson on 2008-03-16
Thanks for the read. Unfortunatly for me, i dont understand half of what I read. From my understanding there is a master user, which contains vital operating information. I need to log onto root somehow to grant access to these folders?

---

### Post by Dacarlson on 2008-03-17
So i logged on Sudo, should i be able to just drag and drop the required file in amsn direcetory?

---

### Post by joel_gil on 2008-04-27
Worked like a charm, LOVE IT!
THANKS!!

---

### Post by lukus on 2008-05-01
The entire folder called music needs to go into /usr/share/amsn/plugins for it to work.

You're gonna need to do the file copy operation as root, so open terminal, and type 'gksudo nautilus' - and copy the folder from there.

Remember to configure it from the amsn window.

---

### Post by peakshysteria on 2008-05-04
Working in Hardy Heron 64 with Rhythmbox and Amsn. Just installed it and configured it. Great work.

But I really would like it to change what's playing once the player switches song. And not at a specific time interval....

---

### Post by joel_gil on 2008-05-14
soo, it worked fine until i installed hardy

now it displays the current song on my nickname instead of on my personal message, anyone else has this problem?

thanks in advance

---

### Post by peakshysteria on 2008-05-15
Can't make it work anymore now.

Edit:

Working fine now again. Not sure yet, but looks like the plugin needs to be configured every time you start Amsn. Looks like it's associating now playing with XMMS each time you log in. If your using something else it's needs to be configured before it'll work. Then it takes 30 second before it's working with the default settings. Running three simultaneous Amsns at once now. All working good now. Logging out and restarting one of them showed the plugin working like it should after 30 seconds (default for checking for now playing). I'll come back if there are changes to this.

---

