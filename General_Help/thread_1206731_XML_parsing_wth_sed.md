---
title: "XML parsing wth sed"
date: 2009-07-07
forum: General Help
---

### Post by timo1023 on 2009-07-07
I would like to create a script that, given an Artist name, prints out the top tracks (pulled from Last FM). I can get a nice XML file of this data using the Last FM API:

[http://ws.audioscrobbler.com/2.0/?method=artist.gettoptracks&artist=ARTISTNAME&api_key=b25b959554ed76058ac220b7b2e0a026](http://ws.audioscrobbler.com/2.0/?method=artist.gettoptracks&artist=ARTISTNAME&api_key=b25b959554ed76058ac220b7b2e0a026)
(EDIT: Sorry that the link doesn't show the full text. Hovering over it should reveal the entire URL)

So, if I wanted to get the top tracks for, say, Animal Collective, I would use the following URL:

[http://ws.audioscrobbler.com/2.0/?method=artist.gettoptracks&artist=Animal+Collective&api_key=b25b959554ed76058ac220b7b2e0a026](http://ws.audioscrobbler.com/2.0/?method=artist.gettoptracks&artist=Animal+Collective&api_key=b25b959554ed76058ac220b7b2e0a026)

A portion of the XML file looks like this:
```
<track rank="1">
<name>My Girls</name>
<playcount>766454</playcount>
<mbid/>
&#8722;
<url>
http://www.last.fm/music/Animal+Collective/_/My+Girls
</url>
<streamable fulltrack="0">0</streamable>
&#8722;
<artist>
<name>Animal Collective</name>
<mbid>0c751690-c784-4a4f-b1e4-c1de27d47581</mbid>
<url>http://www.last.fm/music/Animal+Collective</url>
</artist>
</track>
```

As I stated previously, I would like to extract the titles of the tracks. From my basic knowledge, it seems like sed would be the best for the job. After a little research, I found that the command
```
sed -n /\<name\>/p data.xml
```
yields
```
        <name>My Girls</name>
            <name>Animal Collective</name>
        <name>In the Flowers</name>
            <name>Animal Collective</name>
        <name>Summertime Clothes</name>
            <name>Animal Collective</name>
        <name>Also Frightened</name>
            <name>Animal Collective</name>
        <name>Daily Routine</name>
            <name>Animal Collective</name>
        <name>Bluish</name>
            <name>Animal Collective</name>
        <name>Taste</name>
            <name>Animal Collective</name>
        <name>Lion in a Coma</name>
            <name>Animal Collective</name>
        <name>Guys Eyes</name>
            <name>Animal Collective</name>
        <name>Grass</name>
            <name>Animal Collective</name>
        <name>Peacebone</name>
            <name>Animal Collective</name>
        <name>Fireworks</name>
            <name>Animal Collective</name>
        <name>The Purple Bottle</name>
            <name>Animal Collective</name>
        <name>No More Runnin</name>
            <name>Animal Collective</name>
        <name>Did You See the Words</name>
            <name>Animal Collective</name>
        <name>Leaf House</name>
            <name>Animal Collective</name>
        <name>Unsolved Mysteries</name>
            <name>Animal Collective</name>
        <name>For Reverend Green</name>
            <name>Animal Collective</name>
        <name>Brother Sport</name>
            <name>Animal Collective</name>
        <name>Chores</name>
            <name>Animal Collective</name>
        <name>Banshee Beat</name>
            <name>Animal Collective</name>
        <name>Brothersport</name>
            <name>Animal Collective</name>
        <name>Flesh Canoe</name>
            <name>Animal Collective</name>
        <name>Who Could Win a Rabbit</name>
            <name>Animal Collective</name>
        <name>Bees</name>
            <name>Animal Collective</name>
        <name>Derek</name>
            <name>Animal Collective</name>
        <name>Loch Raven</name>
            <name>Animal Collective</name>
        <name>#1</name>
            <name>Animal Collective</name>
        <name>Winter Wonder Land</name>
            <name>Animal Collective</name>
        <name>Winters Love</name>
            <name>Animal Collective</name>
        <name>Daffy Duck</name>
            <name>Animal Collective</name>
        <name>Cuckoo Cuckoo</name>
            <name>Animal Collective</name>
        <name>Sweet Road</name>
            <name>Animal Collective</name>
        <name>Turn Into Something</name>
            <name>Animal Collective</name>
        <name>The Softest Voice</name>
            <name>Animal Collective</name>
        <name>Kids on Holiday</name>
            <name>Animal Collective</name>
        <name>We Tigers</name>
            <name>Animal Collective</name>
        <name>Water Curses</name>
            <name>Animal Collective</name>
        <name>College</name>
            <name>Animal Collective</name>
        <name>No More Runnin'</name>
            <name>Animal Collective</name>
        <name>Mouth Wooed Her</name>
            <name>Animal Collective</name>
        <name>Visiting Friends</name>
            <name>Animal Collective</name>
        <name>Street Flash</name>
            <name>Animal Collective</name>
        <name>Whaddit I Done</name>
            <name>Animal Collective</name>
        <name>Good Lovin Outside</name>
            <name>Animal Collective</name>
        <name>Cobwebs</name>
            <name>Animal Collective</name>
        <name>Seal Eyeing</name>
            <name>Animal Collective</name>
        <name>Native Belle</name>
            <name>Animal Collective</name>
        <name>Hey Light</name>
            <name>Animal Collective</name>
        <name>Slippi</name>
            <name>Animal Collective</name>

```

How can I refine this command to do what I want? IE, remove the "Animal Collective" <name> lines, remove the <name> tags, and print only the titles.

Thanks for the help,
Tim

---

### Post by timo1023 on 2009-07-07
Well, looks like I worked out my own problem, albeit not very efficiently. Let me know if there is a better way to parse through the file. Here is my script to do what I originally described:

```
#!/bin/bash
#toptracks
#A program to pull top tracks for an artist
#from Last FM. Uses the URL
# "http://ws.audioscrobbler.com/2.0/?method=artist.gettoptracks&artist=ARTISTNAME&api_key=b25b959554ed76058ac220b7b2e0a026"
#
#USAGE: toptracks "ARTIST NAME"
#	i.e.
#		toptracks "Animal Collective"

#Pulls artist from arguments, replace space with `+` for LastFM URL
ARTIST=$(echo $1 | sed "s/ /+/g")

#Gets top tracks XML file from LastFM API
wget -O data.xml "http://ws.audioscrobbler.com/2.0/?method=artist.gettoptracks&artist=${ARTIST}&api_key=b25b959554ed76058ac220b7b2e0a026"

#Parse file: Remove XML Tags and excess, pull only 10 songs
#	the `sed "/${1}/d"` command removes lines with the artist name
sed -n /\<name\>/p data.xml | sed "/${1}/d" | sed 's/<.[a-z]*>//g' | sed 10q


```

Next, I am going to build a playlist file from the songs :). Then I can throw my program a list of artists, and have sample playlists await my listening. I think it's a cool idea. Just a little project for my morning :).

---

