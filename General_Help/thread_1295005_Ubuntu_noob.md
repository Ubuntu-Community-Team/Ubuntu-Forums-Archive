---
title: "Ubuntu noob"
date: 2009-10-19
forum: General Help
---

### Post by uBuNoobTu on 2009-10-19
Alright so I am BRAND NEW to Ubuntu.  I used to have a Mac and I grew up on Microsoft so I understand those pretty easy.  Here is my problem, I am trying to install Limewire for Ubuntu but it says that I need to shut down update manager, syntetsis, and something that starts with an a.  How do I turn this off so I can d/l some stuff from Limewire.  And can anyone please tell me if I can get iTunes or something very similar to iTunes.  If not I am totally getting rid of ubuntu and putting XP on here. I don't want to but if I can't get my music or have a music player that easily organises my **** I am gonna beat up the first homeless guy I see.

---

### Post by Johnny B on 2009-10-19
threatening to leave ubuntu only hurts yourself, not the [community.]("http://ubuntuforums.org/showthread.php?t=634322")

only one package manager is allowed to run at a time, close the others.

---

### Post by buntunub on 2009-10-19
Linux is not Windows and the way you did things on Windows wont work here. Its free and open source and so you will have to learn how to do things the Linux way. Its not for everyone, but those who take the time to learn usually stick with it over Windows for all that they can. There are some things (iTunes, some games, and some extremely closed and proprietary apps like them) that will only work on Windows, or work well anyway. There are some guides out there which one can find using Google that can walk you through getting iTunes working on Linux, but I have never heard of anyone getting it to work 100%. Linux does have a ton of alternatives for pretty much everything however, and you might want to give some of them a go.

---

### Post by vinutux on 2009-10-19
Close all apt-fronends like add/remoove, Synaptic, Update manager on the top panel...etc

for iTunes....try Banshee or Songbird

Or you can install iTunes.exe here via WINE........

---

### Post by aftermgates on 2009-10-19
Regarding Limewire, I would suggest using Frostwire instead. It's easy to set up, easy to use *and* open source.

[http://www.frostwire.com/?id=home]("http://www.frostwire.com/?id=home")

Regarding iTunes, there are several media players for Ubuntu that offer iPod support, including Rhythmbox which comes pre-installed.

---

### Post by |Mitch| on 2009-10-19
As for Limewire, I'd suggest something like Frostwire instead. Or you can get something like deluge and just start downloading torrents. 

Rhythmbox & VLC do all the media handling I need to do. 

The package ubuntu-restricted-extras in Synaptic will get you all the codecs you will need to play media.

---

### Post by uBuNoobTu on 2009-10-19
There is nothing open.  No manager, nothing.  But it still will not let me install anything.  I tried to install frostwire but it says the samething.

---

### Post by |Mitch| on 2009-10-19
Might help to see exactly what your error says; not just "it won't work"

---

### Post by mikey12561 on 2009-10-19
> **|Mitch| said:**
> Might help to see exactly what your error says; not just "it won't work"
Not really understanding why you could be getting this problem. I just installed frost wire just two days ago without problems.

---

### Post by tabibito on 2009-10-19
Perhaps you can tell us more on how exactly you're installing limewire. Are you installing it from synaptic or by any other way?

As for iTunes's alternative you could try SongBird or Amarok. Both are pretty decent for me.

---

### Post by iMisspell on 2009-10-19
As for iTunes, my suggestion - diched it along, with apples ipod bios/firmware and installed _[rockbox]("http://www.google.com/search?q=Rockbox+Jukebox+Firmware")_. 
Thats the route i took about two weeks after i bought my first ipod... and im so happy i did.

Once you are running rockbox you dont need iTunes, just plug your ipod (or other device, rockbox supports alot of different players) and your mp3s are sitting in a folder(s) just like your hard-drive (not number "encrypted" like iTunes does). When you want to add a song/album you just copy it ot your ipod just as if you where copying it to another hard-drive then just re-initialize next time you turn your ipod on.

Head over to a friends house, just plug your ipod in and they can copy what ever songs they like, no iTunes needed.

When you want to play something off your ipod, just fire up what ever player you want and your good to go.

Only disadvantage ive found (and this was over a year ago, so it could have change now) is that i have a Denon AVR-2807 and when i plug my ipod into its docking station the ipod will not display the play list on the TV and Denons AV controller will not control the ipod. But it plays fine if i get up and press the play button on the ipod :)

Rockbox is something to look into if "you" have not.

_

---

### Post by invitingdopeman on 2009-10-19
hey dude im also kinda new to this stuff but as the more i learn the better it becomes Linux in totally deffernt then windows you have find most of the stuff yourself but these forums are great for your problums lot of peeps know what there doing on here make sure you are downloading the Linux version of LIMEWIRE and it should be fine if you need more help feel free to contact me [email]royrobb41388@hotmail.com[/email]

---

### Post by vinutux on 2009-10-19
Restart your system make sure no update manager working on background then install limewire.deb with double click 

or 

open terminal Applicatio > Accessories > Terminal

and type ```
sudo dpkg -i /[COLOR="Red"]pathtoyourdebfile[/COLOR]
```

You can simple drag file to terminal for file path

---

### Post by uBuNoobTu on 2009-10-19
I got Limewire.  I'm sorry I was all pissed off but I have gone from Mac to Linux and I just don't understand all this stuff.  But thanks for all the help guys.  And I know most of you hate iTunes but if anyone can figure out how to hack and get that **** to work on Ubuntu please let me know.

---

### Post by Vunutus on 2009-10-19
> **uBuNoobTu said:**
> I got Limewire.  I'm sorry I was all pissed off but I have gone from Mac to Linux and I just don't understand all this stuff.  But thanks for all the help guys.  And I know most of you hate iTunes but if anyone can figure out how to hack and get that **** to work on Ubuntu please let me know.

You're going at this from the perspective that you HAVE to use the programs you used before on Windows. With some exceptions, this usually isn't true. There are often times free/open-source programs that perform the exact same task you're trying to accomplish, and oftentimes do it BETTER than their proprietary alternative.

If you're dead-set on getting iTunes to work, check out the [Wine AppDB entry on it]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347"), but be warned that it doesn't appear many people, if any, have gotten it to work successfully in Wine.

As suggested above, there are excellent alternatives to iTunes such as Banshee and Songbird, or my favorite, Amarok.

---

### Post by vinutux on 2009-10-19
> **vunutus said:**
> you're going at this from the perspective that you have to use the programs you used before on windows. With some exceptions, this usually isn't true. There are often times free/open-source programs that perform the exact same task you're trying to accomplish, and oftentimes do it better than their proprietary alternative.

If you're dead-set on getting itunes to work, check out the [wine appdb entry on it]("http://appdb.winehq.org/objectmanager.php?sclass=application&iid=1347"), but be warned that it doesn't appear many people, if any, have gotten it to work successfully in wine.

As suggested above, there are excellent alternatives to itunes such as banshee and songbird, or my favorite, amarok.

+1

---

### Post by vinutux on 2009-10-19
If you really addicted to itunes go to the wine way (install wine and install iTunes.exe/itunes 4 windows)

I installerd onece version 8 its worked for me.... But trash it coz of it need more resources (It is not a native app...It is not designed for linux)

I am happy with Banshee/Songbird

.............:)

---

### Post by guriinii on 2009-10-19
Here is a easy guide to using the Terminal:

[http://ubuntuforums.org/showthread.php?t=73885](http://ubuntuforums.org/showthread.php?t=73885)

---

