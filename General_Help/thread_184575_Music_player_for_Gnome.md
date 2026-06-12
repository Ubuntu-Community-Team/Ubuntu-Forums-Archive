---
title: "Music player for Gnome"
date: 2006-05-30
forum: General Help
---

### Post by Lasse_ on 2006-05-30
Hi!

I'm looking for a good, iTunes -like music player for Gnome. 

I have tried amaroK, XMMS and Rhythmbox so far. AmaroK is pretty nice but it's too slow ( on P4 3,4 GHz, 1 Gb DDR ), it takes far too much time to scan the collection ( around 3000 mp3's ) and sometimes amaroK starts to crunch some number, CPU usage climbs to 100% for a while. When I was using Windows I didn't like WinAmp so XMMS isn't what I'm looking for. Rhythmbox is very close to iTunes but it crashes (?) while scanning the collection.

Do I have any other options than install Windows again?

 - Lasse

---

### Post by frodon on 2006-05-30
You can try : banshee, muine, quod libet and listen which are greet music players too.

---

### Post by andlinux21 on 2006-05-30
banshee never heard of it is it i:confused: n the repos?

---

### Post by XQC on 2006-05-30
How about typing the name in Synaptic? ;)

---

### Post by Lasse_ on 2006-05-30
Frodon, thanks a lot.

This Banshee looks like just what I was looking for. It's pretty fast and it has this iTunes look. Banshee is going in for some serious testing.

And it's in the repos, just type sudo apt-get install banshee.

 - Lasse

---

### Post by mynimal on 2006-05-30
[QUOTE=Lasse_]Frodon, thanks a lot.

This Banshee looks like just what I was looking for. It's pretty fast and it has this iTunes look. Banshee is going in for some serious testing.

And it's in the repos, just type sudo apt-get install banshee.

 - Lasse[/QUOTE]
Full iPod support, too. :P Is there an option for those browse panels iTunes has? I've seen them in Rythmbox, but I quite liked them. Maybe in the next release?

---

### Post by Lasse_ on 2006-05-30
[QUOTE=mynimal]Full iPod support, too. :P Is there an option for those browse panels iTunes has? I've seen them in Rythmbox, but I quite liked them. Maybe in the next release?[/QUOTE]

No browse panels in Banshee, just a big info window about the songs and a smaller playlist panel on the left. 

I like those browsers too, hope Banshee gets them at some point.

 - Lasse

---

### Post by XQC on 2006-05-30
[QUOTE=mynimal]Full iPod support, too. :P Is there an option for those browse panels iTunes has? I've seen them in Rythmbox, but I quite liked them. Maybe in the next release?[/QUOTE]
From what I've heard, browse panels will come with 0.11, also smart playlists (finally)

---

### Post by DJiNN on 2006-05-30
I downloaded Banshee the other day (Whilst doing a fresh Dapper install) in the hope of getting something like Amarok but a more GNOME compatible player....

It's not bad, and has some really good features, but for some reason keeps cutting out as it's playing tracks..... don't know why this is & can't seem to find any reason for it. Anyone else having this problem or am i the only one? :)

DJiNN

---

### Post by FredB on 2006-05-30
I agree about the slowness of Amarok. I am using with pleasure Rythmbox.

---

### Post by frodon on 2006-05-30
I love rythmbox too ;) it miss some features like tag editing that quod libet and listen have but i love it anyway.

---

### Post by Lasse_ on 2006-05-30
[QUOTE=FredB]I agree about the slowness of Amarok. I am using with pleasure Rythmbox.[/QUOTE]

On my system amaroK runs quite smoothly when it has completed creating the library. What bothers me in amaroK is that about every 15 minutes it starts to do something what takes 50 - 100 % of my processing capacity ( for five minutes or so ). 

There is also a small pause if you change a track while amaroK is playing something. I could live with that lag but the processor usage is quite disturbing, my HP has some crappy fans which gets very loud when the CPU temp rise.

 - Lasse

---

### Post by Minyaliel on 2006-05-30
In gnome, I use Exaile - it's excellent, much better than banshee.

---

### Post by nemesa on 2006-05-30
Exaile? Would you post a link? I can't find it in synaptic...

---

### Post by FISHERMAN on 2006-05-30
I(former iTunes user) use Quod Libet and like it a lot.

---

### Post by nemesa on 2006-05-30
Sorry.. I find it... ;-)

---

### Post by Noah0504 on 2006-05-30
[QUOTE=frodon]I love rythmbox too ;) it miss some features like tag editing that quod libet and listen have but i love it anyway.[/QUOTE]
I also use Rhythmbox.  I suggest installing Ex Falso for any tag editing that you do.  It's the tagging engine for Quod Libet, which means it's good!

---

### Post by Lasse_ on 2006-05-30
Exaile looks great too, it's pretty close to Banshee but with some twists borrowed from amaroK.

I didn't get it to work with apt so here is Breezy binaries for those who share this problem: [http://www.harold.liberty-host.com/exaile.tar.gz](http://www.harold.liberty-host.com/exaile.tar.gz)

AmaroK would still be my player of choice if it worked with out torturing the CPU. I think it has something to do with that database system amaroK uses. Only the default database SQLite (?) works on my machine and at some point amaroK warned about it to be a little slower than the other two. But it still puzzles me how a music player ( very advanced one though ) can make a reasonably powerful computer hit the ground. Is it just an incompatibility issue between Gnome and a native KDE application or what? 

Amarok has these great features like built in support for last.fm, a robust library system and there's a xchat script for controlling it and to /me what song I'm listening. Those are some important features that other players lack.

I wish there was a native linux version of iTunes.

 - Lasse

---

### Post by Noah0504 on 2006-05-30
[QUOTE=Lasse_]I wish there was a native linux version of iTunes.[/QUOTE]
I think most of us do!  ;)

---

### Post by AirRaven on 2006-05-30
Just a small note- the [MusikCube](http://musikcube.com/) team were working on a port of MusikCube to Linux a while ago. "MusikBox", I believe it was called. Might be an idea to check up on it if it ever gets finished- the Windows MusikCube is far and away the best music player I have *ever* used. It does everything you need in a music player, and works insanely fast. Support for plugins as well.

---

### Post by Lasse_ on 2006-05-30
[QUOTE=AirRaven]Just a small note- the [MusikCube](http://musikcube.com/) team were working on a port of MusikCube to Linux a while ago. "MusikBox", I believe it was called. Might be an idea to check up on it if it ever gets finished- the Windows MusikCube is far and away the best music player I have *ever* used. It does everything you need in a music player, and works insanely fast. Support for plugins as well.[/QUOTE]

There isn't much info about MusikBox, only a couple threads at Cube's forums. Even Google doesn't know much about it. The Windows version looks really good in the screenshots. There were some speculation at the forums about the developers wanting to finish the Windows version before getting into making the Linux counterpart. Time will tell.

 - Lasse

EDIT: Fixed a typo.

---

### Post by !nkubus on 2006-05-30
[QUOTE=DJiNN]I downloaded Banshee the other day (Whilst doing a fresh Dapper install) in the hope of getting something like Amarok but a more GNOME compatible player....

It's not bad, and has some really good features, but for some reason keeps cutting out as it's playing tracks..... don't know why this is & can't seem to find any reason for it. Anyone else having this problem or am i the only one? :)

DJiNN[/QUOTE]


I have exactly the same issue with Banshee. Too bas as it looks like a good player, really clean and support plugins :).Maby one for my "Rockboxed Ipod"  in the future :.

But I couldn't find why the song is skipping a lot. I'm sure it's a Gstreamer buffer issue but where do I change that?

My system is:
AMD Athlo64 3800+ Dual Core
1go ram

it shouldn't skip at all with this config :(

---

### Post by MetalMusicAddict on 2006-05-30
My vote is for [Listen]("http://listengnome.free.fr/"). Currently only for Dapper though.

---

### Post by DJiNN on 2006-05-31
[quote=!nkubus]I have exactly the same issue with Banshee. Too bas as it looks like a good player, really clean and support plugins :).Maby one for my &quot;Rockboxed Ipod&quot;  in the future :.

But I couldn't find why the song is skipping a lot. I'm sure it's a Gstreamer buffer issue but where do I change that?

My system is:
AMD Athlo64 3800+ Dual Core
1go ram

it shouldn't skip at all with this config :([/quote]      Yep, same here..... strange isn't it? I'll look into the Gstreamer thing when i get some time & post anything here if i find it.  In the meantime, i've started using "Exaile" as mentioned by one of the previous posters.... It's VERY good, VERY small but quite a powerful little program, so i'll be sticking with that for a while i think.  If you want to give it a go & you're using Dapper, just use the "Gdebi" command & it will install all of the dependencies as well. Unfortunately in Breezy you have to do it all manually! :(  DJiNN

---

### Post by bluenova on 2006-05-31
Amarok with a mysql database rather than sqlite. On a system like that with 3000 mp3's it'll be the best solution. It's the database that slows amarok down. Switch over to mysql and it'll run much faster.

---

### Post by matrooswolf on 2006-06-10
[QUOTE=Lasse_]On my system amaroK runs quite smoothly when it has completed creating the library. What bothers me in amaroK is that about every 15 minutes it starts to do something what takes 50 - 100 % of my processing capacity ( for five minutes or so ). 
[/QUOTE]
I had the same problem.  Turning off the automatic scanning for updates of the database fixed that.  (settings/configure amarok/collection/)  There is a button (when you are in the tab collection) to update the database when you want.  This actually works very well, only takes a couple of seconds on my 80GB library.

Now Amarok runs picobello! (1.4.0)

I tried a lot of other ones (I liked Listen) (still have to try Exhaile), but Amarok still beats them for me.  I also like the integration with K3b to burn songs.  And the howling wolf Icon is unbeatable ;)

---

### Post by j1mc on 2006-06-10
It looks like it is a long ways off, but [Songbird]("http://www.songbirdnest.com/") sure as heck *looks* like it's going to be a great media player.  :-)  They're using some of the Mozilla codebase for the project (should allow peeps to make cool extensions), and the people behind it have worked on Winamp, the AOL Media Player and the Yahoo Music Engine . . .  it all seems pretty promising.

---

### Post by can3p on 2006-06-13
I use mpd + gmpc, both from svn :)

---

### Post by Edward The Bonobo on 2006-06-13
I want to use Banshee to manage my iPod, having got impatient with gtkpod.

The Banshee documentation is...er...minimal.  Can someone talk me through synching new tracks?  Because I have a tiny HD, I won't be storing my whole library on the PC.  I'll just want to shnch a few albums at a time from HD to iPod.  Is this the 'Manual Synch' option?

---

### Post by Ben Logan on 2006-06-16
[QUOTE=j1mc]It looks like it is a long ways off, but [Songbird]("http://www.songbirdnest.com/") sure as heck *looks* like it's going to be a great media player.  :-)  They're using some of the Mozilla codebase for the project (should allow peeps to make cool extensions), and the people behind it have worked on Winamp, the AOL Media Player and the Yahoo Music Engine . . .  it all seems pretty promising.[/QUOTE]

Ditto.  Songbird LOOKS awesome.

---

### Post by tranceash on 2006-06-17
guys check out Listen its amazing just like amarok but clean and fast interface

---

### Post by lee1026 on 2006-06-17
Anyone here know a basic music player for what I want to do?
1. I want to sort my music based on ratings.
2. I want to be able to have the entire collection in a single playlist.
3. I want to be able to have the computer generate playlists based on those ratings.
4. I need something fast because in entire library mode, ALL of the linux music players I have used have became extremely slow. In windows, I used musikcube.

---

