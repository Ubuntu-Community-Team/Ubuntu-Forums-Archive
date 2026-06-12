---
title: "Showing a daily text on the desktop using Conky and RSS feed"
date: 2010-07-27
forum: General Help
---

### Post by aroeland on 2010-07-27
Hello everybody,

I've been experimenting with Conky for a bit and I found out a few cool things already. Now I would like to show a Bible verse on the desktop though, and I want this verse to change every day. To do this I use an RSS feed on the website Biblegateway.com. with wget I can download the feed, so that's no problem. The downloaded file is in XML though as you can see below:

```
<?xml version="1.0" encoding="utf-8"?><feed xmlns="http://www.w3.org/2005/Atom">
 
 <title>Bible Gateway's Verse of the Day</title>
 <subtitle>A daily word of exultation.</subtitle>
 <link href="http://www.biblegateway.com/votd/get/?format=atom" rel="self"/>
 <link href="http://www.biblegateway.com"/>
 <updated>2010-07-27T00:00:00Z</updated>
 <author>
   <name>Bible Gateway</name>
 </author>
 <id>tag:biblegateway.com,2010-07-27:NIV</id>
 
 <entry>
   <title>Hebrews 12:1</title>
   <rights type="html"><![CDATA[ Copyright ©  1973, 1978, 1984 by Biblica]]></rights>
   <link href="http://www.biblegateway.com/passage/?version=NIV&amp;search=Hebrews+12:1"/>
   <link rel="related" title="Full Copyright" href="http://www.biblegateway.com/versions/index.php?action=getVersionInfo&amp;vid=31&amp;lang=2" />
   <link rel="related" title="Audio" href="http://www.biblegateway.com/resources/audio/flash_play.php?aid=4&amp;book=65&amp;chapter=12" />
   <id>tag:biblegateway.com,2010-07-27:NIV</id>
   <updated>2010-07-27T00:00:00Z</updated>
   <content type="html"><![CDATA[&ldquo;[God Disciplines His Sons] Therefore, since we are surrounded by such a great cloud of witnesses, let us throw off ev
erything that hinders and the sin that so easily entangles, and let us run with perseverance the race marked out for us.&rdquo;]]></content>
 </entry>
 
</feed>
```

So what I would like to know is how I can get the text that's between <content type="html"> and </content>, excluding the XML code. I've tried different things, but so far with not much luck.

Thank you in advance!

---

### Post by ankspo71 on 2010-07-27
Hi,
See if this example will help you get it going for you.
[http://cdwillis.wordpress.com/2009/02/06/38/](http://cdwillis.wordpress.com/2009/02/06/38/)

According to [http://conky.sourceforge.net/docs.html](http://conky.sourceforge.net/docs.html)
It says:
>   
[QUOTE]rss   uri interval_in_minutes action (num_par (spaces_in_front))

    Download and parse RSS feeds. The interval may be a floating point value greater than 0, otherwise defaults to 15 minutes. Action may be one of the following: feed_title, item_title (with num par), item_desc (with num par) and item_titles (when using this action and spaces_in_front is given conky places that many spaces in front of each item). This object is threaded, and once a thread is created it can't be explicitly destroyed. One thread will run for each URI specified. You can use any protocol that Curl supports.[/QUOTE]

Curl looks like a requirement to use RSS feeds in conky. You can install it by copying the command below into your terminal.
```
sudo apt-get install curl
```

Here is another example: [http://crunchbanglinux.org/forums/topic/7723/conky-rss-help/](http://crunchbanglinux.org/forums/topic/7723/conky-rss-help/)

Hope this is what you're looking for.

---

### Post by aroeland on 2010-07-28
Thank you for your reply. I have looked at the examples you gave, but so far I haven't got it to work yet. I guess what most people (including the people in the examples) use it for is to show the titles of the feed, and not the actual story. I want to put the actual text on my desktop. After clicking and searching some more on the page of your first example I think I found something that is very similar to my case. Tomorrow I will look at that more and I will keep you informed. Thank you for your help so far though :-)

---

### Post by aroeland on 2010-08-03
OK, it's working. I did it a bit different, but the result is very nice. A friend of mine helped me with a PHP script that will download the feed, and filter out the text that I want. It then makes sure that the text is not too wide. Here's the script:

```
#!/usr/bin/php
<?php
$file=file_get_contents("http://www.biblegateway.com/votd/get/?format=atom");

preg_match("/&ldquo;(.*)&rdquo;/", $file, $match);

//print_r($match);

$pos=0;
$count=0;
$text=$match[1];
$length=strlen($text);

for($pos=0;$pos<$length;$pos++){
	if($count==25){
		while($text[$pos]!=' '){
			$pos--;
		}
		$text[$pos]="\n";
		$count=0;
	}
	$count++;
}

echo $text;

?>
```

In .conkyrc I start it with the pre_exec command, because it doesn't really need to be updated often.

```
${pre_exec /home/<username>/bibleverse}
```

---

### Post by N00b-un-2 on 2012-10-29
I realize that this is a bit of an old thread, but I just finished my own "Verse Of The Day" Conky script and I stumbled across this because I'm using the exact same RSS feed for mine.  So here is my solution, it handles all of the quirks and hiccups I've come across in using this, like the HTML character codes
VoTD script:
```
#!/bin/bash

address="http://www.biblegateway.com/votd/get/?format=atom&version=NIV"
rm -rf $HOME/.votd/verse
rm -rf $HOME/.votd/red
wget -O $HOME/.votd/votd_raw $address
if [[ -s $HOME/.votd/votd_raw ]]; then
 sed -n '14p' $HOME/.votd/votd_raw | cut -d '>' -f 2 | cut -d '<' -f 1 | tail -1 >> $HOME/.votd/verse
 sed -n '21p' $HOME/.votd/votd_raw | perl -0777 -ne '/(?<=&ldquo;).*(?=&rdquo;)/s;print $&;' $HOME/.votd/votd_raw | sed -e 's,&#8211;,\–,g' | sed -e 's,&#8212;,\—,g' | sed -e 's,&#8216;,\‘,g' | sed -e 's,&#8217;,\’,g' | sed -e 's,&#8220;,\“,g' | sed -e 's,&#8221;,\”,g' | tail -1 >> $HOME/.votd/verse
```

and here is my Conky
conkyrc:
```
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
 
# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes
 
# fiddle with window
use_spacer right

# Use Xft?
use_xft yes
xftfont DejaVu Sans:size=8
xftalpha .9
text_buffer_size 2048
 
# Update interval in seconds
update_interval .5
 
# Draw shades?
draw_shades no
 
# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
uppercase no # set to yes if you want all text to be in uppercase
 
# Stippled borders?
stippled_borders 3
 
# border margins
border_margin 9
 
# border width
border_width 10
 
# Default colors and also border colors, grey90 == #e5e5e5
default_color grey
 
own_window_colour brown
own_window_transparent yes
 
# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
 
# Gap between borders of screen and text
gap_x 30
gap_y 30
 
# stuff after 'TEXT' will be formatted on screen
maximum_width 250 
TEXT
${color 97BF60}DATE/TIME ${hr 2}$color
${font DejaVuSansMono:size=8}${execpi 60 today=`date +%_d`; cal | sed s/"\(^\|[^0-9]\)$today"'\b'/'\1${color 97BF60}'"$today"'$color'/}$font
${voffset -100}${offset 150}${execi 0.5 date '+%x'}
${offset 150}${execi 0.5 date '+%r'}
${offset 160}${execi 600 bash $HOME/.accuweather/acc_rss}${font conkyweather:size=40}${execpi 600  sed -n '2p' $HOME/.accuweather/weather}
${offset 150}${voffset -45}${font}${execpi 600 sed -n '1p' $HOME/.accuweather/weather|cut -d ':' -f 3 | cut -d " " -f 2 | cut -d 'F' -f 1} °F ${execpi 600 sed -n '1p' $HOME/.accuweather/weather | cut -d ':' -f 2} 

${color 97BF60}VERSE OF THE DAY ${hr 2}$color${execi 3600 $HOME/.votd/votd_rss}
${font URW Chancery L:size=12}${execi 3600 sed -n '2p' $HOME/.votd/verse | fold -w 45 -s}
${alignr}~ ${execi 3600 sed -n '1p' $HOME/.votd/verse}$font

${voffset -30}${offset 30}${font DejaVu Sans:size=14}&#10013;$font
$color
${color 97BF60}SYSTEM ${hr 2}$color
${offset 0} OS:
${offset 50}${voffset -13}${exec sed -n '4p' /etc/lsb-release | cut -d "=" -f 2 |  sed -n '4p' /etc/lsb-release | cut -d "=" -f 2 | perl -pi -e 's/"//g'} "${exec sed -n '3p' /etc/lsb-release | cut -d "=" -f 2}"
${offset 0} KERNEL:
${offset 50}${voffset -13}${exec uname -s} ${exec uname -r}
${offset 0} ARCH:
${offset 50}${voffset -13}${exec exec uname -m}
${offset 0} USER:
${offset 50}${voffset -13}${exec whoami}
${offset 0} UPTIME:
${offset 50}${voffset -13}${uptime}
${offset 160}${voffset -40}${font openlogos:size=40}u$font
${color 97BF60}CPU ${hr 2}$color
${exec  cat /proc/cpuinfo | cut -d ":" -f 2 | sed -n '5p' |  perl -pi -e 's/[(tm)]//g' | cut -d " " -f 2,3,4,5,8} 
Core 1: ${execi 1  cat /proc/cpuinfo | cut -d ":" -f 2 | sed -n '7p' | awk '{print $1/1000}' | bc -l}GHz
${voffset -13}${offset 100}${execi 1 sensors | sed -n '3p' | cut -d " " -f 4 | cut -c 2-5 | awk '{print $1*(9/5)+32}'} °F 
${voffset -13}${offset 150}${cpu cpu0}%
${voffset -13}${offset 180}${cpubar cpu0 5,70}
Core 2: ${execi 1  cat /proc/cpuinfo | cut -d ":" -f 2 | sed -n '31p' | awk '{print $1/1000}' | bc -l}GHz
${voffset -13}${offset 100}${execi 1 sensors | sed -n '5p' | cut -d " " -f 4 | cut -c 2-5 | awk '{print $1*(9/5)+32}'} °F 
${voffset -13}${offset 150}${cpu cpu1}%
${voffset -13}${offset 180}${cpubar cpu1 5,70}

${color 97BF60}PROCESSES ${hr 2}$color
${offset 10}NAME
${voffset -13}${offset 100}PID
${voffset -13}${offset 150}CPU%
${voffset -13}${offset 200}MEM%
1${offset 10}${voffset 0}${top name 1}
${offset 100}${voffset -13}${top pid 1}
${offset 150}${voffset -13}${top cpu 1}    
${offset 200}${voffset -13}${top mem 1}
2${offset 10}${voffset 0}${top name 2}
${offset 100}${voffset -13}${top pid 2}
${offset 150}${voffset -13}${top cpu 2}    
${offset 200}${voffset -13}${top mem 2}
3${offset 10}${voffset 0}${top name 3}
${offset 100}${voffset -13}${top pid 3}
${offset 150}${voffset -13}${top cpu 3}    
${offset 200}${voffset -13}${top mem 3}
4${offset 10}${voffset 0}${top name 4}
${offset 100}${voffset -13}${top pid 4}
${offset 150}${voffset -13}${top cpu 4}    
${offset 200}${voffset -13}${top mem 4}
5${offset 10}${voffset 0}${top name 5}
${offset 100}${voffset -13}${top pid 5}
${offset 150}${voffset -13}${top cpu 5}    
${offset 200}${voffset -13}${top mem 5}

${color 97BF60}MEMORY / DISK ${hr 2}$color
RAM:
${voffset -13}${offset 50}$memperc% 
${voffset -13}${offset 100}${membar 6}$color
${voffset 0}${offset 50}$mem
${voffset -13}${offset 125}/ 
${voffset -13}${offset 150}$memmax
HDD:  
${voffset -13}${offset 50}${fs_used_perc /}%
${voffset -13}${offset 100}${fs_bar 6 /}$color
${voffset 0}${offset 50}${fs_used /}
${voffset -13}${offset 125}/
${voffset -13}${offset 150}${fs_size /}
 ${color 97BF60}NETWORK: ${hr 2}
${execi 5 rm -f .conky_eth0; ifconfig -s | grep eth0 > /dev/null && ifconfig -a eth0 | grep 'inet addr:' > /dev/null && touch .conky_eth0}${execi 5 rm -f .conky_eth1; ifconfig -s | grep eth1 > /dev/null && ifconfig -a eth1 | grep 'inet addr:' > /dev/null && touch .conky_eth1}${execi 5 rm -f .conky_eth2; ifconfig -s | grep eth2 > /dev/null && ifconfig -a eth2 | grep 'inet addr:' > /dev/null > /dev/null && touch .conky_eth2}${execi 5 rm -f .conky_tun0; ifconfig -s | grep tun0 > /dev/null && ifconfig -a tun0 | grep 'inet addr:' > /dev/null && touch .conky_tun0}${execi 5 rm -f .conky_wlan0; ifconfig -s | grep wlan0 > /dev/null && ifconfig -a wlan0 | grep 'inet addr:' > /dev/null && touch .conky_wlan0}${if_existing /home/ryan/.conky_eth0}Ethernet:$alignr${addr eth0}
Down: ${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s

Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
${endif}${if_existing /home/ryan/.conky_tun0}Tethered:$alignr${addr tun0}
Down: ${downspeed tun0} k/s ${alignr}Up: ${upspeed tun0} k/s
Total: ${totaldown tun0} ${alignr}Total: ${totalup tun0}
${endif}${if_existing /home/ryan/.conky_wlan0}WiFi:$alignr${addr wlan0}
Down: ${downspeed wlan0} k/s ${alignr}Up: ${upspeed wlan0} k/s
Total: ${totaldown wlan0} ${alignr}Total: ${totalup wlan0}
${endif}
```

and here's a screenshot of my conky
[[IMG]http://img198.imageshack.us/img198/1175/screenshotsanx.png[/IMG]](http://imageshack.us/photo/my-images/198/screenshotsanx.png/)

---

### Post by wildmanne39 on 2012-10-29
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

