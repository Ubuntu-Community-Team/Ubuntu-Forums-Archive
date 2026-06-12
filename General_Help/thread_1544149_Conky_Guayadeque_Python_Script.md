---
title: "Conky Guayadeque Python Script"
date: 2010-08-02
forum: General Help
---

### Post by kaivalagi on 2010-08-02
[SIZE="1"][COLOR="Green"]**ArchLinux : **Package support is present in the AUR. All my packages can be seen here: **[http://aur.archlinux.org/packages.php?SeB=m&K=kaivalagi](http://aur.archlinux.org/packages.php?SeB=m&K=kaivalagi)**

**Ubuntu/Debian : **All the script packages have now been copied into the Conky Companions PPA. Any package updates will be provided by the team through this new ppa. The ppa can be found here: **[https://launchpad.net/~conky-companions/+archive/ppa]("https://launchpad.net/~conky-companions/+archive/ppa")**. To use this ppa first delete the old ppa files using this:
```
sudo rm /etc/apt/sources.list.d/m-buck* && sudo rm /etc/apt/sources.list.d/conkyhardcore*
```
Then follow the modified first post instructions for the scripts[/COLOR][/SIZE]

**_[SIZE=3][COLOR=Blue]Intro[/COLOR][/SIZE]_**

This is a simple script to display what is current playing in Guayadeque. The script talks to Guayadeque using dbus, and allows the outputting of track info and the use of templates...

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
sudo apt-get update && sudo apt-get install conkyguayadeque

```

**[COLOR=Blue]Method 2: Using deb file[/COLOR]**

Run the .deb file available at the Conky Companions PPA site here: [https://launchpad.net/~conky-companions/+archive/ppa/+packages](https://launchpad.net/~conky-companions/+archive/ppa/+packages)

Warning, this will not ensure you are kept up-to-date. Only method 1 will do that ;)

**[COLOR=Blue]Method 3: Using tar.gz file[/COLOR]**

Extract all the contents of the tar.gz file to an appropriate folder, and edit the conkyGuayadeque script to point to the correct location where conkyGuayadeque.py is. The tar.gz file is available at the Conky Companions PPA site here: [https://launchpad.net/~conky-companions/+archive/ppa/+packages](https://launchpad.net/~conky-companions/+archive/ppa/+packages)

Unless you are using a non-Debian based OS I don't suggest this. Users of Debian/Ubuntu flavour OS's should ideally use method 1.

Again will will not receive updates using this method. ONLY method 1 can do this for you ;) ;)

All further details on setup are orientated around the deb package based install, so may differ from what you choose your setup to be, if done using the tarball.


**_[SIZE=3][COLOR=Blue]Usage Help[/COLOR][/SIZE]_**

You can get the current help options at any time by running (change the path as necessary):

```

conkyGuayadeque -h

```or

```

conkyGuayadeque --help

``````
Usage: conkyGuayadeque [options]
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

Development history going forwards can be seen here [URL="https://code.launchpad.net/%7Econky-companions/+junk/conkyguayadeque"]https://code.launchpad.net/~conky-companions/+junk/conkyguayadeque
[/URL] All packages available from me can be found here: [https://launchpad.net/~conky-companions/+archive/ppa]("https://launchpad.net/%7Econky-companions/+archive/ppa")

---

### Post by VastOne on 2010-08-04
Mr K,

Would you please fix the readme file so that it says

Make sure Guayadeque is running first...

instead of

Make sure Banshee is running first...

Cosmetic, but it will avoid confusion!

Thanks

---

### Post by kaivalagi on 2010-08-04
Missed one on the search and replace :) It's updated locally along with with URL being referred to near the end of the file.

I have also added track length (LE) and position percentage (PP) datatypes to the script, only status, coverart and bitrate to sort out.

Let me know when there is a new version of Guayadeque with the additional d-bus methods/properties covering the missing datatypes. I am installing Guayadeque from SVN so should see any checked-in changes if I get the latest revision, what I have installed is currently built from revision 1184 from here [https://guayadeque.svn.sourceforge.net/svnroot/guayadeque/Trunk/](https://guayadeque.svn.sourceforge.net/svnroot/guayadeque/Trunk/)

Once we have it all working and tested I'll release the next version of the script package...for now you just get a replacement .py file attached, save it over the top of /usr/share/conkyguayadeque/conkyGuayadeque.py

Cheers

---

### Post by VastOne on 2010-08-04
> **kaivalagi said:**
> Missed one on the search and replace :) It's updated locally along with with URL being referred to near the end of the file.

Let me know when there is a new version of Guayadeque with the additional d-bus methods. I am installing from SVN so should see any checked-in changes if I get the latest revision

Once we have it all working and tested I'll release the next version of the script

Cheers

Cheers...  Anonbeat will return on the 15th of this month, at which point he has a major release ready to let out of the gate.  I will discuss these changes with him as soon as he returns and we should see them no later than EOD UK time on the 17th.  

Thanks for the Banshee fixes!  This script is running great and I am sure I can answer most of the questions from within here, the G-que thread or at Conky.  The nuts and bolts of the py script are all yours!

---

### Post by VastOne on 2010-08-04
And yes, 1184 is the latest SVN, which is the way that we all keep our daily updates of G-Que.  

We have seen as many as 12 revisions in one day to let you know how active Anonbeat is and why he needed this holiday.... ;)

---

### Post by kaivalagi on 2010-08-04
Edited previous post (you were too quick to reply :))

See the 2 new datatypes...just coverart and bitrate to sort out

---

### Post by VastOne on 2010-08-04
> **kaivalagi said:**
> Edited previous post (you were too quick to reply :))

See the 2 new datatypes...just coverart and bitrate to sort out

Very nice!  Confirmed loaded and working... 
:popcorn:

---

### Post by theLegend on 2010-08-04
Can't wait for the cover art to be implemented! This is a great piece of conky work Mr Kaivalagi (had to copy and paste that, far too complicated for me to remember!). Keep up the good work! :D

---

### Post by VastOne on 2010-08-04
> **theLegend said:**
> Can't wait for the cover art to be implemented! This is a great piece of conky work Mr Kaivalagi (had to copy and paste that, far too complicated for me to remember!). Keep up the good work! :D

Cover should be implemented when Anonbeat returns from Holiday ):P

---

### Post by kaivalagi on 2010-08-04
The coverart might be tricky depending on how it is implemented in the Guayadeque code and whether it can be exposed via d-bus easily - worst case it takes longer to sort out. Bitrate should be straight forward though, probably available in the underlying music library Anonbeat is using in the app.

Hopefully it wont be too much of a messy job to get the rest sorted out

---

### Post by VastOne on 2010-08-04
Kaivalagi,

Is it possible to have seperate templates based on what is playing?

Scenario - Regular library music (that has all it's tags correct) displays perfectly.

But when playing radio stations, the albums are never correct as they generally show the name of the station that is playing as the Album, and that can be 200 characters long.

What I would like to be able to do is not display Albums when a radio station is playing.

I know I can go in a # out the album in the template when I am listening to radio but I was wondering if this could be an automatic function?

No big deal, just an idea in my head and one I would like to purge!

---

### Post by theLegend on 2010-08-05
> **kaivalagi said:**
> The coverart might be tricky depending on how it is implemented in the Guayadeque code and whether it can be exposed via d-bus easily - worst case it takes longer to sort out. Bitrate should be straight forward though, probably available in the underlying music library Anonbeat is using in the app.

Hopefully it wont be too much of a messy job to get the rest sorted out

There is already a conky script that can retrieve the coverart but it depends on there being no embedded image in the mp3 tag (crazy I know!). I've included the code below.

```
#!/usr/bin/perl

$exists = 0;
$status = "not running";
$cover = "";
$artist = "";
$album = "";
$title = "";
$time = 0;
$etime = 0;
$rating = 0;

$icon = "CD";

$tmpcover = "/tmp/conkyCover.png";
$lastcover = "/tmp/lastCover.txt";

#CONVERT TIME TO STRING
sub time_convert{
	my $in = $_[0];
	my $hours = int($in / (60*60));
	my $minutes = int(($in - $hours*(60*60)) / 60);
	my $seconds = $in - $hours*(60*60) - $minutes*60;

	#padding
	if ($seconds < 10){$seconds = "0".$seconds;}
	if ($minutes < 10){$minutes = "0".$minutes;}

	my $str = $minutes.":".$seconds;
	if ($hours > 0){$str = $hours.":".$str;}
	return $str;
}

sub create_stars{
	my $rate = $_[0];
	my $str = "";
	my $i = 0;
	for ($i = 1 ; $i <= $rate ; $i++){ $str = "s".$str;}
	for ($i = $rate+1 ; $i <= 5 ; $i++){$str = $str."r";} 
	return $str;
}

#CHECK IF IT IS RUNNING

@a = `dbus-send --print-reply --reply-timeout=2000 --type=method_call --dest=org.freedesktop.DBus /org/freedesktop/DBus org.freedesktop.DBus.ListNames | grep guayadeque`;
if ($a[0] ne ""){
	$exists = 1;
	#print("exists\n");
}

if ($exists){

	#GET QUAYDEQUE STATUS

	@a = `dbus-send --print-reply --type=method_call --dest=org.mpris.guayadeque /Player org.freedesktop.MediaPlayer.GetStatus | sed "1,2d" | sed "2,20d"`;
	@b = split(/\s+/,$a[0]);
	$st = $b[2];

	#0 = Playing, 1 = Paused, 2 = Stopped
	if ($st == 0){$status = "playing";}
	elsif ($st == 1){$status = "paused";}
	else {$status = "stopped";}

	#GET QUAYADEQUE METADATA

	@a = `dbus-send --print-reply --type=method_call --dest=org.mpris.guayadeque /Player org.freedesktop.MediaPlayer.GetMetadata`;

	for ($i=1;$i<=$#a;$i++){	
		$l = $a[$i];
		
		$l =~ s/^\s+|\s+$//g;
		#print($_,"\n");
		if ($l =~ /"title"/){
			#print($a[$i+1],"------\n");
			@b = split(/\"/,$a[$i+1]);
			$title = $b[1];
		}
		elsif ($l =~ /"artist"/){
			#print($a[$i+1],"------\n");
			@b = split(/\"/,$a[$i+1]);
			$artist = $b[1];
		}	
		elsif ($l =~ /"album"/){
			#print($a[$i+1],"------\n");
			@b = split(/\"/,$a[$i+1]);
			$album = $b[1];		
		}	
		elsif ($l =~ /"mtime"/){
			#print($a[$i+1],"------\n");
			@b = split(/\s+/,$a[$i+1]);
			$time = $b[$#b];		
		}
		elsif ($l =~ /"rating"/){
			#print($a[$i+1],"------\n");
			@b = split(/\s+/,$a[$i+1]);
			$rating = $b[$#b];		
		}			
		elsif ($l =~ /"arturl"/){
			#print($a[$i+1],"------\n");
			@b = split(/file:\/\//,$a[$i+1]);
			$b[1] =~ s/"$//g;
			$b[1] =~ s/\n//g;
			$cover = $b[1];		
		}	
	}
	
	#GET ELAPSED TIME
	@a = `dbus-send --print-reply --type=method_call --dest=org.mpris.guayadeque /Player org.freedesktop.MediaPlayer.PositionGet | sed "1d"`;
	@b = split(/\s+/,$a[0]);
	$etime = $b[$#b];
	
	
	#GET OLD COVER NAME
	if (-e $lastcover){
		open(F1,$lastcover);
		$oldcover = <F1>;
		$oldcover =~ s/\n//g;
		close(F1);
	}
}


#CREATE COVER

if (($exists) and ($cover ne "")){
	if ($cover ne $oldcover){
		system("convert \"$cover\" -thumbnail 98x98 $tmpcover");
		system("convert ~/conky_colors/conkycolors/icons/$icon/base.png $tmpcover -geometry +19+5 -composite ~/conky_colors/conkycolors/icons/$icon/top.png -geometry +0+0 -composite $tmpcover");
		system("echo \"$cover\" > $lastcover");
	}
	else{
		#print("no cover needed\n");
	}
}
else{
	system("convert ~/conky_colors/conkycolors/icons/$icon/base.png ~/conky_colors/conkycolors/icons/$icon/top.png -geometry +0+0 -composite $tmpcover");
}

#CREATE TIME STRINGS

$etime = time_convert(int($etime/1000));
$time = time_convert(int($time/1000));
$time_str = $etime." / ".$time;

#CREATE STAR RATING

$ratestr = create_stars($rating);

print("\${image $tmpcover -s 90x82 -p 24,464}");

print("\${voffset 3}\${goto 120}$artist\n");
print("\${goto 120}$title\n");
print("\${goto 120}$album\n");
print("\${goto 120}$time_str\n");
print("\${goto 120}\${font pizzadude stars:size=11}$ratestr\n");
print("\n");
```

---

### Post by kaivalagi on 2010-08-05
Thanks for that. What I ideally need is the file path to be provided from the app through d-bus as with other players, based on what it is using.

If this proves difficult I'll maybe look at code to handle it without the apps assistance.

edit: looking at the perlk code some pointers may be there for me...I'll keep you updated

---

### Post by kaivalagi on 2010-08-05
> **VastOne said:**
> Kaivalagi,

Is it possible to have seperate templates based on what is playing?

Scenario - Regular library music (that has all it's tags correct) displays perfectly.

But when playing radio stations, the albums are never correct as they generally show the name of the station that is playing as the Album, and that can be 200 characters long.

What I would like to be able to do is not display Albums when a radio station is playing.

I know I can go in a # out the album in the template when I am listening to radio but I was wondering if this could be an automatic function?

No big deal, just an idea in my head and one I would like to purge!

Why not instead use this option for the album output, if it is a lot of characters this will reduce it:

```
  -m LENGTH, --maxlength=LENGTH
                        [default: 0] Define the maximum length of any
                        datatypes output, if truncated the output ends in
                        "..."
```

The alternative you've mentioned would mean no data is presented for internet radio right?

---

### Post by kaivalagi on 2010-08-05
Updated the script, it now returns status and coverart. Status and coverart has been figured out thank's to the perl script above highlighting how. The coverart may not always be available though, hence me thinking it wasn't an available datatype before now..

So coverart may not work 100% but by all accounts only bitrate remains...

Cheers

---

### Post by VastOne on 2010-08-05
> **kaivalagi said:**
> Why not instead use this option for the album output, if it is a lot of characters this will reduce it:

```
  -m LENGTH, --maxlength=LENGTH
                        [default: 0] Define the maximum length of any
                        datatypes output, if truncated the output ends in
                        "..."
```

The alternative you've mentioned would mean no data is presented for internet radio right?

This makes perfect sense and I will use it.

Thanks~!

---

### Post by VastOne on 2010-08-05
> **kaivalagi said:**
> Why not instead use this option for the album output, if it is a lot of characters this will reduce it:

```
  -m LENGTH, --maxlength=LENGTH
                        [default: 0] Define the maximum length of any
                        datatypes output, if truncated the output ends in
                        "..."
```

The alternative you've mentioned would mean no data is presented for internet radio right?

Mr K

Where exactly does this parameter go? In the template on the AL line like this

```
${color1}Album: ${color2}[--datatype=AL] [--maxlength=15]
```

I have tried that and no results so I am assuming it is wrong.

Or would it go in the conkyrc side of it?

Could you give me a sample look of how it should look?

Thanks~!

---

### Post by kaivalagi on 2010-08-05
Here's how:
```
${color1}Album: ${color2}[--datatype=AL --maxlength=15]
```
or
```
${color1}Album: ${color2}[-d AL -m 15]
```

They are all options for the one output so need to be together in the one set of square brackets. A square bracket contents describes the equivalent to a single call straight from the conkyrc/terminal, therefore all options you would have there need to be within.

Cheers

---

### Post by VastOne on 2010-08-05
> **kaivalagi said:**
> Here's how:
```
${color1}Album: ${color2}[--datatype=AL --maxlength=15]
```
or
```
${color1}Album: ${color2}[-d AL -m 15]
```

They are all options for the one output so need to be together in the one set of square brackets. A square bracket contents describes the equivalent to a single call straight from the conkyrc/terminal, therefore all options you would have there need to be within.

Cheers

Brilliant!

Thank you, my knowledge is rising thanks to your well said explanations~!

---

### Post by kaivalagi on 2010-08-05
Once you understand this script all the music players scripts are the same :)

In fact you'll be able to take the template you have designed for one player and use it with others too...so if you do switch apps it's no biggy ;)

I use MPD though so I don't even use one of my scripts...

---

### Post by VastOne on 2010-08-05
> **kaivalagi said:**
> Once you understand this script all the music players scripts are the same :)

In fact you'll be able to take the template you have designed for one player and use it with others too...so if you do switch apps it's no biggy ;)

I use MPD though so I don't even use one of my scripts...

I have been seriously thinking about MPD since I have read so much about dbus, it seems as if MPD is a much easier process to get what is needed to display.  On the other hand, G-Que has been fantastic and now with this script working perfectly, and Anonbeat's continuous support and work, it would be hard move on. I did wonder though if MPD and G-Que could work in conjunction some how but Iam sure that is wishful thinking.  Why is it you like and use MPD?

---

### Post by kaivalagi on 2010-08-05
I use MPD because:
[LIST=1]
[*]It is a daemon (or service) and has no frontend, therefore it is lightweight and simple (much like Arch Linux ;))
[*]I can change my GUI to one of many although I use Sonata these days which has cover art and lyrics support
[*]I can easily setup a streamed output and remote control the service too, so I can listen to music on my phone via the web
[*]I can control it from the terminal too using a few different clients
[*]I use a tool called mpdcron to update when the song changes the /tmp/coverart.jpg and /tmp/lyrics.txt files that I use in conky...
[/LIST]

Not up everyones street though, it is more complicated to setup, but the individual parts always work without fault and most of them don't need to be in memory all the time either.

In the past I've used (in order of oldest first):
XMMS2 (daemon)
Rhythmbox (app)
Exaile (app)
Listen (app)
Banshee (app)
MPD (daemon)
And a bit of Guayadeque recently too :)

---

### Post by theLegend on 2010-08-05
> **kaivalagi said:**
> Updated the script, it now returns status and coverart. Status and coverart has been figured out thank's to the perl script above highlighting how. The coverart may not always be available though, hence me thinking it wasn't an available datatype before now..

So coverart may not work 100% but by all accounts only bitrate remains...

Cheers

Cheers for updating the script so quickly. I've got the status working fine and I've got the coverart location of the image...but how do I display the image in Conky (total conky newbie)?

---

### Post by kaivalagi on 2010-08-05
Use the template option for all output and then in the template for coverart have something like this:

```
${image [--datatype=CA] -p 0,0 -s 256,256}
```

-p 0,0 is defining the top left corner location and -s 256,256 is defining the width and height. See here for more details of the image tag: [http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html)

Although not using the coverart option take a look at the files here: /usr/share/conkyguayadeque/example
The conkyrc has a template based output, using the accompanying file in the folder.

Hope that helps

---

### Post by theLegend on 2010-08-05
> **kaivalagi said:**
> Use the template option for all output and then in the template for coverart have something like this:

```
${image [--datatype=CA] -p 0,0 -s 256,256}
```

-p 0,0 is defining the top left corner location and -s 256,256 is defining the width and height. See here for more details of the image tag: [http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html)

Although not using the coverart option take a look at the files here: /usr/share/conkyguayadeque/example
The conkyrc has a template based output, using the accompanying file in the folder.

Hope that helps

Here is what I have in my template file 

```
${font Liberation Sans:size=9}${goto 32}${color3}Status:${color1}[--datatype=ST]
${goto 32}${color3}Artist:${color1}[--datatype=AR]
${goto 32}${color3}Album:${color1}[--datatype=AL]
${goto 32}${color3}Title:${color1}[--datatype=TI]
${goto 32}${color3}Position:${color1}[--datatype=PT]/[--datatype=LE] - [--datatype=PP]%
${goto 32}${color3}Rating:${font pizzadude stars:size=11}${color1}[--datatype=RT]
${font Liberation Sans:size=9}${goto 32}${color3}Volume:${color1}[--datatype=VO]
${goto 32}${color3}CoverArt:${image [--datatype=CA] -p 36,400 -s 90x82}
```

Unfortunately I'm not getting an image? I'm getting the file location of the cover when I just run the datatype=CA parameter just no image when I use the last line in the template.

And here is my conky script in case this is wrong....

```
######################
# - Conky settings - #
######################
update_interval 1
total_run_times 0
net_avg_samples 1
cpu_avg_samples 1

imlib_cache_size 0
double_buffer yes
no_buffers yes

#####################
# - Text settings - #
#####################
use_xft yes
xftfont Liberation Sans:size=8
override_utf8_locale yes
text_buffer_size 2048

#############################
# - Window specifications - #
#############################
own_window_class Conky
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Size and position
minimum_size 256 993
maximum_width 256
gap_x -5
gap_y 25
alignment top_right
default_bar_size 60 8

#########################
# - Graphics settings - #
#########################
draw_shades no

default_color cccccc

color0 white
color1 E07A1F
color2 white

TEXT
${image ~/.ConkyWizardTheme/pix/background.png -p 0,0 -s 256x993}

${font Liberation Sans:style=Bold:size=8}${voffset 9}${goto 32}SYSTEM $stippled_hr${font}
##############
# - SYSTEM - #
##############
${color0}${voffset 4}${goto 32}${font OpenLogos:size=19}u${font}${color}${goto 60}${voffset -14}Kernel:  ${goto 160}${color2}${kernel}${color}
${goto 60}Uptime: ${goto 160}${color2}${uptime}${color}
# |--UPDATES
${goto 60}Updates: ${goto 160}${font Liberation Sans:style=Bold:size=8}${color1}${execi 360 aptitude search "~U" | wc -l | tail}${color}${font} ${color2}Packages${color}
# |--CPU
${offset 1}${color0}${goto 32}${font Poky:size=16}P${font}${offset -19}${voffset 9}${cpubar cpu0 4,18}${color}${voffset -16}${goto 60}CPU1: ${font Liberation Sans:style=Bold:size=8}${color1}${cpu cpu1}%${color}${font} ${goto 160}${color2}${cpugraph cpu1 8,60 CE5C00 E07A1F}${color}
${goto 60}CPU2: ${font Liberation Sans:style=Bold:size=8}${color1}${cpu cpu2}%${color}${font} ${goto 160}${color2}${cpugraph cpu2 8,60 CE5C00 E07A1F}${color}
${goto 60}CPU3: ${font Liberation Sans:style=Bold:size=8}${color1}${cpu cpu3}%${color}${font} ${goto 160}${color2}${cpugraph cpu3 8,60 CE5C00 E07A1F}${color}
${goto 60}CPU4: ${font Liberation Sans:style=Bold:size=8}${color1}${cpu cpu4}%${color}${font} ${goto 160}${color2}${cpugraph cpu4 8,60 CE5C00 E07A1F}${color}
# |--MEM
${color0}${goto 32}${font Poky:size=16}M${font}${color}${goto 60}${voffset -7}RAM: ${font Liberation Sans:style=Bold:size=8}${color1}$memperc%${color}${font}
${offset 1}${voffset 2}${color0}${goto 32}${membar 4,18}${color}${goto 60}${voffset -2}F: ${color2}${memeasyfree}${color} U: ${color2}${mem}${color}
#############
# - CLOCK - #
#############
${voffset 4}${font Liberation Sans:style=Bold:size=8}${goto 32}DATE $stippled_hr${font}
${voffset -10}${alignc 36}${color2}${font Arial Black:size=30}${time %H:%M}${font}${color}
${alignc}${time %d %B %Y}
###############
# - NETWORK - #
###############
${voffset 4}${font Liberation Sans:style=Bold:size=8}${goto 32}NETWORK $stippled_hr${font}
# |--WLAN0
${if_up wlan0}
${voffset -13}${color0}${goto 32}${font VariShapes Solid:size=14}q${font}${color}${goto 60}${voffset -6}Up: ${font Liberation Sans:style=Bold:size=8}${color1}${upspeed wlan0}${color}${font} ${goto 160}${color2}${upspeedgraph wlan0 8,60 CE5C00 E07A1F}${color}
${goto 60}Total: ${color2}${totalup wlan0}${color}
${voffset -2}${color0}${goto 32}${font VariShapes Solid:size=14}Q${font}${color}${goto 60}${voffset -6}Down: ${font Liberation Sans:style=Bold:size=8}${color1}${downspeed wlan0}${color}${font} ${goto 160}${color2}${downspeedgraph wlan0 8,60 CE5C00 E07A1F}${color}
${goto 60}Total: ${color2}${totaldown wlan0}${color}
${voffset -2}${color0}${font Poky:size=14}Y${font}${color}${goto 60} ${voffset -2}Signal: ${font Liberation Sans:style=Bold:size=8}${color1}${wireless_link_qual wlan0}%${color}${font} ${goto 160}${color2}${wireless_link_bar 8,60 wlan0}${color}
${voffset 4}${color0}$${goto 32}{font Poky:size=13}w${font}${color}${goto 60}${voffset -8}Local IP: ${goto 160}${color2}${addr wlan0}${color}
${goto 60}Public IP: ${goto 160}${color2}${execi 10800 ~/.conkycolors/bin/conkyIp}${color}
# |--ETH0
${else}${if_up eth0}
${voffset -13}${color0}${goto 32}${font VariShapes Solid:size=14}q${font}${color}${goto 60}${voffset -6}Up: ${font Liberation Sans:style=Bold:size=8}${color1}${upspeed eth0}${color}${font} ${goto 160}${color2}${upspeedgraph eth0 8,60 CE5C00 E07A1F}${color}
${goto 60}Total: ${color2}${totalup eth0}${color}
${voffset -2}${color0}${goto 32}${font VariShapes Solid:size=14}Q${font}${color}${goto 60}${voffset -6}Down: ${font Liberation Sans:style=Bold:size=8}${color1}${downspeed eth0}${color}${font} ${goto 160}${color2}${downspeedgraph eth0 8,60 CE5C00 E07A1F}${color}
${goto 60}Total: ${color2}${totaldown eth0}${color}
${voffset -2}${color0}${goto 32}${font Poky:size=13}w${font}${color}${goto 60}${voffset -4}Local IP: ${goto 160}${color2}${addr eth0}${color}
${goto 60}Public IP: ${goto 160}${color2}${execi 10800 ~/conky_colors/conkycolors/bin/conkyIp}${color}
# |--PPP0
${endif}${else}${if_up ppp0}
${voffset -13}${color0}${goto 32}${font VariShapes Solid:size=14}q${font}${color}${goto 60}${voffset -6}Up: ${font Liberation Sans:style=Bold:size=8}${color1}${upspeed ppp0}${color}${font} ${goto 160}${color2}${upspeedgraph ppp0 8,60 CE5C00 E07A1F}${color}
${goto 60}Total: ${color2}${totalup ppp0}${color}
${voffset -2}${color0}${goto 32}${font VariShapes Solid:size=14}Q${font}${color}${goto 60}${voffset -6}Down: ${font Liberation Sans:style=Bold:size=8}${color1}${downspeed ppp0}${color}${font} ${goto 160}${color2}${downspeedgraph ppp0 8,60 CE5C00 E07A1F}${color}
${goto 60}Total: ${color2}${totaldown ppp0}${color}
${voffset -2}${color0}${goto 32}${font Poky:size=13}w${font}${color}${goto 60}${voffset -4}Local IP: ${goto 160}${color2}${addr ppp0}${color}
${endif}${else}${voffset 4}${color0}${font PizzaDude Bullets:size=12}4${font}${color}${goto 60}Network Unavailable${endif}${endif}
# - NVIDIA - #
##############
${voffset -4}${goto 32}${font Liberation Sans:style=Bold:size=8}NVIDIA $stippled_hr${font}
${color0}${voffset -4}${goto 32}${font Poky:size=17}N${font}${color}${goto 60}${voffset -8}GPU Temp:${goto 160}${font Liberation Sans:style=Bold:size=8}${color1} ${exec nvidia-settings -q GPUCoreTemp | grep Attribute | cut -d ' ' -f 6 | cut -c 1-2}${font}${color}°C
${goto 60}GPU Clock:${goto 160}${font Liberation Sans:style=Bold:size=8}${color1} ${exec nvidia-settings -q GPU2DClockFreqs -t}${font}${color}MHz
${goto 60}Video RAM:${goto 160}${font Liberation Sans:style=Bold:size=8}${color1} ${exec nvidia-settings -q VideoRam -t}${font}${color}KiB
${goto 60}Driver Version:${goto 160}${font Liberation Sans:style=Bold:size=8}${color1} ${exec nvidia-settings -q NvidiaDriverVersion -t}${font}${color}
#############
# - Music - #
#############
${voffset -4}
${font Liberation Sans:bold:size=8}${color0}${goto 32}MUSIC $stippled_hr${font}$
#${color4}${font Terminus:style=Bold:size=14}@ ${font #Terminus:style=Bold:size=11}Guayadeque${font}
#${color4}Template Output:

${color1}${execp conkyGuayadeque -n --template=/usr/share/conkyguayadeque/example/conkyGuayadeque.template}
#${color4}Standard Output:
#${voffset 5}${color4} Title:  ${color1}${font}${exec conkyGuayadeque --datatype=TI} 
#${color4} Position:  ${color1}${font}${exec conkyGuayadeque --datatype=PT}/${exec conkyGuayadeque --datatype=LE}
#guaycover script ###############################################################
#${execpi 3 ~/conky_colors/guayCover}${voffset -4}
#################################################################################
########################
# - Hard Drives Info - #
########################
#${voffset -4}
${font Liberation Sans:bold:size=8}${color0}${goto 32}HARD DRIVES $stippled_hr${font}$
${execpi 300 ~/conky_colors/conkycolors/scripts/conkyHD1.py}

########################
# - Clock - #
########################
#${voffset -4}
#${font Liberation Sans:bold:size=8}${color0}Clock $stippled_hr${font}$
#${execpi 30 ~/conky_colors/conkycolors/scripts/conkyClock_m.py}

########################
# Temperatures #
########################
${voffset -4}${font Liberation Sans:bold:size=8}${color0}${goto 32}TEMPERATURES $stippled_hr

${font Liberation Sans:bold:size=8}${color0}${goto 32}CPU TEMP: ${font Liberation Sans:style=Bold:size=8}${color1}${execi 4 sensors | grep -A 0 'temp2' | cut -c15-18} ºC ${font}${color}

${font Liberation Sans:bold:size=8}${color0}${goto 32}HARD DRIVE TEMP: ${font Liberation Sans:style=Bold:size=8}${color1}${execi 4 sensors | grep -A 0 'temp1' | cut -c15-18} ºC

${font Liberation Sans:bold:size=8}${color0}${goto 32}SHORTCUTS $stippled_hr{font}
${color}
${goto 32}Shift-Ctrl-C......Conky config
${goto 32}Shift-Ctrl-U......Updates
${goto 32}Shift-Ctrl-S......System Monitor

```

Any thoughts.... I would so love to solve this one last piece of the puzzle!

---

### Post by VastOne on 2010-08-06
> **kaivalagi said:**
> Use the template option for all output and then in the template for coverart have something like this:

```
${image [--datatype=CA] -p 0,0 -s 256,256}
```

-p 0,0 is defining the top left corner location and -s 256,256 is defining the width and height. See here for more details of the image tag: [http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html)

Although not using the coverart option take a look at the files here: /usr/share/conkyguayadeque/example
The conkyrc has a template based output, using the accompanying file in the folder.

Hope that helps

Is CA still something that Anonbeat must enable before it works properly?

When I run my script and add the CA section, I get a "Unable to load image .../path to file location"

---

### Post by kaivalagi on 2010-08-06
I'll look at the cover art at the weekend...I need to set it up on my machine for testing properly. If a valid file path is coming from Guayadeque there is nothing for anonbeat to worry about.

---

### Post by VastOne on 2010-08-06
FYI -

I have set this in the template after reading threads from you other scripts and it works great and looks fantastic.

I have mine right under the Position field..

```
${execibar 1 conkyGuayadeque --datatype=PP}
```

---

### Post by kaivalagi on 2010-08-06
Good stuff

I am trying to get $image based cover art to work but it doesn't like spaces....

I have tried asking on #conky and got no reply, I have tried variations on a path with and with space chars, nothing works...e.g.

/home/user/Music/A Happy Song/Cover.jpg
file:///home/user/Music/A%20Happy%20Song/Cover.jpg
/home/user/Music/A\ Happy\ Song/Cover.jpg

Ideas anyone? I can manipulate the path to whatever works...I just can't figure out what works with conky when an image path has spaces in it!

---

### Post by VastOne on 2010-08-06
> **kaivalagi said:**
> Good stuff

I am trying to get $image based cover art to work but it doesn't like spaces....

I have tried asking on #conky and got no reply, I have tried variations on a path with and with space chars, nothing works...e.g.

/home/user/Music/A Happy Song/Cover.jpg
file:///home/user/Music/A%20Happy%20Song/Cover.jpg
/home/user/Music/A\ Happy\ Song/Cover.jpg

Ideas anyone? I can manipulate the path to whatever works...I just can't figure out what works with conky when an image path has spaces in it!

I think this is something Anonbeat will have to look at.  I record a lot of music from streams with G-Que and I have had issues with spaces in location paths doing that as well. As soon as he is available, I will talk with him and see if he can spot something.  Or perhaps those gurus over on the conky thread can shed some light.

---

### Post by kaivalagi on 2010-08-06
> **VastOne said:**
> I think this is something Anonbeat will have to look at.  I record a lot of music from streams with G-Que and I have had issues with spaces in location paths doing that as well. As soon as he is available, I will talk with him and see if he can spot something.  Or perhaps those gurus over on the conky thread can shed some light.

This is purely a conky issue, if Anonbeat can help here then great :)

---

### Post by theLegend on 2010-08-06
> **kaivalagi said:**
> Good stuff

I am trying to get $image based cover art to work but it doesn't like spaces....

I have tried asking on #conky and got no reply, I have tried variations on a path with and with space chars, nothing works...e.g.

/home/user/Music/A Happy Song/Cover.jpg
file:///home/user/Music/A%20Happy%20Song/Cover.jpg
/home/user/Music/A\ Happy\ Song/Cover.jpg

Ideas anyone? I can manipulate the path to whatever works...I just can't figure out what works with conky when an image path has spaces in it!

Yeah I thought it might be something to do with spaces in the file name so I tried putting it in quotes but that doesn't do nothing!

EDIT: Reading some conky pages it looks like the best thing to do is to copy the image from the cover location retrieved by the CA datatype into a tempdir (i.e so that it has no spaces I guess). Do you know how to copy the location string outside of the template into conky or maybe create a script? Maybe we could edit the coverGuayadeque.py file so that it does the copying for you?

---

### Post by kaivalagi on 2010-08-06
You can run a second copy of conkyGuayadeque as part of a larger command to copy the cover art to a known location, but you will be doing it every second. Then have an image tag with the known file configured.

---

### Post by theLegend on 2010-08-06
This is what it was doing with the Guaycover script. I was hoping to find a way to just retrieve the image and stick it on the conky screen and it would only change once the song changed.....I'll keep thinking!

---

### Post by kaivalagi on 2010-08-06
A separate process to copy the cover art is sometimes best anyway, I have a process that only fires when the title changes, so images remain "painted" with refreshing every second. I use mpdcron for mpd, for guayadeque if you have a script that triggers "work" from a title change i.e. via the d-bus signals then it's as efficient as can be really.

[COLOR="Navy"]edit: Knocked something together, grab the attached and extract it somewhere, rename to what you want and then call it once guayadeque is running (might break if not). It will run and trigger a file copy when a track changes in Guayadeque :)[/COLOR]

---

### Post by VastOne on 2010-08-06
> **kaivalagi said:**
> A separate process to copy the cover art is sometimes best anyway, I have a process that only fires when the title changes, so images remain "painted" with refreshing every second. I use mpdcron for mpd, for guayadeque if you have a script that triggers "work" from a title change i.e. via the d-bus signals then it's as efficient as can be really.

[COLOR="Navy"]edit: Knocked something together, grab the attached and extract it somewhere, rename to what you want and then call it once guayadeque is running (might break if not). It will run and trigger a file copy when a track changes in Guayadeque :)[/COLOR]

Ok, to be sure, I dloaded and extracted this started G-Que then started the script like so in terminal 
```

/staging/python GetGuayadequeCoverart.py
```

Then went to G-que and started a track with a known image location...

And nothing happens...

But TheLegend and I are hard at work on it resolving it

---

### Post by theLegend on 2010-08-06
> **kaivalagi said:**
> A separate process to copy the cover art is sometimes best anyway, I have a process that only fires when the title changes, so images remain "painted" with refreshing every second. I use mpdcron for mpd, for guayadeque if you have a script that triggers "work" from a title change i.e. via the d-bus signals then it's as efficient as can be really.

[COLOR="Navy"]edit: Knocked something together, grab the attached and extract it somewhere, rename to what you want and then call it once guayadeque is running (might break if not). It will run and trigger a file copy when a track changes in Guayadeque :)[/COLOR]

How to run the command in conky? I've tried execp but it crashes conky

Ran it through the terminal ok and it saves the image to my tmp folder

EDIT: Ok, i've decided to run the script outside of conky and just use the image command in conky...so far so good...now for tracks with embedded images! Cheers buddy!

---

### Post by kaivalagi on 2010-08-06
> **theLegend said:**
> EDIT: Ok, i've decided to run the script outside of conky and just use the image command in conky...so far so good...now for tracks with embedded images! Cheers buddy!

You got the idea :)

I'll be including a script called "conkyGuayadeque-GetCoverArt" in the package next time around.

---

### Post by VastOne on 2010-08-06
> **kaivalagi said:**
> You got the idea :)

I'll be including a script called "conkyGuayadeque-GetCoverArt" in the package next time around.

And in that time we will figure out how to get the embedded ones to work.

Thank you again K!!!

---

### Post by kaivalagi on 2010-08-06
Because arranging a build takes time, here are the latest files

Just make sure you don't run conkyGuayadeque-GetCoverArt until the player is running

Cheers

---

### Post by kaivalagi on 2010-08-06
> **VastOne said:**
> And in that time we will figure out how to get the embedded ones to work.

Thank you again K!!!

No probs, I actually think using this separate process to handle cover art is the way to go, the alternative direct in conky does a image reload every second...

---

### Post by VastOne on 2010-08-06
Kaivalagi

Can you clear something up for me.


In a conversation with theLegend, he stated that he was able to graft the conkyrc example file into his normal conkyrc file.  

I cannot do this, when I put the exact components into where I want it in my conkyrc file, everything from the template shows up, but none of the processes run, every thing stays blank.

So I start mine off this way...From Alt + F2 run application

```
xterm -e conky -c .conkyrc2
```

And it works perfectly.  I use xterm because this window never shuts down, and xterm is low overhead this session, and the conkyguaydeque stays active as long as I have conkyguayadeque running.

I hope I am making sense in this because I am beginning to believe that I am starting this completely the wrong way even though it works.

Let me know what ya think

Thanks

---

### Post by kaivalagi on 2010-08-07
So how do you start conky, I assume it is started from the startup applications options in your OS? You may need to "sleep" for a bit before it runs, to ensure the OS and music player is loaded fully first?

If I misunderstood please explain

---

### Post by theLegend on 2010-08-07
> **kaivalagi said:**
> So how do you start conky, I assume it is started from the startup applications options in your OS? You may need to "sleep" for a bit before it runs, to ensure the OS and music player is loaded fully first?

If I misunderstood please explain

This is how I run conky and have no problems. I've given VastOne the command to start it from the startup apps. Hopefully this will solve his problem. 

My issue is still with the coverart. Where the song playing has embedded art it doesn't seem to pick up the coverart even if there is a cover.jpg file in the same folder. Any thoughts as to why this would be?

---

### Post by kaivalagi on 2010-08-07
> **theLegend said:**
> This is how I run conky and have no problems. I've given VastOne the command to start it from the startup apps. Hopefully this will solve his problem. 

My issue is still with the coverart. Where the song playing has embedded art it doesn't seem to pick up the coverart even if there is a cover.jpg file in the same folder. Any thoughts as to why this would be?

Does it show in Guayadeque, it needs to be known by it before it will be shown.

If it does show in the app but not through the GetCoverart script copying it on track change, we may need Anonbeat to get on the case.

I need a good example of what you are referring too ideally, is the coverart.jpg file not updated?


@VastOne, here's my conky.sh script I call at startup:
```
#!/bin/sh
echo "* Killing all conky instances..."
killall conky

if [ ! -z $1 ]; then
    echo "* Sleeping for $1 seconds..."
    sleep $1
else
    echo "* Sleeping for 30 seconds..."
    sleep 60
fi

echo "* Starting conky with custom config 'conky_mpd.bar'"
conky -c /home/user/.scripts/conky/conky_mpd.bar &

echo "* Starting conky with custom config 'conky_forecast'"
conky -c /home/user/.scripts/conky/conky_forecast &

# check for conkyUpdates.txt (Arch packages ready for update), if not there then start the process to create it
if [ ! -f /tmp/conkyUpdates.txt ]; then
    echo "* Updating hourly cron based conky updates..."
    sudo /etc/cron.hourly/conkyUpdates.sh
fi

```

When called at startup it is just
```
/home/user/.scripts/conky.sh
```
when called if I want to refresh it straight away (in my path):
```
conky.sh 0
```

edit: Added screenshot

---

### Post by theLegend on 2010-08-07
Thats a nice conky set up! And to answer your question, it shows up in the notification applet, the cover art I mean, and it shows in G-Que, it just isn't updated in the /tmp/guayadequecover.jpg location. It only happens for the tracks that have a picture embedded in the tag I believe.

---

### Post by kaivalagi on 2010-08-07
If I could track down an file with embedded art I could reproduce the problem, I'll have a look but not holding out much hope...

edit: found some mp3s with images embedded and couldn't see a way for me to get the image data without using a mp3 library of some sort...

---

### Post by theLegend on 2010-08-07
> **kaivalagi said:**
> If I could track down an file with embedded art I could reproduce the problem, I'll have a look but not holding out much hope...

edit: found some mp3s with images embedded and couldn't see a way for me to get the image data without using a mp3 library of some sort...

I can understand it not finding the embedded image but why doesn't it copy the image in the folder of the song?

Another side issue what does the below section of your conky startup script do? Whats its purpose?

if [ ! -z $1 ]; then
    echo "* Sleeping for $1 seconds..."
    sleep $1
else
    echo "* Sleeping for 30 seconds..."
    sleep 60
fi

---

### Post by kaivalagi on 2010-08-07
> **theLegend said:**
> I can understand it not finding the embedded image but why doesn't it copy the image in the folder of the song?

Another side issue what does the below section of your conky startup script do? Whats its purpose?

if [ ! -z $1 ]; then
    echo "* Sleeping for $1 seconds..."
    sleep $1
else
    echo "* Sleeping for **60** seconds..."
    sleep 60
fi

The if statement checks for an argument, if set it uses it to say how long to sleep, if not set it defaults to 60 seconds sleep time i.e. when called without arg at startup for gnome/kde etc. Just ended up this way to suit the things I've been doing with conky, it allows me to start conky on different desktops with different wait times easily. Some desktops are nippy and others not so...

---

### Post by kaivalagi on 2010-08-07
Updated GetCoverArt script attached which will hopefully now retrieve embedded images from a file if they are there after checking for an image file path. Fingers crossed it fixes what I think is the problem :)

You'll _need_ the "python-eyed3" package installed, something I'll be adding to the package dependencies on the next build along with being dependant on guayadeque :)

---

### Post by theLegend on 2010-08-07
> **kaivalagi said:**
> Updated GetCoverArt script attached which will hopefully now retrieve embedded images from a file if they are there after checking for an image file path. Fingers crossed it fixes what I think is the problem :)

You'll _need_ the "python-eyed3" package installed, something I'll be adding to the package dependencies on the next build along with being dependant on guayadeque :)

You do spoil us Mr K! I've installed the python-eyed3 package no problems and ran this script....works fine with tracks without embedded images, however gets this error when it is embedded :

```
*** Error: Begin
Traceback (most recent call last):
  File ".conky/conkyGuayadeque-GetCoverart.py", line 65, in OnTrackChange
    elif src != self.current and os.path.exists(src) == True:
  File "/usr/lib/python2.6/genericpath.py", line 18, in exists
    st = os.stat(path)
TypeError: coercing to Unicode: need string or buffer, NoneType found
*** Error: End
* Listening: waiting for a track change...

```

Any ideas?

---

### Post by kaivalagi on 2010-08-07
> **theLegend said:**
> Any ideas?
My bad, updated the previous attachment, try again...should hopefully work okay now

---

### Post by theLegend on 2010-08-07
> **kaivalagi said:**
> My bad, updated the previous attachment, try again...should hopefully work okay now

This is a better script as it tells me .......
```

conkyGuayadeque-GetCoverart - Cover art will be copied to '/tmp/guayadeque-coverart.jpg'
* Initialising: Creating a D-Bus session...
* Listening: waiting for a track change...
** Track Changed: No cover art images known, Checking for embedded images in audio file...
**                No image found.
* Listening: waiting for a track change...
```

There is a cover.jpg image in the folder location, so I am trying to work out why G-Que parameter is saying there isn't?

I've run the "conkyGuayadeque --datatype=CA" script in terminal and it is returning a blank line i.e. no image location, which obviously my problem. Its weird cos there is an image in G-Que.

Looking into further, if you go to in edit songs of that album and if there is a picture in the pictures tab then the script is returning no image location...Bizarre!

---

### Post by kaivalagi on 2010-08-07
Something for Anonbeat to help us with I'd say

The script works for embedded images in tags though yes?

---

### Post by theLegend on 2010-08-07
> **kaivalagi said:**
> Something for Anonbeat to help us with I'd say

The script works for embedded images in tags though yes?

If I had the picture to the tag via Easytag so its embedded your script still works fine, whether its retrieving the embedded art or not I don't know, but if the picture is added to the picture tag in Guayadeque thats when your script doesn't work.

I suppose one workaround would be that if it didn't return a file i.e. blank, it would look in the same folder as the track and copy a file called cover.jpg. But I realise this is unnecessary extra work for the script in the long run.

---

### Post by kaivalagi on 2010-08-07
Some use cover.jpg, others folder.jpg...it should be dealt with by Guayadeque properly if the image file is there in the same folder as the audio files. The path should really be presented through a d-bus call for cover art in my opinion. If the app is showing it the app should provide the path to it.

---

### Post by theLegend on 2010-08-07
> **kaivalagi said:**
> Some use cover.jpg, others folder.jpg...it should be dealt with by Guayadeque properly if the image file is there in the same folder as the audio files. The path should really be presented through a d-bus call for cover art in my opinion. If the app is showing it the app should provide the path to it.

I agree with you totally cos it appears in the notification applet of ubuntu every time regardless if its embedded or not....maybe Anonbeat will provide us with the answers we need....its working in the meantime however just fine with a little work, so thanks very much for your hard work in creating the two scripts.

---

### Post by VastOne on 2010-08-07
> **kaivalagi said:**
> So how do you start conky, I assume it is started from the startup applications options in your OS? You may need to "sleep" for a bit before it runs, to ensure the OS and music player is loaded fully first?

If I misunderstood please explain

> **theLegend said:**
> This is how I run conky and have no problems. I've given VastOne the command to start it from the startup apps. Hopefully this will solve his problem. 

No, nothing is is resolved on my end and I will explain it better. 

I run three Conky scripts.

Conkyrc - Left side - All systems info

conky.timedate  - Right side - Time Calender weather and email

I run those via a startup script

```
#!/bin/sh
/usr/bin/conky -q -d &
/usr/bin/conky -c ~/conky-timedate.conf -q -d
```

They run perfect.


When I run

conky -c /usr/share/conkyguayadeque/example/conkyrc &

It works if I run it separate and I can cntrl C and exit that term and it still works. But If I add that line to my startup script

```
#!/bin/sh
/usr/bin/conky -q -d &
/usr/bin/conky -c ~/conky-timedate.conf -q -d &
/usr/bin/conky -c /usr/share/conkyguayadeque/example/conkyrc &
```

The conkyguayadeque loads and all the code is there, but nothing works - everything reads unknown or 0.00

And the term session that opens this stays running and if I cntrl c to exit it, everything quits - all 3 conky sessions.

I have tried to add conkyrc commands to my 2nd script (which is where I want it to reside) but the same thing happens, the code shows up but everything reads 0

I hope this makes better sense and a better Idea of what is going on.

This is a Conky problem and I am posting this same thing over there.

---

### Post by kaivalagi on 2010-08-07
Guayadeque needs to be running before the script, also you should really have a sleep statement before your conky calls, to allow the desktop to load first. When you run that script once everything is loaded (incl guayadeque) does it work okay?

I would add something so your script would look like this (no "&" after sleep command deliberately):

```
#!/bin/sh
guayadeque &
sleep 30
/usr/bin/conky -q -d &
/usr/bin/conky -c ~/conky-timedate.conf -q -d &
/usr/bin/conky -c /usr/share/conkyguayadeque/example/conkyrc &
```

---

### Post by VastOne on 2010-08-07
> **kaivalagi said:**
> Guayadeque needs to be running before the script, also you should really have a sleep statement before your conky calls, to allow the desktop to load first. When you run that script once everything is loaded (incl guayadeque) does it work okay?

I would add something so your script would look like this (no "&" after sleep command deliberately):

```
#!/bin/sh
guayadeque &
sleep 30
/usr/bin/conky -q -d &
/usr/bin/conky -c ~/conky-timedate.conf -q -d &
/usr/bin/conky -c /usr/share/conkyguayadeque/example/conkyrc &
```

No - The code of the conkyguayadeque script shows up but the functions do not work - everything reads 0 % or unknown

Guayadeque is always running prior to this - but I have not added this to a startup script yet because it is not working because of the 3rd line not functioning

---

### Post by kaivalagi on 2010-08-07
No idea....works fine for me and I can't see what could cause problems for you either?

---

### Post by VastOne on 2010-08-07
> **kaivalagi said:**
> No idea....works fine for me and I can't see what could cause problems for you either?

I know, I have an enigma that I am muddling through.  The folks over at the conky thread should help me solve it.

Thanks

---

### Post by theLegend on 2010-08-07
> **kaivalagi said:**
> No idea....works fine for me and I can't see what could cause problems for you either?

This is the comment that everyone dreads when trying to solve a problem! LOL!

I've got two conky scripts running side by side and I copied the example that Mr K gave...works like a charm.

---

### Post by VastOne on 2010-08-07
> **theLegend said:**
> This is the comment that everyone dreads when trying to solve a problem! LOL!

I've got two conky scripts running side by side and I copied the example that Mr K gave...works like a charm.

2nd most dreaded response :(


Well I am SO bloody happy for the both of you...!!!!!!!! =D>

---

### Post by kaivalagi on 2010-08-07
Try copying /usr/share/conkyguayadeque/example/conkyrc and the template file to somewhere in your $HOME folder, then adjust the conky -c command and conkyrc to suit tthe new paths, see if that helps

---

### Post by VastOne on 2010-08-07
> **kaivalagi said:**
> Try copying /usr/share/conkyguayadeque/example/conkyrc and the template file to somewhere in your $HOME folder, then adjust the conky -c command and conkyrc to suit tthe new paths, see if that helps

Shoot me - Now Please....

I restarted from ground zero as if I never had anything conky related before.

Rebuilt everything exactly the same way....


And it works exactly the way I want it to with the G-Que py grafted into my second conky-timedate script.

I did not do anything different, just started from the beginning and added piece by piece.

Shoot me....

Thanks for the help and my apologies for the chasing of gremlins.

---

### Post by theLegend on 2010-08-07
I think Linux just felt sorry for you, and found the gremlins and shot them all and ran the scripts how you wanted them.

---

### Post by VastOne on 2010-08-07
> **theLegend said:**
> I think Linux just felt sorry for you, and found the gremlins and shot them all and ran the scripts how you wanted them.

You may have a point there...Linux noticed my sleep deprivation and took natural pity...

---

### Post by VastOne on 2010-08-07
> **theLegend said:**
> This is a better script as it tells me .......
```

conkyGuayadeque-GetCoverart - Cover art will be copied to '/tmp/guayadeque-coverart.jpg'
* Initialising: Creating a D-Bus session...
* Listening: waiting for a track change...
** Track Changed: No cover art images known, Checking for embedded images in audio file...
**                No image found.
* Listening: waiting for a track change...
```

There is a cover.jpg image in the folder location, so I am trying to work out why G-Que parameter is saying there isn't?


I've run the "conkyGuayadeque --datatype=CA" script in terminal and it is returning a blank line i.e. no image location, which obviously my problem. Its weird cos there is an image in G-Que.

Looking into further, if you go to in edit songs of that album and if there is a picture in the pictures tab then the script is returning no image location...Bizarre!

When I run the following from term

```
/usr/bin/python /usr/share/conkyguayadeque/conkyGuayadeque-GetCoverart.py
```

I get - 

```
conkyGuayadeque-GetCoverart - Cover art will be copied to '/tmp/guayadeque-coverart.jpg'
* Initialising: Creating a D-Bus session...
** Error: Is Guayadeque running? The D-Bus service is not working.
Traceback (most recent call last):
  File "/usr/share/conkyguayadeque/conkyGuayadeque-GetCoverart.py", line 47, in __init__
    self.remote_player = self.bus.get_object('org.mpris.guayadeque', '/Player')
  File "/usr/lib/pymodules/python2.6/dbus/bus.py", line 244, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 241, in __init__
    self._named_service = conn.activate_name_owner(bus_name)
  File "/usr/lib/pymodules/python2.6/dbus/bus.py", line 183, in activate_name_owner
    self.start_service_by_name(bus_name)
  File "/usr/lib/pymodules/python2.6/dbus/bus.py", line 281, in start_service_by_name
    'su', (bus_name, flags)))
  File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 620, in call_blocking
    message, timeout)
DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name org.mpris.guayadeque was not provided by any .service files

```

And yes, G-Que is most definitely running.

You are not seeing anything like this?

And if not, how are you calling the cover art script?

Edit - Solved

Since I was starting G-Que on startup, I set the option in Preferences to start minimized. For whatever reason, Dbus does not see G-Que when started this way. I disabled starting it in minimized and reran the script and it worked perfectly.

---

### Post by VastOne on 2010-08-07
I marked my last one as solved, but I am not too sure yet.  It seems as if for whatever reason, dBus goes to sleep or just plain fails once in a while.  It may just be me as I am running on the cutting edge with some of the newer kernels, 2.6.35.RC5

Anyway, I was getting the same failures with the coverart script and the overall conkyguayadeque loading but failing to do anything at all, no data update.

So I found a command to restart dbus, and did just that, which all it does is basically logs you out and brings you back to the same state.

Once I did that, both the coverart and the conkyguayadeque scripts ran perfectly.

All the times I thought that conkyguayadeque was not working in my scripts was probably dbus taking a nap.

I do not know what causes it and it is completely random, except to say that if I stop the coverart script and restart it, that script finds dbus unavailable every time.

This is info for the masses just in case someone else runs into this

---

### Post by theLegend on 2010-08-08
> **VastOne said:**
> FYI -

I have set this in the template after reading threads from you other scripts and it works great and looks fantastic.

I have mine right under the Position field..

```
${execibar 1 conkyGuayadeque --datatype=PP}
```

I thought I'd show you my screenshot as you shown me yours. One is a full screen, the other a close up of the Guayadeque conky script

---

### Post by theLegend on 2010-08-08
I guess its my turn for Linux to feel sorry for me now! As you know I was having trouble with the embedded images which were in the pictures tab when editing tracks and the python script would not be able to retrieve the coverart, and would only retrieve coverart for tracks not edited with a picture and also tracks that did have the art embedded using Easytag but not showing in Guayadeque picture tab. That was a longer sentence than planned! I'll explain it simpler:

Track with no embedded image art - Works
Track with embedded image via Easytag and not Guayadeque - Works
Track with embedded image in Guayadeque - Didn't work

Notice the didn't work because it does now work! I rebooted my machine and the scripts are all working as said! Yay! Big thumbs up to Mr K, the best python script editor I know! (The fact he is the only one I know is irrelevant!)

---

### Post by VastOne on 2010-08-08
> **theLegend said:**
> I guess its my turn for Linux to feel sorry for me now! As you know I was having trouble with the embedded images which were in the pictures tab when editing tracks and the python script would not be able to retrieve the coverart, and would only retrieve coverart for tracks not edited with a picture and also tracks that did have the art embedded using Easytag but not showing in Guayadeque picture tab. That was a longer sentence than planned! I'll explain it simpler:

Track with no embedded image art - Works
Track with embedded image via Easytag and not Guayadeque - Works
Track with embedded image in Guayadeque - Didn't work

Notice the didn't work because it does now work! I rebooted my machine and the scripts are all working as said! Yay! Big thumbs up to Mr K, the best python script editor I know! (The fact he is the only one I know is irrelevant!)

ROFLMAO...

How are you loading the coverart script.

Send me a snippet of how you have it in your script.

---

### Post by theLegend on 2010-08-08
I've emailed you my script VastOne, hope you like.

On another note, for neatness sake Mr K, you might want to update the first page of this thread to show that the coverart parameter does now work! With a little help of your conkyguayadeque coverart python script.

Now if its not too much to ask, how about getting the lyrics for that track that have been saved in G-Que?:D

---

### Post by kaivalagi on 2010-08-08
> **theLegend said:**
> On another note, for neatness sake Mr K, you might want to update the first page of this thread to show that the coverart parameter does now work! With a little help of your conkyguayadeque coverart python script.

Now if its not too much to ask, how about getting the lyrics for that track that have been saved in G-Que?:D

Updated the first post...I haven't mentioned anything about the other script, can't be bothered right now...I'll possibly take a look at lyrics at some point, just not today. I'll need to know where it puts the lyrics data for a start, I am assuming it can be anywhere?...Sonata puts it into a file, one per artist/title combination...within ~/.lyrics/. There is no d-bus option for lyrics...

---

### Post by kaivalagi on 2010-08-08
[COLOR="Red"]**[SIZE="4"]UPDATE[/SIZE]**[/COLOR]

[LIST]
[*]Updated so can handle position and length past 60 minutes long, 1hr 5min 22secs will be shown as 65:22
[*]Fixed cover art (--datatype=CA) and status (--datatype=ST) 
[*]Added conkyGuayadeque-GetCoverart script to, on track change, copy the coverart to /tmp/guayadeque-coverart.jpg for use in conky (handles image files and embedded)
[*]Updated README
[/LIST]

New packages are now available from the ppa

---

### Post by VastOne on 2010-08-08
K

I posted this over in the Conky, but perhaps it is something you have seen:

Any reason why this

```
${image /tmp/guayadeque-coverart.jpg -p 220,0 -s 100x100}
```

would not update even though the jpg changes and the script that it runs in is updated every second?

It;s as if there is a cache that is created upon the first one and that cache is used instead of the actual change

Is there a variable I am missing?

---

### Post by VastOne on 2010-08-08
> **VastOne said:**
> K

I posted this over in the Conky, but perhaps it is something you have seen:

Any reason why this

```
${image /tmp/guayadeque-coverart.jpg -p 220,0 -s 100x100}
```

would not update even though the jpg changes and the script that it runs in is updated every second?

It;s as if there is a cache that is created upon the first one and that cache is used instead of the actual change

Is there a variable I am missing?

I resolved it

imlib_cache_size 0

This sets the image cache to nothing so there is never a cache

Now it works perfectly

---

### Post by kaivalagi on 2010-08-08
> **VastOne said:**
> I resolved it

imlib_cache_size 0

This sets the image cache to nothing so there is never a cache

Now it works perfectly

Good stuff, the handiest link ever for conky: [http://conky.sourceforge.net/documentation.html](http://conky.sourceforge.net/documentation.html) :D

Or you could have added an "-n" to the image variable options and then you can only do it for some images if you output lots ;)

edit: btw, why not save on posts and edit your latest if no-one has replied and the topic hasn't changed...just stick an "edit:" at the front so people know. I used to post like you have until a moderator on Arch linux forums told me to mend my ways :)

---

### Post by VastOne on 2010-08-08
> **kaivalagi said:**
> Good stuff, the handiest link ever for conky: [http://conky.sourceforge.net/documentation.html](http://conky.sourceforge.net/documentation.html) :D

Or you could have added an "-n" to the image variable options and then you can only do it for some images if you output lots ;)

Yes, thanks for that link because now I want to dig into how to place text into a specific area on within the box area like you can the images.

---

### Post by VastOne on 2010-08-08
> **kaivalagi said:**
> Good stuff, the handiest link ever for conky: [http://conky.sourceforge.net/documentation.html](http://conky.sourceforge.net/documentation.html) :D

Or you could have added an "-n" to the image variable options and then you can only do it for some images if you output lots ;)

edit: btw, why not save on posts and edit your latest if no-one has replied and the topic hasn't changed...just stick an "edit:" at the front so people know. I used to post like you have until a moderator on Arch linux forums told me to mend my ways :)

I normally do that all the time, I was just in a hurry cuz I was so excited....:p:p:p

---

### Post by kaivalagi on 2010-08-08
> **VastOne said:**
> I normally do that all the time, I was just in a hurry cuz I was so excited....:p:p:p

lol, just did it again.

Getting the conky bug proper now then....hours lost :lolflag:

> **VastOne said:**
> Yes, thanks for that link because now I want to dig into how to place text into a specific area on within the box area like you can the images.
offset, voffset and goto...

---

### Post by VastOne on 2010-08-08
> **kaivalagi said:**
> lol, just did it again.

Getting the conky bug proper now then....hours lost :lolflag:


offset, voffset and goto...

Got it bad got it bad got it bad for Conky...


Thanks for the hints, I was heading down that road....

---

### Post by kaivalagi on 2010-08-08
> **VastOne said:**
> Got it bad got it bad got it bad for Conky...
Thanks for the hints, I was heading down that road....

There is a gotcha though, if you use goto and offset to move output up, you will still be left with conky taking up all the space further down it would without them. This has confused a LOT of people in the past.

Have fun :)

btw, I am away from home next week until the weekend, so can't do any development...my work laptop is for windows development where the money comes from...I did try setting up a VM once but the company scans their machines for unlicensed and unwanted software, which got me in trouble before...

---

### Post by VastOne on 2010-08-08
> **kaivalagi said:**
> There is a gotcha though, if you use goto and offset to move output up, you will still be left with conky taking up all the space further down it would without them. This has confused a LOT of people in the past.

Have fun :)

btw, I am away from home next week until the weekend, so can't do any development...my work laptop is for windows development where the money comes from...I did try setting up a VM once but the company scans their machines for unlicensed and unwanted software, which got me in trouble before...

Thanks for that tidbit of info

I worked for 22 years as a Microsoft Consultant traveling the world implementing E-mail, AD, Security and Disaster Recovery plans and procedures. I use to call Bill G my pimp and until he began giving his money away I was not a fan at all even though I made a hell of a living.

I gave it up as I missed too much of my children's life, now I do the simple tasks of converting MS folks and their horribly mucked up computers to Linux for a flat fee.  They and I have never been happier.

Have fun on your trip and don't let the security scans catch you and ruin a great career.

I really appreciate all of your help and insights. Like Anonbeat, it is ppl like you 2 that really make a difference in the FOSS world.

Cheers!

---

### Post by theLegend on 2010-08-09
I've tried to update the conkyguayadeque via the PPA in update manager and then synaptic but I'm getting an error :

conkyguayadeque:
 Depends: guayadeque  but it is not installable

How do I resolve this?

I'm guessing its something to do with how I've installed guayadeque? I've installed it via SVN.

EDIT: Yep I can confirm its how I've installed it.... I'm going to have to work out how to reinstall without breaking everything! :)

I've managed to update the script now.....despite ubuntu getting upset about guayadeque not being able to be overwritten! :)

---

### Post by VastOne on 2010-08-09
> **theLegend said:**
> I've tried to update the conkyguayadeque via the PPA in update manager and then synaptic but I'm getting an error :

conkyguayadeque:
 Depends: guayadeque  but it is not installable

How do I resolve this?

I'm guessing its something to do with how I've installed guayadeque? I've installed it via SVN.

EDIT: Yep I can confirm its how I've installed it.... I'm going to have to work out how to reinstall without breaking everything! :)

I run via svn only and I had no issues running this

```
sudo apt-get update && sudo apt-get install conkyguayadeque
```

As long as you have done steps 1 & 2 on the first page, this should work.

---

### Post by theLegend on 2010-08-09
> **VastOne said:**
> I run via svn only and I had no issues running this

```
sudo apt-get update && sudo apt-get install conkyguayadeque
```

As long as you have done steps 1 & 2 on the first page, this should work.

Thats how I did it initially yep but I had trouble upgrading it, added the guayadeque repository, thought I already had it mind you.

On a different note, for information purposes, if you want nice looking stars in your ratings parameter, I've used this line (after downloading the font of course!)

```
${color3}${goto 36}Rating : ${goto 82}${font pizzadude stars:size=11}${color1}[--datatype=RT --ratingchar=t]
```

---

### Post by VastOne on 2010-08-09
> **theLegend said:**
> Thats how I did it initially yep but I had trouble upgrading it, added the guayadeque repository, thought I already had it mind you.

On a different note, for information purposes, if you want nice looking stars in your ratings parameter, I've used this line (after downloading the font of course!)

```
${color3}${goto 36}Rating : ${goto 82}${font pizzadude stars:size=11}${color1}[--datatype=RT --ratingchar=t]
```

So did you get it to upgrade then?

And thanks for the ratings stars, I do not use the rating function at all as a musician and music-man , I like it all on the same level

---

### Post by theLegend on 2010-08-09
> **VastOne said:**
> So did you get it to upgrade then?

And thanks for the ratings stars, I do not use the rating function at all as a musician and music-man , I like it all on the same level

Thats cool, that your perogative my man, I sometimes like to play all my favourite songs one after the other so it helps to filter it this way. I know there are labels but that's too long winded for me. Plus I like stars! :):KS

---

### Post by jasonpickles on 2010-08-09
So what's the code to get cover art to display? I'm relatively new to conky, and can't figure out how to get it to show.
I've put this ```
${image /tmp/guayadeque-coverart.jpg -p 220,0 -s 100x100}
```
in my conkyGuayadeque.template file, but nothing shows on the desktop.
I think my issue is what code to include to use the conkyGuayadeque-GetCoverart.py.
Thanks.

---

### Post by VastOne on 2010-08-09
Do you have it running?

Make sure G-Que is running and run this

```
/usr/bin/python /usr/share/conkyguayadeque/conkyGuayadeque-GetCoverart.py
```

It should work for you then.

If it does, you may want to use a startup for it like this, the one I use
```

#!/bin/sh
#sleep 50
/usr/bin/python /usr/share/conkyguayadeque/conkyGuayadeque-GetCoverart.py &
/usr/bin/conky -c ~/.conky??? -q -d


```

Of course replacing conky??? with your own.

Let me know if this works, if not we will look at what else may be wrong.

---

### Post by VastOne on 2010-08-09
> **jasonpickles said:**
> So what's the code to get cover art to display? I'm relatively new to conky, and can't figure out how to get it to show.
I've put this ```
${image /tmp/guayadeque-coverart.jpg -p 220,0 -s 100x100}
```
in my conkyGuayadeque.template file, but nothing shows on the desktop.
I think my issue is what code to include to use the conkyGuayadeque-GetCoverart.py.
Thanks.

Also change 

-p 220,0 

to 

-p 0,0  

This will place it at the very start and guarantee you to see it

---

### Post by theLegend on 2010-08-09
> **VastOne said:**
> Also change 

-p 220,0 

to 

-p 0,0  

This will place it at the very start and guarantee you to see it

I agree, I'm guessing your picture is being displayed outside your conky window..... If you're still having problems show us your conky script and we'll try and decipher it for you.

---

### Post by VastOne on 2010-08-09
I was testing why some files would not display the cover art and have determined that any ogg files will not display the cover art.

I validated this by converting an ogg that did not display to a mp3 and played it and the display worked perfectly.

I have quite a few ogg files, so a mass conversion would be ugly.

I think it might be a call from G-Que that needs to correct this but I will wait for K to return to verify.

Edit

It is not a fix for K or Anonbeat as it is a known issue with OGG and there seems to be no remedy in sight.

---

### Post by jasonpickles on 2010-08-09
Thank you fine gentlemen! It's all good now.

---

### Post by VastOne on 2010-08-09
> **jasonpickles said:**
> Thank you fine gentlemen! It's all good now.

You are most welcome, kind sir! 

Welcome to the club!

This is my latest if your interested... I had to do some strange editing to get it the way i wanted and if you see the code you will know what I mean.

It is the way of the Conky though....

---

### Post by theLegend on 2010-08-10
And here is my current conkyGque screenshot. Script and template are attached....

---

### Post by VastOne on 2010-08-10
> **theLegend said:**
> And here is my current conkyGque screenshot. Script and template are attached....

Very Slick...Costello Music, you have good taste as well.

---

### Post by theLegend on 2010-08-13
Having problems with the updating of the conkyguayadeque script...it keeps trying to install the ppa package of guayadeque but I have the svn version installed and it appears to be conflicting.
I run the conkyguayadeque script in terminal and its coming up with some ascii error.....

```
conkyGuayadeque --datatype=CAERROR: Issue calling the dbus service:'ascii' codec can't encode character u'\xb4' in position 31: ordinal not in range(128)

```

Any ideas? I don't want to remove my svn-version cos its easy to update manually.

---

### Post by VastOne on 2010-08-13
> **theLegend said:**
> Having problems with the updating of the conkyguayadeque script...it keeps trying to install the ppa package of guayadeque but I have the svn version installed and it appears to be conflicting.
I run the conkyguayadeque script in terminal and its coming up with some ascii error.....

```
conkyGuayadeque --datatype=CAERROR: Issue calling the dbus service:'ascii' codec can't encode character u'\xb4' in position 31: ordinal not in range(128)

```

Any ideas? I don't want to remove my svn-version cos its easy to update manually.

I just don't get this...I run the SVN and it installs fine, I do not think it is because of that...Lets take this to Chat if you want and go over all your G-Que setup and see if I can see where you differ from me.

---

### Post by kaivalagi on 2010-08-13
I added a dependency to guayadeque (non svn) when I added the necessary dependency to python-eyed3 for the getcoverart script...I'll remove the dependency to the main guayadeque in the new package released.

The error you are seeing will relate to accented characters in the returned output. Take a look through the app to see what the cover art path is, it might well explain things...

I may get time to look this weekend but I can't promise anything.

---

### Post by theLegend on 2010-08-13
> **kaivalagi said:**
> I added a dependency to guayadeque (non svn) when I added the necessary dependency to python-eyed3 for the getcoverart script...I'll remove the dependency to the main guayadeque in the new package released.

The error you are seeing will relate to accented characters in the returned output. Take a look through the app to see what the cover art path is, it might well explain things...

I may get time to look this weekend but I can't promise anything.

Yes its the dependancy of the main guayadeque is upsetting the synaptic when I 'update' the script. It reinstalls it fine but gets a little upset because the main guayadeque wasn't installed....and my problem was like you suggested but it wasn't an accented character but a * which appears before NSync on one of their albums...so it works fine with other albums so I'll just skip this for now! LOL

Thanks for your advice and excellent service once again!

---

### Post by VastOne on 2010-08-13
> **kaivalagi said:**
> I added a dependency to guayadeque (non svn) when I added the necessary dependency to python-eyed3 for the getcoverart script...I'll remove the dependency to the main guayadeque in the new package released.

The error you are seeing will relate to accented characters in the returned output. Take a look through the app to see what the cover art path is, it might well explain things...

I may get time to look this weekend but I can't promise anything.

Welcome back K!

---

### Post by kaivalagi on 2010-08-13
It's good to be back in the "land of the linux"...I've had a right stressful week dealing with java on windows servers (yuk)...

Running tomcat, mysql and java on windows is just wrong, but I am that scummy contractor that should only speak when spoken to ;)

---

### Post by VastOne on 2010-08-13
> **kaivalagi said:**
> It's good to be back in the "land of the linux"...I've had a right stressful week dealing with java on windows servers (yuk)...

Running tomcat, mysql and java on windows is just wrong, but I am that scummy contractor that should only speak when spoken to ;)

That is down right blasphemous to have that combo on a MS server.

The ROI on a low grade unix/linux box would pay for itself in a years time....

Amazing!!!

Glad that your brain did not rot dealing with the manure...

---

### Post by kaivalagi on 2010-08-13
What's worse is that they just spent a small fortune on a latest hardware to try and get better performance....should have put RH on the same hardware and saved a small fortune as well as getting decent vendor support....

I am just waiting for the day when directors realise that Microsoft everything is not good...until then I have to keep the linux evangelism restricted to people that understand.

---

### Post by VastOne on 2010-08-13
> **kaivalagi said:**
> What's worse is that they just spent a small fortune on a latest hardware to try and get better performance....should have put RH on the same hardware and saved a small fortune as well as getting decent vendor support....

I am just waiting for the day when directors realise that Microsoft everything is not good...until then I have to keep the linux evangelism restricted to people that understand.

The last job I was on as a contractor we are in the middle of the night doing a Active Directory upgrade and Exchange 2005 upgrade.

Right in the middle at the exact crucial point it keeps failing with a bizarre NON GOOGLE search result message.

So while the employees (I wont even say IT ppl) were scrambling around to get the tapes to back out of this, I calmly ask if they had MS support and of course they did not.

So, we called, they spent 850.00 US to find out that someone had loaded an obscure audio component (Made by MS) that in no way should ever be close to a Server.

So, the tech guy bumps me up 7 notches to a guy who has me tun this secret code that only MS and a certified MS person could know about.

Within seconds we were upgrading fine..

After that job, I quit the business because I could no longer take the inept way companies run their business and the fact that MS could continue to rape them for an obscure audio driver that should have just popped up as a service and said "SHUT ME OFF"~  Not that hard if you think about it....

Rant complete....

---

### Post by kaivalagi on 2010-08-13
lol, reminds me of a few screw ups in the past...too many people like to call themselves experts because they have installed a server at home, sounds like those type people to me!

---

### Post by theLegend on 2010-08-14
> **kaivalagi said:**
> lol, reminds me of a few screw ups in the past...too many people like to call themselves experts because they have installed a server at home, sounds like those type people to me!

Not that I don't appreciate your banter guys, but this is just a tad off-topic!!! LOL :)

---

### Post by kaivalagi on 2010-08-14
Post a relevant question then :P

Back on topic then :-k .....

What can I do to the script to stop the error you got? An asterisk is in the ascii char table so shouldn't have caused that problem...can you provide the full cover art path that didn't make it through?

edit: I think /xb4 would be related to this:
U+00B4	´	c2 b4	ACUTE ACCENT

[http://www.utf8-chartable.de/unicode-utf8-table.pl](http://www.utf8-chartable.de/unicode-utf8-table.pl)

@theLegend, can you try the attached py file with the coverart you had trouble with before? I want to see if the 'replace' options for unicode encoding stop errors from occurring...

---

### Post by VastOne on 2010-08-14
On Topic

Checksum value = yes

Regarding the lyrics, I have made two requests, one to osd-lyrics to add Guayadeque and one to eightbillion on the Conky thread to look at Guayadeque and add support.

I think one of those two will come through...

---

### Post by VastOne on 2010-08-14
bitrate Value BR now added to Guayadeque to send to dbus

Tested and not working


it is added from g-que as bitrate  

but does it need to be bitrate k/s?

Edit

Using dbus-monitor, I can see that

```
 )
      dict entry(
         string "bitrate"
         variant             int32 128
```

is definitely getting a return from G-Que now.

---

### Post by theLegend on 2010-08-14
> **kaivalagi said:**
> Post a relevant question then :P

Back on topic then :-k .....

What can I do to the script to stop the error you got? An asterisk is in the ascii char table so shouldn't have caused that problem...can you provide the full cover art path that didn't make it through?

edit: I think /xb4 would be related to this:
U+00B4	´	c2 b4	ACUTE ACCENT

[http://www.utf8-chartable.de/unicode-utf8-table.pl](http://www.utf8-chartable.de/unicode-utf8-table.pl)

@theLegend, can you try the attached py file with the coverart you had trouble with before? I want to see if the 'replace' options for unicode encoding stop errors from occurring...

Ok I'll try that script in a moment. In the meantime I thought I'd post my latest incarnation of the conky screenshot for Guayadeque.....

Actually, I've just remembered I renamed the album in question....I better put it back! :)

Getting this error now:

ERROR: Issue calling the dbus service:'ascii' codec can't encode character u'\xb4' in position 31: ordinal not in range(128)
Unknown

And its not because of the asterix cos I took that back out...maybe something to do with the coverart file?

PROBLEM SOLVED! Well more like problem worked out! The folder name for where the album was saved had a ' (apostrophe) at the start so I removed this and all is working well.

---

### Post by VastOne on 2010-08-14
> **theLegend said:**
> 

PROBLEM SOLVED! Well more like problem worked out! The folder name for where the album was saved had a ' (apostrophe) at the start so I removed this and all is working well.

Good Catch

Well done!

:popcorn:

---

### Post by Spike-X on 2010-08-15
Before I possibly waste a whole lot of time getting the cover art script to run...does it only work on embedded images? Most of my cover art is stored in the respective album folders as cover.jpg. Will that work?

---

### Post by VastOne on 2010-08-15
> **Spike-X said:**
> Before I possibly waste a whole lot of time getting the cover art script to run...does it only work on embedded images? Most of my cover art is stored in the respective album folders as cover.jpg. Will that work?

Yes.

I have several folders with their own jpg and they run the same way.

---

### Post by jasonpickles on 2010-08-15
Is there a way to remove/kill a conky script once a program exits.
For example, I made a script to load my conky script for Guayadeque, when the music program loads. But once I close Guayadeque, it still shows, and I would like to have it disappear.
Clear as mud?

---

### Post by VastOne on 2010-08-15
> **jasonpickles said:**
> Is there a way to remove/kill a conky script once a program exits.
For example, I made a script to load my conky script for Guayadeque, when the music program loads. But once I close Guayadeque, it still shows, and I would like to have it disappear.
Clear as mud?

What still shows?  The script or Guayadeque?

To kill a conky script type 


```
ps -e | grep 'conky'
```

in terminal you will see something like this

```
2051 ?        00:01:32 conky
13680 ?        00:02:19 conky
14977 ?        00:00:09 conky
14978 ?        00:00:47 conky
```

Then you would kill it by

```
kill 13680
```  

or whatever number(s) you see

or 

you could type 

```
sudo killall -v conky
```

And that will kill all conky running

---

### Post by jasonpickles on 2010-08-15
> **VastOne said:**
> What still shows?  The script or Guayadeque?

To kill a conky script type 


```
ps -e | grep 'conky'
```

in terminal you will see something like this

```
2051 ?        00:01:32 conky
13680 ?        00:02:19 conky
14977 ?        00:00:09 conky
14978 ?        00:00:47 conky
```

Then you would kill it by

```
kill 13680
```  

or whatever number(s) you see

or 

you could type 

```
sudo killall -v conky
```

And that will kill all conky running
Well, the situation is this. I have a two conky scripts that load once compiz kicks in. These scripts display weather info and system info. I created a scripts to launch a third script to display the guayadeque info when the music play loads. What I would like to do, is have that guayadeque conky script to be killed once the music player exits, while still having my weather and system info conky scrits still running.
Clearer and cleaner mud? lol.

---

### Post by VastOne on 2010-08-15
> **jasonpickles said:**
> Well, the situation is this. I have a two conky scripts that load once compiz kicks in. These scripts display weather info and system info. I created a scripts to launch a third script to display the guayadeque info when the music play loads. What I would like to do, is have that guayadeque conky script to be killed once the music player exits, while still having my weather and system info conky scrits still running.
Clearer and cleaner mud? lol.

The easiest thing would be to not start G-Que in that script, just start it outside of it and when you close it it wont matter.

---

### Post by jasonpickles on 2010-08-15
> **VastOne said:**
> The easiest thing would be to not start G-Que in that script, just start it outside of it and when you close it it wont matter.
Boo-urns. Not exactly what I was hoping for an answer, but I appreciate the help.

---

### Post by Spike-X on 2010-08-15
> **VastOne said:**
> Yes.

I have several folders with their own jpg and they run the same way.
Good to know, thanks!

*rolls up sleeves*

---

### Post by kaivalagi on 2010-08-15
> **jasonpickles said:**
> Boo-urns. Not exactly what I was hoping for an answer, but I appreciate the help.

Not a complete solution but you can store the pid of a process on startup and then you have the ability to stop a specific app via the pid too

e.g. to start

```
conky -c /the/gque/conkyrc &
pid=$!
echo $pid > /tmp/gqueconky.pid

guayadeque &
pid=$!
echo $pid > /tmp/gque.pid
```

to stop:

```
if [ -s  /tmp/gqueconky.pid ] ;then	
	until ! read pid
		do
		kill "${pid}"
		done < /tmp/gqueconky.pid
		rm -f /tmp/gqueconky.pid			
fi

if [ -s  /tmp/gque.pid ] ;then	
	until ! read pid
		do
		kill "${pid}"
		done < /tmp/gque.pid
		rm -f /tmp/gque.pid			
fi
```

Hope that helps some, you just need to figure out the bits in between...and how to trigger conky killing off gque stopping

The other option is to hide the entire conky output for qgue when it isn't running, conky has a if_running variable you can use. 

```
if_running (process) - if PROCESS is running, display everything $if_running and the matching $endif. This uses the ``pidof'' command, so the -x switch is also supported.
```

Check out: conky.sourceforge.net/variables.html

Cheers

---

### Post by kaivalagi on 2010-08-15
Looks like I finally got launchpad working for me now so I can build packages through a Ubuntu VM :) I forgot about the OpenGPG key needed for the VM to be able to upload source packages for a build....doh
Expect a new package soon with bitrate support :)
edit: 2.02 version of the package published, changes can be found here: [https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkyguayadeque_2.02_source.changes](https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkyguayadeque_2.02_source.changes)

---

### Post by VastOne on 2010-08-15
> **kaivalagi said:**
> Looks like I finally got launchpad working for me now so I can build packages through a Ubuntu VM :) I forgot about the OpenGPG key needed for the VM to be able to upload source packages for a build....doh
Expect a new package soon with bitrate support :)
edit: 2.02 version of the package published, changes can be found here: [https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkyguayadeque_2.02_source.changes](https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkyguayadeque_2.02_source.changes)

Updated and working perfectly.... :guitar:

Package Complete.... Brilliant...

Do you have anything setup for donations?

---

### Post by kaivalagi on 2010-08-15
> **VastOne said:**
> Updated and working perfectly....
Good stuff...any more suggestions for features let me know

> **VastOne said:**
> Do you have anything setup for donations?

I setup a donations link on my site but not sure it if works as I have recieved zero donations as yet :)
kaivalagi.com link below....reminds me I need to actually add some content ;)

---

### Post by VastOne on 2010-08-15
> **kaivalagi said:**
> I setup a donations link on my site but not sure it if works as I have recieved zero donations as yet :)
kaivalagi.com link below.

(Turn on Scottish Accent) 

We'll Have to remedy that now, won't we...

---

### Post by VastOne on 2010-08-15
> **kaivalagi said:**
> Or you could have added an "-n" to the image variable options and then you can only do it for some images if you output lots ;)

K,

Would you expand on this please.  Specifically what the -n option is and where to place it. I tried a few and could not get it to work and I am pretty sure I have the syntax wrong.

I am still having a very strange issue with a tiny few of my covers. In G-Que and in dBus, a cover image I have supplied comes across as it should. But from out of what appears to be no where another image is pulled to the /tmp area by the script.

The strange part is that I do a complete scan for cover * jpg and look at anything that has those variables in it and there are none anywhere on my machine, but I still get the same image every time.

Again, this is only on 2-3 artists, but it is annoying in that I cannot trace what it is and why it is happening.

Thanks

---

### Post by kaivalagi on 2010-08-16
I think you have the image cache setting in the conkyrc above the TEXT line which is fine, but it means that the cache options are applied to every image you use...maybe some images you use dont change so this would be a waste on system resources.

Where you would normally have an image tag like this:

```
${image /path/to/image.jpg -p 0,0 -s 64,64}
```

To have image specific caching removed, you would have this:

```
${image /path/to/image.jpg -p 0,0 -s 64,64 -n}
```

You issue you just posted though looks like something else anyway, if caching is turned off for all content whatever jytre file image is should be displayed. I wonder if you are getting an image path back from GQue/Coverart script that differs from what GQue is showing? Try checking the image based on the path the tmp image is copied from (you'll see the source file path output in the terminal by the script on track change) against what GQue is showing.

Cheers

---

### Post by sausageandeggs on 2010-08-16
> **jasonpickles said:**
> Is there a way to remove/kill a conky script once a program exits.
For example, I made a script to load my conky script for Guayadeque, when the music program loads. But once I close Guayadeque, it still shows, and I would like to have it disappear.
Clear as mud?
This is my (hackish) way of doing this, just in case its of any use to you

This starts gque, gives you 30 seconds to pick a track to play b4 starting the coverart script and will then kill it when gq quits. I have music info built into my main conky but it should be easy to adapt this to your needs
```

#!/bin/bash

guayadeque &
sleep 30
/usr/bin/conkyGuayadeque-GetCoverart &

conkgq=$(pgrep guayadeque)

while [[ ! -z $conkgq ]];do
    sleep 30
    conkgq=$(pgrep guayadeque)
done

pkill -f /usr/share/conkyguayadeque/conkyGuayadeque-GetCoverart.py

```

---

### Post by VastOne on 2010-08-16
Hmmm...Quoting seems to be broken atm and I sense a malfunction with the forums database farm..

Anyway, K. 

I resolved my issues with the cover art images.  I did not know a file could save multiple cover images at one time and these few I had did in fact have 2 images.  

Thanks

Edit - 

Anonbeat also added a nice optional feature to G-Que that eliminates G-Que from searching the directory for cover art, thus pulling all cover art from the embedded files. This is perfect for me because I do not use cover art but instead embed images in each file. FYI

---

### Post by jasonpickles on 2010-08-17
> **sausageandeggs said:**
> This is my (hackish) way of doing this, just in case its of any use to you

This starts gque, gives you 30 seconds to pick a track to play b4 starting the coverart script and will then kill it when gq quits. I have music info built into my main conky but it should be easy to adapt this to your needs
```

#!/bin/bash

guayadeque &
sleep 30
/usr/bin/conkyGuayadeque-GetCoverart &

conkgq=$(pgrep guayadeque)

while [[ ! -z $conkgq ]];do
    sleep 30
    conkgq=$(pgrep guayadeque)
done

pkill -f /usr/share/conkyguayadeque/conkyGuayadeque-GetCoverart.py

```

Cool. I'll look into adapting this. Thanks!

---

### Post by VastOne on 2010-08-18
> **sausageandeggs said:**
> This is my (hackish) way of doing this, just in case its of any use to you

This starts gque, gives you 30 seconds to pick a track to play b4 starting the coverart script and will then kill it when gq quits. I have music info built into my main conky but it should be easy to adapt this to your needs
```

#!/bin/bash

guayadeque &
sleep 30
/usr/bin/conkyGuayadeque-GetCoverart &

conkgq=$(pgrep guayadeque)

while [[ ! -z $conkgq ]];do
    sleep 30
    conkgq=$(pgrep guayadeque)
done

pkill -f /usr/share/conkyguayadeque/conkyGuayadeque-GetCoverart.py

```

Very nice ... I have incorporated this into mine and appreciate the work on it, it works great for me was something I needed.

---

### Post by camaron1 on 2010-08-18
Hello,
I've tried to give the script a go installing from PPA and when I try to run it from terminal this is what I get:

```
jorge@jorge-lucid:~$ conkyGuayadeque
ERROR: Issue calling the dbus service:'ascii' codec can't encode character u'\xe1' in position 27: ordinal not in range(128)
```

Any ideas?

Thanks in advance

---

### Post by VastOne on 2010-08-18
> **camaron1 said:**
> Hello,
I've tried to give the script a go installing from PPA and when I try to run it from terminal this is what I get:

```
jorge@jorge-lucid:~$ conkyGuayadeque
ERROR: Issue calling the dbus service:'ascii' codec can't encode character u'\xe1' in position 27: ordinal not in range(128)
```

Any ideas?

Thanks in advance

look [_[COLOR="Red"]here[/COLOR]_]("http://ubuntuforums.org/showpost.php?p=9720714&postcount=114")

this part of it

> **theLegend said:**
> PROBLEM SOLVED! Well more like problem worked out! The folder name for where the album was saved had a ' (apostrophe) at the start so I removed this and all is working well.

---

### Post by kaivalagi on 2010-08-18
> **camaron1 said:**
> Hello,
I've tried to give the script a go installing from PPA and when I try to run it from terminal this is what I get:

```
jorge@jorge-lucid:~$ conkyGuayadeque
ERROR: Issue calling the dbus service:'ascii' codec can't encode character u'\xe1' in position 27: ordinal not in range(128)
```

Any ideas?

Thanks in advance

Your calling conkyGuayadeque script without any options which means it will default to --datatype=TI or the track title.
i.e.
```
  -d DATATYPE, --datatype=DATATYPE
                        **[default: TI]** The data type options are: ST (status),
                        CA (coverart), TI (title), AL (album), AR (artist), GE
                        (genre), YR (year), TN (track number), FN (file name),
                        BR (bitrate k/s), LE (length), PP (current position in
                        percent), PT (current position in time), VO (volume),
                        RT (rating). Not applicable at command line when using
                        templates.

```

I'd say the track title has some accented characters that are causing issue with output. Can you tell me what the track title is please?

Although what VastOne has suggested is not quite on the button it does relate to the same issue, characters trying to be output are not within the standard ascii character set.

---

### Post by camaron1 on 2010-08-18
Thanks to Kaivalagi and Vastone for the sugestions. I won't be able to do anything till tomorrow evening but once i do i'll get back to you. 

I've been having general issues across ubuntu with character recognition. As i'm spanish i use at least a couple of characters non-existent in english. What annoys me is that I never had this kind of problems before and don't know why it is happening now. 

Thanks for you help

---

### Post by VastOne on 2010-08-19
K

Do you use python 2 or 3?

I want to learn and am wondering which to start with. I guess my major concern is libraries if I start in 3 but am wondering your thoughts.

---

### Post by kaivalagi on 2010-08-19
> **VastOne said:**
> K

Do you use python 2 or 3?

I want to learn and am wondering which to start with. I guess my major concern is libraries if I start in 3 but am wondering your thoughts.

I use 2....3 has lots of improvements but I just haven't gotten into it yet...also worth noting is that python 3 is not available by default on lots of systems but python 2.6+ is...

The [http://docs.python.org/](http://docs.python.org/) site is THE best documentation around and will suffice once you get to grips with the basics of programming. If you learn best by example you may well get by just reading there...

---

### Post by VastOne on 2010-08-19
> **kaivalagi said:**
> I use 2....3 has lots of improvements but I just haven't gotten into it yet...also worth noting is that python 3 is not available by default on lots of systems but python 2.6+ is...

The [http://docs.python.org/](http://docs.python.org/) site is THE best documentation around and will suffice once you get to grips with the basics of programming. If you learn best by example you may well get by just reading there...

Thank you kind sir!

---

### Post by theLegend on 2010-08-24
Do you have any advice on how to take the image that is taken from the cover using your script and convert it into an image that has its brightness / contrast changed so that I can have the song info overlay on top of it and make it clearer. I know I could take the image and load it into GIMP and change the image but I was thinking of doing it automatedly (is that a proper word?). I thought I'd might try ImageMagick as a cli command or something?

---

### Post by kaivalagi on 2010-08-25
> **theLegend said:**
> Do you have any advice on how to take the image that is taken from the cover using your script and convert it into an image that has its brightness / contrast changed so that I can have the song info overlay on top of it and make it clearer. I know I could take the image and load it into GIMP and change the image but I was thinking of doing it automatedly (is that a proper word?). I thought I'd might try ImageMagick as a cli command or something?

How about creating a semi transparent png (1x1 pixels) and trying to load it using $image in conky after the coverart is loaded, and have it sit over the top? Not sure if it would work but it's worth a shot!

If you knew python you could have the getcoverart script manipulating the image as you could do with imagemagick for example. The python imaging library can do this stuff fairly easily, I've done it before with my gtk-desktop-info app (see sig).

The problem with using ImageMagick is when do you know it needs to do something, the image is replaced on track change in python...but using the same named file.

---

### Post by VastOne on 2010-08-26
K,

When you get a chance will you update the first page here re the Bit/Rate fix is now in?


Thanks.

---

### Post by kaivalagi on 2010-08-27
> **VastOne said:**
> K,
When you get a chance will you update the first page here re the Bit/Rate fix is now in?
Thanks.

Done, no red in sight ;)

---

### Post by kaivalagi on 2010-08-30
**[COLOR=Green][SIZE=4]UPDATE[/SIZE][/COLOR]**

Changes as follows:
[LIST]
[*]Added --secondsoutput / -S option to output time in seconds
[/LIST]
 
Package changes can be seen here:  [https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkyguayadeque_2.03_source.changes](https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkyguayadeque_2.03_source.changes)

The apt packages should be available shortly

Cheers

---

### Post by VastOne on 2010-08-30
> **kaivalagi said:**
> Done, no red in sight ;)

Thank you!

> **kaivalagi said:**
> **[COLOR=Green][SIZE=4]UPDATE[/SIZE][/COLOR]**

Changes as follows:
[LIST]
[*]Added --secondsoutput / -S option to output time in seconds
[/LIST]
 
Package changes can be seen here:  [https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkyguayadeque_2.03_source.changes](https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkyguayadeque_2.03_source.changes)

The apt packages should be available shortly

Cheers

apt package there and I am updated via apt.

Cheers

---

### Post by jpope on 2010-09-11
First I want to say thanks to kaivalagi for this script. Here is my current setup:
[[IMG]http://imgur.com/HIcEb.png[/IMG]](http://imgur.com/HIcEb.png)

The only issue that I am having, and maybe I've missed it throughout this thread, is the script doesn't find the covers when playing ogg files. I used Easytag to update the tags and add the coverart. Is there anything else I need to check?

Thanks.

---

### Post by VastOne on 2010-09-11
> **jpope said:**
> First I want to say thanks to kaivalagi for this script. Here is my current setup:
[[IMG]http://imgur.com/HIcEb.png[/IMG]](http://imgur.com/HIcEb.png)

The only issue that I am having, and maybe I've missed it throughout this thread, is the script doesn't find the covers when playing ogg files. I used Easytag to update the tags and add the coverart. Is there anything else I need to check?

Thanks.

It is an issue with ogg and not the script. For whatever reasons well documented on the web, ogg does not pass the covers. I ran into this and converted all my ogg files.

---

### Post by _Toshi_ on 2010-09-21
Thanks for the scrip it works great.

I'm trying to write a Guayadeque plugin for AWN and I'd like to use your album art script if you don't mind.

The script seems simple enough, but I've been wondering about the getCoverartPath function.

When is the arturl property set? It seems that all my images are being read from ID3 tag and I'd like to test with the other method as well.

---

### Post by kaivalagi on 2010-09-23
> **_Toshi_ said:**
> Thanks for the scrip it works great.

I'm trying to write a Guayadeque plugin for AWN and I'd like to use your album art script if you don't mind.

The script seems simple enough, but I've been wondering about the getCoverartPath function.

When is the arturl property set? It seems that all my images are being read from ID3 tag and I'd like to test with the other method as well.

Sounds like a question for Anonbeat, the Guayadeque author?

---

### Post by anonbeat on 2010-09-24
> **_Toshi_ said:**
> Thanks for the scrip it works great.

I'm trying to write a Guayadeque plugin for AWN and I'd like to use your album art script if you don't mind.

The script seems simple enough, but I've been wondering about the getCoverartPath function.

When is the arturl property set? It seems that all my images are being read from ID3 tag and I'd like to test with the other method as well.

> **kaivalagi said:**
> Sounds like a question for Anonbeat, the Guayadeque author?

The mpris GetMetadata method of the Player interface will contains the current track metadata. The entry 'arturl' will give you the file path to the cover art

---

### Post by kaivalagi on 2010-09-24
> **anonbeat said:**
> The mpris GetMetadata method of the Player interface will contains the current track metadata. The entry 'arturl' will give you the file path to the cover art

Thanks :)

---

### Post by _Toshi_ on 2010-09-26
I see.

What I meant was that there is no arturl entry returned by the GetMetadata method. All my cover art is stored in the tags themselves. So what I'm asking is, how do I tag my files to use an external file with a arturl property rather than saving the images directly embeded in the ID3 tag?

---

### Post by kaivalagi on 2010-09-26
> **_Toshi_ said:**
> I see.

What I meant was that there is no arturl entry returned by the GetMetadata method. All my cover art is stored in the tags themselves. So what I'm asking is, how do I tag my files to use an external file with a arturl property rather than saving the images directly embeded in the ID3 tag?

I think the standard thing is to have a "folder.jpg" file or similar in the directory alongside the mp3's or similar? Most players pick up on that I think...if not that they'll tend to fetch the artwork on the fly using online search facilities

The getcoverart python script included in this threads package can also grab the image from the id3 tags if stored that way...e.g.

```
    def getCoverartImage(self,savepath):

        # get file apth
        if "location" in self.props:
            location = self.props["location"]
        
        srcfilepath = location.replace("file://","").replace("%20"," ")
        dstfolder = os.path.dirname(savepath) 
        dstfile = savepath.replace(os.path.dirname(savepath)+"/","")
        
        tag = eyeD3.Tag()
        
        if os.path.isfile(srcfilepath):
            if os.path.splitext(srcfilepath)[1] == ".mp3":
                # Extract picture
                try:
                    tag.link(srcfilepath)
                    for image in tag.getImages():
                        image.writeFile(dstfolder, dstfile)
                        return savepath
                except:
                    print "Unable to extract image for: " + srcfilepath
                    traceback.print_exc()
        return ""
```

---

### Post by VastOne on 2010-09-26
K, 

I posted [[COLOR="Red"]_this_[/COLOR]]("http://community.wikidot.com/forum/t-270086/theory-question-in-getting-a-python-script-to-run") on a forum with an intriguing idea (in my mind anyway).. No need for anything from you but would like to hear your take on it.

T

---

### Post by kaivalagi on 2010-09-27
> **VastOne said:**
> K, 

I posted [[COLOR="Red"]_this_[/COLOR]]("http://community.wikidot.com/forum/t-270086/theory-question-in-getting-a-python-script-to-run") on a forum with an intriguing idea (in my mind anyway).. No need for anything from you but would like to hear your take on it.

T

Nice idea, the only issue I see is that you want something to run on a PC that is hosted on a website, this screams security issues, but if that was explained and the user was willing then it could work.

In my mind you would need this sequence of events (but there may be more suitable means?):
[LIST=1]
[*]On site, click a button
[*]Site generates script for sownload, containing the user credentials for the upload
[*]script downloaded and started on the client
[*]script fetches data from guayadeque then uploads to site using credentials
[*]site polls for new uploads, finds this one and does something with it
[/LIST]

It is not a simple thing to do though, and for what you want it, to me, seems a lot for very little

---

### Post by _Toshi_ on 2010-09-27
> **VastOne said:**
> K, 

I posted [[COLOR="Red"]_this_[/COLOR]]("http://community.wikidot.com/forum/t-270086/theory-question-in-getting-a-python-script-to-run") on a forum with an intriguing idea (in my mind anyway).. No need for anything from you but would like to hear your take on it.

T
Wouldn't it be easier to use some of the scrobbling functionality that's arleady built into Guayadeque? Guayadeque supports scrobbling with Last.fm and Libre.fm. You could write a server side script that queries the last.fm API and returns recently played tracks and such.

Of course a user would need a last.fm account and have it set up in Guayadeque, but it solves a number of problems. Users do not have to run an additional script. Users are probably more likely to trust the player's built in scrobbling than the additional script. You wouldn't have to query the script directly from a web page. You wouldn't have to save any information on your own server. It also allows you to report from other players.

---

### Post by VastOne on 2010-09-27
> **kaivalagi said:**
> Nice idea, the only issue I see is that you want something to run on a PC that is hosted on a website, this screams security issues, but if that was explained and the user was willing then it could work.

In my mind you would need this sequence of events (but there may be more suitable means?):
[LIST=1]
[*]On site, click a button
[*]Site generates script for sownload, containing the user credentials for the upload
[*]script downloaded and started on the client
[*]script fetches data from guayadeque then uploads to site using credentials
[*]site polls for new uploads, finds this one and does something with it
[/LIST]

It is not a simple thing to do though, and for what you want it, to me, seems a lot for very little

> **_Toshi_ said:**
> Wouldn't it be easier to use some of the scrobbling functionality that's arleady built into Guayadeque? Guayadeque supports scrobbling with Last.fm and Libre.fm. You could write a server side script that queries the last.fm API and returns recently played tracks and such.

Of course a user would need a last.fm account and have it set up in Guayadeque, but it solves a number of problems. Users do not have to run an additional script. Users are probably more likely to trust the player's built in scrobbling than the additional script. You wouldn't have to query the script directly from a web page. You wouldn't have to save any information on your own server. It also allows you to report from other players.

Thank you both for your thoughts on this, it is exactly the input I was looking for.  Security is not as much of an issue in relative terms because the credentials would already be established by the user in joining the the [_[COLOR="Red"]Guayadeque wiki[/COLOR]_]("http://guayadeque.wikidot.com/start"). I would really like to show more of the Conky Guayadeque setup on the wiki but this may be more than it is worth.

Thanks

---

### Post by kaivalagi on 2010-09-27
@_Toshi - Much better idea, would not be player specific either...all the players I've used I have always had scrobbling setup

---

### Post by rotwang888 on 2010-09-28
Howdy.  Sorry if I'm missing something, but I'd like to try installing via tar.gz on Fedora, but all the packages on the launchpad page have Ubuntu release names. So, er, which one do I want?  Thanks.

---

### Post by kaivalagi on 2010-09-29
> **rotwang888 said:**
> Howdy.  Sorry if I'm missing something, but I'd like to try installing via tar.gz on Fedora, but all the packages on the launchpad page have Ubuntu release names. So, er, which one do I want?  Thanks.
Shouldn't matter which ubu version so long as the package version number is the latest one i.e. what's current. All the various packages for each ubuntu version essentially have the same contents as it's written in python so I can do that :)

---

### Post by _Toshi_ on 2010-10-04
Just a bit of feedback to my own question.

It seems Guayadeque only recognises pictures stored as 'cover.jpg' as cover art for files in the same directory. This will set 'arturl' in the dictionary returned by GetMetadata.

---

### Post by kaivalagi on 2010-10-04
> **_Toshi_ said:**
> Just a bit of feedback to my own question.

It seems Guayadeque only recognises pictures stored as 'cover.jpg' as cover art for files in the same directory. This will set 'arturl' in the dictionary returned by GetMetadata.

Sounds like Guayadeque ought to expand upon this a little? Either with a user customisable delimited list of file name patterns (preferred) or atleast adding folder.jpg and other similar well used conventions...have you made a request? Anonbeat is one of the better developers out there that will listen to sensible requests ;)
I would put a request in but I don;t use the app, I'm an MPD user myself, I just like supporting multiple apps if I can that's all

---

### Post by _Toshi_ on 2010-10-04
> **kaivalagi said:**
> Sounds like Guayadeque ought to expand upon this a little? Either with a user customisable delimited list of file name patterns (preferred) or atleast adding folder.jpg and other similar well used conventions...have you made a request? Anonbeat is one of the better developers out there that will listen to sensible requests ;)
I would put a request in but I don;t use the app, I'm an MPD user myself, I just like supporting multiple apps if I can that's all

Well it's not a feature I use much myself. I like writing the images to the tags. I was just curious so I could test my plugin.

---

### Post by kaivalagi on 2010-10-25
**[COLOR=Red][SIZE=4]UPDATE[/SIZE][/COLOR]**

Updates as follows:
[LIST]
[*]Updated the /usr/bin/ script to use the python2 sym link instead of python as Python 3 is either here (Arch) or coming (Ubuntu)
[*]Updated to provide a copy of coverart files in a custom path to avoid file naming issues. The file where coverart gets copied to when using the --datatype=CA option is determined by the -c/--coverartpath option, note that if this option is set to an empty string i.e. "" the original file path is provided for the coverart path. The default path is /tmp/cover.
[/LIST]

Package changes can be seen here:  [https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkyguayadeque_2.04_source.changes](https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkyguayadeque_2.04_source.changes)

The apt packages should be available soon

Cheers

**[COLOR="Red"][SIZE="3"]Note For 10.10 Users[/SIZE][/COLOR]**
I do beleive that Ubuntu 10.10 has a bug not having the python2 symbolic link, all other distro's I've used including previous versions of Ubuntu do have a python2 sym link...chances are it's been forgotten about in the hurry to rollout 10.10....

To fix things so the script can work as it is supposed to post the latest update just add a symbolic link in for python2 like this:
```
sudo ln -s /usr/bin/python2.6 /usr/bin/python2
```

---

### Post by VastOne on 2010-10-25
> **kaivalagi said:**
> **[COLOR=Red][SIZE=4]UPDATE[/SIZE][/COLOR]**



**[COLOR="Red"][SIZE="3"]Note For 10.10 Users[/SIZE][/COLOR]**
I do beleive that Ubuntu 10.10 has a bug not having the python2 symbolic link, all other distro's I've used including previous versions of Ubuntu do have a python2 sym link...chances are it's been forgotten about in the hurry to rollout 10.10....

To fix things so the script can work as it is supposed to post the latest update just add a symbolic link in for python2 like this:
```
sudo ln -s /usr/bin/python2.6 /usr/bin/python2
```

Thanks K for posting this sym link fix so fast

I was scurrying around like crazy trying to find what was broke on my machine and then I checked back here and you had the Sym Link fix...

I really appreciate it...

---

### Post by kaivalagi on 2010-10-25
> **VastOne said:**
> Thanks K for posting this sym link fix so fast

I was scurrying around like crazy trying to find what was broke on my machine and then I checked back here and you had the Sym Link fix...

I really appreciate it...

No worries, it's just a shame I take action to fix the scripts for the future and they break on the latest Ubuntu version, I was testing with 10.04 LTS...like mentioned I think the release team forgot the sym links that are normally there and as Python 3 is getting rolled out all over they're even more important right now...

Imagine Arch and host of other distros go from using 2.7 to 3.1 for the standard /usr/bin/python sym link (note Ubuntu is still using 2.6...) then lots of applications break...so application developers either upgrade their code for Python 3 (this takes a good deal of time) or start using /usr/bin/python2 sym links (quick and easy)...but wait a minute the most used Linux distro is missing what everyone else and it's older versions had......hence me thinking it's a balls up by Ubuntu!

---

### Post by EdwardR on 2010-11-17
First of all - huge thanks to kaivalagi for your conky scripts.  I have conkyForecast and conkyGuayadeque running and I love them!

The other day I ripped a cd with an accented letter in the album name.  When I played it, the artist, track, album and other info in conky went blank and the cover art remained showing the previous album.  When I switched to a track from a different album, all the info and cover art were updated.  Then I tried another album where the artist's name had an accented letter but there were no accents in the album or track names.  Again, the fields in conky went blank and the cover art did not update.  So I edited the tags for the artist and removed the accented letter and when I played it, everything displayed correctly in conky.

So it looks like the conkyGuayadeque script does not like accented letters.

thanks

---

### Post by kaivalagi on 2010-11-18
Seems to work for me if I insert an accented char (in this case ó) into the artist name...I get that output from the script fine.

Can you try running the conkyGuayadeque command in the terminal to make sure it is/isn't the script...best running a template based command...an example would be...

test template (/path/to/template/conkyGuayadeque.template):
```
${goto 32}${color3}Status:${color1}[--datatype=ST]
${goto 32}${color3}Artist:${color1}[--datatype=AR]
${goto 32}${color3}Album:${color1}[--datatype=AL]
${goto 32}${color3}Title:${color1}[--datatype=TI]
${goto 32}${color3}Position:${color1}[--datatype=PT]/[--datatype=LE] - [--datatype=PP]%
${goto 32}${color3}Rating:${color1}[--datatype=RT]
${goto 32}${color3}Volume:${color1}[--datatype=VO]
${goto 32}${color3}Bitrate:${color1}[--datatype=BR]
${goto 32}${color3}CoverArt:${image [--datatype=CA] -p 36,400 -s 90x82 -n}
```

test command:
```
conkyGuayadeque --template=/path/to/template/conkyGuayadeque.template
```

If it works then it will be a conky thing, if it doesn't work please give me a list of the tag values for the mp3 so I can try and reproduce the issue

I get output like this:
```
]$ conkyGuayadeque --template=/path/to/template/conkyGuayadeque.template
${goto 32}${color3}Status:${color1}Playing
${goto 32}${color3}Artist:${color1}BadBoy**[COLOR="Red"]ó[/COLOR]**Bounce
${goto 32}${color3}Album:${color1}Misc
${goto 32}${color3}Title:${color1}BadBoy**[COLOR="red"]ô[/COLOR]**Bounce
${goto 32}${color3}Position:${color1}2:21/39:39 - 5%
${goto 32}${color3}Rating:${color1}Unknown
${goto 32}${color3}Volume:${color1}0
${goto 32}${color3}Bitrate:${color1}128
${goto 32}${color3}CoverArt:${image  -p 36,400 -s 90x82 -n}


```
Cheers

---

### Post by EdwardR on 2010-11-19
Thanks!  I'm tied up the next couple of days with work and travel, but I will try it early next week and report back.

---

### Post by kaivalagi on 2010-11-19
> **EdwardR said:**
> Thanks!  I'm tied up the next couple of days with work and travel, but I will try it early next week and report back.

Sounds a lot like my life at the moment! Will be me Sunday evening onwards :)

---

### Post by kaivalagi on 2010-11-21
**[COLOR=Purple][SIZE=4]UPDATE[/SIZE][/COLOR]**

Updates as follows:
[LIST]
[*]Updated the /usr/bin/ script to dynamically call the available python exec as /usr/bin/python is linked to Python 3 (Arch) or will be at some point (Ubuntu)
[/LIST]

Package changes can be seen here:  [https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkyguayadeque_2.05_source.changes](https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkyguayadeque_2.05_source.changes)

The apt packages should be available soon

---

### Post by EdwardR on 2010-11-22
OK here's what I get when running the command from a terminal.  When playing a track without any accents I get good results, e.g.

```
${goto 32}${color3}Status:${color1}Playing
${goto 32}${color3}Artist:${color1}Men at Work
${goto 32}${color3}Album:${color1}Business as Usual
${goto 32}${color3}Title:${color1}Who Can It Be Now?
${goto 32}${color3}Position:${color1}0:03/3:28 - 1%
${goto 32}${color3}Rating:${color1}Unknown
${goto 32}${color3}Volume:${color1}96
${goto 32}${color3}Bitrate:${color1}256
${goto 32}${color3}CoverArt:${image /tmp/cover -p 36,400 -s 90x82 -n}

```When playing a track with an accent in the album name:

```
ERROR: Issue calling the dbus service:'ascii' codec can't encode character u'\xf1' in position 47: ordinal not in range(128)
ERROR: Issue calling the dbus service:'ascii' codec can't encode character u'\xf1' in position 47: ordinal not in range(128)
ERROR: Issue calling the dbus service:'ascii' codec can't encode character u'\xf1' in position 47: ordinal not in range(128)
ERROR: Issue calling the dbus service:'ascii' codec can't encode character u'\xf1' in position 47: ordinal not in range(128)
ERROR: Issue calling the dbus service:'ascii' codec can't encode character u'\xf1' in position 47: ordinal not in range(128)
ERROR: Issue calling the dbus service:'ascii' codec can't encode character u'\xf1' in position 47: ordinal not in range(128)
ERROR: Issue calling the dbus service:'ascii' codec can't encode character u'\xf1' in position 47: ordinal not in range(128)
ERROR: Issue calling the dbus service:'ascii' codec can't encode character u'\xf1' in position 47: ordinal not in range(128)
ERROR: Issue calling the dbus service:'ascii' codec can't encode character u'\xf1' in position 47: ordinal not in range(128)
ERROR: Issue calling the dbus service:'ascii' codec can't encode character u'\xf1' in position 47: ordinal not in range(128)
ERROR: Issue calling the dbus service:'ascii' codec can't encode character u'\xf1' in position 47: ordinal not in range(128)
${goto 32}${color3}Status:${color1}Unknown
${goto 32}${color3}Artist:${color1}Unknown
${goto 32}${color3}Album:${color1}Unknown
${goto 32}${color3}Title:${color1}Unknown
${goto 32}${color3}Position:${color1}0:00/0:00 - 0%
${goto 32}${color3}Rating:${color1}Unknown
${goto 32}${color3}Volume:${color1}0
${goto 32}${color3}Bitrate:${color1}Unknown
${goto 32}${color3}CoverArt:${image  -p 36,400 -s 90x82 -n}
```The name of this album is "15 Años de Musica" by the group Mocedades.

I had been having the same problem with tracks by Sinéad O'Conner.  I edited the tags to replace the "é" with an "e" and the info started showing properly in conkyGuayadeque.  Just for grins, I ran your command from a terminal while playing a "Sinead O'Conner" track and the output was fine.  Then I edited the tags to "Sinéad O'Conner" and lo and behold, the output was also fine, showing the accent.  So I went back to my Mocedades tracks and deleted the "ñ" , but got the same error message.  I got the same error message after replacing the ñ.

A quick google of the error message makes me wonder if it is not something to do with trying to convert some unicode character to UTF-8.  I also wonder if there is not some other tag in the file with an accent that is not showing in my tag editor since the error messages all say "position 47".  But I really don't know what I am talking about and don't want to send you down a wrong path.

---

### Post by VastOne on 2010-11-23
deleted - wrong thread will take to exaile

---

### Post by VastOne on 2010-12-09
K,

I have run into this as part of trying to break down the script and it's functions..

The Guayadeque scripts when pulling the embedded images to the /tmp directory pull the entire file and use it as the cover, so if you are playing a 40 meg song (I have some single file albums this big) that 40 meg file is the cover file in /tmp and continues to update

This is totally different than the Exaile one that does the same function.  It parses out the image only and that size is what is in cover and there is much less updates.

The interesting thing is that even when you stop the song from playing, the file is continuously updated in /tmp

this goes on until I remove 

${image [--datatype=CA] -p 0,172 -s 375x375}

from the Conky RC or exit the program...

I can see why you like MPD, and how mpdcron just uses a one time call.. I hope to get there with some scripts I am working on...

Thanks

---

### Post by kaivalagi on 2010-12-09
I am not sure I understand, both the guayadeque and exaile GetCover scripts work in exactly the same way, grabbing the image from the mp3 tag of the file where it is and saving the image to a file in /tmp when the tack changes

If you are refering to the image created using the CA datatype of the main script then both scripts will copy the file over and over on each exec, hence the creation of the GetCover scripts...

The mpdcron stuff fires on the track change event which in theoty is the same frequency of execution as the GetCover scripts

Or have I missed something? Is something not behaving as it should?

---

### Post by VastOne on 2010-12-09
> **kaivalagi said:**
> I am not sure I understand, both the guayadeque and exaile GetCover scripts work in exactly the same way, grabbing the image from the mp3 tag of the file where it is and saving the image to a file in /tmp when the tack changes

If you are refering to the image created using the CA datatype of the main script then both scripts will copy the file over and over on each exec, hence the creation of the GetCover scripts...

The mpdcron stuff fires on the track change event which in theoty is the same frequency of execution as the GetCover scripts

Or have I missed something? Is something not behaving as it should?

Right... Both do work the same way but where Exaile just grabs the actual jpg from the file, Guayadeque grabs the entire file (the whole song) and brings it over to the /tmp directory and I am trying to figure out if it is a script issue or a program issue.

More on this - 

I have gone to using only the Guayadeque-GetCoverart.py which obviously creates the guayadeque-coverart.jpg file

instead of this call

${image [--datatype=CA] -p 0,172 -s 375x375}

I switched and am now using

${image /tmp/guayadeque-coverart.jpg -p 0,172 -s 375x375}

This file, /tmp/guayadeque-coverart.jpg stays static until there is a music change, just as it is designed to do..

But something else in the script is creating a file 'cover' in /tmp that keeps on going (updating) after the song is completed and will not stop until there is an exit of the program or to stop (comment out) this line from conkyrc

#${execp conkyGuayadeque --template=~/conkyGuayadeque.template}

When starting a song in Guayadeque without conkyGuayadeque running, there is no 'cover' file created in /tmp at all

---

### Post by kaivalagi on 2010-12-10
/tmp/cover could be created by a player or if you are using --datatype=CA on another script maybe? If it is being created over and over that sounds like a conky script being execed with execp every second that is using a CA datatype to me...

---

### Post by VastOne on 2010-12-10
> **kaivalagi said:**
> /tmp/cover could be created by a player or if you are using --datatype=CA on another script maybe? If it is being created over and over that sounds like a conky script being execed with execp every second that is using a CA datatype to me...

Not using the datatype=CA at all in any script, and it sure does look like it is....

It cannot be from the player, if you stop the conkyGuayadeque script the cover file is never created

Weird thing is that Exaile does the same exact thing but only extracts the jpg as the cover file and does not move the whole file like Gque does

---

### Post by VastOne on 2010-12-10
> **kaivalagi said:**
> /tmp/cover could be created by a player or if you are using --datatype=CA on another script maybe? If it is being created over and over that sounds like a conky script being execed with execp every second that is using a CA datatype to me...

K,

I took this section out of conkyGuayadeque.py 
```

 if coverart != None and self.options.coverartpath != "":
                            self.logInfo("Copying coverart from %s to %s"%(coverart, self.options.coverartpath))
                            shutil.copy(coverart, self.options.coverartpath)
                            coverart = self.options.coverartpath
```

and the 'cover'  file is no longer created in /tmp

using the conkyGuayadeque-GetCoverart.py gets the cover on a track change only, as it should..

I do not know enough about all of this to know why that code is doing what it is doing, but it is the source of it...

---

### Post by kaivalagi on 2010-12-11
Nice one, you've pointed me in the direction of the issue that's for sure.

That part of the code you removed is indeed responsible for the copying of the coverart file using "self.options.coverartpath" as a destination which by default is /tmp/cover

I need to move the copy operation to somewhere where it is only done when datatype=CA is actually requested, and for all the player scripts too... ](*,)

edit: The copying code is now in place like this:
```

                elif datatype == "CA": #coverart
                    if self.musicData.coverart == None or len(self.musicData.coverart) == 0:
                        output = None
                    else:
                        self.logInfo("Copying coverart from %s to %s"%(self.musicData.coverart, self.options.coverartpath))
                        shutil.copy(self.musicData.coverart, self.options.coverartpath)
                        self.musicData.coverart = self.options.coverartpath                        
                        output = self.musicData.coverart

```
I've attached the new version of .py, please give it a go before I get busy updating all the scripts and do a release for them at some point this weekend

---

### Post by VastOne on 2010-12-11
> **kaivalagi said:**
> Nice one, you've pointed me in the direction of the issue that's for sure.

That part of the code you removed is indeed responsible for the copying of the coverart file using "self.options.coverartpath" as a destination which by default is /tmp/cover

I need to move the copy operation to somewhere where it is only done when datatype=CA is actually requested, and for all the player scripts too... ](*,)

I am cramming and impatient, sorry, but some of this is actually starting to adhere.. 

I have gone back to some of the basic fundamentals in the Python Guides you sent to me and have stopped trying to run before I can walk...or crawl for that matter..

What I am saying is I hope to be a lot more help in the future and not so much of a pain..

Thanks

---

### Post by kaivalagi on 2010-12-11
Don't worry, I was in your position once and understand, you're working at and not giving up which is the main thing, you'll get there in time....

PM me if you get stuck with any fundamentals

p.s. I updated the above attachment slightly, removing a redundant if statement for the copy file section
p.p.s. Exaile will be a problem as the image comes from the api and needs saving to be used...

---

### Post by VastOne on 2010-12-11
> **kaivalagi said:**
> Don't worry, I was in your position once and understand, you're working at and not giving up which is the main thing, you'll get there in time....

PM me if you get stuck with any fundamentals

p.s. I updated the above attachment slightly, removing a redundant if statement for the copy file section

Thanks for the advice, support and kindness...

I have tested the first one, and it is no longer copying the cover to the /tmp...  I will make sure with the new revision too...

One thing that bugs me about this is in Exaile, when using Datatype=CA, it only copies the jpg, just the image, not the entire file.. Guayadeque copies the entire song as the cover..  Is this unique to the program, or in how each is extracted (different tools) from the script?

Edit - Revision worked too... As far as Exaile goes, IMHO it works perfectly just as it is!... It does what it is supposed to do..

---

### Post by kaivalagi on 2010-12-11
> **VastOne said:**
> Thanks for the advice, support and kindness...

I have tested the first one, and it is no longer copying the cover to the /tmp...  I will make sure with the new revision too...

One thing that bugs me about this is in Exaile, when using Datatype=CA, it only copies the jpg, just the image, not the entire file.. Guayadeque copies the entire song as the cover..  Is this unique to the program, or in how each is extracted (different tools) from the script?

That is strange, it copies the coverart image file for me...I think maybe because you have cover art tags in the mp3's it points at them instead?

> **VastOne said:**
> Edit - Revision worked too... As far as Exaile goes, IMHO it works perfectly just as it is!... It does what it is supposed to do..

Sorted Exaile out too, just not as neat and tidy is all, in case you want to give it a try

first bit of code:
```
                        coverart = ""
                        try:                         
                            coverart = "".join(chr(byte) for byte in iface.GetCoverData())
                            # Below now done in datatype=CA section
                            #if coverart:
                            #    img = Image.open(StringIO(imgString))
                            #    img.save(self.options.coverartpath, "JPEG")
                            #    coverart = self.options.coverartpath
                        except:
                            coverart = ""
```

second bit:
```
                elif datatype == "CA": #coverart
                    if self.musicData.coverart == None or len(self.musicData.coverart) == 0:
                        output = None
                    else:
                        img = Image.open(StringIO(coverart))
                        img.save(self.options.coverartpath, "JPEG")
                        self.musicData.coverart = self.options.coverartpath                        
                        output = self.musicData.coverart
                            
```

---

### Post by VastOne on 2010-12-11
> **kaivalagi said:**
> That is strange, it copies the coverart image file for me...I think maybe because you have cover art tags in the mp3's it points at them instead?



I think that because of the way that Exaile is done, there is a better extraction process (tool??) that you are using in the Exaile scripts... 

I will test those revisions as well and let you know..

Thanks

---

### Post by kaivalagi on 2010-12-11
I'm going to update them all now, made all the changes and already uploaded the packages for ArchLinux...time to submit builds to launchpad for Ubuntu now :)

---

### Post by kaivalagi on 2010-12-11
**[COLOR=Red][SIZE=4]UPDATE[/SIZE][/COLOR]**

Updates as follows:
[LIST]
[*]Added use_tag_image_only flag to the GetCover script, if set to true (false by default) only tag images will get used for cover art output
[*]Updated main script to only actually copy over found cover art when --datatype=CA is requested
[/LIST]

Package changes can be seen here:  [https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkyguayadeque_2.06_source.changes](https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkyguayadeque_2.06_source.changes)

The apt packages should be available soon

---

### Post by VastOne on 2010-12-11
> **kaivalagi said:**
> That is strange, it copies the coverart image file for me...I think maybe because you have cover art tags in the mp3's it points at them instead?



Sorted Exaile out too, just not as neat and tidy is all, in case you want to give it a try

first bit of code:
```
                        coverart = ""
                        try:                         
                            coverart = "".join(chr(byte) for byte in iface.GetCoverData())
                            # Below now done in datatype=CA section
                            #if coverart:
                            #    img = Image.open(StringIO(imgString))
                            #    img.save(self.options.coverartpath, "JPEG")
                            #    coverart = self.options.coverartpath
                        except:
                            coverart = ""
```

second bit:
```
                elif datatype == "CA": #coverart
                    if self.musicData.coverart == None or len(self.musicData.coverart) == 0:
                        output = None
                    else:
                        img = Image.open(StringIO(coverart))
                        img.save(self.options.coverartpath, "JPEG")
                        self.musicData.coverart = self.options.coverartpath                        
                        output = self.musicData.coverart
                            
```

For me, the conkyExaile.py no longer works using datatype=CA, nothing is written to /tmp at all.

I looked for the obvious, synatax, order.. I could not find it but will continue to try

---

### Post by kaivalagi on 2010-12-11
Working for me, I updated the conkyExaile script along with all the others via launchpad this morning, just update with the new package and it should work for you

Be careful, if you were using the mpd script I gave you it sym links /tmp/cover to the image files of songs if available e.g. ~/Music/Folder1/Folder2/folder.jpg....if that sym link is there and one of these scripts copies to /tmp/cover it will actually overwrite the cover art image that is sym linked

---

### Post by VastOne on 2010-12-12
> **kaivalagi said:**
> Working for me, I updated the conkyExaile script along with all the others via launchpad this morning, just update with the new package and it should work for you

Be careful, if you were using the mpd script I gave you it sym links /tmp/cover to the image files of songs if available e.g. ~/Music/Folder1/Folder2/folder.jpg....if that sym link is there and one of these scripts copies to /tmp/cover it will actually overwrite the cover art image that is sym linked

Running 

conkyGuayadeque-GetCoverart.py

I now get the following error
```

conkyGuayadeque-GetCoverart - Cover art will be copied to '/tmp/guayadeque-coverart.jpg'
* Initialising: Creating a D-Bus session...
* Listening: waiting for a track change...
*** Error: Begin
Traceback (most recent call last):
  File "/usr/share/conkyguayadeque/conkyGuayadeque-GetCoverart.py", line 60, in OnTrackChange
    if use_tag_image_only == True:
NameError: global name 'use_tag_image_only' is not defined
*** Error: End
* Listening: waiting for a track change...
^CTraceback (most recent call last):
  File "/usr/share/conkyguayadeque/conkyGuayadeque-GetCoverart.py", line 139, in <module>
    loop.run()
KeyboardInterrupt
```

---

### Post by kaivalagi on 2010-12-12
> **VastOne said:**
> Running 

conkyGuayadeque-GetCoverart.py

I now get the following error
```

conkyGuayadeque-GetCoverart - Cover art will be copied to '/tmp/guayadeque-coverart.jpg'
* Initialising: Creating a D-Bus session...
* Listening: waiting for a track change...
*** Error: Begin
Traceback (most recent call last):
  File "/usr/share/conkyguayadeque/conkyGuayadeque-GetCoverart.py", line 60, in OnTrackChange
    if use_tag_image_only == True:
NameError: global name 'use_tag_image_only' is not defined
*** Error: End
* Listening: waiting for a track change...
^CTraceback (most recent call last):
  File "/usr/share/conkyguayadeque/conkyGuayadeque-GetCoverart.py", line 139, in <module>
    loop.run()
KeyboardInterrupt
```

My bad, I didn't test it and missed something...

Change this:
```
            if use_tag_image_only == True:
                src = None
            else:
                src = self.getCoverartPath()

```

to this:
```
            if [COLOR="Green"]**self.**[/COLOR]use_tag_image_only == True:
                src = None
            else:
                src = self.getCoverartPath()

```

The variable is part of the class so needs referring to with self, it is not global

edit: fixed package on it's way...

---

### Post by kaivalagi on 2010-12-12
**[COLOR=Orange][SIZE=4]UPDATE[/SIZE][/COLOR]**

Updates as follows:
[LIST]
[*]Fixed bug with GetCover script due to the tag image flag that was added
[/LIST]

Package changes can be seen here:  [https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkyguayadeque_2.07_source.changes](https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkyguayadeque_2.07_source.changes)

The apt packages should be available soon

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

### Post by EdwardR on 2011-01-19
Referring back to my post #169, I figured out a workaround for the problem with accented letters causing conkyGuayadeque to not display any data for the playing track.  It seems to be triggered if the file path contains an accented character, not the tags in the music file.  Renaming the folder names with un-accented letters and running an "update library" in Guayadeque caused the conky to display the track info and cover art properly.

---

### Post by kaivalagi on 2011-01-25
**[COLOR=Purple][SIZE=4]UPDATE[/SIZE][/COLOR]**

Updates as follows:
[LIST]
[*]Fixed potential bug with %20 not being represented as spaces when dealing with cover art paths
[/LIST]

Package changes can be seen here:  [https://launchpad.net/~conky-companions/+archive/ppa/+files/conkyguayadeque_2.08_source.changes](https://launchpad.net/~conky-companions/+archive/ppa/+files/conkyguayadeque_2.08_source.changes)

The apt packages should be available soon

---

### Post by kaivalagi on 2011-01-26
**[COLOR=Red][SIZE=4]UPDATE[/SIZE][/COLOR]**

Updates as follows:
[LIST]
[*]Updated both main scripts to handle URL encoded paths generically using urllib.unquote functions. Should sort out any cover art path issues *maybe*
[/LIST]

Package changes can be seen here:  [https://launchpad.net/~conky-companions/+archive/ppa/+files/conkyguayadeque_2.09_source.changes](https://launchpad.net/~conky-companions/+archive/ppa/+files/conkyguayadeque_2.09_source.changes)

The apt packages should be available soon

---

### Post by Spike-X on 2011-03-12
After abandoning the idea for a while, I've finally got cover art working!

[[IMG]http://img.photobucket.com/albums/v235/Spike-X/th_Screenshot-7-1.png[/IMG]](http://smg.photobucket.com/albums/v235/Spike-X/?action=view&current=Screenshot-7-1.png)

---

### Post by kaivalagi on 2011-03-12
> **Spike-X said:**
> After abandoning the idea for a while, I've finally got cover art working!

[[IMG]http://img.photobucket.com/albums/v235/Spike-X/th_Screenshot-7-1.png[/IMG]](http://smg.photobucket.com/albums/v235/Spike-X/?action=view&current=Screenshot-7-1.png)

Good job...post your files for others then ;)

---

### Post by Spike-X on 2011-03-14
I might have to clean up my conkyrc first, it's a mess.

The most important part was getting the coverart template code right. I didn't realise at first that I had to set it as an image. Here's how it looks now:

```
${image [--datatype=CA] -p 1610,16 -s 150x150 -f 1}
```

---

### Post by Sector11 on 2011-04-08
[center][ Nouveau : Conky Pitstop - c'est bilingue. ](http: // conky.pitstop.free.fr/fr)
[img]http://dl.dropbox.com/u/16070765/full_CPS-Flag.png[/img]
[New: Conky Pitstop - it's bilingual.](http://conky.pitstop.free.fr/)[/center]

---

### Post by medusa~ on 2011-04-30
Don't know about the rest! I am not a geek, just a curious user. I had a problem with all this post, which is, I didn't find a working sample script in .conkyrc. I mean how its written, not some conkyGuayadeque -h output.

Anywhere, after looking at difficult .conkyrc codes that looks like rocket science mostly when it comes to display TEXT section, here is how i displayed my guayadeque info

```

${color #28AF63}${alignc}CURRENT SONG INFO ::.
${if_running guayadeque}${color #28AF63}Artist: ${color #FF6600}${goto 50}${exec conkyGuayadeque -d AR}
${color #28AF63}Title: ${color #FF6600}${goto 50}${exec conkyGuayadeque -d TI}
${color #28AF63}Album: ${color #FF6600}${goto 50}${exec conkyGuayadeque -d AL}
${color #28AF63}Genre: ${color #FF6600}${goto 50}${exec conkyGuayadeque -d GE}${goto 130}${color #28AF63}Year: ${color #FF6600}${exec conkyGuayadeque -d YR}
${color #28AF63}Position: ${color #FF6600}${exec conkyGuayadeque -d PT}${goto 130}${color #28AF63}Length: ${color #FF6600}${exec conkyGuayadeque -d LE}${color #28AF63}$else${color #f2f2f2}${alignc}${font sans:size=6:bold}No Activity${font}$endif

```I believe will help someone, somewhere. Community giving back is in my blood.
Conky Screenshot attached! look at the bottom!!!

---

