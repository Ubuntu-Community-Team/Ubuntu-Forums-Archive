---
title: "[ANN] Banshee plugin for PS3 Media server"
date: 2012-03-26
forum: General Help
---

### Post by niranjan_rao on 2012-03-26
Greetings,

Alpha release of banshee plugin for PS3 media server is now available at hhttps://github.com/nhrdl/Banshee-PS3-Media-Server-Plugin. It is tested with Banshee 2.2.1 database file and latest PS3 media source code from github.

Why the plugin:
I am a big bollywood music fan. I have fair collection of music which I like listennig from my tablet. My problem was filtering the music as easily as possible. For example, many songs in bollywood movies are duets. If I want to listen to songs from certain pair, it was getting very tedious in current frameworks and those I managed to find and was able to work with my setup.

Most of the DLNA servers were very limited in capabilities in terms of filtering the music. My plugin sort of helps to fill that gap to some extent. Banshee, like other many other players, does hold music data in the easily understandable database format. The plugin code basically acts as an interface between banshee database and PS3 media server.

You start with one of Artist, Composer, Conductor, Year or Album. You can keep drilling to one entry, rest of the folder contents are automatically adjusted based on your selection. So if you start with Artist A, album list will be adjusted where artist A appears.

Code is currently usable from my machine where I tested it. I am releasing it with the hope that it will be useful to others also. Most importantly code is generic enough that it can be easily customized to make it work say with media monkey database etc. I am also toying with idea of parsing notes field and showing those entries as well.

Known Issues:
I am not expert of PS3 Media server code. I managed to make it work after some debugging and reverse engineering the server code. My player is able to play the music, but comments from dev team are certainly apprecitated if I am not following any coding/plugin guidelines . It does work on my devices, but only after inspecting server output where it works and adjusting my output accordingly.

Banshee DB format can change. It is working with the format available on my machine. Code is working directly with DB and does not use any Banshee API

Music needs to be on local disk - not sure/not tested what happens if the music urls in banshee db are not local.

Bugs/comments/suggestions are welcome. Bugs/comments should be entered on github as I don't frequent forums that much. I do have day job and will try to adress as many issues as possible as quickly as possible.

---

