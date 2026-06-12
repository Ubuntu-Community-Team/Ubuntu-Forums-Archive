---
title: "Conky Clementine Python Script"
date: 2010-12-14
forum: General Help
---

### Post by kaivalagi on 2010-12-14
[SIZE="1"][COLOR="Green"]**ArchLinux : **Package support is present in the AUR. All my packages can be seen here: **[http://aur.archlinux.org/packages.php?SeB=m&K=kaivalagi](http://aur.archlinux.org/packages.php?SeB=m&K=kaivalagi)**

**Ubuntu/Debian : **All the script packages have now been copied into the Conky Companions PPA. Any package updates will be provided by the team through this new ppa. The ppa can be found here: **[https://launchpad.net/~conky-companions/+archive/ppa]("https://launchpad.net/~conky-companions/+archive/ppa")**. To use this ppa first delete the old ppa files using this:
```
sudo rm /etc/apt/sources.list.d/m-buck* && sudo rm /etc/apt/sources.list.d/conkyhardcore*
```
Then follow the modified first post instructions for the scripts[/COLOR][/SIZE]

**_[SIZE=3][COLOR=Blue]Intro[/COLOR][/SIZE]_**

This is a simple script to display what is current playing in Clementine. The script talks to Clementine using dbus, and allows the outputting of track info and the use of templates...

There is a README with the install, I suggest you give it atleast a quick once over! It can be found in the installation folder, normally following the path of /usr/share/conky<scriptname>/

**_[SIZE=3][COLOR=Blue]Basic Install[/COLOR][/SIZE]_**

**[COLOR=Blue]Method 1: Using apt[/COLOR]**

1) Add the repository to your OS install:
```
sudo add-apt-repository ppa:conky-companions/ppa
```
[INDENT]* Note if you are running 9.10 or below then refer to the PPA link at the end of this post for help on installing from the ppa, good guidance can be found on the launchpad site[/INDENT]

2) Now that is done simply run the following to update your repo cache and install the script: 

```
sudo apt-get update && sudo apt-get install conkyclementine

```

**[COLOR=Blue]Method 2: Using deb file[/COLOR]**

Run the .deb file available at the Conky Companions PPA site here: [https://launchpad.net/~conky-companions/+archive/ppa/+packages](https://launchpad.net/~conky-companions/+archive/ppa/+packages)

Warning, this will not ensure you are kept up-to-date. Only method 1 will do that ;)

**[COLOR=Blue]Method 3: Using tar.gz file[/COLOR]**

Extract all the contents of the tar.gz file to an appropriate folder, and edit the conkyClementine script to point to the correct location where conkyClementine.py is. The tar.gz file is available at the Conky Companions PPA site here: [https://launchpad.net/~conky-companions/+archive/ppa/+packages](https://launchpad.net/~conky-companions/+archive/ppa/+packages)

Unless you are using a non-Debian based OS I don't suggest this. Users of Debian/Ubuntu flavour OS's should ideally use method 1.

Again will will not receive updates using this method. ONLY method 1 can do this for you ;) ;)

All further details on setup are orientated around the deb package based install, so may differ from what you choose your setup to be, if done using the tarball.


**_[SIZE=3][COLOR=Blue]Usage Help[/COLOR][/SIZE]_**

You can get the current help options at any time by running (change the path as necessary):

```

conkyClementine -h

```or

```

conkyClementine --help

``````
Usage: conkyClementine [options]
Options:
  -h, --help            show this help message and exit
  -t FILE, --template=FILE
                        define a template file to generate output in one call.
                        A displayable item in the file is in the form
                        [--datatype=TI]. The following are possible options
                        within each item: --datatype,--ratingchar. Note that
                        the short forms of the options are not currently
                        supported! None of these options are applicable at
                        command line when using templates.
  -d DATATYPE, --datatype=DATATYPE
                        [default: TI] The data type options are: ST (status),
                        CA (coverart), TI (title), AL (album), AR (artist), GE
                        (genre), YR (year), TN (track number), FN (file name),
                        BR (bitrate k/s), LE (length), PP (current position in
                        percent), PT (current position in time), VO (volume),
                        RT (rating). Not applicable at command line when using
                        templates.
  -r CHAR, --ratingchar=CHAR
                        [default: *] The output character for the ratings
                        scale. Command line option overridden if used in
                        templates.
  -s TEXT, --statustext=TEXT
                        [default: Playing,Paused,Stopped] The text must be
                        comma delimited in the form 'A,B,C'. Command line
                        option overridden if used in templates.
  -n, --nounknownoutput
                        Turn off unknown output such as "Unknown" for title
                        and "0:00" for length. Command line option overridden
                        if used in templates.
  -S, --secondsoutput   Force all position and length output to be in seconds
                        only.
  -m LENGTH, --maxlength=LENGTH
                        [default: 0] Define the maximum length of any
                        datatypes output, if truncated the output ends in
                        "..."
  -v, --verbose         Request verbose output, not a good idea when running
                        through conky!
  -V, --version         Displays the version of the script.
  --errorlogfile=FILE   If a filepath is set, the script appends errors to the
                        filepath.
  --infologfile=FILE    If a filepath is set, the script appends info to the
                        filepath.

```

**_[SIZE=3][COLOR=Blue]Development History[/COLOR][/SIZE]_**

Much thanks goes to [VastOne]("http://ubuntuforums.org/member.php?u=696842") for co-authoring this script off the back of my other player scripts, adapting it slightly for Clementine use. Note to others out there, if you have a player and want a script for it you too could help the cause, the player app just needs to publish to d-bus and you need to learn a little python ;)

Development history going forwards can be seen here [URL="https://code.launchpad.net/%7Econky-companions/+junk/conkyclementine"]https://code.launchpad.net/~conky-companions/+junk/conkyclementine
[/URL] All packages available from me can be found here: [https://launchpad.net/~conky-companions/+archive/ppa]("https://launchpad.net/%7Econky-companions/+archive/ppa")

---

### Post by VastOne on 2010-12-14
You can see my Conky Clementine setup from [_[COLOR="Blue"]here at[/COLOR]_]("http://conky-pitstop.wikidot.com/g10ii:g-2010-ii") Conky-Pitstop

---

### Post by ludentic on 2011-01-19
Nice script! Thumbs up! I was wondering if is there a way to recognize whether Clementine is playing radio or the library.
Thank you!

---

### Post by ludentic on 2011-01-20
Ok figured out how to change when Clementine is playing radio. I added this lines to my conky file:


# Music section for Clementine. Only shows if Clementine is a running process: It also shows "Radio" or "Music Player"
${if_running clementine}${if_match "${execi 5 conkyClementine --datatype=ST}" == "Playing"}${font Droid Sans:bold:size=10}${color0}Clementine ${font}${if_match "${execi 5 conkyClementine --datatype=FN}" > "http"}Radio${else}Music Player${endif} ${hr 2}${color}

${font Droid Sans:oblique:size=9}${execi 5 conkyClementine --datatype=TI | fold -w36}${font}

${execi 5 conkyClementine --datatype=AR | fold -w36}${font}${endif}${endif}

---

### Post by VastOne on 2011-01-20
> **ludentic said:**
> Ok figured out how to change when Clementine is playing radio. I added this lines to my conky file:


# Music section for Clementine. Only shows if Clementine is a running process: It also shows "Radio" or "Music Player"
${if_running clementine}${if_match "${execi 5 conkyClementine --datatype=ST}" == "Playing"}${font Droid Sans:bold:size=10}${color0}Clementine ${font}${if_match "${execi 5 conkyClementine --datatype=FN}" > "http"}Radio${else}Music Player${endif} ${hr 2}${color}

${font Droid Sans:oblique:size=9}${execi 5 conkyClementine --datatype=TI | fold -w36}${font}

${execi 5 conkyClementine --datatype=AR | fold -w36}${font}${endif}${endif}

Very nice...

Would you be so kind and post your conky config files for a closer examination?

Thanks~!

---

### Post by VastOne on 2011-01-20
> **ludentic said:**
> Nice script! Thumbs up! I was wondering if is there a way to recognize whether Clementine is playing radio or the library.
Thank you!

Thanks

---

### Post by VastOne on 2011-01-20
> **ludentic said:**
> Ok figured out how to change when Clementine is playing radio. I added this lines to my conky file:


# Music section for Clementine. Only shows if Clementine is a running process: It also shows "Radio" or "Music Player"
${if_running clementine}${if_match "${execi 5 conkyClementine --datatype=ST}" == "Playing"}${font Droid Sans:bold:size=10}${color0}Clementine ${font}${if_match "${execi 5 conkyClementine --datatype=FN}" > "http"}Radio${else}Music Player${endif} ${hr 2}${color}

${font Droid Sans:oblique:size=9}${execi 5 conkyClementine --datatype=TI | fold -w36}${font}

${execi 5 conkyClementine --datatype=AR | fold -w36}${font}${endif}${endif}

If you wrap this info in code ```
 Music section for Clementine. Only shows if Clementine is a running process: It also shows "Radio" or "Music Player"
${if_running clementine}${if_match "${execi 5 conkyClementine --datatype=ST}" == "Playing"}${font Droid Sans:bold:size=10}${color0}Clementine ${font}${if_match "${execi 5 conkyClementine --datatype=FN}" > "http"}Radio${else}Music Player${endif} ${hr 2}${color}

${font Droid Sans:oblique:size=9}${execi 5 conkyClementine --datatype=TI | fold -w36}${font}

${execi 5 conkyClementine --datatype=AR | fold -w36}${font}${endif}${endif}
```  it shows up much cleaner...

---

### Post by kaivalagi on 2011-01-25
**[COLOR=Purple][SIZE=4]UPDATE[/SIZE][/COLOR]**

Updates as follows:
[LIST]
[*]Fixed potential bug with %20 not being represented as spaces when dealing with cover art paths
[/LIST]

Package changes can be seen here:  [https://launchpad.net/~conky-companions/+archive/ppa/+files/conkyclementine_2.01_source.changes](https://launchpad.net/~conky-companions/+archive/ppa/+files/conkyclementine_2.01_source.changes)

The apt packages should be available soon

---

### Post by kaivalagi on 2011-01-26
**[COLOR=Red][SIZE=4]UPDATE[/SIZE][/COLOR]**

Updates as follows:
[LIST]
[*]Updated both main scripts to handle URL encoded paths generically using urllib.unquote functions. Should sort out any cover art path issues *maybe*
[/LIST]

Package changes can be seen here:  [https://launchpad.net/~conky-companions/+archive/ppa/+files/conkyclementine_2.02_source.changes](https://launchpad.net/~conky-companions/+archive/ppa/+files/conkyclementine_2.02_source.changes)

The apt packages should be available soon

---

### Post by laite on 2011-01-27
Hi! 

Does anybody know how to get nowplaying info (at least Artist/Track) to conky when playing last.fm radios? Otherwise (when playing from HD) this works just fine.

To be more clear, "conkyClementine -d ST" (as well as all the other datatypes) in console returns:

ERROR: Issue calling the dbus service:'NoneType' object has no attribute 'find'
Unknown

---

### Post by VastOne on 2011-01-27
> **laite said:**
> Hi! 

Does anybody know how to get nowplaying info (at least Artist/Track) to conky when playing last.fm radios? Otherwise (when playing from HD) this works just fine.

To be more clear, "conkyClementine -d ST" (as well as all the other datatypes) in console returns:

ERROR: Issue calling the dbus service:'NoneType' object has no attribute 'find'
Unknown

You are getting this error while playing last.fm radio only?  

This indicates that last.fm radio is not sending any mpris info to the dbus session. 

I so not have an account to play last.fm radio so I cannot verify this.

While in Clementine, and with notifications enabled, does last.fm show anything on a track change?

---

### Post by VastOne on 2011-01-27
> **laite said:**
> Hi! 

Does anybody know how to get nowplaying info (at least Artist/Track) to conky when playing last.fm radios? Otherwise (when playing from HD) this works just fine.

To be more clear, "conkyClementine -d ST" (as well as all the other datatypes) in console returns:

ERROR: Issue calling the dbus service:'NoneType' object has no attribute 'find'
Unknown

On message #4 here, ludentic shows how he got radio to play, perhaps this can help you...

---

### Post by laite on 2011-01-27
> **VastOne said:**
> You are getting this error while playing last.fm radio only?  

It seems that last.fm and Soma FM both make this error.

> **VastOne said:**
> 
While in Clementine, and with notifications enabled, does last.fm show anything on a track change?

Yes, OSD shows track changes correctly

> **VastOne said:**
> 
On message #4 here, ludentic shows how he got radio to play, perhaps this can help you...

Unfortunately this didn't work with last.fm because it just tests the value of ST (status) and FN (filename), both which are empty in my case (or "unknown").

---

### Post by kaivalagi on 2011-01-27
Have a play with d-feet (d-bus probing tool) to see if anything is populated by Clementine to it's d-bus interface when playing last.fm...if you find out anything positive give me the heads up and I'll see what I can sort out...unfortunately it might just be (probably) a "feature" of the player just like nearly all of the others I've created scripts for.

edit: key lines from the script to highlight the d-bus methods used for title:

```
remote_player = bus.get_object('org.mpris.clementine', '/Player')
iface_player = dbus.Interface(remote_player, 'org.freedesktop.MediaPlayer')
...
props = iface_player.GetMetadata()
...
if "title" in props:
  title = props["title"]
else:
  title = None

```

---

### Post by laite on 2011-02-02
> **kaivalagi said:**
> Have a play with d-feet (d-bus probing tool) to see if anything is populated by Clementine to it's d-bus interface when playing last.fm...if you find out anything positive give me the heads up and I'll see what I can sort out...unfortunately it might just be (probably) a "feature" of the player just like nearly all of the others I've created scripts for.


I attached picture of what happens and there really is all the info, artist 'Elisa', album 'Then comes the Sun' and track title 'The Window' on the bottom.

---

### Post by VastOne on 2011-02-02
While that station is playing, run the following



```
python conkyClementine.py --datatype=TI
```

```
python conkyClementine.py --datatype=AR
```

```
python conkyClementine.py --datatype=AL
```

Any one of these should return the data

Let me know the results.

I am playing a radio station now on Clementine, Icecast/Rock/Galwayland Radio Mix

and each of these are working as they should

---

### Post by laite on 2011-02-02
> **VastOne said:**
> 
Let me know the results.

I am playing a radio station now on Clementine, Icecast/Rock/Galwayland Radio Mix

and each of these are working as they should

With Icecast stations this works, return shows track/artist/title correctly in console.
With last.fm/Soma FM I got error message:
ERROR: Issue calling the dbus service:'NoneType' object has no attribute 'find'
Unknown

EDIT: Also, Icecast stations show correctly in conky, whereas last/Soma show just 'unknown'

---

### Post by VastOne on 2011-02-02
> **laite said:**
> With Icecast stations this works, return shows track/artist/title correctly in console.
With last.fm/Soma FM I got error message:
ERROR: Issue calling the dbus service:'NoneType' object has no attribute 'find'
Unknown

EDIT: Also, Icecast stations show correctly in conky, whereas last/Soma show just 'unknown'

Run Clem from the terminal, and your conkyclementine from a separate terminal.

Play the station and see if there are any additional errors that Clem terminal may be reporting.

I do not have a last.fm account so I cannot replicate this and debug it, but if the script is returning icecast with no issues, then it is obviously working.. 

As K said, this has been an issue with other players, but having said that, it looks from the screen shot you sent that the data is making it to dbus as it should

---

### Post by VastOne on 2011-02-02
> **laite said:**
> With Icecast stations this works, return shows track/artist/title correctly in console.
With last.fm/Soma FM I got error message:
ERROR: Issue calling the dbus service:'NoneType' object has no attribute 'find'
Unknown

EDIT: Also, Icecast stations show correctly in conky, whereas last/Soma show just 'unknown'

In dfeet Dbus, execute the metadata again, and post the Source tab below next to the Pretty Print

---

### Post by VastOne on 2011-02-02
OK, I am able to replicate this by using the SomaFM radio stations.  

Let me look into it more and I will report back

---

### Post by VastOne on 2011-02-02
In doing a google search for 

> Issue calling the dbus service:'NoneType' object has no attribute 'find'Unknown

There are hundreds of references to many python based apps...

Just saying we are not on an island here...

---

### Post by kaivalagi on 2011-02-03
that error stems from no string data coming back which the .find method used won't be useable with either

I'm taking a look at it all now

edit: @VastOne, for info we need to debug the code to find out what is wrong, the code is home grown so searching google wont help. I have already found the culprit and am testing through all the code to make sure nothing else crops up too....location.find doesn't work when there is no location...

The reason we have issues is because the properties returned via d-bus are minimal for last fm and soma fm when compared to other sources, and code breaks when checking for things that are normally there with say mp3s etc....if you compare playing an mp3 and somafm in d-feet you'll see the difference in info retrieved for the getmetadata method...

For debugging I am using pydev in eclipse...

edit2: Find attached fixed .py file, let me know how you get on if this replaces your local version...should be working now. Once I get the thumbs up I'll release the changes in a new v2.03 package

---

### Post by VastOne on 2011-02-03
> **kaivalagi said:**
> that error stems from no string data coming back which the .find method used won't be useable with either

I'm taking a look at it all now

edit: @VastOne, for info we need to debug the code to find out what is wrong, the code is home grown so searching google wont help. I have already found the culprit and am testing through all the code to make sure nothing else crops up too....location.find doesn't work when there is no location...

The reason we have issues is because the properties returned via d-bus are minimal for last fm and soma fm when compared to other sources, and code breaks when checking for things that are normally there with say mp3s etc....if you compare playing an mp3 and somafm in d-feet you'll see the difference in info retrieved for the getmetadata method...

For debugging I am using pydev in eclipse...

edit2: Find attached fixed .py file, let me know how you get on if this replaces your local version...should be working now. Once I get the thumbs up I'll release the changes in a new v2.03 package

It works now for me...

I am getting the complete information from SomaFM

Thanks for the lesson and pydev info, it was the one tool I had forgotten to use

---

### Post by kaivalagi on 2011-02-03
> **VastOne said:**
> It works now for me...

I am getting the complete information from SomaFM

Thanks for the lesson and pydev info, it was the one tool I had forgotten to use

Good stuff

IM me if you need any pointers on setting up/using pydev

---

### Post by laite on 2011-02-03
> **kaivalagi said:**
> 
edit2: Find attached fixed .py file, let me know how you get on if this replaces your local version...should be working now. Once I get the thumbs up I'll release the changes in a new v2.03 package

Works with last.fm and Soma, thank you so much!

---

### Post by kaivalagi on 2011-02-03
> **laite said:**
> Works with last.fm and Soma, thank you so much!

No worries, that's confirmed to be working from 2 users so I shall get busy with an update ;)

---

### Post by kaivalagi on 2011-02-03
**[COLOR=Green][SIZE=4]UPDATE[/SIZE][/COLOR]**

Updates as follows:
[LIST]
[*]Updated script to work with last fm and soma fm info properly, only title, artist and coverart are available as this is the limitation set by the player
[/LIST]

Package changes can be seen here:  [https://launchpad.net/~conky-companions/+archive/ppa/+files/conkyclementine_2.03_source.changes](https://launchpad.net/~conky-companions/+archive/ppa/+files/conkyclementine_2.03_source.changes)

The apt packages should be available soon

---

### Post by Blitz_B on 2011-02-14
Thanks so much for this was using your banshee script before but now i have switched to kde so had to change my media player this works perfectly 

Thought i would post what i have done with it :) keep the great work up ;)

---

### Post by VastOne on 2011-02-14
> **Blitz_B said:**
> Thanks so much for this was using your banshee script before but now i have switched to kde so had to change my media player this works perfectly 

Thought i would post what i have done with it :) keep the great work up ;)

Very nice... Glad it works out for you!

---

### Post by stratoka on 2011-03-22
hi, i cant get it vork the part where it supposed to shuw the album art:( i followed the steps exactly but nothibg happens, what did i mess up?

---

### Post by kaivalagi on 2011-03-23
> **stratoka said:**
> hi, i cant get it vork the part where it supposed to shuw the album art:( i followed the steps exactly but nothibg happens, what did i mess up?

Post up your conkyrc and template then we might be able to help, we can't read your mind you know :)

---

### Post by VastOne on 2011-03-23
> **stratoka said:**
> hi, i cant get it vork the part where it supposed to shuw the album art:( i followed the steps exactly but nothibg happens, what did i mess up?

conkyClementine-GetCoverart.py must be running AFTER you start Clementine.

If it is running and still no results do this

Run Clementine

Go to terminal and start

python conkyClementine-GetCoverart.py

In Clementine play several songs that have cover art

From terminal, report back here what conkyClementine-GetCoverart.py is reporting when it is changing or trying to change the cover art

---

### Post by kaivalagi on 2011-03-26
> **kaivalagi]...bunch of chat about templates and --[datatype=CA]...[/quote]
[QUOTE=karmila said:**
> Wow :D

Thanks Mark, I had same question with conkyClementine and this answer solved my problem.
> **kaivalagi]You could do it this way but you may not even need the --datatype=CA thing as if you run the conkyClementine-GetCoverart script it will create a file in a known path instead on track change (much more efficient)...not all players work with an alternative script like this but clementine does as it presents the event handlers in it's d-bus methods  said:**
> 

[QUOTE=karmila;10602294]That would be much better.

This is CA part from my conkyrc
```
${execp conkyClementine --template=/path/to/conkyClementine.template}

```

And this is the template
```
${image [--datatype=CA] -p 30,290 -s 62x62}
```

I run GetCoverart.py script at terminal and see how it works but how to add the script to conkyrc?

You don't add the script to conky, you just ensure it's running when you've logged in. When you first give it a go though just run it in the terminal window like so:

```
]$ conkyClementine-GetCoverart --verbose
conkyClementine-GetCoverart - Cover art will be copied to '/tmp/cover'
* Initialising: Creating a D-Bus session...
* Listening: waiting for a track change...

```

In the longer term either start the script through startup applications or another means...the script will copy coverart to a known location on track change (/tmp/cover) so in conky all you'll need is a straight forward image variable in either the main conkyrc or a template if you're using one already

e.g.
```
${image /tmp/cover -p 10, 10 -s 150x150}
```

---

### Post by karmila on 2011-03-26
> **kaivalagi said:**
> You don't add the script to conky, you just ensure it's running when you've logged in. When you first give it a go though just run it in the terminal window like so:

```
]$ conkyClementine-GetCoverart --verbose
conkyClementine-GetCoverart - Cover art will be copied to '/tmp/cover'
* Initialising: Creating a D-Bus session...
* Listening: waiting for a track change...

```In the longer term either start the script through startup applications or another means...the script will copy coverart to a known location on track change (/tmp/cover) so in conky all you'll need is a straight forward image variable in either the main conkyrc or a template if you're using one already

e.g.
```
${image /tmp/cover -p 10, 10 -s 150x150}
```

It's really clear now for me. I should have known about this after read VastOne post above. 

When I ran conkyClementine-GetCoverart script (as VastOne told) before I could see /clementine-art-*.jpg automatically copied to /tmp/cover but I didn't get the idea, lol. 

Thanks K :D

---

### Post by Sector11 on 2011-04-08
[center][ Nouveau : Conky Pitstop - c'est bilingue. ](http: // conky.pitstop.free.fr/fr)
[img]http://dl.dropbox.com/u/16070765/full_CPS-Flag.png[/img]
[New: Conky Pitstop - it's bilingual.](http://conky.pitstop.free.fr/)[/center]

---

### Post by jhnhskll on 2011-05-01
So is it possible to make a script that launches conkyClementine-GetCoverart *after* Clementine is run? This seems to me as it is the only functional way to always have album art working correctly.

---

### Post by VastOne on 2011-05-02
> **jhnhskll said:**
> So is it possible to make a script that launches conkyClementine-GetCoverart *after* Clementine is run? This seems to me as it is the only functional way to always have album art working correctly.

I run it from a script that runs on start up that I entered in 

System > Preferences > Startup Applications

start-conky.sh

```
#!/bin/sh
sleep 30
clementine &
sleep 10
/usr/bin/python /usr/share/conkyclementine/conkyClementine-GetCoverart.py -q -d &
sleep 10
/usr/bin/conky -c ~/.conkyrc -q -d &
sleep 10
/usr/bin/conky -c ~/.conkyrc2 -q -d &
sleep 10
/usr/bin/conky -c ~/conky-timedate.conf -q -d &
```

Remember to change this to reflect your files...For me this starts Clementine, the GetCover script and my 3 different conky screens

You could also add

```
conkclem=$(pgrep clementine)

while [[ ! -z $conkclem ]];do
    sleep 30
    conkclem=$(pgrep clementine)
done

pkill -f /usr/share/conkyclementine/Conkyclementine-GetCoverart.py
```

at the end of that script and it would kill the Conkyclementine-GetCoverart.py script when it detects that Clementine is no longer running

Just remember to restart the Conkyclementine-GetCoverart.py script any time you stop Clementine

You could have another script just for restarting Clementine and the GetCover script:

startclem.sh

```
#!/bin/sh
clementine &
sleep 10
/usr/bin/python /usr/share/conkyclementine/conkyClementine-GetCoverart.py -q -d &

```

---

### Post by paganuntu on 2011-05-05
Hello everyone !

I'm sorry for being such a newbie, but after struggling two hours with my computer I think I really need your help ! 

I'd like my conky to show clementine cover art.
I understood that I had to make a script that launches the get cover art function.


So in order to make you understand what I done : 


I created a script : 

```
#!/bin/bash

conkyClementine-GetCoverart --verbose
```This  script launches on startup. 




And here's my conckyrc part that is about clementine : 

```
Now Playing ${color FF6600}${hr}${color}
${if_running banshee-1}
Title: ${exec banshee-1 --query-title | cut -f2- -d" "}
Artist: ${exec banshee-1 --query-artist | cut -f2- -d" "}
Album: ${exec banshee-1 --query-album | cut -f2- -d" "}${else}${if_running rhythmbox}
Title: ${exec rhythmbox-client --no-start --print-playing-format %tt} 
Artist: ${exec rhythmbox-client --no-start --print-playing-format %aa} 
Album: ${exec rhythmbox-client --no-start --print-playing-format %at}${else}${if_running exaile}
Title: ${execi 10 exaile --get-title}
Artist: ${execi 10 exaile --get-artist}
Album: ${execi 10 exaile --get-album} }${else}${if_running amarok}
Title: ${exec dcop amarok player title}
Artist: ${exec dcop amarok player artist}
Album: ${exec dcop amarok player album}${else}$[B]{if_running clementine}${image /tmp/cover -p 10, 10 -s 150×150}${execi 10 conkyClementine -d CA > /dev/null}
${offset 0}${color}Artist: ${color}${execi 5 conkyClementine -d AR}
${offset 0}${color}Titre: ${color}${execi 5 conkyClementine -d TI}
${offset 0}${color}Album: ${color}${execi 5 conkyClementine -d AL}[/B]
${else}Player Status Unavailable${endif}${endif}${endif}${endif}
```





So i would really enjoy some help, because I don't want to mess up all my ubuntu and that's the first script I ever made ! 


Any suggestions ? 


Thanks in advance, and thank you for making clementine usable in Concky !

---

### Post by kaivalagi on 2011-05-05
Maybe you need to ensure Clementine is running before you run the cover art script...so you might find it better to have a script like detailed above or something simple like this:

```
#!/bin/bash
clementine &
sleep 10
conkyClementine-GetCoverart &

```

---

### Post by paganuntu on 2011-05-05
> **kaivalagi said:**
> Maybe you need to ensure Clementine is running before you run the cover art script...so you might find it better to have a script like detailed above or something simple like this:

```
#!/bin/bash
clementine &
sleep 10
conkyClementine-GetCoverart &

```





Still doesn't work !!! 

Actually I think I should try it in a whole new conckrc file ? Maybe it doesn't work because of that ? 



So if I got it well : 

1 - I make an executable script that launches on startup as you just said
2 - I use a new conckyrc : what have I to put in there ? because the one I use now doesn't seem to work properly ! 


Thanks again for your consideration for my issue !

---

### Post by kaivalagi on 2011-05-06
The cover art script should create a "known" file for the image...check to make sure that is there when tracks are changed then use the $image variable as you have to display it...start simple and work up...

Cheers

---

### Post by VastOne on 2011-05-06
I have a complete how to [_[COLOR="Blue"]here on Conky-Pitstop[/COLOR]_]("http://conky-pitstop.wikidot.com/g10ii:g-2010-ii") on how to setup Conky with Clementine...

Click the tab The Codes and then go down to Conky Clementine by VastOne and you can open that and find all the setup

---

### Post by Sector11 on 2011-05-06
> **VastOne said:**
> I have a complete how to [_[COLOR="Blue"]here on Conky-Pitstop[/COLOR]_]("http://conky-pitstop.wikidot.com/g10ii:g-2010-ii") on how to setup Conky with Clementine...

Click the tab The Codes and then go down to Conky Clementine by VastOne and you can open that and find all the setup

Better to link to [the "new" Conky PitStop]("http://conky.pitstop.free.fr/wiki/index.php5?title=Main_Page"): Galleries - 2010 (2) - [VastOne (tar.gz)]("http://conky.pitstop.free.fr/wiki/index.php5?title=Gallery_2010_%282%29")

---

### Post by cccthestyle on 2011-05-16
cant seem to get the album art to show

the GetAlbumart script is doing its job just fine, /tmp/cover is showing the correct album artwork. 

my template looks like this: ```
[--datatype=TI]
[--datatype=AR]
[--datatype=AL]
[--datatype=BR]kbps
[--datatype=YR]
${image /tmp/cover -p 0,397 -s 170x170}
```

but my conky is turning out like this:

---

### Post by Sector11 on 2011-05-16
> **cccthestyle said:**
> cant seem to get the album art to show

the GetAlbumart script is doing its job just fine, /tmp/cover is showing the correct album artwork. 

my template looks like this: ```
[--datatype=TI]
[--datatype=AR]
[--datatype=AL]
[--datatype=BR]kbps
[--datatype=YR]
${image /tmp/cover -p 0,397 -s 170x170}
```

but my conky is turning out like this:

Hi ..
```
-c PATH, --coverartpath=PATH the "default: /tmp/cover"
```

With conkyForecast I found that I couldn't access my weather cache if it was in /tmp/ unless I was root.  And I don't use clementine, but try something.

In your config set the path to something like:

```
~/clem-art
```
or if you keep your conkys in a separate a sun-folder in that:
```
~/conky/clem-art
```

mine for conkyforcast is:
```
~/Conky/cache
```
Just a thought and may not work.

---

### Post by cccthestyle on 2011-05-16
@Sector: while trying out your fix, i figured out that in conkyrc you need to run conkyClementine with execp instead of execi which fixed my no album artwork problem

i can now get album artwork displayed using either /tmp/cover or ~/.conky/cover but the artwork fails to change. GetAlbumart script is still working fine, but the artwork displayed in conky never changes

example:

edit: relevant code

conkyrc:
```
${if_running clementine}${if_match "${execi 15 conkyClementine --datatype=ST}" == "Playing"}${execp conkyClementine --template=/home/clutch/.conky/conkyClementine.template}${endif}
```

conkyClementine.template:
```
[--datatype=TI --maxlength=27]
[--datatype=AR --maxlength=27]
[--datatype=AL --maxlength=27]
[--datatype=BR]kbps
[--datatype=YR]
${image /tmp/cover -p 0,397 -s 170x170}
```

---

### Post by Sector11 on 2011-05-16
> **cccthestyle said:**
> @Sector: while trying out your fix, i figured out that in conkyrc you need to run conkyClementine with execp instead of execi which fixed my no album artwork problem

i can now get album artwork displayed using either /tmp/cover or ~/.conky/cover but the artwork fails to change. GetAlbumart script is still working fine, but the artwork displayed in conky never changes

example:

Yea, that doesn't look like the Beatles cover at all.
Did you look at [VastOne's HowTo]("http://conky.pitstop.free.fr/wiki/images/10-2-VastOne-1.tar.gz") posted earlier?

---

### Post by VastOne on 2011-05-16
> **cccthestyle said:**
> @Sector: while trying out your fix, i figured out that in conkyrc you need to run conkyClementine with execp instead of execi which fixed my no album artwork problem

i can now get album artwork displayed using either /tmp/cover or ~/.conky/cover but the artwork fails to change. GetAlbumart script is still working fine, but the artwork displayed in conky never changes

example:

Are you running the conkyClemetine-GetCoverart.py script to pull the cover art?

---

### Post by VastOne on 2011-05-16
> **Sector11 said:**
> Yea, that doesn't look like the Beatles cover at all.
Did you look at [VastOne's HowTo]("http://conky.pitstop.free.fr/wiki/images/10-2-VastOne-1.tar.gz") posted earlier?

For some reason the conkyClementine-GetCoverart.py is not included in that README or the needed files... I will work on that at CPS

---

### Post by cccthestyle on 2011-05-16
> **VastOne said:**
> Are you running the conkyClemetine-GetCoverart.py script to pull the cover art?

yeah, and when i look at /tmp/cover it's showing the correct artwork, just for some reason when i change albums the artwork doesnt change in conky. i edited my last post and put up my conkyrc and template

---

### Post by VastOne on 2011-05-16
> **cccthestyle said:**
> @Sector: while trying out your fix, i figured out that in conkyrc you need to run conkyClementine with execp instead of execi which fixed my no album artwork problem

i can now get album artwork displayed using either /tmp/cover or ~/.conky/cover but the artwork fails to change. GetAlbumart script is still working fine, but the artwork displayed in conky never changes

example:

edit: relevant code

conkyrc:
```
${if_running clementine}${if_match "${execi 15 conkyClementine --datatype=ST}" == "Playing"}${execp conkyClementine --template=/home/clutch/.conky/conkyClementine.template}${endif}
```

conkyClementine.template:
```
[--datatype=TI --maxlength=27]
[--datatype=AR --maxlength=27]
[--datatype=AL --maxlength=27]
[--datatype=BR]kbps
[--datatype=YR]
${image /tmp/cover -p 0,397 -s 170x170}
```

${image /tmp/clementine-coverart.jpg

Is how it should be in /tmp

---

### Post by VastOne on 2011-05-16
> **cccthestyle said:**
> yeah, and when i look at /tmp/cover it's showing the correct artwork, just for some reason when i change albums the artwork doesnt change in conky. i edited my last post and put up my conkyrc and template

post everything.. your entire conky and clementine process please...

Make sure to remove any passwords

---

### Post by kaivalagi on 2011-05-16
> **VastOne said:**
> ${image /tmp/clementine-coverart.jpg

Is how it should be in /tmp

Latest version is /tmp/cover via either method (main script or getcoverart one)

main script options:
```
        self.parser.add_option("-d", "--datatype", dest="datatype", default="TI", type="string", metavar="DATATYPE", help=u"[default: %default] The data type options are: ST (status), CA (coverart), TI (title), AL (album), AR (artist), GE (genre), YR (year), TN (track number), FN (file name), BR (bitrate k/s), LE (length), PP (current position in percent), PT (current position in time), VO (volume), RT (rating). Not applicable at command line when using templates.")
        self.parser.add_option("-c", "--coverartpath", **[COLOR="Red"]dest="coverartpath", default="/tmp/cover"[/COLOR]**, type="string", metavar="PATH", help=u"[default: %default] The file where coverart gets copied to if found when using the --datatype=CA option. Note that if set to an empty string i.e. \"\" the original file path is provided for the coverart path.")        
        self.parser.add_option("-r", "--ratingchar", dest="ratingchar", default="*", type="string", metavar="CHAR", help=u"[default: %default] The output character for the ratings scale. Command line option overridden if used in templates.")

```

getcoverart:
```
class Clementine_GetCoverart:

    **[COLOR="red"]COVERART_DESTINATION = "/tmp/cover"[/COLOR]**
    current = ""
    use_tag_image_only = False
    
    def __init__(self):
        
        try:
            print "conkyClementine-GetCoverart - Cover art will be copied to '%s'"%self.COVERART_DESTINATION
```

---

### Post by cccthestyle on 2011-05-16
> **VastOne said:**
> post everything.. your entire conky and clementine process please...

Make sure to remove any passwords

ok here should be all of it

---

### Post by kaivalagi on 2011-05-16
> **cccthestyle said:**
> yeah, and when i look at /tmp/cover it's showing the correct artwork, just for some reason when i change albums the artwork doesnt change in conky. i edited my last post and put up my conkyrc and template

sounds like the $image variable is caching things....either use "-n" within the $image variable options or set all $image variables to not cache using "imlib_cache_size 0" before the TEXT line in the conkyrc

From [conky documentation]("http://conky.sourceforge.net/documentation.html"):
```
**imlib_cache_size**

Imlib2 image cache size, in bytes. 
Defaults to 4MiB. 
Increase this value if you use $image lots. 
**Set to 0 to disable the image cache.**
```


> **VastOne said:**
> post everything.. your entire conky and clementine process please...

Make sure to remove any passwords
Fingers crossed it's the above...don't mean to step on toes, just trying to help ;)

---

### Post by cccthestyle on 2011-05-16
> **kaivalagi said:**
> sounds like the $image variable is caching things....either use "-n" within the $image variable options or set all $image variables to not cache using "imlib_cache_size 0" before the TEXT line in the conkyrc

From [conky documentation]("http://conky.sourceforge.net/documentation.html"):
```
**imlib_cache_size**

Imlib2 image cache size, in bytes. 
Defaults to 4MiB. 
Increase this value if you use $image lots. 
**Set to 0 to disable the image cache.**
```

THIS!! throwing -n with $image fixed it!!! woohoo thanks a lot :D

edit: how my artwork got fixed, in summary: conkyClementine in conkyrc needs to be run with execp and either "imlib_cache_size 0" needs to be added before the TEXT line in the conkyrc or $image needs to be run with "-n" in conkyClementine.template

---

### Post by VastOne on 2011-05-16
> **kaivalagi said:**
> sounds like the $image variable is caching things....either use "-n" within the $image variable options or set all $image variables to not cache using "imlib_cache_size 0" before the TEXT line in the conkyrc

From [conky documentation]("http://conky.sourceforge.net/documentation.html"):
```
**imlib_cache_size**

Imlib2 image cache size, in bytes. 
Defaults to 4MiB. 
Increase this value if you use $image lots. 
**Set to 0 to disable the image cache.**
```

Fingers crossed it's the above...don't mean to step on toes, just trying to help ;)



I think you got it nailed... It was just what I was going to compare..

FYI mine is set to 0

like so

imlib_cache_size 0

Good catch K

---

### Post by vehemoth on 2011-06-18
Do you think It would be possible to get upcoming track info from the current clementine playlist, maybe have an option for datatype=tr but so many places ahead, such as datatype=tr -1 which would give the name of the next track that will play.

---

### Post by kaivalagi on 2011-06-18
Looks like it may be possible, the dbus methods expose tracklists...not sure when I would get time though.

For anyone interested in having a go the script would need to also connect to /Tracklist and retrieve the list using the GetAll method which provides the dictionary list, attached is the interface I am talking about as provided through the d-feet tool...

---

### Post by VastOne on 2011-06-18
> **kaivalagi said:**
> Looks like it may be possible, the dbus methods expose tracklists...not sure when I would get time though.

For anyone interested in having a go the script would need to also connect to /Tracklist and retrieve the list using the GetAll method which provides the dictionary list, attached is the interface I am talking about as provided through the d-feet tool...

Thanks for the tip K, I'll give it a shot

---

### Post by kaivalagi on 2011-06-18
> **VastOne said:**
> Thanks for the tip K, I'll give it a shot
PM'ed ya, hope that helps

---

### Post by Sector11 on 2011-06-18
> **VastOne said:**
> Thanks for the tip K, I'll give it a shot

I've been watching the "gmb" stuff - you do Python too?
Damn ... you're a very versatile fellow  :D

---

### Post by VastOne on 2011-06-18
> **Sector11 said:**
> I've been watching the "gmb" stuff - you do Python too?
Damn ... you're a very versatile fellow  :D

Only what my hero K, has first laid out in perfection for me...  All I did was take his script for the other music apps and made it work for Clementine

I have one ready for GMB also but cannot solve the riddle of the right key to Debian FTP Masters... to get it uploaded to Conky Companions

Thanks Bro!

Got the PM K, I appreciate that....

---

### Post by Sector11 on 2011-06-18
> **VastOne said:**
> Only what my hero K, has first laid out in perfection for me...  All I did was take his script for the other music apps and made it work for Clementine

I have one ready for GMB also but cannot solve the riddle of the right key to Debian FTP Masters... to get it uploaded to Conky Companions

Thanks Bro!

Got the PM K, I appreciate that....

I wish I could understand this stuff (Python, bash, LUA) every time I try something I feel like I stepped into quicksand.  :frown:

---

### Post by VastOne on 2011-06-18
> **Sector11 said:**
> I wish I could understand this stuff (Python, bash, LUA) every time I try something I feel like I stepped into quicksand.  :frown:

It really is a matter of trial and error to me.. a lot like conky, just more variables... and the willingness to try anything at the risk of failure but also knowing there is an answer....

---

### Post by vagrale13 on 2011-06-29
With latest version *Clementine*, length time and progress bar doesn' t work. :confused:

conkyrc 
```
Title: ${exec conkyClementine --datatype=TI --maxlength=32}}
Artist: ${exec conkyClementine --datatype=AR --maxlength=32}
Album: ${exec conkyClementine --datatype=AL --maxlength=30}
Time: ${exec conkyClementine --datatype=PT --maxlength=32} / ${exec conkyClementine --datatype=LE --maxlength=32} ${color #8370FF}${execibar 2 conkyClementine --datatype=PP}
```Here the versions
```
:~$ conkyClementine --version
conkyClementine v.2.03

:~$ clementine --version
Clementine 0.7.1 r3447
```

---

### Post by VastOne on 2011-06-29
> **vagrale13 said:**
> With latest version *Clementine*, length time and progress bar doesn' t work. :confused:

conkyrc 
```
Title: ${exec conkyClementine --datatype=TI --maxlength=32}}
Artist: ${exec conkyClementine --datatype=AR --maxlength=32}
Album: ${exec conkyClementine --datatype=AL --maxlength=30}
Time: ${exec conkyClementine --datatype=PT --maxlength=32} / ${exec conkyClementine --datatype=LE --maxlength=32} ${color #8370FF}${execibar 2 conkyClementine --datatype=PP}
```Here the versions
```
:~$ conkyClementine --version
conkyClementine v.2.03

:~$ clementine --version
Clementine 0.7.1 r3447
```

I will load it and d-feet and take a look and report back

Edit - Is the r3447 a svn version of Clementine or is that the latest deb/ppa version?

---

### Post by VastOne on 2011-06-29
> **vagrale13 said:**
> With latest version *Clementine*, length time and progress bar doesn' t work. :confused:

conkyrc 
```
Title: ${exec conkyClementine --datatype=TI --maxlength=32}}
Artist: ${exec conkyClementine --datatype=AR --maxlength=32}
Album: ${exec conkyClementine --datatype=AL --maxlength=30}
Time: ${exec conkyClementine --datatype=PT --maxlength=32} / ${exec conkyClementine --datatype=LE --maxlength=32} ${color #8370FF}${execibar 2 conkyClementine --datatype=PP}
```Here the versions
```
:~$ conkyClementine --version
conkyClementine v.2.03

:~$ clementine --version
Clementine 0.7.1 r3447
```


Your code works fine for me using

versions
```
:~$ conkyClementine --version
conkyClementine v.2.03

:~$ clementine --version
Clementine 0.7.1 
```  

The version of Clementine I have is the latest stable deb/ppa release

If you are using an svn version, I would head over to the Clementine Google apps page and report an issue on that build

---

### Post by vagrale13 on 2011-06-30
> **VastOne said:**
> If you are using an svn version, I would head over to the Clementine Google apps page and report an issue on that build
I test this *ppa* [https://launchpad.net/~me-davidsansome/+archive/clementine-dev]("https://launchpad.net/%7Eme-davidsansome/+archive/clementine-dev")

---

### Post by VastOne on 2011-06-30
> **vagrale13 said:**
> I test this *ppa* [https://launchpad.net/~me-davidsansome/+archive/clementine-dev]("https://launchpad.net/%7Eme-davidsansome/+archive/clementine-dev")

I would then go over to the google app site and let David know that the latest has broken the things you are having issues with...

When I used Clementine, I saw this type of thing fairly often as I used the dev ppa too...  I would report the issue and it would get resolved quickly...

Te dbus process is still the same, so the code on the new Clementine release must be the issue...

---

### Post by vagrale13 on 2011-07-01
> **VastOne said:**
> I would then go over to the google app site and let David know that the latest has broken the things you are having issues with...

When I used Clementine, I saw this type of thing fairly often as I used the dev ppa too...  I would report the issue and it would get resolved quickly...

Te dbus process is still the same, so the code on the new Clementine release must be the issue...
Ok... then just wait to fixed with updates. :popcorn:

---

### Post by vagrale13 on 2011-09-16
Today, with last updates the problem fixed :popcorn:
```
Clementine 0.7.3-116-g309634b
```

---

