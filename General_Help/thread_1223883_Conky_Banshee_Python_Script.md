---
title: "Conky Banshee Python Script"
date: 2009-07-26
forum: General Help
---

### Post by kaivalagi on 2009-07-26
[SIZE="1"][COLOR="Green"]**ArchLinux : **Package support is present in the AUR. All my packages can be seen here: **[http://aur.archlinux.org/packages.php?SeB=m&K=kaivalagi](http://aur.archlinux.org/packages.php?SeB=m&K=kaivalagi)**

**Ubuntu/Debian : **All the script packages have now been copied into the Conky Companions PPA. Any package updates will be provided by the team through this new ppa. The ppa can be found here: **[https://launchpad.net/~conky-companions/+archive/ppa]("https://launchpad.net/~conky-companions/+archive/ppa")**. To use this ppa first delete the old ppa files using this:
```
sudo rm /etc/apt/sources.list.d/m-buck* && sudo rm /etc/apt/sources.list.d/conkyhardcore*
```
Then follow the modified first post instructions for the scripts[/COLOR][/SIZE]

**_[SIZE=3][COLOR=Blue]Intro[/COLOR][/SIZE]_**

This is a simple script to display what is current playing in Banshee. The script talks to Banshee using dbus, and allows the outputting of track info and the use of templates...

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
sudo apt-get update && sudo apt-get install conkybanshee

```

**[COLOR=Blue]Method 2: Using deb file[/COLOR]**

Run the .deb file available at the Conky Companions PPA site here: [https://launchpad.net/~conky-companions/+archive/ppa/+packages](https://launchpad.net/~conky-companions/+archive/ppa/+packages)

Warning, this will not ensure you are kept up-to-date. Only method 1 will do that ;)

**[COLOR=Blue]Method 3: Using tar.gz file[/COLOR]**

Extract all the contents of the tar.gz file to an appropriate folder, and edit the conkyBanshee script to point to the correct location where conkyBanshee.py is. The tar.gz file is available at the Conky Companions PPA site here: [https://launchpad.net/~conky-companions/+archive/ppa/+packages](https://launchpad.net/~conky-companions/+archive/ppa/+packages)

Unless you are using a non-Debian based OS I don't suggest this. Users of Debian/Ubuntu flavour OS's should ideally use method 1.

Again will will not receive updates using this method. ONLY method 1 can do this for you ;) ;)

All further details on setup are orientated around the deb package based install, so may differ from what you choose your setup to be, if done using the tarball.


**_[SIZE=3][COLOR=Blue]Usage Help[/COLOR][/SIZE]_**

You can get the current help options at any time by running (change the path as necessary):

```

conkyBanshee -h

```or

```

conkyBanshee --help

``````
Usage: conkyBanshee [options]
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

Development history going forwards can be seen here [URL="https://code.launchpad.net/%7Econky-companions/+junk/conkybanshee"]https://code.launchpad.net/~conky-companions/+junk/conkybanshee
[/URL] All packages available from me can be found here: [https://launchpad.net/~conky-companions/+archive/ppa]("https://launchpad.net/%7Econky-companions/+archive/ppa")

---

### Post by cwk on 2009-08-05
I'm having a little trouble getting the cover art to display. I don't usually use $image, so I'm sure it's a simple syntax issue.

```
${alignc}${image ${exec conkyBanshee --datatype=CA}}
```

This gives me the following error: 

Conky: not implemented obj type 44

Any ideas what I'm doing wrong? Great script btw.

---

### Post by kaivalagi on 2009-08-06
> **cwk said:**
> I'm having a little trouble getting the cover art to display. I don't usually use $image, so I'm sure it's a simple syntax issue.

```
${alignc}${image ${exec conkyBanshee --datatype=CA}}
```

This gives me the following error: 

Conky: not implemented obj type 44

Any ideas what I'm doing wrong? Great script btw.

In all honesty I dont use the image tag in conky, and as this thread is fairly new I would suggest posting into the conkyrc thread where people have used it and succeeded. By all means post the solution here so others using this script though.

---

### Post by opothehippo on 2009-08-11
Thanks so much for the script. It works great and was easy to use because I already knew your conkyForecast script.

If anyone figures out how to show the album art, I (and most likely other members using this script) would love to know.

---

### Post by cwk on 2009-08-11
Got it. See this page of the conkyrc thread: [http://ubuntuforums.org/showthread.php?t=281865&page=850](http://ubuntuforums.org/showthread.php?t=281865&page=850)

---

### Post by kaivalagi on 2009-08-12
> **opothehippo said:**
> Thanks so much for the script. It works great and was easy to use because I already knew your conkyForecast script.

If anyone figures out how to show the album art, I (and most likely other members using this script) would love to know.

There is a post on this same thing with conkyRhythmbox, the howto posted will work for this script too if you swap out conkyRhythmbox for conkyBanshee in your conkyrc:

[http://ubuntuforums.org/showpost.php?p=7677777&postcount=151](http://ubuntuforums.org/showpost.php?p=7677777&postcount=151)

Hope that helps

---

### Post by Morton's Red Stapler on 2009-08-17
that doesnt seem to work for banshee, though it does work for both Exaile and Rhythmbox, not sure why it wont work on Banshee.

---

### Post by kaivalagi on 2009-08-17
> **Morton's Red Stapler said:**
> that doesnt seem to work for banshee, though it does work for both Exaile and Rhythmbox, not sure why it wont work on Banshee.

Is Banshee showing album art in the player for the songs? Are you playing mp3s?

---

### Post by zyxyellowxyz on 2009-08-17
> **kaivalagi said:**
> Is Banshee showing album art in the player for the songs? Are you playing mp3s?

I'm having the same problem as it doesn't show the picture. The only error I get is:```
Conky: Unable to load image '/home/<name>/.album'
```

I am using ```
${alignc}${exec cp "`conkyBanshee --datatype=CA | sed -e 's/\\\//g'`" /home/<name>/.album}${image /home/<name>/.album -p 0,2 -s 64x64}
```

I also have the line that [this post]("http://ubuntuforums.org/showpost.php?p=7677777&postcount=151") suggested I add to my conkyrc```
imlib_cache_size 0
```

And I still get the error. The image is in ~/.album but conky is unable to load it for some reason. Any guesses?

**edit** I am playing MP3s, and the album art is showing in Banshee

---

### Post by kaivalagi on 2009-08-18
> **zyxyellowxyz said:**
> I'm having the same problem as it doesn't show the picture. The only error I get is:```
Conky: Unable to load image '/home/<name>/.album'
```

I am using ```
${alignc}${exec cp "`conkyBanshee --datatype=CA | sed -e 's/\\\//g'`" /home/<name>/.album}${image /home/<name>/.album -p 0,2 -s 64x64}
```

I also have the line that [this post]("http://ubuntuforums.org/showpost.php?p=7677777&postcount=151") suggested I add to my conkyrc```
imlib_cache_size 0
```

And I still get the error. The image is in ~/.album but conky is unable to load it for some reason. Any guesses?

**edit** I am playing MP3s, and the album art is showing in Banshee

<name> needs replacing with YOUR username

if it is then you need to make sure you are running conky v1.7.1+, as previous versions do not support the image tag in your conkyrc

If "conkyBanshee --datatype=CA" run in the terminal return the album art then the problem is not with my script but with the scripting surrounding it...

---

### Post by zyxyellowxyz on 2009-08-18
> **kaivalagi said:**
> <name> needs replacing with YOUR username
It was/is, I just left it out because I don't like to share it with the world.
> **kaivalagi said:**
> if it is then you need to make sure you are running conky v1.7.1+, as previous versions do not support the image tag in your conkyrc
I had just unistalled conky and recompiled it from source to make sure I had images enabled.```
Conky 1.7.1.1 compiled Mon Aug 17 18:31:57 CDT 2009 for Linux 2.6.28-14-generic (i686)

Compiled in features:

System config file: /usr/local/etc/conky/conky.conf

 X11:
  * Xdamage extension
  * XDBE (double buffer extension)
  * Xft

 Music detection:
  * MPD
  * MOC

 General:
  * OpenMP
  * math
  * hddtemp
  * portmon
  * RSS
  * Lua
  * nvidia
  * config-output
**  * Imlib2**
  * ALSA mixer support
  * apcupsd
```

> **kaivalagi said:**
> If "conkyBanshee --datatype=CA" run in the terminal return the album art then the problem is not with my script but with the scripting surrounding it...
My husband ended up being able to fix it by changing it to this:
```
${execi cp "`conkyBanshee --datatype=CA | sed -e 's/\\\//g'`" /home/<name>/.album/image.jpg}${image /home/<name>/.album/image.jpg -p 0,2 -s 64x64}
```
Apparently it was having troubles calling the different image names from the ~/.album folder so now when the images get copied, they're all named image.jpg.
Apparently that was the only thing that was wrong when I posted that yesterday. It works now, and I'm happy. :D

---

### Post by kaivalagi on 2009-08-18
> **zyxyellowxyz said:**
> My husband ended up being able to fix it by changing it to this:
```
${execi cp "`conkyBanshee --datatype=CA | sed -e 's/\\\//g'`" /home/<name>/.album/image.jpg}${image /home/<name>/.album/image.jpg -p 0,2 -s 64x64}
```
Apparently it was having troubles calling the different image names from the ~/.album folder so now when the images get copied, they're all named image.jpg.
Apparently that was the only thing that was wrong when I posted that yesterday. It works now, and I'm happy. :D

Good times :)

---

### Post by WiseGuy1020 on 2009-08-24
Hey K,

I have two problems with the Banshee script and I was hoping you might help me with it.


1. Whenever banshee is playing a song that lacks just a year,genre,or track number conkyBanshee will not display at all.

2. When banshee is playing a song that does have all of the tags the datatypes PP and LE are displaying as question marks.

edit: The above was using the -n option. With the -n option removed #2 still happens. And the #1 scenario with the -n option removed is all unknowns even if some of the tags are known.(screen-shot #3) 



Please help me out.

Thanks,

D.

---

### Post by WiseGuy1020 on 2009-08-27
the datatypes PP and LE are displaying fine after a reinstall.

But when conkyBanshee comes across a song that does not have all the tags filled out it displays unknown for every datatype.

Thanks for your help. I am using a bunch of your other scripts and they all work perfectly.

D.

---

### Post by kedde on 2009-09-25
I solved the year problem like this:

get the tar.gz file from 
[https://launchpad.net/~m-buck/+archive/conky/+sourcepub/682918/+listing-archive-extra](https://launchpad.net/~m-buck/+archive/conky/+sourcepub/682918/+listing-archive-extra)

Edited conkyBanshee.py from the tar.gz after the lines:

                        ```

                        title = props["name"]
                        album = props["album"]
                        artist = props["artist"]
```
                        
I added the following code:
                        ```

                        try:
                            year = str(props["year"])
                            tracknumber = str(props["track-number"])
                            genre = props["genre"]
                        except:
                            year = "?"
                            tracknumber = "?"
                            genre = "?"
```

and removed these lines:
                       ```
 
                        year = str(props["year"])
                        tracknumber = str(props["track-number"])
                        genre = props["genre"]
```
                        
lastly run the setup 

( I already had conkyBanshee installed using the apt method, so I just executed the command:
 ```
sudo cp conkyBanshee.py /usr/share/conkybanshee/conkyBanshee.py
```

)

---

### Post by kaivalagi on 2009-09-25
> **kedde said:**
> I solved the year problem like this:

get the tar.gz file from 
[https://launchpad.net/~m-buck/+archive/conky/+sourcepub/682918/+listing-archive-extra](https://launchpad.net/~m-buck/+archive/conky/+sourcepub/682918/+listing-archive-extra)

Edited conkyBanshee.py from the tar.gz after the lines:


Nice call...I don't use Banshee plus all my music is tagged properly so I need some heads up on the underlying issues from someone he is a little more techy that yourself :)

Your above fix will work but could result in all ?'s when only once tag isn't available - I suggest for now that you wrap each call with it's own try/catch block...I have a busy weekend so won't get a fix out anytime soon, maybe next week.

Is the underlying issue that any dbus call for tag data that isn't there will throw an exception? If that is the case it sounds like a bug with the Banshee dbus service to me...it needs raising with them :) I don't think any of the other dbus services I use in python has this behaviour...

---

### Post by tekniklr on 2009-09-25
I'm working on this right now. I'm listening to SomaFM, so the Album and Cover values are blank too. Here is code that seems to be working, (starting at line 142 of conkyBanshee.py)
```
                        try:
                            title = props["name"]
                        except:
                            title = "?"

                        try:
                            album = props["album"]
                        except:
                            album = "?"

                        try:
                            artist = props["artist"]
                        except:
                            artist = "?"

                        try:
                            year = str(props["year"])
                        except:
                            year = "?"

                        try:
                            tracknumber = str(props["track-number"])
                        except:
                            tracknumber = "?"

                        try:
                            genre = props["genre"]
                        except:
                            genre = "?"
```
And at line 176 (after the above changes), for the coverart:
```
                        # get coverart url or file link
                        if "artwork-id" in props:
                            coverart = os.path.join(os.path.expanduser("~/.cache/album-art/"),str(props["artwork-id"]) +".jpg")
                            if coverart.find("http://") != -1:
                                coverart = ""
                        else:
                            coverart = ""
```
My apologies if this is messy or just plain wrong. I'm a perl/PHP sort of girl, and this is my first time playing with python. It seems to work, so I figured I'd share!

---

### Post by kaivalagi on 2009-09-26
> **tekniklr said:**
> I'm working on this right now. I'm listening to SomaFM, so the Album and Cover values are blank too.

...

My apologies if this is messy or just plain wrong. I'm a perl/PHP sort of girl, and this is my first time playing with python. It seems to work, so I figured I'd share!

Thanks, code looks okay to me, although I think try/catch block aren't necessary looking at the code again...this sort of thing is better:

```

if "name" in props:
    title = props["name"]
else:
    title = None
```

Later on in the code null values are handled based on the --nounknownoutput option, so setting it to None if not available makes sense.

I'm gonna start making the changes you, kedde and WiseGuy1020 highlighted and I'll post the deb package here before publishing so you guys can test it to make sure all is good :)

[COLOR="Blue"]Edit: @All users who posted issues, a new deb package and tarball are attached here. The deb package will install on Jaunty (and poss' Intrepid), please test and let me know of any issues. If all is okay a proper package for all Ubuntu versions will be released. Cheers[/COLOR]

[COLOR="Red"]Edit Again: No response back but I have been running the new conkyBanshee locally all day without issues so I am starting to get the package published soon...3 hrs for a built to start on launchpad :([/COLOR]

---

### Post by kaivalagi on 2009-09-27
**[COLOR=Green][SIZE=4]UPDATE[/SIZE][/COLOR]**

The script has had the following changes made:

[LIST]
[*]Updated music info retrieval to stop unnecessary exceptions
[/LIST]
Package changes can be seen here: [http://launchpadlibrarian.net/32492584/conkybanshee_2.01_source.changes](http://launchpadlibrarian.net/32492584/conkybanshee_2.01_source.changes)

All apt packages are now available and the first post has been updated

Chimo

---

### Post by bluebyt on 2009-10-03
Hi,
  The cover doesn't display and the position is not good.

script:
```
use_xft yes
xftfont Liberation Sans:size=8
override_utf8_locale yes

text_buffer_size 2048
update_interval 1
total_run_times 0
double_buffer yes
no_buffers yes
net_avg_samples 1
cpu_avg_samples 1

own_window_class Conky
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

default_color 2B2B2B
draw_shades no

color0 1E1C1A
color1 E07A1F
color2 1E1C1A

alignment bottom_right
gap_x 25
gap_y 40
minimum_size 182 0
maximum_width 182

imlib_cache_size 0

TEXT
${font Liberation Sans:style=Bold:size=8}SYSTEM $stippled_hr${font}
${color0}${voffset 6}${font OpenLogos:size=19}u${font}${color}${goto 32}${voffset -14}Kernel:  ${alignr}${color2}${kernel}${color}
${goto 32}Uptime: ${alignr}${color2}${uptime}${color}
${offset 1}${color0}${font Poky:size=16}P${font}${offset -19}${voffset 9}${cpubar cpu0 4,18}${color}${voffset -15}${voffset -1}${goto 32}CPU1: ${font Liberation Sans:style=Bold:size=8}${color1}${cpu cpu1}%${color}${font} ${alignr}${color2}${cpugraph cpu1 8,60 CE5C00 E07A1F}${color}
${color0}${font Poky:size=16}M${font}${color}${goto 32}${voffset -7}RAM: ${font Liberation Sans:style=Bold:size=8}${color1}$memperc%${color}${font}
${offset 1}${voffset 2}${color2}${membar 4,18}${color}${goto 32}${voffset -2}F: ${color2}${memeasyfree}${color} U: ${color2}${mem}${color}
${voffset 2}${color0}${font Poky:size=15}a${font}${color}${goto 32}${voffset -10}Processes: ${color2}${alignr 13}CPU${alignr}RAM${color}
${voffset -1}${goto 42}${color2}${top name 1}${color}${font Liberation Sans:style=Bold:size=8}${color1} ${goto 124}${top cpu 1}${alignr }${top mem 1}${color}${font}
${voffset -1}${goto 42}${color2}${top name 2}${color}${font Liberation Sans:style=Bold:size=8}${color1} ${goto 124}${top cpu 2}${alignr }${top mem 2}${color}${font}
${voffset -1}${goto 42}${color2}${top name 3}${color}${font Liberation Sans:style=Bold:size=8}${color1} ${goto 124}${top cpu 3}${alignr }${top mem 3}${color}${font}
${voffset 4}${font Liberation Sans:style=Bold:size=8}DATE $stippled_hr${font}
${voffset -12}${goto 28}${font Arial Black:size=38}${color2}${time %H}${color}${font}${voffset -28}${font Liberation Sans:style=Bold:size=11}${color2}${time :%M}${time :%S}${color}${font}
${voffset -3}${goto 100}${font Liberation Sans:style=Bold:size=8}${color2}${time %A}${color}${font}
${voffset -1}${goto 100}${time %d %B %Y}
${voffset 2}${color0}${font Poky:size=15}d${font}${color}${voffset -6}${font Liberation Mono:size=8}${execpi 10800 DJS=`date +%_d`; cal | sed 's/^/${alignc} /' | sed s/" $DJS "/" "'${font Liberation Mono:style=bold:size=8}${color1}'"$DJS"'${color}${font}${font Liberation Mono:size=8}'" "/}${font}${font}${voffset -14}
${voffset -2}${font Liberation Sans:style=Bold:size=8}PHOTO $stippled_hr${font}
${execi 10800 ~/.conky/conkyPhoto.sh}${image /tmp/conkyPhoto.png -s 150x150 -p 20,330}${voffset 142}
${voffset 4}${font Liberation Sans:style=Bold:size=8}BANSHEE $stippled_hr${font}
${execi 10 ~/.conky/conkyCover.sh}${execpi 10 ~/.conky/conkyBanshee.py -t ~/.conky/conkyPlayer.template}
${voffset 4}${font Liberation Sans:style=Bold:size=8}WEATHER $stippled_hr${font}
${if_existing /proc/net/route wlan0}
${execpi 10800 ~/.conky/conkyForecast.py --location=CAXX0243 -t ~/.conky/conkyForecast.template}
${else}${if_existing /proc/net/route eth0}
${execpi 10800 ~/.conky/conkyForecast.py --location=CAXX0243 -t ~/.conky/conkyForecast.template}
${endif}${else}${if_existing /proc/net/route ppp0}
${execpi 10800 ~/.conky/conkyForecast.py --location=CAXX0243 -t ~/.conky/conkyForecast.template}
${endif}${else}${voffset 4}${color0}${font PizzaDude Bullets:size=12}4${font}${color}${goto 32}Weather Unavailable${endif}${endif}
```

---

### Post by kaivalagi on 2009-10-04
> **bluebyt said:**
> Hi,
  The cover doesn't display and the position is not good.


Should work but you need to have $image support in conky and the template setup to support. To make sure you get a cover art image path try running this:

```
conkyBanshee --datatype=CA
```

You should get an image path like this:

```
/home/mark/.cache/album-art/atribecalledquest-beatsrhymesandlife.jpg
```

I can't help you with your conkyrc 'cause I don't use conky to do this, I use my app "gtk-desktop-info", see my sig for more on it. Try searching or posting a question on use of the $image command here: [http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

Hope that helps

---

### Post by bluebyt on 2009-10-04
I get nothing when I run this: conkyBanshee --datatype=CA

I have Conky-all 1.7.2

---

### Post by kaivalagi on 2009-10-04
> **bluebyt said:**
> I get nothing when I run this: conkyBanshee --datatype=CA

I have Conky-all 1.7.2

Are you running the latest version of the script:

```
> conkyBanshee --version
conkyBanshee v.2.01
```

Also, does this happen for all your music, and is the music you are playing showing cover art in Banshee too? Banshee needs to have the cover art working before the script will bring back results...

---

### Post by bluebyt on 2009-10-04
Yes
conkyBanshee --version
conkyBanshee v.2.01

Yes this is happening for all my music and the cover are showing in Banshee.

I tried with ConkyExaile and ConkyRhythmbox and the cover are not showing up either.

---

### Post by kaivalagi on 2009-10-05
> **bluebyt said:**
> Yes
conkyBanshee --version
conkyBanshee v.2.01

Yes this is happening for all my music and the cover are showing in Banshee.

I tried with ConkyExaile and ConkyRhythmbox and the cover are not showing up either.

Strange, I you're gonna need to help me out here, what version of OS/window manager etc are you running. Also, run this and post back the results:

```
conkyBanshee --datatype=CA --verbose
```

I get:

```
*** INITIAL OPTIONS:
    datatype: CA
    template: None
    ratingchar: *
    nounknownoutput: False
    maxlength: 0
    verbose: True
    errorlogfile: None
    infologfile: None
INFO: Calling dbus interface for music data
INFO: Setting up dbus interface
INFO: Calling dbus interface for music data
INFO: Preparing output for datatype:CA
/home/mark/.cache/album-art/asherroth-2009asleepinthebreadaisle.jpg
```

---

### Post by bluebyt on 2009-10-05
Ubuntu karmic 9.10 beta -- gnome 2.28

conkyBanshee --datatype=CA --verbose:
*** INITIAL OPTIONS:
    datatype: CA
    template: None
    ratingchar: *
    nounknownoutput: False
    maxlength: 0
    verbose: True
    errorlogfile: None
    infologfile: None



Thanks you very much!

---

### Post by kaivalagi on 2009-10-05
> **bluebyt said:**
> Ubuntu karmic 9.10 beta -- gnome 2.28

conkyBanshee --datatype=CA --verbose:
*** INITIAL OPTIONS:
    datatype: CA
    template: None
    ratingchar: *
    nounknownoutput: False
    maxlength: 0
    verbose: True
    errorlogfile: None
    infologfile: None



Thanks you very much!

Karmic beta aye, I have had other issues reported from Karmic beta users. These have happened with previous betas too, the python libraries tend to get messed up before release candidate sometimes.

I will be upgrading after the full release is out (I don't do betas anymore) so won't be able to resolve the issue easily until after then.

You may be able to give me a heads up on the situation and a possible "blind" fix by installing/running "d-feet", it displays all the d-bus interfaces on your machine. Open it after Banshee is running, navigate to the banshee d-bus interface and take a screenshot like the one I have attached for the interface in Jaunty...

Sorry I can't be of more help, but this is the risk you take when you update to a Beta version, hence why I don't anymore...

Let me know what you find out anyway, something obvious might rear it's head...

Cheers

---

### Post by bluebyt on 2009-10-06
Here the D-Feet screenshot.
Thanks you for your help!

---

### Post by kaivalagi on 2009-10-06
> **bluebyt said:**
> Here the D-Feet screenshot.
Thanks you for your help!

Looks the same...nothing obviously wrong

Have you tried uninstalling/reinstalling the conkybanshee package since the upgrade to Karmic? It may turn up issues with package dependancies....

To be honest I can't see what the issue is though, it will probably need to wait until I do the upgrade myself so I can debug the code and understand what's happening.

---

### Post by coldflame23 on 2009-10-17
[IMG]http://omploader.org/vMmtiNQ[/IMG]

```
background yes
    use_xft yes
    xftfont DejaVu Sans:size=5.5
    xftalpha 0.5
    update_interval 1.0
    total_run_times 0
    own_window yes
    own_window_type normal
    own_window_transparent yes
    own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
    double_buffer yes
    minimum_size 180 20
    maximum_width 300
    draw_shades no
    draw_outline no
    draw_borders no
    draw_graph_borders yes
    default_color black
    default_shade_color white
    default_outline_color green
    alignment top_right
    gap_x 10
    gap_y 2
    no_buffers yes
    uppercase no
    cpu_avg_samples 2
    override_utf8_locale yes
    imlib_cache_size 0lol

TEXT

SYSTEM ${hr 2}
${font StyleBats:size=16}x${font}   Hostname: $alignr$nodename
${font OpenLogos:size=16}t${font}   CrunchBang Linux  ${alignr}9.04.01
${font OpenLogos:size=16}u${font}   Kernel:  ${alignr}${kernel}
${font StyleBats:size=16}A${font}   CPU1 ${alignr}${cpu cpu1}% ${cpubar cpu1 8,60}
${font StyleBats:size=16}A${font}   CPU2 ${alignr}${cpu cpu2}% ${cpubar cpu2 8,60}
${font StyleBats:size=16}K${font}   Temp: ${alignr}${acpitemp}C
${font StyleBats:size=16}g${font}   RAM: $memperc% ${alignr}${membar 8,60}
${font StyleBats:size=16}j${font}   SWAP: $swapperc% ${alignr}${swapbar 8,60}

PROCESSES ${hr 2}
NAME $alignr PID    CPU
${top name 1} $alignr ${top pid 1} ${top cpu 1}
${top name 2} $alignr ${top pid 2} ${top cpu 2}
${top name 3} $alignr ${top pid 3} ${top cpu 3}
${top name 4} $alignr ${top pid 4} ${top cpu 4}

HD ${hr 2}
${voffset 4}${font Pie charts for maps:size=14}7${font}   ${voffset -5}Linux: ${alignr}${fs_bar 8,60 /}

${font Pie charts for maps:size=14}7${font}   ${voffset -5}Media: ${alignr}${fs_bar 8,60 /media/sda1}

Music ${hr 2}
${alignc}${exec conkyBanshee --datatype=AR}
${alignc}${exec conkyBanshee --datatype=CA}}
${alignc}${exec conkyBanshee --datatype=TI}
${alignc}${exec conkyBanshee --datatype=AL} (${exec conkyBanshee --datatype=YR})
${alignc}${exec conkyBanshee --datatype=PT} / ${alignc}${exec conkyBanshee --datatype=LE}
NETWORK ${hr 2}
${if_existing /proc/net/route wlan0}
${voffset -6}${font PIZZADUDEBULLETS:size=14}O${font}Up: ${upspeed wlan0} kb/s ${alignr}${upspeedgraph wlan0 8,60 789E2D A7CC5C}
${voffset 4}${font PIZZADUDEBULLETS:size=14}U${font}Down: ${downspeed wlan0} kb/s ${alignr}${downspeedgraph wlan0 8,60 789E2D A7CC5C}
${voffset 4}${font PIZZADUDEBULLETS:size=14}N${font}Upload: ${alignr}${totalup wlan0}
${voffset 4}${font PIZZADUDEBULLETS:size=14}T${font}Download: ${alignr}${totaldown wlan0}
${voffset 4}${font PIZZADUDEBULLETS:size=14}a${font}   Local Ip: ${alignr}${addr wlan0}

Signal: ${wireless_link_qual wlan0}% ${alignr}${wireless_link_bar 8,60 wlan0}${else}${if_existing /proc/net/route eth0}
Up: ${upspeed eth0} kb/s ${alignr}${upspeedgraph eth0 8,60 789E2D A7CC5C}
Down: ${downspeed eth0} kb/s ${alignr}${downspeedgraph eth0 8,60 789E2D A7CC5C}
Upload: ${alignr}${totalup eth0}
Download: ${alignr}${totaldown eth0}${endif}${else}${if_existing /proc/net/route eth1}
Up: ${upspeed eth0} kb/s ${alignr}${upspeedgraph eth1 8,60 789E2D A7CC5C}
Down: ${downspeed eth0} kb/s ${alignr}${downspeedgraph eth0 8,60 789E2D A7CC5C}
Upload: ${alignr}${totalup eth0}
Download: ${alignr}${totaldown eth0}${endif}${else}${font PizzaDude Bullets:size=14}4${font}   Network Unavailable${endif}

WEATHER ${hr 2}
${if_existing /proc/net/route wlan0}
${voffset -8}${alignr 56}${font ConkyWeather:style=Bold:size=40}${execi 600 conkyForecast --location=POXX0022 --datatype=WF}${font}
${voffset -52}${font Weather:size=40}y${font}   ${voffset -38}${font Trebuchet MS:size=26}${execi 600 conkyForecast --location=POXX0022 --datatype=HT}${font}


${voffset 0}${font}Barometer Tendency: ${alignr}${execi 600 conkyForecast --location=POXX0022 --datatype=BD}
${voffset 0}Humidity: ${alignr}${execi 600 conkyForecast --location=POXX0022 --datatype=HM}
${voffset 0}${font}Wind Speed: ${alignr}${execi 600 conkyForecast --location=POXX0022 --hideunits --datatype=WS} km/h ${execi 600 conkyForecast --location=POXX0022 --hideunits --datatype=WD}
${voffset 0}Daylight: ${alignr}${execi 600 conkyForecast --location=POXX0022 --datatype=SR} - ${execi 600 conkyForecast --location=POXX0022 --datatype=SS}

${else}${if_existing /proc/net/route eth0}
${voffset -8}${alignr 56}${font ConkyWeather:style=Bold:size=40}${execi 600 conkyForecast --location=POXX0022 --datatype=WF}${font}
${voffset -52}${font Weather:size=40}y${font}   ${voffset -38}${font Trebuchet MS:size=26}${execi 600 conkyForecast --location=POXX0022 --datatype=HT}${font}

${voffset 0}${font}Barometer Tendency: ${alignr}${execi 600 conkyForecast --location=POXX0022 --datatype=BD}
${voffset 0}Humidity: ${alignr}${execi 600 conkyForecast --location=POXX0022 --datatype=HM}
${voffset 0}${font}Wind Speed: ${alignr}${execi 600 conkyForecast --location=POXX0022 --hideunits --datatype=WS} km/h ${execi 600 conkyForecast --location=POXX0022 --hideunits --datatype=WD}
${voffset 0}Daylight: ${alignr}${execi 600 conkyForecast --location=POXX0022 --datatype=SR} - ${execi 600 conkyForecast --location=POXX0022 --datatype=SS}

```

conkyBanshee isn't displaying cdcover . only location of file.

---

### Post by kaivalagi on 2009-10-17
> **coldflame23 said:**
> conkyBanshee isn't displaying cdcover . only location of file.

That's because conky can't display an image from a script directly, the script returns the path to the coverart, it's then up to you to make it work with conky :)

You'll need to use the $image variable in your conkyrc, there is help here: [http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html)

There are also posts on displaying images in conky in the conkyrc thread somewhere. You might want to ask again in that thread whilst also posting your conkyrc: [http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

You can also look at examples with the forecast script which work the same way here: [http://conky.linux-hardcore.com/?page_id=2487](http://conky.linux-hardcore.com/?page_id=2487)

Also, it is worth mentioning that you have an awful amount of execs for the forecast and banshee scripts, you only need one for each if you use templates with the scripts. The example files for both forecast and banshee scripts will explain how, read through the first post here and at the forecast thread for info on where to look.

You have a bit of reading to do but it will be worth it!

Note: you need version 1.7.2 of conky to use this feature (karmic version by default, if you're no using karmic then find a suitable deb or compile conky yourself)

Hope that helps

Chimo

---

### Post by kaivalagi on 2009-11-01
[COLOR=Red]I have switched OS and now use **ArchLinux** rather than any debian based distro. It looks like the continuing support of my scripts will be **without ppa updates**, and instead my time will support AUR based installs once I get to understand them. I will provide the usual tarball downloads of the source for non Arch users from within these forum.[/COLOR]

---

### Post by kaivalagi on 2010-01-09
[SIZE="1"][COLOR="RoyalBlue"]**ArchLinux : **Package support is present in the AUR. All my packages can be seen here: [http://aur.archlinux.org/packages.php?SeB=m&K=kaivalagi](http://aur.archlinux.org/packages.php?SeB=m&K=kaivalagi)[/COLOR][/SIZE]

**[COLOR="Blue"][SIZE="3"]IMPORTANT NEWS[/SIZE]**

All the script packages have now been copied into the Conky Hardcore PPA. Any package updates will be provided by the team through this new ppa.

The ppa can be found here: [https://launchpad.net/~conkyhardcore/+archive/ppa]("https://launchpad.net/~conkyhardcore/+archive/ppa")

To use this ppa first delete the old ppa files using this:
```
sudo rm /etc/apt/sources.list.d/m-buck*
```
Then follow the modified first post instructions for the scripts
[/COLOR]

---

### Post by Ahriman on 2010-01-31
So, just a quick question:
Is there a way to get the progress of the current song as a progress bar?

---

### Post by kaivalagi on 2010-01-31
> **Ahriman said:**
> So, just a quick question:
Is there a way to get the progress of the current song as a progress bar?

The below give a value from 0 to 100 for progress:

```
conkyBanshee --datatype=PP
```

If that is combined with $execibar you will get a bar, e.g.:

```
${execibar 1 conkyBanshee --datatype=PP}

```

---

### Post by llawwehttam on 2010-02-15
I know this thread is old but as an Arch user I just installed from source but the script gets no data. I am running banshee but all I see in conky is 'unknown' for everything.

Any ideas?

---

### Post by kaivalagi on 2010-02-15
> **llawwehttam said:**
> I know this thread is old but as an Arch user I just installed from source but the script gets no data. I am running banshee but all I see in conky is 'unknown' for everything.

Any ideas?

Using Arch myself, now installing Banshee

---

### Post by wimille on 2010-02-15
Hi

I discovered conky a few days ago and i started to make my own conkyrc. I also used Banshee as audio player. And so, i wanted to have information (title, cover and artist) in my conky. 

And i've found your script. It works great. And, with the image function, its possible now to have my albumart in conky.

My code :
```

 ${exec cp "`conkyBanshee --datatype=CA | sed -e 's/\\\//g'`" /home/beware/.conky/album}${image /home/beware/.conky/album -p 29,380 -s 192x192}

```

And a screenshot to see the result :
(Text is in french 'cause i'm french :) and i'm using arch)
[[IMG]http://img199.imageshack.us/img199/4512/conkybeware.th.png[/IMG]](http://img199.imageshack.us/i/conkybeware.png/)

Thanks to you for the script.

---

### Post by kaivalagi on 2010-02-15
> **wimille said:**
> Hi

I discovered conky a few days ago and i started to make my own conkyrc. I also used Banshee as audio player. And so, i wanted to have information (title, cover and artist) in my conky. 

And i've found your script. It works great. And, with the image function, its possible now to have my albumart in conky.

Thanks to you for the script.

Glad you like it, Cheers

---

### Post by kaivalagi on 2010-02-15
> **llawwehttam said:**
> I know this thread is old but as an Arch user I just installed from source but the script gets no data. I am running banshee but all I see in conky is 'unknown' for everything.

Any ideas?

Okay, I just tested it with banshee out of extra and it works fine:

```
 [mark@towerpc1 ~]$ conkyBanshee --datatype=AR
A Tribe Called Quest
 [mark@towerpc1 ~]$ conkyBanshee --datatype=TI
Award Tour
 [mark@towerpc1 ~]$ conkyBanshee --datatype=PP
29
 [mark@towerpc1 ~]$ conkyBanshee --datatype=LE
3:28

```

Sounds like the mp3 files or whatever you have do not have any info available? What are you playing, and can you confirm there is id3 info?

[COLOR="Blue"]Edit: use conkybanshee-bzr in the AUR to install!
e.g. yaourt -S conkybanshee-bzr[/COLOR]

---

### Post by WiseGuy1020 on 2010-02-16
Wow k. That is hilarious. I just switched to Arch myself. It is awesome that all your stuff is in the AUR.

Keep up the good work.

---

### Post by kaivalagi on 2010-02-17
> **WiseGuy1020 said:**
> Wow k. That is hilarious. I just switched to Arch myself. It is awesome that all your stuff is in the AUR.

Keep up the good work.

I have a topic dedicated to this stuff on the Arch forums: [http://bbs.archlinux.org/viewtopic.php?id=85524](http://bbs.archlinux.org/viewtopic.php?id=85524). The AUR is perfect for these scripts, they get pulled down and built from my launchpad site (bzr) on install

Arch is great, I'll never go back to Ubuntu I don't think, Arch is more cutting edge and updates are in smaller chunks more often...plus I have much more control of what **MY** OS is doing...suits me :)

---

### Post by wimille on 2010-02-26
Hi,

I'm a Arch user, and this morning i've updated banshee (v1.54). And i've noticed that the cover is now in : $HOME/.cache/media-art and no more in $HOME/.cache./album-art

I don't know if this change is also available on other distribution.

---

### Post by kaivalagi on 2010-02-26
> **wimille said:**
> Hi,

I'm a Arch user, and this morning i've updated banshee (v1.54). And i've noticed that the cover is now in : $HOME/.cache/media-art and no more in $HOME/.cache./album-art

I don't know if this change is also available on other distribution.

As you can appreciate I don't use all the players I have scripts for and so I can't test banshee (I use mpd + sonata)

I think this may be one of these scenarios where Arch has a newer version of banshee in it's repos than in Ubuntu's. Can anyone tell us what the current version in the Ubuntu repos is?

I've attached a newer version of the script which has the old coverart path replaced with the new on line 174. Copy the contents of the attached tarball over the top of the existing py file here: /usr/share/conkybanshee/conkyBanshee.py

If this is an issue for more and more people I will rollout updates in the AUR and PPA

Cheers

---

### Post by wimille on 2010-02-26
Hi

I'm also using Ubuntu on my server, so i can tell you what version is present. On official repos (ubuntu/universe for karmic) it's version 1.51.

Also, i've tried your new version, and it's work perfectly. Thanks.

---

### Post by kaivalagi on 2010-02-27
> **wimille said:**
> Hi

I'm also using Ubuntu on my server, so i can tell you what version is present. On official repos (ubuntu/universe for karmic) it's version 1.51.

Also, i've tried your new version, and it's work perfectly. Thanks.

I think I'll update the package in the AUR with a new code revision but not update the PPA packages yet...

[COLOR="Blue"]Edit: conkybanshee-bzr in the AUR has been updated as the default banshee version in Arch is 1.5.3 already...[/COLOR]

---

### Post by Pablo Pablovski on 2010-02-28
Works perfectly with ubuntu 9.10 64bit and the latest version of Banshee (1.5.4), downloaded from the PPA this morning. 

Thanks, kaivalagi!

---

### Post by kaivalagi on 2010-02-28
> **Pablo Pablovski said:**
> Works perfectly with ubuntu 9.10 64bit and the latest version of Banshee (1.5.4), downloaded from the PPA this morning. 

Thanks, kaivalagi!

That's good to know, I think I'll have to code it so it handles either location i.e. if it finds a file in either path use it

Once that is done I'll upload the source and I'll have to ask someone nicely to build it for Ubuntu as I do not have the tools available, I'm using a non-debian system now.

---

### Post by kaivalagi on 2010-03-01
> **wimille said:**
> Hi

I'm also using Ubuntu on my server, so i can tell you what version is present. On official repos (ubuntu/universe for karmic) it's version 1.51.

Also, i've tried your new version, and it's work perfectly. Thanks.

Wimille, I don't suppose you installed the latest version of this script from the AUR recently?

I made further changes to the script before rolling it out to ensure it worked as before if the new path wasn't found. If you are running conkybanshee-bzr could you make sure it is the latest version and let me know if it still works like the quick fix I did? Thanks!

---

### Post by wimille on 2010-03-02
Hi,

In fact, i did not use the bzr version of package. I've installed package name : conky-banshee. 
So, i make the change today, and install the bzr package from AUR (version 4.2). 

But, i'm sorry it doesn't work. If i do : conkyBanshee --datatype=CA,  the link is still in /.cache/album-art/ where the file does not exist.


PS : i hope i well answer to your question, English is not my native language, and maybe  i not well understood your question.

---

### Post by kaivalagi on 2010-03-02
> **wimille said:**
> Hi,

In fact, i did not use the bzr version of package. I've installed package name : conky-banshee. 
So, i make the change today, and install the bzr package from AUR (version 4.2). 

But, i'm sorry it doesn't work. If i do : conkyBanshee --datatype=CA,  the link is still in /.cache/album-art/ where the file does not exist.


PS : i hope i well answer to your question, English is not my native language, and maybe  i not well understood your question.

You're fine, making sense to me...your english is fine :)

Yeah, I saw the same when I ran the script but assumed it was because there was a file there to be used...I'll double check...maybe if the old folder is present it will still use that. Expect a new AUR update soon :)

Edit: Found the bug, I didn't expand the user path properly so it thought the new path wasn't there...sorted now though, just tested myself and all looks okay. I have uploaded the changes and an AUR update should pull the new files down.

---

### Post by wimille on 2010-03-02
Well done!

Thanks for your work.
I've just finished the update and it works good.
The path is now correct when i use conkybanshee --datatype=CA

---

### Post by kaivalagi on 2010-03-02
> **wimille said:**
> Well done!

Thanks for your work.
I've just finished the update and it works good.
The path is now correct when i use conkybanshee --datatype=CA

Excellent! Thanks for helping out with the details

---

### Post by kaivalagi on 2010-03-02
[SIZE="4"]**[COLOR="Red"]UPDATE[/COLOR]**[/SIZE]

Thanks to MobileDiesel we now have the new version of conkyBanshee package available at the conky hardcore ppa, changes are here: [http://launchpadlibrarian.net/39999997/conkybanshee_2.03_source.changes](http://launchpadlibrarian.net/39999997/conkybanshee_2.03_source.changes)

As mentioned in previous posts the main change is the handling of new coverart paths for Banshee 1.5.3+, old paths are still supported if new paths are not found.

Cheers

---

### Post by kaivalagi on 2010-03-12
**[COLOR=Red][SIZE=4]UPDATE[/SIZE][/COLOR]**

I have updated the script to include a bitrate datatype, used via --datatype=BR

Package changes can be seen here:  [https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkybanshee_2.04_source.changes](https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkybanshee_2.04_source.changes)

The apt packages are available now

Cheers

---

### Post by monkey21stc on 2010-05-28
Hi I am new here, and I am not sure whether this discussion is still active but my baanshee song ratings do not seem to appear when I use the command ${exec conkyBanshee --ratingchar=* --datatype=RT} could use some help thank you!

regards,
Monk

---

### Post by anfreita09 on 2010-06-16
I've done a few hours of looking into this problem, and I've reached a dead-end/limit to my knowledge and abilities in trying to figure this out. Here is a screen shot of my conky setup:
[IMG]file:///tmp/moz-screenshot.png[/IMG][IMG]file:///tmp/moz-screenshot-1.png[/IMG][IMG]http://img46.imageshack.us/f/69739548.png/[/IMG]
[http://img46.imageshack.us/f/69739548.png/](http://img46.imageshack.us/f/69739548.png/)

I have all of the conkyBanshee elements installed correctly because it is able to pull most of the data from banshee and display it. However, for some reason, I am not able to get the length of the track. The code I used to pull the track length data is
${exec conkyBanshee -d LE}

I would really appreciate any help I can get with fixing this.

Thanks,
Andrew

---

### Post by kaivalagi on 2010-06-17
> **monkey21stc said:**
> Hi I am new here, and I am not sure whether this discussion is still active but my baanshee song ratings do not seem to appear when I use the command ${exec conkyBanshee --ratingchar=* --datatype=RT} could use some help thank you!


Hi Monk,
Ratings are not currently supported by the script (not sure if it's mentioned, there might be a post further up?). They were not supported by the banshee dbus service for some time, that is until very recently...I only just checked banshee v1.6.1 which I have installed and ratings are now available again.

I'll need to play around with the code at some point to get the output sorted and then organise a release (I am not running Ubuntu anymore). 
Cheers

**[COLOR="Navy"]edit: code changes made and replacement .py file attached, but it will be some time before conkyBanshee is released as a package as I rely on someone else for this right now.[/COLOR]**

---

### Post by kaivalagi on 2010-06-17
> **anfreita09 said:**
> ...for some reason, I am not able to get the length of the track. The code I used to pull the track length data is
${exec conkyBanshee -d LE}
...


Hi anfreita,
I run the command and get length output fine, is what you are playing showing a length in the banshee frontend?
Try running this in a terminal window and posting back the output (added verbose output option, not good for conky output though!):
```
conkyBanshee -d LE -v
```
I need to see the error details, if any...

---

### Post by anfreita09 on 2010-06-17
There don't appear to be any errors, but here's the output:

```
andrew@Apollo:/mnt/home$ conkyBanshee -d LE -v
*** INITIAL OPTIONS:
    datatype: LE
    template: None
    ratingchar: *
    nounknownoutput: False
    maxlength: 0
    verbose: True
    errorlogfile: None
    infologfile: None
INFO: Calling dbus interface for music data
INFO: Setting up dbus interface
INFO: Calling dbus interface for music data
INFO: Preparing output for datatype:LE
0:00

```Thanks!
-Andrew

---

### Post by kaivalagi on 2010-06-18
Andrew, Is it the same for all music you play? Are you playing mp3s?

---

### Post by anfreita09 on 2010-06-18
Yes it is the case for everything I play and all my music is mp3

---

### Post by kaivalagi on 2010-06-18
> **anfreita09 said:**
> Yes it is the case for everything I play and all my music is mp3

Then I really am stumped...it's working fine for me

Did you install in the same way as described in the first pot...maybe you have an old script?

---

### Post by kaivalagi on 2010-06-19
[COLOR="Red"]**[SIZE="4"]UPDATE[/SIZE]**[/COLOR]

[LIST]
[*]Updated /usr/bin/ startup script to not used misused PYTHONPATH variable now
[*]Added ratings option (--datatype=RT) output now it's available again from the Banshee dbus service :)
[/LIST]

New packages are now available from the ppa

---

### Post by monkey21stc on 2010-06-20
Hi kaivalagi!

Thank You so much for updating conkyBanshee! :D I really appreciate it and also for taking the time to look through our issues even though you no longer use Ubuntu. Thanks again!

Regards,
Monk

---

### Post by kaivalagi on 2010-06-20
No probs Monk, I still use a couple of the scripts and if time is spare enjoy fixing up issues...the script fixes I make from issues raised here benefit me and other Arch users too :)

---

### Post by LinuxFree on 2010-08-17
How do I get this to work for Debian? I'm using Squeeze/Sid right now (Squeeze with one Sid directory for the latest software). I'm not sure which version of conkyBanshee to download or how to use it with my conky.

---

### Post by kaivalagi on 2010-08-17
> **LinuxFree said:**
> How do I get this to work for Debian? I'm using Squeeze/Sid right now (Squeeze with one Sid directory for the latest software). I'm not sure which version of conkyBanshee to download or how to use it with my conky.

No idea, all the deb packages contain the same python code so at a guess use the hardy one...

---

### Post by LinuxFree on 2010-08-17
Hey, I'm trying conkyBanshee right now on DreamLinux4 (based on Debian Squeeze) and I can't get the album art to work. I've got conky 1.8.x and conkyBanshee 2.06 hardy. Everything else works fine but the album art.

Here' what happens when I type in 'conkyBanshee --datatype=CA'

```
bravo@dream:~$ conkyBanshee --datatype=CA
/home/bravo/.cache/media-art/album-e35162fdc280c313e826797f6ec3236d.jpg
```

Things I've tried:
```
${execi cp "`conkyBanshee --datatype=CA | sed -e 's/\\\//g'`" /home/bravo/.cache/media-art/album}${image /home/bravo/.cache/media-art/album -p 0,2 -s 64x64}
```
```
${execi cp "`conkyBanshee --datatype=CA | sed -e 's/\\\//g'`" /home/bravo/.cache/media-art/.album}${image /home/bravo/.cache/media-art/.album -p 0,2 -s 64x64}
```
${execi cp "`conkyBanshee --datatype=CA | sed -e 's/\\\//g'`" /home/bravo/.cache/media-art/.album/image.jpg}${image /home/bravo/.cache/media-art/.album/image.jpg -p 0,2 -s 64x64}
 
...and the list goes on. One time I actually ended up getting my computer's uptime which was both hilarious and humiliating. Any ideas for a fix?

---

### Post by kaivalagi on 2010-08-30
> **LinuxFree said:**
> Any ideas for a fix?
Not sure why I didn't pick up on your post earlier, try asking about this in the main conkyrc thread as it's more about what conky 
needs rather than the script itself. Cheers

---

### Post by kaivalagi on 2010-08-30
**[COLOR=Green][SIZE=4]UPDATE[/SIZE][/COLOR]**

Changes as follows:
[LIST]
[*]Added --secondsoutput / -S option to output time in seconds
[/LIST]
 
Package changes can be seen here:  [https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkybanshee_2.07_source.changes](https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkybanshee_2.07_source.changes)

The apt packages should be available shortly

Cheers

---

### Post by savalas on 2010-10-17
Hello at all,

I'm using the following conkyrc for Banshee:

```
use_xft yes
xftfont HandelGotDLig:size=17
background yes
xftalpha 0.8
update_interval 1.0
total_run_times 0
override_utf8_locale yes
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_borders no
draw_shades no
draw_graph_borders 
stippled_borders 0
border_margin 5
border_width 1
default_color 000000
alignment	
gap_x 15
gap_y 5
alignment bottom_left
minimum_size 900
maximum_width 1600

TEXT

Banshee - Interpret: ${execi 10 conkyBanshee --datatype=AR}  Titel: ${execi 10 conkyBanshee --datatype=TI}
```

I mostly listen to online radio stations, and want to ask whether it is possible to put out not only artist (AR) and title (TI), but also the name of the radio station? Is this possible?

---

### Post by kaivalagi on 2010-10-17
> **savalas said:**
> I mostly listen to online radio stations, and want to ask whether it is possible to put out not only artist (AR) and title (TI), but also the name of the radio station? Is this possible?

Radio station is not available through a seperate data type, you may be lucky and find it under track name or artist or something though?

---

### Post by savalas on 2010-10-17
Many thanx for your reply kaivalagi!

Have to live with that! Is that not a feature of conky or not integrated in the Banshee Python Script? Maybe a chance in the future? Would be a nice to have thing!

---

### Post by kaivalagi on 2010-10-17
> **savalas said:**
> Many thanx for your reply kaivalagi!

Have to live with that! Is that not a feature of conky or not integrated in the Banshee Python Script? Maybe a chance in the future? Would be a nice to have thing!

It's because the data is not available in Banshee's dbus service which the script connects to get get information, so only a banshee change would bring what you want

---

### Post by wimille on 2010-10-18
Hi,

like an old message, i've the same problem with conkyBanshe.
When i try :
```

conkyBanshee -v -d LE  # (or with PP)
*** INITIAL OPTIONS:
    datatype: PP
    template: None
    ratingchar: *
    nounknownoutput: True
    secondsoutput: False
    maxlength: 0
    verbose: True
    errorlogfile: None
    infologfile: None
INFO: Calling dbus interface for music data
INFO: Setting up dbus interface
INFO: Calling dbus interface for music data
INFO: Preparing output for datatype:PP
0

```

I've no error but the result is always 0.

For help :
i use Ubuntu 10.10, banshee 1.7.6 and i've installed script from PPA.
Others datatypes i use (TI, AR and CA) work fine

EDIT : I've upgraded banshee to version 1.8. But the problem is still there.

---

### Post by kaivalagi on 2010-10-20
> **wimille said:**
> I've no error but the result is always 0.


What are you playing? mp3's? ogm's? flac? stream? Having the same media file would be a good thing to test with...

---

### Post by kaivalagi on 2010-10-25
**[COLOR=Red][SIZE=4]UPDATE[/SIZE][/COLOR]**

Updates as follows:
[LIST]
[*]Updated main /usr/bin/ script to use Python2 rather than Python as Python3 is here (Arch) or approaching (Ubuntu)
[*]Updated to provide a copy of coverart files in a custom path to avoid file naming issues. The file where coverart gets copied to when using the --datatype=CA option is determined by the -c/--coverartpath option, note that if this option is set to an empty string i.e. "" the original file path is provided for the coverart path. The default setting is /tmp/cover
[/LIST]

Package changes can be seen here:  [https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkybanshee_2.08_source.changes](https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkybanshee_2.08_source.changes)

The apt packages should be available soon

Cheers

**[COLOR="Red"][SIZE="3"]Note For 10.10 Users[/SIZE][/COLOR]**
I do beleive that Ubuntu 10.10 has a bug not having the python2 symbolic link, all other distro's I've used including previous versions of Ubuntu do have a python2 sym link...chances are it's been forgotten about in the hurry to rollout 10.10....

To fix things so the script can work as it is supposed to post the latest update just add a symbolic link in for python2 like this:
```
sudo ln -s /usr/bin/python2.6 /usr/bin/python2
```

---

### Post by 098799 on 2010-10-25
Doesn't work that way @ Ubuntu 10.10, at least at mine.

Had to manualy change /usr/bin/python2 to /usr/bin/python2.6

Other than that, everything's fine. The script works wonders.

---

### Post by kaivalagi on 2010-10-25
My 10.04 VM has the attached sym links, what does "ls -al /usr/bin/python*" show for you in 10.10?

I had to switch from /usr/bin/python as Arch have moved on to Python 3 and the same is likely with Ubuntu at some point soon I guess...

I really don't want to have to keep compatibility with python 2 and 3...

---

### Post by tstreit on 2010-10-25
How would you manually change the script to use python 2.6?

I am trying to get conkyBanshee to work under Ubuntu 10.10 and having a terrible time.

Thanks

---

### Post by kaivalagi on 2010-10-25
I do beleive that Ubuntu 10.10 has a bug not having the python2 symbolic link, all other distro's I've used including previous versions of Ubuntu do have a python2 sym link...chances are it's been forgotten about in the hurry to rollout 10.10....

To fix things so the script can work as it is supposed to just add a symbolic link in for python2 like this:

```
sudo ln -s /usr/bin/python2.6 /usr/bin/python2
```

---

### Post by tstreit on 2010-10-25
Thank you, I finally figured it out right before you posted this.

Now I am going to try and figure out album art work. :-)

I see that it is copying the album art to /tmp/cover not sure how to make it display.

---

### Post by 098799 on 2010-10-25
Only
```
lrwxrwxrwx 1 root root       9 2010-09-16 12:07 /usr/bin/python -> python2.6
-rwxr-xr-x 1 root root 2605008 2010-09-15 19:10 /usr/bin/python2.6

```

thx, symlinking works as well.

---

### Post by kaivalagi on 2010-10-25
> **098799 said:**
> thx, symlinking works as well.

I do suspect this is a temporary issue with 10.10, although it could be that the python2 sym link is one of those "unwritten linux standards"...

If you sym link the problem will be catered for regardless of any updates I push out in the future ;)

---

### Post by kaivalagi on 2010-10-25
> **tstreit said:**
> I see that it is copying the album art to /tmp/cover not sure how to make it display.

Just point to /tmp/cover with the $image variable in conky e.g.:
```
${image /tmp/cover -p 5,5 -s 64x64}
```

If you want to use some other filepath then use the -c/--coverartpath option with the script and change the image variable for that filepath. Linux is not windows, an extension is not really required in most cases, rename an image to lose it's extension and then see what happens when you double click it...it still gets opened :)

---

### Post by tstreit on 2010-10-25
Thanks I will give that a try.

---

### Post by tstreit on 2010-10-25
Okay, I have it displaying using this code:

```
${exec cp "`conkyBanshee --datatype=CA | sed -e 's/\\\//g'`" /home/tstreit/.cache/media-art}${image /tmp/cover -p 165,600 -s 64x64}
```

But I have to shutdown conky each time for the art work to update.

Any suggestions?

---

### Post by kaivalagi on 2010-10-25
You don't need this method anymore as the cover art will always be called the same thing...the script now copies the content to the same file name on each request.

try:
```
${exec conkyBanshee --datatype=CA}${image /tmp/cover -p 165,600 -s 64x64}
```

Or better still use a template file then in the template have this:
```
${image [--datatype=CA] -p 165,600 -s 64x64}
```

A template file can be used to load lots of datatypes in one go and feed this back into conky through a **execp** or **execpi** variable. The example files found in /usr/share/conkybanshee/example/ should help you as they demonstrate both the way you do things and the way templates work.

Hope that helps

---

### Post by wimille on 2010-10-27
Hi,

I use banshee to play mp3. 
I don't understand the last part of your answer :
'Having the same media file would be a good thing to test with...'

You want my music to perform some test?

---

### Post by kaivalagi on 2010-10-27
> **wimille said:**
> Hi,

I use banshee to play mp3. 
I don't understand the last part of your answer :
'Having the same media file would be a good thing to test with...'

You want my music to perform some test?

Well I have never seen this issue, it's not a problem with my mp3 or flac files. The script is not erroring either so it suggests the problem is with banshee or it's dbus service methods for some media files.

You could test the dbus side of things which is where I get the info for banshee from...

Install a tool called d-feet and use it to request the current position from banshee when you are playing the track, if it works then it's the script if not then it's banshee...like I said I haven't seen this problem before I can't understand why it is happening...if I can't reproduce it I can't fix it.

Hope that helps

---

### Post by wimille on 2010-10-27
Hi,
sorry but  i don't understand how to use d-feet. I launch it, i open 'system' and 'session' bus. And yes some lines contains banshee. But after that i don't know what i'll have to do

---

### Post by kaivalagi on 2010-10-27
> **wimille said:**
> Hi,
sorry but  i don't understand how to use d-feet. I launch it, i open 'system' and 'session' bus. And yes some lines contains banshee. But after that i don't know what i'll have to do

Typically I am trying run it and can't because of python issues...otherwise I would take some screenshots.

I'll attempt to explain the steps:
[LIST=1]
[*]click on the banshee service in d-feet
[*]Expand out the node on the right hand tree which has a name matching "/org/bansheeproject/Banshee/PlayerEngine"
[*]You should see a function called GetPosition(), right click it and pick something like execute
[*]You should now see a dialog popup, with banshee running make a call to the function and see what the results are
[/LIST]

I've had to do this blind without the application in front of me so there may be discrepancies but the basic principles are there

The GetPosition method is what I am calling from within the script to get the position which is always showing as zero for you.

Let me know if you are still stuck

---

### Post by wimille on 2010-10-27
Well, i've done what you wrote and i've got this :

[[IMG]http://img844.imageshack.us/img844/6929/dbusfeet.th.png[/IMG]]("http://img844.imageshack.us/i/dbusfeet.png/")


No GetPosition function (i mean if  i do the right things)

UPDATE:
i've found a problem on Banshee. On my computer, i can't modify the position in the song when it's playing.

UPDATE 2 :
i've deleted the last version (1.8.0), deactivate the ppa repository and reinstall the default version for Ubuntu Maverick (1.76). And now it's work.

---

### Post by kaivalagi on 2010-10-27
> **wimille said:**
> i've deleted the last version (1.8.0), deactivate the ppa repository and reinstall the default version for Ubuntu Maverick (1.76). And now it's work.

The function in d-feet was Position...the code side of it is GetPosition for "get" the position, not that it matters now.

Glad to have been of help...like I said before the script works fine for everyone else so it had to be Banshee really didn't it ;)

---

### Post by serein on 2010-11-05
how do i get conky to show no image when not playing...?
as it is now, i get half of the last played image...

---

### Post by kaivalagi on 2010-11-06
You're probably going to need to create a script which calls my script to figure out the status of the player and creates a file if playing...

Here's an attempt at a script (should work...):
```
#!/bin/sh
status=`conkyBanshee --datatype=ST`
if [ $status = Playing ]; then
  touch /tmp/banshee_playing
else
  if [ -f /tmp/banshee_playing ]; then
    rm /tmp/banshee_playing
  fi
fi

```

The script will need executing via a exec call in the conkyrc file, i.e.
```
${exec /path/to/script.sh
```

Here's the if_existing conky help:
```
if_existing	file (string)	if FILE exists, display everything between if_existing and the matching $endif. The optional second paramater checks for FILE containing the specified string and prints everything between $if_existing and the matching $endif.
```

So you would want something like:
```
${if_existing "/tmp/banshee_playing"}
...do stuff when player is playing...
$endif
```

There may be a better solution using $if_matching...someone may jump in to help more...

Hope that helps

---

### Post by whiterabbit7500 on 2010-11-20
having a problem with the script in 10.10

installed from repos, all ok. But getting the following when testing it in terminal.

```
david@WR-Desktop:~$ conkyBanshee --datatype=CA
/usr/bin/conkyBanshee: 3: /usr/bin/python2: not found
```

seems it's missing python, but i know for a fact it's installed and working as I've used it before. Ideas?

---

### Post by kaivalagi on 2010-11-21
**[COLOR=Purple][SIZE=4]UPDATE[/SIZE][/COLOR]**

Updates as follows:
[LIST]
[*]Updated the /usr/bin/ script to dynamically call the available python exec as /usr/bin/python is linked to Python 3 (Arch) or will be at some point (Ubuntu)
[/LIST]

Package changes can be seen here:  [https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkybanshee_2.09_source.changes](https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkybanshee_2.09_source.changes)

The apt packages should be available soon

---

### Post by kaivalagi on 2010-11-21
> **whiterabbit7500 said:**
> having a problem with the script in 10.10

installed from repos, all ok. But getting the following when testing it in terminal.

```
david@WR-Desktop:~$ conkyBanshee --datatype=CA
/usr/bin/conkyBanshee: 3: /usr/bin/python2: not found
```

seems it's missing python, but i know for a fact it's installed and working as I've used it before. Ideas?

The latest update should sort out any issues...for info if you'd have looked at the previous update post ([COLOR="Red"]red[/COLOR] update text) in this thread you would know what the issue was ;)

---

### Post by kaivalagi on 2010-12-11
**[COLOR=Red][SIZE=4]UPDATE[/SIZE][/COLOR]**

Updates as follows:
[LIST]
[*]Updated main script to only actually copy over found cover art when --datatype=CA is requested
[/LIST]

Package changes can be seen here:  [https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkybanshee_2.10_source.changes](https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkybanshee_2.10_source.changes)

The apt packages should be available soon

---

### Post by Fedik on 2010-12-12
After updating cover art not shown.
I use code in template:
${image [--datatype=CA] -p 8,38 -s 100x100 -f 3}

If write only [--datatype=CA]  shown /tmp/cover, and image is there, but cover art not shown.

Please tell what need change in my code?

---

### Post by kaivalagi on 2010-12-12
Sorry, I can't understand what your problem is? /tmp/cover is an image, yes? The script outputs /tmp/cover for the CA datatype?

Could the image variable being cached? Try adding a -n to the image variable maybe i.e.
```
${image [--datatype=CA] -p 8,38 -s 100x100 -f 3 -n}
```

I have tested the script and it creates a new /tmp/cover for each song when datatype=CA is requested and I see it on the desktop using a template...

Might help if you post your conkyrc and template

Cheers

---

### Post by Fedik on 2010-12-12
Thank you for your reply, and sorry, for bad english.
Cover art not shown, after update Script to last version.Before that everything worked.
```
${image [--datatype=CA] -p 8,38 -s 100x100 -f 3 -n}
```
did not help
> **kaivalagi said:**
> /tmp/cover is an image, yes? The script outputs /tmp/cover for the CA datatype?

yes and yes, but cover art not shown in conky...

Found another way.
I change
```
${image [--datatype=CA] -p 8,38 -s 100x100 -f 6}
```
to
```
${image /tmp/cover -p 8,38 -s 100x100 -f 6 }
```
and now cover is shown

My conky config```

# Default Fonts
use_xft yes
xftfont Ubuntu:size=10
override_utf8_locale yes

# Performance Settings
update_interval 1
total_run_times 0
double_buffer yes
no_buffers yes
net_avg_samples 2
text_buffer_size 1024

# Window Settings
own_window yes
own_window_transparent yes
own_window_type override
#own_window_type panel
#own_window_type normal
#own_window_type desktop
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
#background no
#own_window_colour red


# Window border
draw_borders no
draw_shades no

# border width
border_width 1



# Stippled borders?
stippled_borders 0

# Default Color
#default_color 6b1908
default_color white
default_outline_color white
default_shade_color 7F7F7F

# Color Title.
#color0 DD3A21
#color0 00FF00
color0 1e90ff
#color0 1e272c

# Size and position
minimum_size 228 1030
maximum_width 228
gap_x 0
gap_y 20
alignment top_right

TEXT
${if_running banshee-1}
${GOTO 12}${font Ubuntu:bold:size=12}${color0}Banshee${font}${color}
${execpi 8 conkyBanshee --template=/home/fedik/.ConkyWizardTheme/conkyBanshee.template}${endif}
${GOTO 12}${font Ubuntu:bold:size=12}${color0}&#1057;&#1080;&#1089;&#1090;&#1077;&#1084;&#1072;${font}${color}
${GOTO 12}CPU:${GOTO 100}${cpugraph cpu0 10,75} ${cpu cpu0} %
${GOTO 12}RAM:${GOTO 100}${membar 10,75} ${memperc} %
${GOTO 12}&#1055;&#1088;&#1086;&#1094;&#1077;&#1089;&#1110;&#1074;:${GOTO 100}$processes ($running_processes)
${GOTO 12}&#1055;&#1088;&#1072;&#1094;&#1102;&#1108;:${GOTO 100}${uptime}

${GOTO 12}${font Ubuntu:bold:size=12}${color0}&#1044;&#1080;&#1089;&#1082;&#1080;${font}${color}
${GOTO 12}&#1057;&#1080;&#1089;&#1090;&#1077;&#1084;&#1072; (/):${GOTO 110}${fs_used /} / ${fs_free /}
${GOTO 12}${fs_bar 4,210 /}
${GOTO 12}DATA :${GOTO 110}${fs_used /media/DATA} / ${fs_free /media/DATA}
${GOTO 12}${fs_bar 4,210 /media/DATA}
${GOTO 12}DATA II :${GOTO 110}${fs_used /media/DATA_II} / ${fs_free /media/DATA_II}
${GOTO 12}${fs_bar 4,210 /media/DATA_II}
${GOTO 12}ProgramFails :${GOTO 110}${fs_used /media/ProgramFails} / ${fs_free /media/ProgramFails}
${GOTO 12}${fs_bar 4,210 /media/ProgramFails}

${GOTO 12}${font Ubuntu:bold:size=12}${color0}&#1052;&#1077;&#1088;&#1077;&#1078;&#1072;${font}${color}${if_gw eth0}
${GOTO 12}&#1042;&#1110;&#1076;&#1076;&#1072;&#1095;&#1072;:${GOTO 100}${totalup eth0} / ${upspeed eth0}/s
${GOTO 12}&#1054;&#1090;&#1088;&#1080;&#1084;&#1072;&#1085;&#1085;&#1103;:${GOTO 100}${totaldown eth0} / ${downspeed eth0}/s
${GOTO 12}&#1047;’&#1108;&#1076;&#1085;&#1072;&#1085;&#1100;:${GOTO 100}${tcp_portmon 1 65535 count}
${GOTO 12}${color0}IP &#1072;&#1076;&#1088;&#1077;&#1089;&#1072;:${color}${GOTO 100}${addr eth0}${else}
${GOTO 12}&#1052;&#1077;&#1088;&#1077;&#1078;&#1072; &#1074;&#1110;&#1076;&#1089;&#1091;&#1090;&#1085;&#1103; ${endif}

${GOTO 12}${font Ubuntu:bold:size=12}${color0}&#1058;&#1086;&#1087; &#1087;&#1088;&#1086;&#1094;&#1077;&#1089;&#1110;&#1074;${font}${color}
${GOTO 12}&#1055;&#1088;&#1086;&#1094;&#1077;&#1089;        ${GOTO 160}ID     ${GOTO 193} % ${font Ubuntu:size=8}
${GOTO 12}1. ${top name 1}        ${GOTO 150}${top pid 1} ${GOTO 190}${top cpu 1}
${GOTO 12}2. ${top name 2}        ${GOTO 150}${top pid 2} ${GOTO 190}${top cpu 2}
${GOTO 12}3. ${top name 3}        ${GOTO 150}${top pid 3} ${GOTO 190}${top cpu 3}
${GOTO 12}4. ${top name 4}        ${GOTO 150}${top pid 4} ${GOTO 190}${top cpu 4}
${GOTO 12}5. ${top name 5}        ${GOTO 150}${top pid 5} ${GOTO 190}${top cpu 5}${font}
${GOTO 12}&#1055;&#1088;&#1086;&#1094;&#1077;&#1089;        ${GOTO 160}ID     ${GOTO 193} MiB ${font Ubuntu:size=8}
${GOTO 12}1. ${top_mem name 1}        ${GOTO 150}${top_mem pid 1} ${GOTO 190}${top_mem mem_res 1}
${GOTO 12}2. ${top_mem name 2}        ${GOTO 150}${top_mem pid 2} ${GOTO 190}${top_mem mem_res 2}
${GOTO 12}3. ${top_mem name 3}        ${GOTO 150}${top_mem pid 3} ${GOTO 190}${top_mem mem_res 3}${font}

${GOTO 12}${font Ubuntu:bold:size=12}${color0}&#1055;&#1086;&#1075;&#1086;&#1076;&#1072;${font}${color}${if_gw eth0}
${GOTO 12}&#1052;&#1110;&#1089;&#1090;&#1086;: ${GOTO 120}${execi 3600 conkyForecast  --datatype=CN},	${execi 3600 conkyForecast  --datatype=CO}
${GOTO 12}&#1058;&#1077;&#1084;&#1087;&#1077;&#1088;&#1072;&#1090;&#1091;&#1088;&#1072;: ${GOTO 120}${execi 3600 conkyForecast  --datatype=HT}
${GOTO 12}&#1057;&#1093;&#1110;&#1076;/&#1047;&#1072;&#1093;&#1110;&#1076;: ${GOTO 120}${execi 43200 conkyForecast  --datatype=SR}/${execi 43200 conkyForecast  --datatype=SS}
${voffset 8}${font ConkyWeather:bold:size=36}${execi 3600 conkyForecast --centeredwidth=6 --datatype=WF}${font}${voffset -36}${font Moon Phases:size=36}${execi 43200 conkyForecast  --datatype=MF}${font}
${GOTO 12}${font Ubuntu:bold:size=8}${execi 3600 conkyForecast --centeredwidth=26 --datatype=CC}${execi 3600 conkyForecast --centeredwidth=23 --datatype=MP}${font}
${GOTO 12}${color0}&#1055;&#1088;&#1075;&#1085;&#1086;&#1079;${color}
${GOTO 12}${font ConkyWeather:size=32}${execi 3600 conkyForecast --startday=1 --endday=4  --datatype=WF}${font}
${GOTO 26}${execi 3600 conkyForecast  --startday=1 --endday=4 --spaces=10 --datatype=HT}
${GOTO 12}${font Ubuntu:size=8}${execi 3600 conkyForecast  --startday=1 --endday=4 --spaces=6 --datatype=DW}${font}
${else}
${GOTO 12}&#1030;&#1085;&#1090;&#1077;&#1088;&#1085;&#1077;&#1090; &#1085;&#1077;&#1076;&#1086;&#1089;&#1090;&#1091;&#1087;&#1085;&#1080;&#1081;${endif}

```
Banshe template (last)
```

${GOTO 120}${font Ubuntu:bold:size=8}[--datatype=TI]${font}
${GOTO 120}${font Ubuntu:bold:size=8}[--datatype=AR]${font}
${GOTO 120}${font Ubuntu:bold:size=8}[--datatype=AL]${font}
${GOTO 120}${font Ubuntu:bold:size=8}[--datatype=YR]${font}
${GOTO 120}${font Ubuntu:size=8}[--datatype=ST] - [--datatype=PP]%${font} ${image /tmp/cover -p 8,38 -s 100x100 -f 6 }

```

---

### Post by kaivalagi on 2010-12-12
Mmmmm, working for me using this in the template:
```
${image [--datatype=CA] -p 36,400 -s 90x82 -n}

```

I think if you use /tmp/cover your image will not get refreshed by the script? --datatype=CA needs to be called to refresh it with this change...

I notice you are using -f 6 which I think should be refreshing the image after 6 redraws which I assume is 6 seconds (refresh at once per second), so if the above works for me yours should work too...could you try -n rather than -f 6 just so we can see whether it is that or not? I have never used the -f option for the image variable so can't say it works :)

---

### Post by Fedik on 2010-12-13
> **kaivalagi said:**
> 
I think if you use /tmp/cover your image will not get refreshed by the script? --datatype=CA needs to be called to refresh it with this change...

Do not know why but image refreshed without --datatype=CA :-)


I tried:```
${image [--datatype=CA] -p 36,400 -s 90x82 -n}
```and```
${image [--datatype=CA]}
```and without banchee template```
${image ${execpi 3 conkyBanshee --datatype=CA}}
``` but nothing.

---

### Post by kaivalagi on 2010-12-13
> **Fedik said:**
> Do not know why but image refreshed without --datatype=CA :-)

I tried:... but nothing.

Are you sure you are running with the latest version, sounds well out of sync to me?

cover art in the older version would have been refreshed regardless of the datatypes requested but not now, --datatype=CA must be present to copy the song cover art file to /tmp/cover

"conkyBanshee --version" gives me "v.2.10"

Here's some proof from my console

1) No cover art file yet as no CA datatype requested:
```

 [USER@PC ~]$ conkyBanshee --datatype=TI
This Is What It Means
 [USER@PC ~]$ ls /tmp/cover
ls: cannot access /tmp/cover: No such file or directory

```

2) The file is now present, only after requesting CA datatype:
```

 [USER@PC ~]$ conkyBanshee --datatype=CA
/tmp/cover
 [USER@PC ~]$ ls /tmp/cover
-rw-r--r-- 1 USER USER 14281 Dec 13 13:03 /tmp/cover

```

3) Now we change the album playing in the player...The cover art file remains unchanged, same datetime, we need a CA request for that:
```

 [USER@PC ~]$ conkyBanshee --datatype=TI
Secret Circles
 [USER@PC ~]$ ls /tmp/cover
-rw-r--r-- 1 USER USER 14281 Dec 13 13:03 /tmp/cover

```

4) The file now changed due to CA request:
```

 [USER@PC ~]$ conkyBanshee --datatype=CA
/tmp/cover
 [USER@PC ~]$ ls /tmp/cover
-rw-r--r-- 1 USER USER 15584 Dec 13 13:04 /tmp/cover

```

---

### Post by Fedik on 2010-12-13
hm..
Ubuntu 10.10
Banshee version - 1.9.0
```
X~$ conkyBanshee --version
conkyBanshee v.2.10
X~$ conkyBanshee --datatype=TI
Baby
X~$ ls -l /tmp/cover
-rw-r--r-- 1 usr usr 30493 2010-12-13 17:20 /tmp/cover

```
after waiting some time
```
X~$ ls -l /tmp/cover
-rw-r--r-- 1 usr usr 30493 2010-12-13 17:22 /tmp/cover
```
after track change  ```
X~$ ls -l /tmp/cover
-rw-r--r-- 1 usr usr 66080 2010-12-13 17:25 /tmp/cover
```

I try to reinstall the Script but nothing changed.

---

### Post by kaivalagi on 2010-12-13
Are you running conky at the same time you are testing the script?

No way can called the script once have the cover art repeatedly updated over a few minutes, something else needs to call it over and over, such as conky.

It will be something to do with your setup I am sure! Try "killall conky" then "rm /tmp/cover" then play songs through banshee and see if the cover file turns up?

Other than that I am stumped, what you are suggesting doesn't fit with the way the script works standalone...

---

### Post by Fedik on 2010-12-13
Sorry, I forget disable conky.
Again:```
:~$ conkyBanshee --datatype=TI
4000 Rainy Nights
:~$ ls -l /tmp/cover
ls: &#1085;&#1077; &#1074;&#1076;&#1072;&#1108;&#1090;&#1100;&#1089;&#1103; &#1086;&#1090;&#1088;&#1080;&#1084;&#1072;&#1090;&#1080; &#1076;&#1086;&#1089;&#1090;&#1091;&#1087; &#1076;&#1086; /tmp/cover: No such file or directory
:~$ conkyBanshee --datatype=CA
/tmp/cover
:~$ ls -l /tmp/cover
-rw-r--r-- 1 usr usr 8865 2010-12-13 22:08 /tmp/cover

```
after waiting ~3 min.```
:~$ ls -l /tmp/cover
-rw-r--r-- 1 usr usr 8865 2010-12-13 22:08 /tmp/cover

```
change track and again:```
:~$ ls -l /tmp/cover
-rw-r--r-- 1 usr usr 8865 2010-12-13 22:08 /tmp/cover
:~$ conkyBanshee --datatype=CA
/tmp/cover
:~$ ls -l /tmp/cover
-rw-r--r-- 1 usr usr 162164 2010-12-13 22:13 /tmp/cover
```
all is well. 
If write [--datatype=CA] in Banchee template I see /tmp/cover, but if ${image [--datatype=CA]} - nothing.

Ok, thank you for help. 
I will use ${image /tmp/cover}

---

### Post by kaivalagi on 2010-12-13
> **Fedik said:**
> If write [--datatype=CA] in Banchee template I see /tmp/cover, but if ${image [--datatype=CA]} - nothing.

Ok, thank you for help. 
I will use ${image /tmp/cover}

No worries, I still think it will be something wrong in the template

If you run the same command from your conkyrc in the console and get an image variable output with /tmp/cover inside it when using --datatype=CA in the template then it's not the script that's the issue it's the template

Cheers

---

### Post by kaivalagi on 2010-12-14
**[COLOR="Red"][SIZE="3"]IMPORTANT NEWS[/SIZE][/COLOR]**

All the script packages have now been copied into the **Conky Companions PPA**. Any package updates will be provided by the team through this new ppa. The ppa can be found here: **[https://launchpad.net/~conky-companions/+archive/ppa]("https://launchpad.net/~conky-companions/+archive/ppa")**. To use this ppa first delete the old ppa files using this: 

```
sudo rm /etc/apt/sources.list.d/m-buck* && sudo rm /etc/apt/sources.list.d/conkyhardcore*

```
Then follow the modified first post instructions for the scripts

[COLOR="Red"]**Script updates will only be published through this new ppa going forwards**[/COLOR]

---

### Post by Fedik on 2010-12-26
> **kaivalagi said:**
> No worries, I still think it will be something wrong in the template

If you run the same command from your conkyrc in the console and get an image variable output with /tmp/cover inside it when using --datatype=CA in the template then it's not the script that's the issue it's the template

Cheers

hi,
I found the cause of the problem.
this is because of comments in the Banchee template
Full code (it not work):```

#${GOTO 12}&#1053;&#1072;&#1079;&#1074;&#1072;:${GOTO 68}[--datatype=TI]
#${GOTO 12}&#1040;&#1088;&#1090;&#1080;&#1089;&#1090;:${GOTO 68}[--datatype=AR]
#${GOTO 12}&#1040;&#1083;&#1100;&#1073;&#1086;&#1084;:${GOTO 68}[--datatype=AL]
#${GOTO 12}&#1056;&#1110;&#1082;:${GOTO 68}[--datatype=YR]
#${GOTO 12}&#1055;&#1086;&#1079;&#1080;&#1094;&#1110;&#1103;:${GOTO 68}[--datatype=PT]/[--datatype=LE] - [--datatype=PP]%
#${GOTO 12}&#1056;&#1077;&#1081;&#1090;&#1080;&#1085;&#1075;:${GOTO 68}[--datatype=RT]
#${GOTO 12}Volume:${GOTO 68}[--datatype=VO]
#${GOTO 12}&#1057;&#1090;&#1072;&#1090;&#1091;&#1089;:${GOTO 68}[--datatype=ST]
#${GOTO 68}[--datatype=CA]
${GOTO 120}${font Ubuntu:bold:size=8}[--datatype=TI]${font}
${GOTO 120}${font Ubuntu:bold:size=8}[--datatype=AR]${font}
${GOTO 120}${font Ubuntu:bold:size=8}[--datatype=AL]${font}
${GOTO 120}${font Ubuntu:bold:size=8}[--datatype=YR]${font}
${GOTO 120}${font Ubuntu:size=8}[--datatype=ST] - [--datatype=PP]%${font} ${image [--datatype=CA] -p 8,38 -s 100x100 -n}

```

And it work:```

${GOTO 120}${font Ubuntu:bold:size=8}[--datatype=TI]${font}
${GOTO 120}${font Ubuntu:bold:size=8}[--datatype=AR]${font}
${GOTO 120}${font Ubuntu:bold:size=8}[--datatype=AL]${font}
${GOTO 120}${font Ubuntu:bold:size=8}[--datatype=YR]${font}
${GOTO 120}${font Ubuntu:size=8}[--datatype=ST] - [--datatype=PP]%${font} ${image [--datatype=CA] -p 8,38 -s 100x100 -n}

```
I thought this is not important ago in first post published the code without comments.

Cheers and happy holidays

---

### Post by Sector11 on 2011-04-08
[center][ Nouveau : Conky Pitstop - c'est bilingue. ](http: // conky.pitstop.free.fr/fr)
[img]http://dl.dropbox.com/u/16070765/full_CPS-Flag.png[/img]
[New: Conky Pitstop - it's bilingual.](http://conky.pitstop.free.fr/)[/center]

---

### Post by jmadero on 2011-04-28
How hard would it be to implement a playlist length and percentage done? I think this would be a cool addition.

---

### Post by kaivalagi on 2011-04-29
> **jmadero said:**
> How hard would it be to implement a playlist length and percentage done? I think this would be a cool addition.

Nice idea...but looking at the d-bus offerings there isn't anything that helps....the playerengine is track related and the only thing related to playlists is for enqueuing songs (see screenshot attached)

---

### Post by ambdeep on 2011-05-11
I am using the following code for conkyBanshee and it is using up nearly 30% of my cpu. Please tell me how to fix this.
```
${font Santana:size 12:style=Bold}Music${font}

${GOTO 70}${exec conkyBanshee --datatype=TI}
${GOTO 70}${exec conkyBanshee --datatype=AR}
${GOTO 70}${exec conkyBanshee --datatype=AL}
${GOTO 70}${exec conkyBanshee --datatype=YR}
${GOTO 70}${exec conkyBanshee --datatype=PT} / ${exec conkyBanshee --datatype=LE} - ${exec conkyBanshee --datatype=PP}% (${exec conkyBanshee --datatype=ST})${GOTO 500}${exec conkyBanshee --datatype=CA}
${execibar 1 conkyBanshee --datatype=PP}
${image /tmp/cover -p 0,35 -s 64x64}
```

---

### Post by kaivalagi on 2011-05-11
> **ambdeep said:**
> I am using the following code for conkyBanshee and it is using up nearly 30% of my cpu. Please tell me how to fix this.
```
${font Santana:size 12:style=Bold}Music${font}

${GOTO 70}${exec conkyBanshee --datatype=TI}
${GOTO 70}${exec conkyBanshee --datatype=AR}
${GOTO 70}${exec conkyBanshee --datatype=AL}
${GOTO 70}${exec conkyBanshee --datatype=YR}
${GOTO 70}${exec conkyBanshee --datatype=PT} / ${exec conkyBanshee --datatype=LE} - ${exec conkyBanshee --datatype=PP}% (${exec conkyBanshee --datatype=ST})${GOTO 500}${exec conkyBanshee --datatype=CA}
${execibar 1 conkyBanshee --datatype=PP}
${image /tmp/cover -p 0,35 -s 64x64}
```


Use one exec call and a template to request all of that...

so the call would be:
```
${execp conkyBanshee --template=/path/to/template}
``` 

the template would be something like:
```
${font Santana:size 12:style=Bold}Music${font}

${GOTO 70}[--datatype=TI]
${GOTO 70}[--datatype=AR]
${GOTO 70}[--datatype=AL]
${GOTO 70}[--datatype=YR]
${GOTO 70}[--datatype=PT] / [--datatype=LE] - [--datatype=PP]% ([--datatype=ST])${GOTO 500}[--datatype=CA]
${execibar 1 [--datatype=PP]}
${image /tmp/cover -p 0,35 -s 64x64}
```
Note sure of the execibar bit...you may need a seperate call for that...

The example files here have a working template, see here: /usr/share/conkybanshee/example/
You can run them using: conky -c /usr/share/conkybanshee/example/conkyrc
Also see the first post for more info on the options/arguments of the script...

---

### Post by jmadero on 2011-05-18
How could I do a feature request to get these additional tools to add the playlist length/% addition? Thanks, I'm going to pursue this one a bit ;) 


Also I'm using Banshee 2.0 in Natty and conkybanshee actually isn't working any more. I've read that I can install from source but I'd prefer not to, any idea when it'll be added to the ppa?

---

### Post by kaivalagi on 2011-05-18
> **jmadero said:**
> How could I do a feature request to get these additional tools to add the playlist length/% addition? Thanks, I'm going to pursue this one a bit ;) 


Also I'm using Banshee 2.0 in Natty and conkybanshee actually isn't working any more. I've read that I can install from source but I'd prefer not to, any idea when it'll be added to the ppa?

conkyBanshee is built for Natty too but if not working something drastic has changed with the player, look at the d-bus methods available via a tool such as d-feet....I doubt I'll run Natty or Banshee for some time so you'd be best trying to fault find and report back...I use MPD (music player daemon), Sonata frontend (customised a little as it's python :)) and mpdcron these days...all the other players are naff in comparison I think ;)

As for putting in a feature request for banshee changes I have no idea...try the banshee website but it might be best looking at what version 2 offers first...

---

### Post by layr on 2011-06-05
**1.** Why doesn't album art obey to offset/voffset commands? When the image is printed, it's at the top of the screen and have had no luck getting it down.

**2.** Kaivalagi, earlier you descripted other user how to print picture only when banshee is running.

I created .sh file:
```
#!/bin/sh
status=`conkyBanshee --datatype=ST`
if [ $status = Playing ]; then
  touch /tmp/banshee_playing
else
  if [ -f /tmp/banshee_playing ]; then
    rm /tmp/banshee_playing
  fi
fi
```
and .conkyrc has these lines:
```
${exec ~/.conky/banshee_running.sh}
${if_existing "/tmp/banshee_playing"}
${exec cp "`conkyBanshee --datatype=CA | sed -e 's/\\\//g'`" /home/laur/.album.jpg}${image /home/laur/.album.jpg -p 0,2 -s 64x64}
$endif
```
No error, but now it doesn't even show album art. Did i misunderstand your instructions?

**3.** What would be the point of using templates? I'm not going to print two sets of banshee info :P

---

### Post by kaivalagi on 2011-06-05
It looks okay....

3 things you can check straight off independently to remove the guessing game...

1) ensure you have a "banshee_playing" file in /tmp when banshee is playing and not one when it's not

2) why not change the big long line for displaying the coverart to be [COLOR="Green"]just some text[/COLOR] so you can make sure everything else is working...also [COLOR="Blue"]add a "sh"[/COLOR] in for good measure (not sure if chmod +x is needed on the .sh file without it) and [COLOR="Purple"]a full path[/COLOR]:
e.g.
```
${exec [COLOR="Blue"]sh[/COLOR] [COLOR="Purple"]/home/laur[/COLOR]/.conky/banshee_running.sh}
${if_existing "/tmp/banshee_playing"}
[COLOR="green"]Banshee is playing![/COLOR]
$endif
```

3) have just the one liner in a conky and ensure when banshee is playing you dom actually see covert art

e.g.
```
${exec cp "`conkyBanshee --datatype=CA | sed -e 's/\\\//g'`" /home/laur/.album.jpg}${image /home/laur/.album.jpg -p 0,2 -s 64x64}
```

Does the image /home/laur/.album.jpg get updated etc etc...

If you have answers to all these questions and still have issues let me know what they are...

Hope that helps

---

### Post by layr on 2011-06-05
Bash is working as it should. Somewhy the 'if' command in .conkyrc is failing.
(the oneliner alone works also just fine. My first question left aside that is:P)

**EDIT:**
I accidentally debugged this issue; the quotation marks had to be removed from the tmp location, so the code in .conkyrc looks something like this:
```
${exec sh /home/laur/.conky/banshee_running.sh}
${if_existing /tmp/banshee_playing}
Banshee is playing!
$endif
```
(PS what about the formatting issue? Haven't yet found a way to reposition albumart in the conky layout)
**EDIT 2:**
Hurr-durr, those **0,2** at the end of the albumart line are x,y coordinates. Now i feel dumb:D
**EDIT 3:**
Is the albumart supposed to be behind the .lua drawn background?

---

### Post by kaivalagi on 2011-06-05
> **layr said:**
> Is the albumart supposed to be behind the .lua drawn background?
There has been talk on this in the main thread, I don't use lua to draw backgrounds though so I don;t know the details...it can be worked around...it was posted about in the last week on the mega thread so may be worth you going through the posts

The point of a template would be that you don't have to have a copy command, you just call a template to bring in all the data including a pre-populated $image variable (this being key!)

e.g.

in the template:

```
${image [--datatype=CA] -p 0,2 -s 64x64}
```

so that when rendered it will be output as:

```
${image /tmp/cover -p 0,2 -s 64x64}

```

Not sure about the need for sed anymore either....banshee cover art is always /tmp/cover I think...

---

### Post by Sector11 on 2011-06-05
> **kaivalagi said:**
> There has been talk on this in the main thread, I don't use lua to draw backgrounds though so I don;t know the details...it can be worked around...it was posted about in the last week on the mega thread so may be worth you going through the posts

NEW background LUA script *goes behind images*, [check it out on the conkyForecast thread]("http://ubuntuforums.org/showpost.php?p=10905934&postcount=3271").

---

### Post by layr on 2011-06-05
Also has there been any discussion/solution with the songs that don't have album art (last cover stays and terminal output is approximately: )
```
Traceback (most recent call last):
  File "/usr/share/conkybanshee/conkyBanshee.py", line 244, in getOutputData
    shutil.copy(self.musicData.coverart, self.options.coverartpath)
  File "/usr/lib/python2.6/shutil.py", line 84, in copy
    copyfile(src, dst)
  File "/usr/lib/python2.6/shutil.py", line 50, in copyfile
    with open(src, 'rb') as fsrc:
IOError: [Errno 2] No such file or directory: '/home/laur/.cache/media-art/album-5b20b3b88499cda2276ca3c7a3d98c3e.jpg'
ERROR: Unknown error when calling getOutputData:[Errno 2] No such file or directory: '/home/laur/.cache/media-art/album-5b20b3b88499cda2276ca3c7a3d98c3e.jpg'
cp: cannot stat `': No such file or directory
```

Thanks Sector (Y)

---

### Post by kaivalagi on 2011-06-06
> **layr said:**
> Also has there been any discussion/solution with the songs that don't have album art (last cover stays and terminal output is approximately: )
```
Traceback (most recent call last):
  File "/usr/share/conkybanshee/conkyBanshee.py", line 244, in getOutputData
    shutil.copy(self.musicData.coverart, self.options.coverartpath)
  File "/usr/lib/python2.6/shutil.py", line 84, in copy
    copyfile(src, dst)
  File "/usr/lib/python2.6/shutil.py", line 50, in copyfile
    with open(src, 'rb') as fsrc:
IOError: [Errno 2] No such file or directory: '/home/laur/.cache/media-art/album-5b20b3b88499cda2276ca3c7a3d98c3e.jpg'
ERROR: Unknown error when calling getOutputData:[Errno 2] No such file or directory: '/home/laur/.cache/media-art/album-5b20b3b88499cda2276ca3c7a3d98c3e.jpg'
cp: cannot stat `': No such file or directory
```


Looks like cover art corruption to me....banshee is telling the script where to find coverart and when it is trying to copy it the error happens...I need to add a filepath check, delete the file there already and then return nothing if not there I guess....I'll get around to it one day...it would be a simple thing to fix via python, a nice little file operation exercise for someone ;)

---

### Post by mrskeggster on 2011-06-23
> **kaivalagi said:**
> conkyBanshee is built for Natty too but if not working something drastic has changed with the player, look at the d-bus methods available via a tool such as d-feet....I doubt I'll run Natty or Banshee for some time so you'd be best trying to fault find and report back...I use MPD (music player daemon), Sonata frontend (customised a little as it's python :)) and mpdcron these days...all the other players are naff in comparison I think ;)

As for putting in a feature request for banshee changes I have no idea...try the banshee website but it might be best looking at what version 2 offers first...


Hi All,

Recently installed Natty, found conky and figured I had to have conkyBanshee as part of it!
Unfortunately it hasn't been working, Album, Artists, Title and Rating all come up as unknown.
Looked into this a bit - downloaded d-feet and checked the dbus messages. Attached is what I found.
Looking through the Python script I can see a bunch of methods that no longer appear to exist.
I'm not sure whether this is due to the latest version of Ubuntu or Banshee, but that seems to be the issue.

I had a look on the Banshee site, seems like they may be changing some things around as well:
[http://banshee.fm/contribute/write-code/dbus-interfaces/](http://banshee.fm/contribute/write-code/dbus-interfaces/)

I'm still quite new to the inner-workings of Ubuntu and Applications but I looked through d-feet for the interfaces mentioned and couldn't find specifically the first one, didn't really look for the rest of them as the first seems to be where the gold's at.

My guess - feel free to correct me, is that the dbus messages in the latest version of Banshee (I have 2.0.0-2ubuntu1 looking in the software center) are in the middle of being recoded, and that the methods used in the conkyBanshee script are now deprecated, however the new methods haven't been implemented/written/whatever yet.

This is my guess, if there are others out there that have further info, it would be good to hear.
Also if anyone is running Natty and the latest Banshee and have this script working - I'd love to hear from you.

Hope that sheds some light, again being new to all this it's been a bit of guesswork on my part.

Cheers,


Nate


EDIT:
Looking at Banshee features it has: *MPRIS 2.0 D-Bus interface
It also states that this is turned off by default - anyone have any idea how to turn it on?

---

### Post by kaivalagi on 2011-06-24
No idea how to turn the dbus side of things on, plugins maybe?

I suggest you get it running and try the script again before I do anything more as I can't just change the scripts to work for Natty as this will affect older versions of the app being used...

One of the music player scripts had "Get" prefixes added to properties fetching, it could be this one....I'm off to work now but if the methods I am calling are the same as the properties listed in d-feet but with a Get on the front it might just still work?

---

### Post by savalas on 2011-10-15
I have a fresh installed Ubuntu 11.10. After running ```
sudo add-apt-repository ppa:conky-companions/ppa 
``` I can't find the package conkybanshee in synaptic!?

A ```
sudo apt-get update && sudo apt-get install conkybanshee
```
doesn't help either!

What I'm doing wrong?

---

### Post by Sector11 on 2011-10-15
> **savalas said:**
> I have a fresh installed Ubuntu 11.10. After running ```
sudo add-apt-repository ppa:conky-companions/ppa 
``` I can't find the package conkybanshee in synaptic!?

A ```
sudo apt-get update && sudo apt-get install conkybanshee
```
doesn't help either!

What I'm doing wrong?


Not a clue but you can get it here:

[https://launchpad.net/~conky-companions/+archive/ppa/+packages?field.name_filter=&field.status_filter=published&field.series_filter=hardy](https://launchpad.net/~conky-companions/+archive/ppa/+packages?field.name_filter=&field.status_filter=published&field.series_filter=hardy)

---

### Post by savalas on 2011-10-15
Hello Sector11,

many thanx for your response. Your tip helped a lot! :)

Is this a bug in conky ppa or in Ubuntu 11.10? Is there a solution in the future,...do you know anything?

---

### Post by Sector11 on 2011-10-15
> **savalas said:**
> Hello Sector11,

many thanx for your response. Your tip helped a lot! :)

Is this a bug in conky ppa or in Ubuntu 11.10? Is there a solution in the future,...do you know anything?

I am not an Ubuntu user so I don't know.
But I use and support Mark's apps to the best of my ability.

---

### Post by jmadero on 2011-10-20
There is currently no Ubuntu 11.10 ppa for conkybanshee. To get it to work simply do this:

sudo gedit /etc/apt/sources.list.d/conky-companions-ppa-oneiric.list


change oneiric to natty in the two lines, save it, do sudo apt-get update, then sudo apt-get install conkybanshee

---

### Post by rivetrik on 2011-11-18
any idea on how to fix this or what i did wrong? i cant seem to get it to read banshee...



[IMG][IMG]http://i42.tinypic.com/28ulch0.jpg[/IMG][/IMG]

---

### Post by kaivalagi on 2011-11-18
> **rivetrik said:**
> any idea on how to fix this or what i did wrong? i cant seem to get it to read banshee...
What happens when you execute the following in the terminal:
```
conkyBanshee --version --datatype=TI
```

I'd recommend posting your conkyrc and template files too, so we can see how you are exec'ing in conky

---

### Post by rivetrik on 2011-11-18
> **kaivalagi said:**
> What happens when you execute the following in the terminal:
```
conkyBanshee --version --datatype=TI
```

I'd recommend posting your conkyrc and template files too, so we can see how you are exec'ing in conky

the reult of conkyBanshee --version --datatype=TI

"conkyBanshee v.2.10"


and here is my script
use_xft yes
xftfont verdana:size=8
alignment top_right
xftalpha 0.8
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
stippled_borders 10
border_margin 4
border_width 1
default_shade_color grey
default_outline_color black
default_color BADCDD
use_spacer none
no_buffers yes
uppercase no
color1 4D6844



TEXT
 ${font DejaVu Sans:size=9:style=bold}MUSIC${font} ${hr 2}
${execi 2 .conkyscripts/Case}
${image /tmp/conkyCover.png -p 2,514 -s 86x86 -f 3}
${font DejaVu Sans:size=8}${voffset -32} ${alignr}${exec .conky-scripts/conkyBanshee --datatype=AL}
${alignr}»${execi 2 .conkyscripts/conkyBanshee --datatype=TI}«
${alignr}von ${execi 2 .conkyscripts/conkyBanshee --datatype=AR}${font}

${font weather:size=82}${color C9CFD4}${execi 600 ~/scripts/conditions.sh}${color 6f6f6f}${font}${voffset -25}  ${execi 1200 ~/scripts/pogodynka.sh}

   ${color 6f6f6f}${font weather:size=28}x ${font}HDD ${execi 1 ~/scripts/hddmonit.sh}°C 
    
   ${color}${font PizzaDude Bullets:size=16}v${font}   Up: ${upspeed eth1} Kb/s 
   ${font PizzaDude Bullets:size=16}r${font}   Down: ${downspeed eth1} Kb/s 

   ${font PizzaDude Bullets:size=16}M${font}   Upload: ${totalup eth1}
   ${font PizzaDude Bullets:size=16}S${font}   Download: ${totaldown eth1}

   ${color ffffff}${font StyleBats:size=16}A${font}  CPU0: ${cpu cpu0}% ${cpubar cpu0}
   ${font StyleBats:size=16}A${font}  CPU1: ${cpu cpu1}% ${cpubar cpu1}

   ${color 6f6f6f}${font StyleBats:size=16}8${font}  Battery: ${battery_percent}% ${battery_bar}

   ${font FreeSans:size=16}@${font}${execpi 300 python ~/scripts/gmail_parser.py "slade752" "Lugner11" 3}

   ${color 6f6f6f}${font PizzaDude Bullets:size=16}J${font}   $mem / $memmax

   ${font StyleBats:size=18}P${font}  Work:  ${uptime_short}


            ${color 6f6f6f}${font Radio Space:size=14}${time %A %d %Y}
      ${font Radio Space:size=55}${time %I:%M}

   and my templete 

#!/usr/bin/env python2
# -*- coding: utf-8 -*-
###############################################################################
# conkyBanshee.py is a simple python script to gather 
# details of from Banshee for use in conky.
#
#  Author: Kaivalagi
# Created: 26/07/2009

from datetime import datetime
from optparse import OptionParser
import sys
import traceback
import codecs
import os
import shutil

try:
    import dbus
    DBUS_AVAIL = True
except ImportError:
    # Dummy D-Bus library
    class _Connection:
        get_object = lambda *a: object()
    class _Interface:
        __init__ = lambda *a: None
        ListNames = lambda *a: []
    class Dummy: pass
    dbus = Dummy()
    dbus.Interface = _Interface
    dbus.service = Dummy()
    dbus.service.method = lambda *a: lambda f: f
    dbus.service.Object = object
    dbus.SessionBus = _Connection
    DBUS_AVAIL = False


class CommandLineParser:

    parser = None

    def __init__(self):

        self.parser = OptionParser()
        self.parser.add_option("-t", "--template", dest="template", type="string", metavar="FILE", help=u"define a template file to generate output in one call. A displayable item in the file is in the form [--datatype=TI]. The following are possible options within each item: --datatype,--ratingchar. Note that the short forms of the options are not currently supported! None of these options are applicable at command line when using templates.")
        self.parser.add_option("-d", "--datatype", dest="datatype", default="TI", type="string", metavar="DATATYPE", help=u"[default: %default] The data type options are: ST (status), CA (coverart), TI (title), AL (album), AR (artist), GE (genre), YR (year), TN (track number), FN (file name), BR (bitrate k/s), LE (length), PP (current position in percent), PT (current position in time), VO (volume), RT (rating). Not applicable at command line when using templates.")
        self.parser.add_option("-c", "--coverartpath", dest="coverartpath", default="/tmp/cover", type="string", metavar="PATH", help=u"[default: %default] The file where coverart gets copied to if found when using the --datatype=CA option. Note that if set to an empty string i.e. \"\" the original file path is provided for the coverart path.")
        self.parser.add_option("-r", "--ratingchar", dest="ratingchar", default="*", type="string", metavar="CHAR", help=u"[default: %default] The output character for the ratings scale. Command line option overridden if used in templates.")
        self.parser.add_option("-s", "--statustext", dest="statustext", default="Playing,Paused,Stopped", type="string", metavar="TEXT", help=u"[default: %default] The text must be comma delimited in the form 'A,B,C'. Command line option overridden if used in templates.")
        self.parser.add_option("-n", "--nounknownoutput", dest="nounknownoutput", default=False, action="store_true", help=u"Turn off unknown output such as \"Unknown\" for title and \"0:00\" for length. Command line option overridden if used in templates.")
        self.parser.add_option("-S", "--secondsoutput", dest="secondsoutput", default=False, action="store_true", help=u"Force all position and length output to be in seconds only.")
        self.parser.add_option("-m", "--maxlength", dest="maxlength", default="0", type="int", metavar="LENGTH", help=u"[default: %default] Define the maximum length of any datatypes output, if truncated the output ends in \"...\"")
        self.parser.add_option("-v", "--verbose", dest="verbose", default=False, action="store_true", help=u"Request verbose output, not a good idea when running through conky!")
        self.parser.add_option("-V", "--version", dest="version", default=False, action="store_true", help=u"Displays the version of the script.")
        self.parser.add_option("--errorlogfile", dest="errorlogfile", type="string", metavar="FILE", help=u"If a filepath is set, the script appends errors to the filepath.")
        self.parser.add_option("--infologfile", dest="infologfile", type="string", metavar="FILE", help=u"If a filepath is set, the script appends info to the filepath.")                

    def parse_args(self):
        (options, args) = self.parser.parse_args()
        return (options, args)

    def print_help(self):
        return self.parser.print_help()

class MusicData:
    def __init__(self,status,coverart,title,album,length,artist,tracknumber,genre,year,filename,bitrate,current_position_percent,current_position,rating,volume):
        self.status = status
        self.coverart = coverart
        self.title = title
        self.album = album
        self.length = length
        self.artist = artist
        self.tracknumber = tracknumber
        self.genre = genre
        self.year = year
        self.filename = filename
        self.bitrate = bitrate
        self.current_position_percent = current_position_percent
        self.current_position = current_position
        self.rating = rating
        self.volume = volume
        
class BansheeInfo:
    
    error = u""
    musicData = None
    
    def __init__(self, options):
        self.options = options
        
    def testDBus(self, bus, interface):
        obj = bus.get_object('org.freedesktop.DBus', '/org/freedesktop/DBus')
        dbus_iface = dbus.Interface(obj, 'org.freedesktop.DBus')
        avail = dbus_iface.ListNames()
        return interface in avail
        
    def getOutputData(self, datatype, ratingchar, statustext, nounknownoutput, maxlength):
        output = u""
        
        if nounknownoutput == True:
            unknown_time = ""
            unknown_number = ""
            unknown_string = ""
        else:
            unknown_time = "0:00"
            unknown_number = "0"
            unknown_string = "Unknown"
        
        try:
                
            bus = dbus.SessionBus()
            if self.musicData == None:
                
                if self.testDBus(bus, 'org.bansheeproject.Banshee'):
                
                    self.logInfo("Calling dbus interface for music data")
    
                    try:
                        self.logInfo("Setting up dbus interface")
                        
                        # setup dbus hooks
                        remote_player = bus.get_object('org.bansheeproject.Banshee', '/org/bansheeproject/Banshee/PlayerEngine')
                        iface_player = dbus.Interface(remote_player, 'org.bansheeproject.Banshee.PlayerEngine')
                        
                        self.logInfo("Calling dbus interface for music data")
                    
                        # prepare song properties for data retrieval
                        volume = str(iface_player.GetVolume())
                        
                        status = self.getStatusText(iface_player.GetCurrentState(), statustext)

                        # grab the data into variables
                        location = iface_player.GetCurrentUri()

                        # handle a file or stream differently for filename
                        if location.find("file://") != -1:
                            filename = location[location.rfind("/")+1:]
                        elif len(location) > 0:
                            filename = location
                        else:
                            filename = ""

                        # try to get all the normal stuff...the props return an empty string if nothing is available

                        props = iface_player.GetCurrentTrack()

                        if "name" in props:
                            title = props["name"]
                        else:
                            title = None
                            
                        if "album" in props:
                            album = props["album"]
                        else:
                            album = None
                            
                        if "artist" in props:
                            artist = props["artist"]
                        else:
                            artist = None
                            
                        if "year" in props:
                            year = str(props["year"])
                        else:
                            year = None
                        
                        if "track-number" in props:
                            tracknumber = str(props["track-number"])
                        else:
                            tracknumber = None

                        if "bit-rate" in props:
                            bitrate = str(props["bit-rate"])+"k/s"
                        else:
                            bitrate = None
                            
                        if year == "0": year = None
                        if tracknumber == "0": tracknumber = None
                        if bitrate == "0": bitrate = None

                        # TODO: get album art working for internet based (if feasible)...
                        # get coverart url or file link
                        if "artwork-id" in props:
                            if os.path.exists(os.path.expanduser("~/.cache/media-art/")):
                                path_prefix = os.path.expanduser("~/.cache/media-art/")
                            else:
                                path_prefix = os.path.expanduser("~/.cache/album-art/")
                            
                            coverart = os.path.join(path_prefix,str(props["artwork-id"]) +".jpg")
                            if coverart.find("http://") != -1:
                                coverart = None
                        else:
                            coverart = None

                        # common details
                        if "genre" in props:
                            genre = props["genre"]
                        else:
                            genre = None
                        
                        length_seconds = int(iface_player.GetLength() / 1000)
                        current_seconds = int(iface_player.GetPosition() / 1000)
                        current_position = str(int(current_seconds/60)).rjust(1,"0")+":"+str(int(current_seconds%60)).rjust(2,"0")

                        if length_seconds > 0:
                            current_position_percent = str(int((float(current_seconds) / float(length_seconds))*100))
                        else:
                            length_seconds = 0
                            current_position_percent = "0"

                        if self.options.secondsoutput == True:
                            length = str(length_seconds)
                            current_position = str(current_seconds)
                        else:
                            length = str(length_seconds/60).rjust(1,"0")+":"+str(length_seconds%60).rjust(2,"0")
                            current_position = str(int(current_seconds/60)).rjust(1,"0")+":"+str(int(current_seconds%60)).rjust(2,"0")
                                
                        rating = int(iface_player.GetRating())
                        #"0" # not supported
                        

                        volume = str(iface_player.GetVolume())

                        self.musicData = MusicData(status,coverart,title,album,length,artist,tracknumber,genre,year,filename,bitrate,current_position_percent,current_position,rating,volume)
                        
                    except Exception, e:
                        self.logError(e.__str__())

            if self.musicData != None:
                
                self.logInfo("Preparing output for datatype:"+datatype)

                if datatype == "ST": #status
                    if self.musicData.status == None or len(self.musicData.status) == 0:
                        output = None
                    else:
                        output = self.musicData.status

                elif datatype == "CA": #coverart
                    if self.musicData.coverart == None or len(self.musicData.coverart) == 0:
                        output = None
                    else:
                        self.logInfo("Copying coverart from %s to %s"%(self.musicData.coverart, self.options.coverartpath))
                        shutil.copy(self.musicData.coverart, self.options.coverartpath)
                        self.musicData.coverart = self.options.coverartpath                        
                        output = self.musicData.coverart
                            
                elif datatype == "TI": #title
                    if self.musicData.title == None or len(self.musicData.title) == 0:
                        output = None
                    else:
                        output = self.musicData.title
                        
                elif datatype == "AL": #album
                    if self.musicData.album == None or len(self.musicData.album) == 0:
                        output = None
                    else:
                        output = self.musicData.album
                        
                elif datatype == "AR": #artist
                    if self.musicData.artist == None or len(self.musicData.artist) == 0:
                        output = None
                    else:
                        output = self.musicData.artist

                elif datatype == "TN": #tracknumber
                    if self.musicData.tracknumber == None or len(self.musicData.tracknumber) == 0:
                        output = None
                    else:
                        output = self.musicData.tracknumber
                        
                elif datatype == "GE": #genre
                    if self.musicData.title == genre or len(self.musicData.genre) == 0:
                        output = None
                    else:
                        output = self.musicData.genre
                        
                elif datatype == "YR": #year
                    if self.musicData.year == None or len(self.musicData.year) == 0:
                        output = None
                    else:
                        output = self.musicData.year
                                                
                elif datatype == "FN": #filename
                    if self.musicData.filename == None or len(self.musicData.filename) == 0:
                        output = None
                    else:
                        output = self.musicData.filename

                elif datatype == "BR": #bitrate
                    if self.musicData.bitrate == None or len(self.musicData.bitrate) == 0:
                        output = None
                    else:
                        output = self.musicData.bitrate
                        
                elif datatype == "LE": # length
                    if self.musicData.length == None or len(self.musicData.length) == 0:
                        output = None
                    else:
                        output = self.musicData.length
                        
                elif datatype == "PP": #current position in percent
                    if self.musicData.current_position_percent == None or len(self.musicData.current_position_percent) == 0:
                        output = None
                    else:
                        output = self.musicData.current_position_percent
                        
                elif datatype == "PT": #current position in time
                    if self.musicData.current_position == None or len(self.musicData.current_position) == 0:
                        output = None
                    else:
                        output = self.musicData.current_position
                        
                elif datatype == "VO": #volume
                    if self.musicData.volume == None or len(self.musicData.volume) == 0:
                        output = None
                    else:
                        output = self.musicData.volume
                        
                elif datatype == "RT": #rating
                    if self.musicData.rating == None or self.isNumeric(self.musicData.rating) == False:
                        output = None
                    else:
                        rating = int(self.musicData.rating)
                        if rating > 0:
                            output = u"".ljust(rating,ratingchar)
                        elif rating == 0:
                            output = u""
                        else:
                            output = None
                else:
                    self.logError("Unknown datatype provided: " + datatype)
                    return u""

            if output == None or self.musicData == None:
                if datatype in ["LE","PT"]:
                    if self.options.secondsoutput == True:
                        output = unknown_number
                    else:
                        output = unknown_time
                elif datatype in ["PP","VO","YR","TN"]:
                    output = unknown_number
                elif datatype == "CA":
                    output = ""                  
                else:
                    output = unknown_string
            
            if maxlength > 0 and len(output) > maxlength:
                output = output[:maxlength-3]+"..."
                
            return output
        
        except SystemExit:
            self.logError("System Exit!")
            return u""
        except Exception, e:
            traceback.print_exc()
            self.logError("Unknown error when calling getOutputData:" + e.__str__())
            return u""

    def getStatusText(self, status, statustext):
        
        if status != None:        
            statustextparts = statustext.split(",")
            
            if status == "playing":
                return statustextparts[0]
            elif status == "paused":
                return statustextparts[1]
            elif status == "stopped":
                return statustextparts[2]
            
        else:
            return status
        
    def getTemplateItemOutput(self, template_text):
        
        # keys to template data
        DATATYPE_KEY = "datatype"
        RATINGCHAR_KEY = "ratingchar"
        STATUSTEXT_KEY = "statustext"        
        NOUNKNOWNOUTPUT_KEY = "nounknownoutput"
        MAXLENGTH_KEY = "maxlength"
        
        datatype = None
        ratingchar = self.options.ratingchar #default to command line option
        statustext = self.options.statustext #default to command line option
        nounknownoutput = self.options.nounknownoutput #default to command line option
        maxlength = self.options.maxlength #default to command line option
        
        for option in template_text.split('--'):
            if len(option) == 0 or option.isspace():
                continue
            
            # not using split here...it can't assign both key and value in one call, this should be faster
            x = option.find('=')
            if (x != -1):
                key = option[:x].strip()
                value = option[x + 1:].strip()
                if value == "":
                    value = None
            else:
                key = option.strip()
                value = None
            
            try:
                if key == DATATYPE_KEY:
                    datatype = value
                elif key == RATINGCHAR_KEY:
                    ratingchar = value
                elif key == STATUSTEXT_KEY:
                    statustext = value                    
                elif key == NOUNKNOWNOUTPUT_KEY:
                    nounknownoutput = True
                elif key == MAXLENGTH_KEY:
                    maxlength = int(value)
                else:
                    self.logError("Unknown template option: " + option)

            except (TypeError, ValueError):
                self.logError("Cannot convert option argument to number: " + option)
                return u""
                
        if datatype != None:
            return self.getOutputData(datatype, ratingchar, statustext, nounknownoutput, maxlength)
        else:
            self.logError("Template item does not have datatype defined")
            return u""


    def getOutputFromTemplate(self, template):
        output = u""
        end = False
        a = 0
        
        # a and b are indexes in the template string
        # moving from left to right the string is processed
        # b is index of the opening bracket and a of the closing bracket
        # everything between b and a is a template that needs to be parsed
        while not end:
            b = template.find('[', a)
            
            if b == -1:
                b = len(template)
                end = True
            
            # if there is something between a and b, append it straight to output
            if b > a:
                output += template[a : b]
                # check for the escape char (if we are not at the end)
                if template[b - 1] == '\\' and not end:
                    # if its there, replace it by the bracket
                    output = output[:-1] + '['
                    # skip the bracket in the input string and continue from the beginning
                    a = b + 1
                    continue
                    
            if end:
                break
            
            a = template.find(']', b)
            
            if a == -1:
                self.logError("Missing terminal bracket (]) for a template item")
                return u""
            
            # if there is some template text...
            if a > b + 1:
                output += self.getTemplateItemOutput(template[b + 1 : a])
            
            a = a + 1

        return output
    
    def writeOutput(self):

        if self.options.template != None:
            #load the file
            try:
                fileinput = codecs.open(os.path.expanduser(self.options.template), encoding='utf-8')
                template = fileinput.read()
                fileinput.close()
            except Exception, e:
                self.logError("Error loading template file: " + e.__str__())
            else:
                output = self.getOutputFromTemplate(template)
        else:
            output = self.getOutputData(self.options.datatype, self.options.ratingchar, self.options.statustext, self.options.nounknownoutput, self.options.maxlength)

        print output.encode("utf-8")

    def isNumeric(self,value):
        try:
            temp = int(value)
            return True
        except:
            return False
        
    def logInfo(self, text):
        if self.options.verbose == True:
            print >> sys.stdout, "INFO: " + text

        if self.options.infologfile != None:
            datetimestamp = datetime.now().strftime("%Y-%m-%d %H:%M:%S") 
            fileoutput = open(self.options.infologfile, "ab")
            fileoutput.write(datetimestamp+" INFO: "+text+"\n")
            fileoutput.close()
            
    def logError(self, text):
        print >> sys.stderr, "ERROR: " + text
        
        if self.options.errorlogfile != None:
            datetimestamp = datetime.now().strftime("%Y-%m-%d %H:%M:%S") 
            fileoutput = open(self.options.errorlogfile, "ab")
            fileoutput.write(datetimestamp+" ERROR: "+text+"\n")
            fileoutput.close()
        
def main():
    
    parser = CommandLineParser()
    (options, args) = parser.parse_args()

    if options.version == True:
        print >> sys.stdout,"conkyBanshee v.2.10"
    else:
        if options.verbose == True:
            print >> sys.stdout, "*** INITIAL OPTIONS:"
            print >> sys.stdout, "    datatype:", options.datatype
            print >> sys.stdout, "    template:", options.template
            print >> sys.stdout, "    ratingchar:", options.ratingchar
            print >> sys.stdout, "    nounknownoutput:", options.nounknownoutput
            print >> sys.stdout, "    secondsoutput:", options.secondsoutput
            print >> sys.stdout, "    maxlength:", options.maxlength
            print >> sys.stdout, "    verbose:", options.verbose
            print >> sys.stdout, "    errorlogfile:",options.errorlogfile
            print >> sys.stdout, "    infologfile:",options.infologfile
            
        bansheeinfo = BansheeInfo(options)
        bansheeinfo.writeOutput()
    
if __name__ == '__main__':
    main()
    sys.exit()

---

### Post by kaivalagi on 2011-11-18
Not sure why I suggested --version although it may help, please run this instead and post the output:

```
conkyBanshee --verbose --datatype=AL
```

Also your template posting was of the python script itself, you are not using a template file (next time you post large amounts of data like that please put it in quote or code tags)

I can see from your conkyrc this is what is calling the script:

```
${exec .conky-scripts/conkyBanshee --datatype=AL}
```

For a start you may want to just use the following assuming you installed the script as described in the first post of this thread:

```
${exec conkyBanshee --datatype=AL}
```

If that doesn't work then try putting the full path in for the location of the script e.g.:

```
${exec /home/user/.conky-scripts/conkyBanshee --datatype=AL}
```

Hope that helps

---

### Post by Axess_Denied on 2012-01-26
I have thoroughly read this thread and checked other sources for a way to show the "now playing" information from Banshee in Conky.

The solution, for me, has become quite convoluted.

Firstly, I attempted to use a supplied template.

```

#${if_running banshee}
${execp ~/conkyBanshee.py --template=~/conkyBanshee.template}
#$endif

``` 

This code works well. The template was constructed poorly and attempting to edit this file was detrimental.

After getting most of the information to display in Conky, I figured I try for the album art. That process took a good bit of tinkering with the myriad suggestions offered in this thread.

The best working solution, so far, has been to embed the album art code within the above condition.

```

#${if_running banshee}
${execp ~/conkyBanshee.py --template=~/conkyBanshee.template}
${execpi 1 ~/conkyBanshee.py --datatype=CA}${image /tmp/cover -p 65,475 -s 150x150 -n}
#$endif

```

This, however, results in the text /tmp/covers displaying beside the album art (see attached photo). 

Anyone have a solution to this problem?

---

### Post by kaivalagi on 2012-01-26
2 Options I can think of, they're not tested but should get you there...

**[COLOR="Red"]1)[/COLOR]** Run the command through a script file which doesn't return the data? e.g. create runme.sh which contains:

```
#!/bin/sh
conkyBanshee --datatype=CA
```

then use:

```
${execpi 1 ~/runme.sh}${image /tmp/cover -p 65,475 -s 150x150 -n}
```

[COLOR="red"]**2)**[/COLOR] Use a template for the image output i.e. template file named "cover.template":

```
${image [--datatype=CA] -p 65,475 -s 150x150 -n}
```

and inside the conkyrc:

```
${execpi 1 ~/conkyBanshee.py --template=cover.template}
```

---

### Post by Axess_Denied on 2012-01-26
> **kaivalagi said:**
> 2 Options I can think of, they're not tested but should get you there...

**[COLOR="Red"]1)[/COLOR]** Run the command through a script file which doesn't return the data? e.g. create runme.sh which contains:

```
#!/bin/sh
conkyBanshee --datatype=CA
```

then use:

```
${execpi 1 ~/runme.sh}${image /tmp/cover -p 65,475 -s 150x150 -n}
```

[COLOR="red"]**2)**[/COLOR] Use a template for the image output i.e. template file named "cover.template":

```
${image [--datatype=CA] -p 65,475 -s 150x150 -n}
```

and inside the conkyrc:

```
${execpi 1 ~/conkyBanshee.py --template=cover.template}
```

Excellent! Thank you kindly. Sorry for the PM, should have guessed you'd subscribe.

---

### Post by kaivalagi on 2012-01-27
> **Axess_Denied said:**
> Excellent! Thank you kindly. Sorry for the PM, should have guessed you'd subscribe.

No problem and no worries ;)

---

### Post by Axess_Denied on 2012-02-29
After all of the great help here, I finally got my Conky config the way I wanted it.

Take a look and let me know what you think.

---

### Post by kaivalagi on 2012-03-01
Nice, I thin you should share the music parts of it for other banshee users :)

---

### Post by Axess_Denied on 2012-03-01
> **kaivalagi said:**
> Nice, I thin you should share the music parts of it for other banshee users :)

Great point!

Here is the conky config for Banshee only using the Banshee script discussed in this thread:

```
${voffset -6}${color slate grey}${font Verdana:size=12}Music: ${hr 2}
#${if_running banshee}
${execp ~/conkyBanshee.py --template=~/conkyBanshee.template}
${execpi 1 ~/conkyBanshee.py --template=cover.template}
#$endif
```

Here is the template that displays Banshee information (conkyBanshee.template):

```
${font verdana:bold:size=8}${color white} [--datatype=TI]
${font verdana:size=8}${color grey}  [--datatype=AR]
${font verdana:size=8}${color grey}  [--datatype=AL]  ([--datatype=YR])
${font verdana:size=6}${color white}  [--datatype=PT] / ${color grey}[--datatype=LE]
```

Here is the template to display cover art (cover.template):

```
${image [--datatype=CA] -p 32,506 -s 215x215 -n}
```

---

