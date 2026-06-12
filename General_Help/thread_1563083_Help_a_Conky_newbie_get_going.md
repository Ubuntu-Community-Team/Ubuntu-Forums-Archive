---
title: "Help a Conky newbie get going?"
date: 2010-08-28
forum: General Help
---

### Post by anthony62490 on 2010-08-28
I recently obtained a Conky script that should monitor the current song from a radio stream called Nectarine. So I installed Conky, created my .conkyrc file followed the following steps:

```
Insert this line at end of .conf file:
${execpi 30 ~/nectarine.pl}
```

```

and create file nectarine.pl with execute atribute
#!/usr/bin/perl

# use module
use XML::Simple;
use Data::Dumper;

# create object
$tempfile = "$ENV{HOME}/.conky/nectarine_queue.tmp";
`wget -O $tempfile "http://www.scenemusic.net/demovibes/xml/queue/"`;
$xml = new XML::Simple;
my $xs1 = XML::Simple->new();

# read XML file
my $doc = $xs1->XMLin($tempfile);

print 'Nectarine $hr '."\n";
print '${color 000000}Song: ${color}' . $doc->{now}->{entry}->{song}->{content} ."\n";
print '${color 000000}Artist: ${color}' . $doc->{now}->{entry}->{artist}->{content} . " ( " . $doc->{now}->{entry}->{song}->{length} . " )\n";
print '${color 000000}Requester: ${color}' . $doc->{now}->{entry}->{requester}->{content} . "\n".'${color 000000}RequestTime: ${color}' . $doc->{now}->{entry}->{request_time} . "\n";
print "------------------------------------------------------\n";

foreach my $key (keys (%{$doc->{queue}})){
$len = 10;
for ($i=0; $i < $len ; $i++){
print '${color 000000} '.$i.' ${color} ${color FFCCAA}' . $doc->{queue}->{$key}->[$i]->{song}->{content} .'${color} - ';
print $doc->{queue}->{$key}->[$i]->{artist}->{content} ." ( " .$doc->{queue}->{$key}->[$i]->{song}->{length}. " ) \n";
}
}
```

So now I have two files ".conkyrc and nectarine.pl". 
.conkyrc is only one line long
nectarine.pl has all of the scripting info and it has been marked as an executable file.

Terminal Output:
```

anthony@anthony-desktop:~$ conky
Conky: /home/anthony/.conkyrc: 1: no such configuration: '${execpi'
Conky: missing text block in configuration; exiting
***** Imlib2 Developer Warning ***** :
	This program is calling the Imlib call:

	imlib_context_free();

	With the parameter:

	context

	being NULL. Please fix your program.

```

Any idea what's going on here?

---

### Post by anthony62490 on 2010-08-28
bump

---

### Post by Ginsu543 on 2010-08-28
Have you tried removing the ${ and } from the line in your .conkyrc file? ${} is usually used for displaying text in Conky, not to run a program or call another script.

---

### Post by anthony62490 on 2010-08-29
> **Ginsu543 said:**
> Have you tried removing the ${ and } from the line in your .conkyrc file? ${} is usually used for displaying text in Conky, not to run a program or call another script.
Hmm. This would make sense. I have modified .conkyrc and the contents look like this:
```
execpi 30 ~/nectarine.pl
```

Terminal Output:
```
anthony@anthony-desktop:~$ conky 
Conky: /home/anthony/.conkyrc: 1: no such configuration: 'execpi'
Conky: missing text block in configuration; exiting
***** Imlib2 Developer Warning ***** :
	This program is calling the Imlib call:

	imlib_context_free();

	With the parameter:

	context

	being NULL. Please fix your program.
```

I gather that "execpi" stands for Execute Command Prompt + Interval. It looks like I may be missing a package, but I can't find any package called Execpi.

---

### Post by Ginsu543 on 2010-08-29
Sorry I can't be more specific in my help... I'm just not very familiar with this particular script. But as I was reading your output, a thought occurred to me. Which version of Conky did you install? Did you install the one in the default Ubuntu repos? If you look for Conky in Synaptic Package Manager, you should be able to see **conky**, **conky-all**, **conky-cli**, and **conky-std**. If you installed conky, I suggest you try installing the **conky-all** package instead. It's Conky with all features enabled. Perhaps then your Conky will recognize the execpi command.

---

### Post by anthony62490 on 2010-08-29
Heh. Sorry. I've got the conky-all package. Well, thanks for your help. I managed to get a different to show some signs of functionality. I'll keep tweaking until someone can help me out with this particular script. Thank you for your time.

---

### Post by Ginsu543 on 2010-08-29
Try adding "TEXT" at the beginning of your .conkyrc, like this:
```

TEXT
${execpi 30 ~/nectarine.pl}

```

---

### Post by anthony62490 on 2010-08-29
Okay, that seemed to inject at least some semblance of life into it. I put in the TEXT block and the terminal came up with this:

```
anthony@anthony-desktop:~$ conky
Conky: desktop window (1c000ab) is subwindow of root window (c3)
Conky: drawing to desktop window
Conky: drawing to single buffer
Can't locate XML/Simple.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /home/anthony/nectarine.pl line 4.
BEGIN failed--compilation aborted at /home/anthony/nectarine.pl line 4.
```

It may be helpful to note that other than this one script, I have no other Conky settings. So, I could probably run this using only the nectarine script (but maybe not. I'm not too familiar with Perl).

---

### Post by DemonBob on 2010-08-30
> **anthony62490 said:**
> Okay, that seemed to inject at least some semblance of life into it. I put in the TEXT block and the terminal came up with this:

```
anthony@anthony-desktop:~$ conky
Conky: desktop window (1c000ab) is subwindow of root window (c3)
Conky: drawing to desktop window
Conky: drawing to single buffer
Can't locate XML/Simple.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /home/anthony/nectarine.pl line 4.
BEGIN failed--compilation aborted at /home/anthony/nectarine.pl line 4.
```

It may be helpful to note that other than this one script, I have no other Conky settings. So, I could probably run this using only the nectarine script (but maybe not. I'm not too familiar with Perl).

sudo apt-get install libxml-simple-perl

---

### Post by anthony62490 on 2010-08-30
> **DemonBob said:**
> sudo apt-get install libxml-simple-perl

Okay, I have installed and reset X Windows. I now got this from my dear terminal:
```
anthony@anthony-desktop:~$ conky
Conky: desktop window (1c000ab) is subwindow of root window (c3)
Conky: drawing to desktop window
Conky: drawing to single buffer
/home/anthony/.conky/nectarine_queue.tmp: No such file or directory
File does not exist: /home/anthony/.conky/nectarine_queue.tmp at /home/anthony/nectarine.pl line 14

```


So I created .conky and tried on more time. Now I've got this:
```
anthony@anthony-desktop:~$ conky
Conky: desktop window (1c000ab) is subwindow of root window (c3)
Conky: drawing to desktop window
Conky: drawing to single buffer
--2010-08-30 01:17:36--  http://www.scenemusic.net/demovibes/xml/queue/
Resolving www.scenemusic.net... 188.40.20.83
Connecting to www.scenemusic.net|188.40.20.83|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [application/xml]
Saving to: `/home/anthony/.conky/nectarine_queue.tmp'

    [ <=>                                   ] 6,742       39.3K/s   in 0.2s    

2010-08-30 01:17:36 (39.3 KB/s) - `/home/anthony/.conky/nectarine_queue.tmp' saved [6742]

Conky: unknown variable co
Conky: unknown variable co
Conky: unknown variable co
--2010-08-30 01:18:06--  http://www.scenemusic.net/demovibes/xml/queue/
Resolving www.scenemusic.net... 188.40.20.83
Connecting to www.scenemusic.net|188.40.20.83|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [application/xml]
Saving to: `/home/anthony/.conky/nectarine_queue.tmp'

    [ <=>                                   ] 6,741       42.3K/s   in 0.2s    

2010-08-30 01:18:06 (42.3 KB/s) - `/home/anthony/.conky/nectarine_queue.tmp' saved [6741]

Conky: unknown variable co
Conky: unknown variable co
Conky: unknown variable co
Conky: unknown variable co
Conky: unknown variable co
Conky: unknown variable co
Conky: unknown variable co
Conky: unknown variable co

```

**It appears to be working decently, but there are some issues(flickering, position, general feel) If you have any help with these problems, feel free to help ; Otherwise, consider this question solved. Thanks to all.**

---

### Post by DemonBob on 2010-08-30
> **anthony62490 said:**
> Okay, I have installed and reset X Windows. I now got this from my dear terminal:
```
anthony@anthony-desktop:~$ conky
Conky: desktop window (1c000ab) is subwindow of root window (c3)
Conky: drawing to desktop window
Conky: drawing to single buffer
/home/anthony/.conky/nectarine_queue.tmp: No such file or directory
File does not exist: /home/anthony/.conky/nectarine_queue.tmp at /home/anthony/nectarine.pl line 14

```


So I created .conky and tried on more time. Now I've got this:
```
anthony@anthony-desktop:~$ conky
Conky: desktop window (1c000ab) is subwindow of root window (c3)
Conky: drawing to desktop window
Conky: drawing to single buffer
--2010-08-30 01:17:36--  http://www.scenemusic.net/demovibes/xml/queue/
Resolving www.scenemusic.net... 188.40.20.83
Connecting to www.scenemusic.net|188.40.20.83|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [application/xml]
Saving to: `/home/anthony/.conky/nectarine_queue.tmp'

    [ <=>                                   ] 6,742       39.3K/s   in 0.2s    

2010-08-30 01:17:36 (39.3 KB/s) - `/home/anthony/.conky/nectarine_queue.tmp' saved [6742]

Conky: unknown variable co
Conky: unknown variable co
Conky: unknown variable co
--2010-08-30 01:18:06--  http://www.scenemusic.net/demovibes/xml/queue/
Resolving www.scenemusic.net... 188.40.20.83
Connecting to www.scenemusic.net|188.40.20.83|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [application/xml]
Saving to: `/home/anthony/.conky/nectarine_queue.tmp'

    [ <=>                                   ] 6,741       42.3K/s   in 0.2s    

2010-08-30 01:18:06 (42.3 KB/s) - `/home/anthony/.conky/nectarine_queue.tmp' saved [6741]

Conky: unknown variable co
Conky: unknown variable co
Conky: unknown variable co
Conky: unknown variable co
Conky: unknown variable co
Conky: unknown variable co
Conky: unknown variable co
Conky: unknown variable co

```

**It appears to be working decently, but there are some issues(flickering, position, general feel) If you have any help with these problems, feel free to help ; Otherwise, consider this question solved. Thanks to all.**

Post your complete conkyrc config.

---

### Post by anthony62490 on 2010-08-30
> **DemonBob said:**
> Post your complete conkyrc config.

.conkyrc
```
TEXT
${execpi 30 ~/nectarine.pl}
```

nectarine.pl
```
#!/usr/bin/perl

# use module
use XML::Simple;
use Data::Dumper;

# create object
$tempfile = "$ENV{HOME}/.conky/nectarine_queue.tmp";
`wget -O $tempfile "http://www.scenemusic.net/demovibes/xml/queue/"`;
$xml = new XML::Simple;
my $xs1 = XML::Simple->new();

# read XML file
my $doc = $xs1->XMLin($tempfile);

print 'Nectarine $hr '."\n";
print '${color 000000}Song: ${color}' . $doc->{now}->{entry}->{song}->{content} ."\n";
print '${color 000000}Artist: ${color}' . $doc->{now}->{entry}->{artist}->{content} . " ( " . $doc->{now}->{entry}->{song}->{length} . " )\n";
print '${color 000000}Requester: ${color}' . $doc->{now}->{entry}->{requester}->{content} . "\n".'${color 000000}RequestTime: ${color}' . $doc->{now}->{entry}->{request_time} . "\n";
print "------------------------------------------------------\n";

foreach my $key (keys (%{$doc->{queue}})){
$len = 10;
for ($i=0; $i < $len ; $i++){
print '${color 000000} '.$i.' ${color} ${color FFCCAA}' . $doc->{queue}->{$key}->[$i]->{song}->{content} .'${color} - ';
print $doc->{queue}->{$key}->[$i]->{artist}->{content} ." ( " .$doc->{queue}->{$key}->[$i]->{song}->{length}. " ) \n";
}
}
```

In addition, I had to create a folder called "home/anthony/.conky"
It looks like it contains every song that has played while conky was running. It looks like this (condensed):
```
&#8722;
<playlist>
 <now>
  <entry request_time="2010-08-30 14:05:15">
   <artist id="1373" flag="se">Dubmood</artist>
   <artist id="1604" flag="se">Zabutom</artist>
   <song id="7638" length="2:17">St-style</song>
   <requester flag="fam">Koekenbakker</requester>
  </entry>
  <timeleft>86</timeleft>
 </now>
 <queue>
  <entry request_time="2010-08-30 14:05:17">
   <artist id="1041" flag="NL">Scavenger</artist>
   <song id="8226" length="2:38">Chaos (TCC 1993 Invite)</song>
   <requester flag="fam">Koekenbakker</requester>
  </entry>
  <entry request_time="2010-08-30 14:05:17">
   <artist id="1687" flag="se">Goto80</artist>
   <song id="27746" length="4:33">Killer Piller</song>
   <requester flag="fam">Koekenbakker</requester>
  </entry>
 </history>
</playlist>
```


Terminal Output:
```
anthony@anthony-desktop:~$ conky
Conky: desktop window (18000ab) is subwindow of root window (c3)
Conky: drawing to desktop window
Conky: drawing to single buffer
--2010-08-30 10:42:21--  http://www.scenemusic.net/demovibes/xml/queue/
Resolving www.scenemusic.net... 188.40.20.83
Connecting to www.scenemusic.net|188.40.20.83|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [application/xml]
Saving to: `/home/anthony/.conky/nectarine_queue.tmp'

    [  <=>                                  ] 12,774      40.1K/s   in 0.3s    

2010-08-30 10:42:22 (40.1 KB/s) - `/home/anthony/.conky/nectarine_queue.tmp' saved [12774]

**At this point, it waited for about thirty seconds before the following was displayed.**

--2010-08-30 10:42:51--  http://www.scenemusic.net/demovibes/xml/queue/
Resolving www.scenemusic.net... 188.40.20.83
Connecting to www.scenemusic.net|188.40.20.83|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [application/xml]
Saving to: `/home/anthony/.conky/nectarine_queue.tmp'

    [  <=>                                  ] 12,774      40.4K/s   in 0.3s    

2010-08-30 10:42:52 (40.4 KB/s) - `/home/anthony/.conky/nectarine_queue.tmp' saved [12774]
```

It is definitely showing signs of life, but it jumps in and out every five seconds or so.

---

### Post by DemonBob on 2010-08-30
> **anthony62490 said:**
> .conkyrc
```
TEXT
${execpi 30 ~/nectarine.pl}
```

nectarine.pl
```
#!/usr/bin/perl

# use module
use XML::Simple;
use Data::Dumper;

# create object
$tempfile = "$ENV{HOME}/.conky/nectarine_queue.tmp";
`wget -O $tempfile "http://www.scenemusic.net/demovibes/xml/queue/"`;
$xml = new XML::Simple;
my $xs1 = XML::Simple->new();

# read XML file
my $doc = $xs1->XMLin($tempfile);

print 'Nectarine $hr '."\n";
print '${color 000000}Song: ${color}' . $doc->{now}->{entry}->{song}->{content} ."\n";
print '${color 000000}Artist: ${color}' . $doc->{now}->{entry}->{artist}->{content} . " ( " . $doc->{now}->{entry}->{song}->{length} . " )\n";
print '${color 000000}Requester: ${color}' . $doc->{now}->{entry}->{requester}->{content} . "\n".'${color 000000}RequestTime: ${color}' . $doc->{now}->{entry}->{request_time} . "\n";
print "------------------------------------------------------\n";

foreach my $key (keys (%{$doc->{queue}})){
$len = 10;
for ($i=0; $i < $len ; $i++){
print '${color 000000} '.$i.' ${color} ${color FFCCAA}' . $doc->{queue}->{$key}->[$i]->{song}->{content} .'${color} - ';
print $doc->{queue}->{$key}->[$i]->{artist}->{content} ." ( " .$doc->{queue}->{$key}->[$i]->{song}->{length}. " ) \n";
}
}
```

In addition, I had to create a folder called "home/anthony/.conky"
It looks like it contains every song that has played while conky was running. It looks like this (condensed):
```
&#8722;
<playlist>
 <now>
  <entry request_time="2010-08-30 14:05:15">
   <artist id="1373" flag="se">Dubmood</artist>
   <artist id="1604" flag="se">Zabutom</artist>
   <song id="7638" length="2:17">St-style</song>
   <requester flag="fam">Koekenbakker</requester>
  </entry>
  <timeleft>86</timeleft>
 </now>
 <queue>
  <entry request_time="2010-08-30 14:05:17">
   <artist id="1041" flag="NL">Scavenger</artist>
   <song id="8226" length="2:38">Chaos (TCC 1993 Invite)</song>
   <requester flag="fam">Koekenbakker</requester>
  </entry>
  <entry request_time="2010-08-30 14:05:17">
   <artist id="1687" flag="se">Goto80</artist>
   <song id="27746" length="4:33">Killer Piller</song>
   <requester flag="fam">Koekenbakker</requester>
  </entry>
 </history>
</playlist>
```


Terminal Output:
```
anthony@anthony-desktop:~$ conky
Conky: desktop window (18000ab) is subwindow of root window (c3)
Conky: drawing to desktop window
Conky: drawing to single buffer
--2010-08-30 10:42:21--  http://www.scenemusic.net/demovibes/xml/queue/
Resolving www.scenemusic.net... 188.40.20.83
Connecting to www.scenemusic.net|188.40.20.83|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [application/xml]
Saving to: `/home/anthony/.conky/nectarine_queue.tmp'

    [  <=>                                  ] 12,774      40.1K/s   in 0.3s    

2010-08-30 10:42:22 (40.1 KB/s) - `/home/anthony/.conky/nectarine_queue.tmp' saved [12774]

**At this point, it waited for about thirty seconds before the following was displayed.**

--2010-08-30 10:42:51--  http://www.scenemusic.net/demovibes/xml/queue/
Resolving www.scenemusic.net... 188.40.20.83
Connecting to www.scenemusic.net|188.40.20.83|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [application/xml]
Saving to: `/home/anthony/.conky/nectarine_queue.tmp'

    [  <=>                                  ] 12,774      40.4K/s   in 0.3s    

2010-08-30 10:42:52 (40.4 KB/s) - `/home/anthony/.conky/nectarine_queue.tmp' saved [12774]
```

It is definitely showing signs of life, but it jumps in and out every five seconds or so.


Add this above TEXT

```
background no
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
```

---

### Post by stinkeye on 2010-08-31
As DemonBob said you need [**_[COLOR="DarkRed"]Conky config file settings[/COLOR]_**]("http://conky.sourceforge.net/config_settings.html") above "**TEXT**".
Everything above "**TEXT**" determines how conky is displayed.
Everything below "**TEXT**" determines what is displayed.

Eg...have a look at the default conky config at **/etc/conky/conky.conf**

You could just copy everything above "**TEXT**" from /etc/conky/conky.conf
to your .conkyrc and the adjust the settings to how you want it to display.


This is the config above "**TEXT**" that I use to display vnstats
with a transparent background in the bottom right corner of my screen.
```
background yes
font Sans Seriff:size=9
xftfont DejaVu Sans Mono:bold:size=10
use_xft yes
xftalpha 0.8
update_interval 1.0
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades yes
draw_outline no
draw_borders no
draw_graph_borders no
minimum_size 300
maximum_width 300
default_color 919FAA
default_shade_color 333333
default_outline_color 00ff00
alignment br
gap_x 10
gap_y 10
no_buffers yes
cpu_avg_samples 2
override_utf8_locale yes
uppercase no # set to yes if you want all text to be in uppercase
use_spacer right

# colours
#off white
color1 BDAC88

# cream
color2 D2B16A

# cyan
#color3 08A1A1

# bluemoon
color3 919FAA

# yellow
color4 F1BC49

# Green
color5 00940F

#dark cyan
color6 074C4C


#grey
color7 6b6b6b

#orange
color8 AF560D

#yellow
color9 F1BC49
```

---

### Post by anthony62490 on 2010-08-31
> **DemonBob said:**
> Add this above TEXT

```
background no
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
```

Hey, that works nicely. Thanks. Now that this has been implemented though, two new issues have come up.

1. I changed conkyrc to say "${execpi 5 ~/nectarine.pl}". I figured that changing the number directly after an interval command would increase the refresh rate. Now I'm getting strange results. Every five seconds, the output blinks and the font gets roughly 2x bigger. In addition to this, the small font output is displayed on top of the larger one.

2. (with refresh rate set to 30) Conky seems to work great when I start it manually, but if I set it to run on startup, it is displayed in front of all my windows. This would be nice if it didn't also display a good chunk of my desktop picture with it. In addition to all of this, Compiz seems to think that my Glowing Windows effect applies to Conky, even though own_window_hints is set to "undecorated"

If screenshots would be useful, all you need to do is ask.

---

### Post by stinkeye on 2010-08-31
execpi interval can't be less than update_interval in configuration.

[**_[COLOR="DarkRed"]Conky Variables[/COLOR]_**]("http://conky.sourceforge.net/variables.html")


To auto start conky see here "STEP 2 - Setting up conky to autostart on boot."
[**_[COLOR="DarkRed"]HOW TO: A Beginners Guide to Setting up Conky[/COLOR]_**]("http://ubuntuforums.org/showthread.php?p=5436679#post5437628")

From that post your startup script would be```
#!/bin/bash
sleep 20 &&	# 0 good for Xfce - use 20 to 30 for Gnome
conky &
``` 



For the glowing effect I assume its from CCSM > effects > window decoration
Change your shadow windows box to read
```
(any) & !(class=Conky) 
```

---

### Post by anthony62490 on 2010-09-01
Hey, thanks for your help. It took a bit of fiddling, but I finally got exactly what I was after. For posterity's sake, I will record my finished product...

**/home/anthony/.conkyrc**
```
update_interval 5.0
alignment bottom_right
background yes
default_color AA272C
draw_shades yes
default_shade_color black
gap_x 30
draw_borders yes
border_inner_margin 5
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
use_xft yes
xftfont Bitstream Vera Sans:size=8
lua_load /home/anthony/scripts/draw_bg.lua
lua_draw_hook_pre draw_bg

TEXT
${color grey}CPU: ${color}${cpugraph 25,75 000000 ffffff}${color grey}RAM:${color} ${memgraph 25,75 000000 ffffff}
${color grey}CPU: ${color}${freq} Mhz $alignr${color grey}RAM:${color} $mem/$memmax
${color grey}Usage:${color} $cpu%  $alignr${color grey} Usage:${color} $memperc%
${hr}
${color grey}/home${color} $alignc ${fs_used /home} / ${fs_size /home} $alignr No Temp
${color AA272C}${fs_bar 5,200 /home} ${fs_used_perc /home} % ${color}

${color grey}HDD2${color} $alignc ${fs_used /media/e8b87328-8dc3-4993-83f0-14a5878f6edb} / ${fs_size /media/e8b87328-8dc3-4993-83f0-14a5878f6edb} $alignr ${hddtemp /dev/sdb 127.0.0.1 7634}C
${color AA272C}${fs_bar 5,200 /media/e8b87328-8dc3-4993-83f0-14a5878f6edb} ${fs_used_perc /media/e8b87328-8dc3-4993-83f0-14a5878f6edb} %${color}


NAME $alignr PID    CPU
${color grey}${top name 1} $alignr ${top pid 1} ${top cpu 1}
${top name 2} $alignr ${top pid 2} ${top cpu 2}
${top name 3} $alignr ${top pid 3} ${top cpu 3}
${top name 4} $alignr ${top pid 4} ${top cpu 4}
${top name 5} $alignr ${top pid 5} ${top cpu 5}${color}

${execpi 30 /home/anthony/scripts/nectarine.pl}
```

**/home/anthony/sripts/nectarine.pl**
```
#!/usr/bin/perl

# use module
use XML::Simple;
use Data::Dumper;

# create object
$tempfile = "$ENV{HOME}/.conky/nectarine_queue.tmp";
`wget -O $tempfile "http://www.scenemusic.net/demovibes/xml/queue/"`;
$xml = new XML::Simple;
my $xs1 = XML::Simple->new();

# read XML file
my $doc = $xs1->XMLin($tempfile);

print 'NECTARINE $hr '."\n";
print '${color grey}Song: ${color}' . $doc->{now}->{entry}->{song}->{content} ."\n";
print '${color grey}Artist: ${color}' . $doc->{now}->{entry}->{artist}->{content} . " ( " . $doc->{now}->{entry}->{song}->{length} . " )\n";
print '${color grey}Requester: ${color}' . $doc->{now}->{entry}->{requester}->{content} . "\n";
print '${color grey}RequestTime: ${color}' . $doc->{now}->{entry}->{request_time} . "\n";
print "------------------------------------------------------\n";

foreach my $key (keys (%{$doc->{queue}})){
$len = 10;
for ($i=0; $i < $len ; $i++){
print '${color FFCCAA} '.$i. $doc->{queue}->{$key}->[$i]->{song}->{content} .'${color} - ';
print $doc->{queue}->{$key}->[$i]->{artist}->{content} ." ( " .$doc->{queue}->{$key}->[$i]->{song}->{length}. " ) \n";
}
}
```

**/home/anthony/scripts/draw_bg.lua**
```
--[[
Background by londonali1010 (2009)

This script draws a background to the Conky window. It covers the whole of the Conky window, but you can specify rounded corners, if you wish.

To call this script in Conky, use (assuming you have saved this script to ~/scripts/):
	lua_load ~/scripts/draw_bg.lua
	lua_draw_hook_pre draw_bg

Changelog:
+ v1.0 -- Original release (07.10.2009)
]]

-- Change these settings to affect your background.
-- "corner_r" is the radius, in pixels, of the rounded corners. If you don't want rounded corners, use 0.

corner_r=15

-- Set the colour and transparency (alpha) of your background.

bg_colour=0x000000
bg_alpha=0.5

require 'cairo'
function rgb_to_r_g_b(colour,alpha)
	return ((colour / 0x10000) % 0x100) / 255., ((colour / 0x100) % 0x100) / 255., (colour % 0x100) / 255., alpha
end

function conky_draw_bg()
	if conky_window==nil then return end
	local w=conky_window.width
	local h=conky_window.height
	local cs=cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual, w, h)
	cr=cairo_create(cs)
	
	cairo_move_to(cr,corner_r,0)
	cairo_line_to(cr,w-corner_r,0)
	cairo_curve_to(cr,w,0,w,0,w,corner_r)
	cairo_line_to(cr,w,h-corner_r)
	cairo_curve_to(cr,w,h,w,h,w-corner_r,h)
	cairo_line_to(cr,corner_r,h)
	cairo_curve_to(cr,0,h,0,h,0,h-corner_r)
	cairo_line_to(cr,0,corner_r)
	cairo_curve_to(cr,0,0,0,0,corner_r,0)
	cairo_close_path(cr)
	
	cairo_set_source_rgba(cr,rgb_to_r_g_b(bg_colour,bg_alpha))
	cairo_fill(cr)
end
```

---

### Post by Ginsu543 on 2010-09-01
Can you post a screenshot? Would love to see what all your hard work looks like. :)

---

### Post by anthony62490 on 2010-09-11
> **Ginsu543 said:**
> Can you post a screenshot? Would love to see what all your hard work looks like. :)

Why soitenly. Here you go. Keep in mind, it's a work in progress. Also, I need to speak with the author of the Nectarine script about that last line. I'm not sure what causes that.

---

