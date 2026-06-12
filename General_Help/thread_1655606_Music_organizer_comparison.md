---
title: "Music organizer comparison"
date: 2010-12-29
forum: General Help
---

### Post by sigixv on 2010-12-29
A short comparison of a few of the most popular music organisers for linux.
A more extensive list:
[http://en.wikipedia.org/wiki/List_of_Linux_audio_software#Audio_players]("http://en.wikipedia.org/wiki/List_of_Linux_audio_software#Audio_players")
[http://en.wikipedia.org/wiki/Comparison_of_audio_player_software]("http://en.wikipedia.org/wiki/Comparison_of_audio_player_software")

In this test it is not the goal to advocate 1 single program as an ideal solution for all. Choose yourself the application which meets your needs best. For Windows migrators: over there the situation isn't any different => [http://www.skytopia.com/project/articles/music/players.html](http://www.skytopia.com/project/articles/music/players.html)
Consider this article as a way to save yourself some time for testing all the applications to get a general idea about them *;)


Applications in this test must be able to manage a local music library, support ID3 tagging, creation of playlists and mounting/synching of mp3 players.
My focus here went mainly towards big music libraries, customization, iPod support en speed/RAM usage.

Applications which only play playlists or a single map are excluded because their goals are totally different (type XMMS). They use little RAM and are speedy, but lack the organizer functions found in the real deal.
True tag-editors are also not included. Albeit very functional in their domain, they can be used in addition to a player like XMMS, but they also fail to comply with the demands for an all-in-one application.
The possibility to run music from an external server (such as GMPC) has not been taken into account.



Testing machine:
Ubuntu 10.10 (Maverick) Linux 2.6.35-24-generic in a windows dual boot with Gnome 2.23.0 / all codecs installed
5.8 GiB RAM and Intel Quad Core: 4x 2.67GHz with HDD= 7200rpm (containing both the OS as the music library)

Music:
306.5 GB / 61917 tracks/ biggest= 383.5 MB / smallest= 11.9 kB / +- 90% MP3 @ 128 & 160kbps CBR


Take into account the programming code when considering RAM usage. The dependencies are automatically loaded when starting these applications and they all have their specific effect on the used OS and desktop environment.
Also will there be huge differences in user experience for smaller music libraries since each program uses it's specific database scripts.



_**AMAROK**_

[[IMG]http://img525.imageshack.us/img525/2421/amarok.th.png[/img]](http://img525.imageshack.us/i/amarok.png/)

Written in:      C++ (Qt)
RAM: * * * * * * 200-250 MiB (206 measured in pic)
Radio: * * * * * Yes
Video: * * * * * No
Podcast: * * * * Yes
Playlist: * * * *Yes
iPod: * * * * * *Yes
Playqueue: * * * Yes
View: * * * * * *Playlist + Browser
Custom: * * * *  Elements have limited selection and drag&drop
Plugins: * * * * Good

The application has a strong focus towards playlists and doesn't support a standard library view. General impression is very clean but not very intuitive. Operates very slow and tends to freeze often (even in KDE environment). Hellish when trying to tag large numbers of tracks. Not recommended on minimal hardware.


_**BANSHEE**_

[[IMG]http://img443.imageshack.us/img443/315/bansheec.th.png[/img]](http://img443.imageshack.us/i/bansheec.png/)

Written in: C# (Mono)
RAM: * * * *300-870 MiB (666 measured in pic)
Radio: * * *Yes
Video: * * *Yes
Podcast: * *Yes
Playlist: * Yes
iPod: * * * Yes
Playqueue: *Yes
View: * * * Elements have limited selection and drag&drop
Plugins: * *Good


A very nice application and extremely intuitive. Contains a lot of possibilities as extentions and is a true all in one media suite with very easy tagging. Is however incredibly instable, has poor library software resulting in high RAM usage. Can cause damage to files when crashing (personal experience) en will subsequently refuge to start again. Ideal application to have a hate-love affair with. 


_**CLEMENTINE**_

[[IMG]http://img189.imageshack.us/img189/1962/clementine.th.png[/img]](http://img189.imageshack.us/i/clementine.png/)

Written in: C++ (Qt) - Amarok 1.4 Fork
RAM: * * * *300-950 MiB (863 measured in pic)
Radio: * * *Yes
Video: * * *No
Podcast:  * Yes
Playlist:* *Yes
iPod: * ** *Yes
Playqueue: *Yes
View: * *   Playlist, Bibliotheek (via Smart Playlist)
Custom: * * Elements have limited selection and drag&drop
Plugins: * *Good

Clear lay-out, easy to customize en smooth operating. Strong integration with last FM (nice & ban buttons, etc). Loading libraries is very slow en turns into a memory hog and is prone to freeze or crash. Perhaps a good solution for smaller libraries.


_**EXAILE**_

[[IMG]http://img515.imageshack.us/img515/7606/exaile.th.png[/img]](http://img515.imageshack.us/i/exaile.png/)

Written in: Python - Amarok 1.4 Fork
RAM: * * * *260-500 MiB (335 measured in pic)
Radio: * * *Yes
Video: * * *No
Podcast:* * Yes
Playlist:* *Yes
iPod: * *  *Yes
Playqueue: *Yes
View: * * * Playlist, Library (via Smart Playlist)
Custom: * * Elements have limited selection and drag&drop
Plugins: * *Very good

Has a similar focus as Clementine but is far less successfull in achieving this. Has a disorganised feel to it and everything is less polished then Clementine. For instance: an iPod has to be mounted through the devices tab, whereas in Clementine all this is done automaticly. Crashes often without warning. *[size=8pt]and off course when i run it in terminal it doesn't crash... *sigh*[/size]*


_**GMUSICBROWSER**_

[[IMG]http://img191.imageshack.us/img191/5847/gmusicbrowser.th.png[/img]](http://img191.imageshack.us/i/gmusicbrowser.png/)

Written in: Perl
RAM: * * * *200-230 MiB (228 measured in pic)
Radio: * * *No
Video: * * *No
Podcast:* * No
Playlist:* *Yes
iPod: * ** *No (can be added as a file location)
Playqueue: *Yes
View: * *   Multiple possibilities with extensive options and filters
Custom: * * Elements have limited selection and drag&drop
Plugins: * *Reasonable

No-nonsense managementapplication. You have a lot of music files on your disk and want them easy accessible with the option to change the interface quickly depending on your needs at a given time? This is the application for you.
Interface is easily (and extensively) modifiable towards your needs. Tagging is good. Filtering and search options are very elaborate. It's a perfect workhorse without bloated gizmos. Interface is functional and useful before considering aesthetics. Abundance of synching mp3 players and podcast neccisates an supplementary application for these functions.


_**GUAYADEQUE**_

[[IMG]http://img6.imageshack.us/img6/5229/guayadeque.th.png[/img]](http://img6.imageshack.us/i/guayadeque.png/)

Written in: wxWidgets with SQLite database
RAM: * * * *45-60 MiB (!) (52.6 measured in pic)
Radio: * * *Yes
Video: * * *No
Podcast: * *Yes
Playlist: * Yes
iPod: * * * No* (in development)
Playqueue: *Yes
View: * * * Playlist, Library + browser, file system
Custom: * * Highly adjustable: drag&drop, size adjustments and adjustments within each element possible
Plugins: * *Fair

Easy to customize visually making it very functional and intuitive. Extremely strong database system resulting in very low memory dependencies. Tagging is ok. Junior project and therefore missing some functionality such as iPod support and limited plugins. Very promising app and already quite good. Highly recommendable for people with systems on limited RAM.



_**JAJUK**_

[[IMG]http://img63.imageshack.us/img63/7629/jajuk.th.png[/img]](http://img63.imageshack.us/i/jajuk.png/)

Written in: Java
RAM: * * * *600-1100 MiB (670 measured in pic)

I was unable to fully test this application because it was totally unuseable. Timelag after clicking and action would often exceed 1minute (without the application being grayed out).
General impressions are an ancient (even downright ugly) interface. Impressions resemble Exaile with the tree-list. The "DJ"-function seemed however promising but i was unable to test due to problems mentioned above.
Totally unuseable for large music libraries.

(end part 1)

---

### Post by sigixv on 2010-12-29
Part 2

_**JUK**_

[[IMG]http://img692.imageshack.us/img692/1904/jukbp.th.png[/img]](http://img692.imageshack.us/i/jukbp.png/)

Written in: C++ (Qt)
RAM: * * * *180 - 1200 MiB (!) (230 measured in pic)
Radio: * * *No
Video: * * *No
Podcast: * *No
Playlist: * Yes
iPod: * * * No
Playqueue: *Yes
View: * * * Library
Custom: * * Only the library colums
Plugins: * *Low

Was able to load the music library increbly fast. Very good tagging system. Otherwise only a very limited music player. Nice option for tagging your files but for other uses is the application too limited and does the database seem quite unstable (ridiculous high RAM)


_**LISTEN**_

[[IMG]http://img691.imageshack.us/img691/403/listena.th.png[/img]](http://img691.imageshack.us/i/listena.png/)

Written in: Python
RAM: * * * *120 - 700 MiB (536 measured in pic)
Radio: * * *Yes
Video: * * *No
Podcast: * *Yes
Playlist: * Yes
iPod: * * * Yes
Playqueue: *Yes
View: * * * Filesytem, Library + browser
Custom: * * Elements can be selected and dragged
Plugins: * *Good

Fair application, mainly oriented towards playlists. Inuitive enough but you have to be a fan of the playlist/play queue concept. Not reccomendable for tagging. RAM usage tends to jump up and down a lot during sessions. (Reason?)


_**QUOD LIBET**_

[[IMG]http://img833.imageshack.us/img833/9210/quodlibet.th.png[/img]](http://img833.imageshack.us/i/quodlibet.png/)

Written in: python
RAM: * * * *300 - 350 MiB (318 measured in pic)
Radio: * * *Yes
Video: * * *No
Podcast: * *Yes
Playlist: * Yes
iPod: * * * Yes
Playqueue: *Yes
View: * * * Multiple views are supported including library + browser
Custom: * * Elements are selectable + drag&drop
Plugins: * *Fair

Is bundled with the tagging application Ex Falso. Fair application and ok for tagging. Uses like Gmusicbrowser filters for search queries. Memory consumption is high in respect to the functionality offered. I consider it less user friendly for an every day app compared to others reviewed here.



_**RHYTHMBOX**_

[[IMG]http://img705.imageshack.us/img705/711/rhythmbox.th.png[/img]](http://img705.imageshack.us/i/rhythmbox.png/)

Written in: C
RAM: * * * *135 - 180 MiB (157 measured in pic)
Radio: * * *Yes
Video: * * *No
Podcast: * *Yes
Playlist: * Yes
iPod: * * * Yes
Playqueue: *Yes
View: * * * Library + browser
Custom: * * Minimal
Plugins: * *Good

Easy to use and intuitive but hardly anything is to be customized. Memory dependencies are low and the application is highly stable. Lack of customization options most certainly contribute to the fact that it's stable, but nearly everywhere this app marks a sufficient score. This justifies why Rhythmbox still is the default media app for most gnome linux distros... This being said, nowhere does Rhythmbox really excell either and that's why you are reading this text probably. 


_**SONGBIRD**_

[[IMG]http://img17.imageshack.us/img17/4733/songbirdx.th.png[/img]](http://img17.imageshack.us/i/songbirdx.png/)

Written in: ?
RAM: * * * *220 - 800 MiB (240 measured in pic)
Radio: * * *Yes
Video: * * *No
Podcast: * *Yes
Playlist: * Yes
iPod: * * * No
Playqueue: *No
View: * * * Library + browser
Custom: * * Elements can be selected + drag&drop
Plugins: * *Good

Official linux support has been discontinued. Application is very intuitive but has only few possibilities en seems much more cross platform oriented than the others. It has a clear interface and is sufficiently adjustable. Stability is not one of its stronpoints and file management is insufficient. No support for removeable media.




**_Personal conclusion:_**
(so what do i personally think given *my situation*)

Banshee is an extremely good application, if it were only able to run stable.

Gmusicbrowser is very strong but can only be used on local files.

Rhythmbox and Listen are good options for daily use.

Guayadeque, for being only a recent project, has a lot going for it and i am already looking forward to project's status in a years time. Hopefully this might become **the** solution for music in linux...

And the others?... well those i installed this week for the last time on my machine.

---

### Post by morgengenuss on 2011-03-14
interesting review! (i know it's a late reply)

btw, about the aesthetics of gmusicbrowser, you can checkout the shimmer-version of it, it beautifies the player quite a bit ;)

---

### Post by nothingspecial on 2011-03-14
guayadeque now has ipod support

[http://guayadeque.org/](http://guayadeque.org/)

---

### Post by camaron1 on 2011-03-14
Guayadeque is already the de facto linux player/organizer when it comes to big libraries and if you want a stable, flexible and feature-rich app. Once you use it for a while there is not coming back.

---

### Post by brx75 on 2011-03-22
I love gMusicBrowser for the customizable UI and the library management where I love to organize my library myself not following common Artist/Album/Number - Track filesystem layout.

---

### Post by kellemes on 2011-03-22
> **sigixv said:**
> 

I was unable to fully test this application because it was totally unuseable. Timelag after clicking and action would often exceed 1minute (without the application being grayed out).
General impressions are an ancient (even downright ugly) interface. Impressions resemble Exaile with the tree-list. The "DJ"-function seemed however promising but i was unable to test due to problems mentioned above.
Totally unuseable for large music libraries.

(end part 1)

First learn how to install and use Java-based applications before writing reviews..
Jajuk works flawless on my machine(s) with 4T of music.

---

### Post by mannyto210 on 2011-07-20
> 
_**JAJUK**_



Written in: Java
RAM: * * * *600-1100 MiB (670 measured in pic)

I was unable to fully test this application because it was totally unuseable. Timelag after clicking and action would often exceed 1minute (without the application being grayed out).
General impressions are an ancient (even downright ugly) interface. Impressions resemble Exaile with the tree-list. The "DJ"-function seemed however promising but i was unable to test due to problems mentioned above.
Totally unuseable for large music libraries.

(end part 1)I've made a rule of thumb for myself..., anything JAVA based is NOT getting in any of my OSes (Neother Windows nor Linux nor BSD). Java has become such a HOG to run and resource-hungry. 

Anyway. I have to agree about Guayadeque (...interesting name, byt he way..., I kinda' like it). I have 20k songs, mostly mp3 and have been using Rhythmbox, but *just starting* the program was eating all my CPU and all my memory, after that it went kinda' ok. Banshee was just unusable, it would get stuck a lot. I started using this one and it is such a breeze! Its wonderful. I fully recommend it! It is also very configurable and didn't have to tweak anything in Gnome for it to use separate music folders together (like Rhythmbox).

I love it!

---

### Post by bayvista on 2011-07-26
Great article. Many thanks, Saved me hours of work. Tried Clementine and Rhythmbox before settling on Gmusicbrowser.

---

### Post by Inoki on 2011-12-28
Not exactly the most accurate review.

Banshee can easily be broken with plugins, Clementine is a resource hog though it's polished the most compared to all the others but Quod Libet is my all time favourite and it's absolutely NOT TRUE that it cannot handle large libraries.

Before you jump into conclusions test things properly.

---

