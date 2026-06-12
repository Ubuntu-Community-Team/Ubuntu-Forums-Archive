---
title: "Making 'For Newbie' script to pop up at Login"
date: 2010-07-27
forum: General Help
---

### Post by inameiname on 2010-07-27
I'm trying to set up an easy script which I will list in my startup apps list to run at startup and display a paragraph or two welcoming a new user to my custom-made Ubuntu OS. 

Currently, I have a python script that reads a text file of the same name and in the same folder which works great for one-line things, such as jokes, or quotes, or something, but I think I want something a little better for this instance. I'll attach the script because I like the format.

Ideally, I'd love to have it open say one page, perhaps a large font, "Welcome", and then along with the 'close' button as found in that python script's format, a 'next' or 'forward', or something which will go to another page, so it'd be like an easy guide to get started.

Anybody have any idea how to make something like this? Or perhaps just how to tweak the script I already have for this purpose? If tweaking is possible, the three things that need to be tweaked is (1) to enable it to read more than one line at a time, (2) allow for a 'next' button so as to go on to a new text file or paragraph, and (3) do so not in a random way. 

Any help would be great.

> 
#!/usr/bin/env python
import gtk, pygtk, os, sys
from random import randint
os.chdir(sys.path[0])
q = open('./For-Newbies.txt')
quotes = q.readlines()
q.close()
md = gtk.MessageDialog(None, gtk.DIALOG_DESTROY_WITH_PARENT, gtk.MESSAGE_INFO, gtk.BUTTONS_CLOSE, quotes[randint(0, len(quotes)-1)])
md.set_title("For Newbies")
md.set_position(gtk.WIN_POS_CENTER)
md.run()
md.destroy()


---

### Post by kevin.krenz on 2010-07-27
You might consider using an html file rather than a text file, and have a web browser display it upon logging in.

---

### Post by inameiname on 2010-07-27
Hmmm, interesting idea, thanks. So you'd mean an html document that I can say click from one page to next? Not sure how to make those.

---

### Post by inameiname on 2010-07-27
I just decided to change that script I mentioned into one that reads several txt files, one after the other. Not very pretty, but it works. 

```

#!/usr/bin/env python
import gtk, pygtk, os, sys
from random import randint
os.chdir(sys.path[0])
q = open('./For-Newbies-1.txt')
quotes = q.readlines()
q.close()
md = gtk.MessageDialog(None, gtk.DIALOG_DESTROY_WITH_PARENT, gtk.MESSAGE_INFO, gtk.BUTTONS_OK, quotes[randint(0, len(quotes)-1)])
md.set_title("For Newbies (1/10)")
md.set_position(gtk.WIN_POS_CENTER)
md.run()
md.destroy()

import gtk, pygtk, os, sys
from random import randint
os.chdir(sys.path[0])
q = open('./For-Newbies-2.txt')
quotes = q.readlines()
q.close()
md = gtk.MessageDialog(None, gtk.DIALOG_DESTROY_WITH_PARENT, gtk.MESSAGE_INFO, gtk.BUTTONS_OK, quotes[randint(0, len(quotes)-1)])
md.set_title("For Newbies (2/10)")
md.set_position(gtk.WIN_POS_CENTER)
md.run()
md.destroy()

import gtk, pygtk, os, sys
from random import randint
os.chdir(sys.path[0])
q = open('./For-Newbies-3.txt')
quotes = q.readlines()
q.close()
md = gtk.MessageDialog(None, gtk.DIALOG_DESTROY_WITH_PARENT, gtk.MESSAGE_INFO, gtk.BUTTONS_OK, quotes[randint(0, len(quotes)-1)])
md.set_title("For Newbies (3/10)")
md.set_position(gtk.WIN_POS_CENTER)
md.run()
md.destroy()

import gtk, pygtk, os, sys
from random import randint
os.chdir(sys.path[0])
q = open('./For-Newbies-4.txt')
quotes = q.readlines()
q.close()
md = gtk.MessageDialog(None, gtk.DIALOG_DESTROY_WITH_PARENT, gtk.MESSAGE_INFO, gtk.BUTTONS_OK, quotes[randint(0, len(quotes)-1)])
md.set_title("For Newbies (4/10)")
md.set_position(gtk.WIN_POS_CENTER)
md.run()
md.destroy()

import gtk, pygtk, os, sys
from random import randint
os.chdir(sys.path[0])
q = open('./For-Newbies-5.txt')
quotes = q.readlines()
q.close()
md = gtk.MessageDialog(None, gtk.DIALOG_DESTROY_WITH_PARENT, gtk.MESSAGE_INFO, gtk.BUTTONS_OK, quotes[randint(0, len(quotes)-1)])
md.set_title("For Newbies (5/10)")
md.set_position(gtk.WIN_POS_CENTER)
md.run()
md.destroy()

import gtk, pygtk, os, sys
from random import randint
os.chdir(sys.path[0])
q = open('./For-Newbies-6.txt')
quotes = q.readlines()
q.close()
md = gtk.MessageDialog(None, gtk.DIALOG_DESTROY_WITH_PARENT, gtk.MESSAGE_INFO, gtk.BUTTONS_OK, quotes[randint(0, len(quotes)-1)])
md.set_title("For Newbies (6/10)")
md.set_position(gtk.WIN_POS_CENTER)
md.run()
md.destroy()

import gtk, pygtk, os, sys
from random import randint
os.chdir(sys.path[0])
q = open('./For-Newbies-7.txt')
quotes = q.readlines()
q.close()
md = gtk.MessageDialog(None, gtk.DIALOG_DESTROY_WITH_PARENT, gtk.MESSAGE_INFO, gtk.BUTTONS_OK, quotes[randint(0, len(quotes)-1)])
md.set_title("For Newbies (7/10)")
md.set_position(gtk.WIN_POS_CENTER)
md.run()
md.destroy()

import gtk, pygtk, os, sys
from random import randint
os.chdir(sys.path[0])
q = open('./For-Newbies-8.txt')
quotes = q.readlines()
q.close()
md = gtk.MessageDialog(None, gtk.DIALOG_DESTROY_WITH_PARENT, gtk.MESSAGE_INFO, gtk.BUTTONS_OK, quotes[randint(0, len(quotes)-1)])
md.set_title("For Newbies (8/10)")
md.set_position(gtk.WIN_POS_CENTER)
md.run()
md.destroy()

import gtk, pygtk, os, sys
from random import randint
os.chdir(sys.path[0])
q = open('./For-Newbies-9.txt')
quotes = q.readlines()
q.close()
md = gtk.MessageDialog(None, gtk.DIALOG_DESTROY_WITH_PARENT, gtk.MESSAGE_INFO, gtk.BUTTONS_OK, quotes[randint(0, len(quotes)-1)])
md.set_title("For Newbies (9/10)")
md.set_position(gtk.WIN_POS_CENTER)
md.run()
md.destroy()

import gtk, pygtk, os, sys
from random import randint
os.chdir(sys.path[0])
q = open('./For-Newbies-10.txt')
quotes = q.readlines()
q.close()
md = gtk.MessageDialog(None, gtk.DIALOG_DESTROY_WITH_PARENT, gtk.MESSAGE_INFO, gtk.BUTTONS_CLOSE, quotes[randint(0, len(quotes)-1)])
md.set_title("For Newbies (10/10)")
md.set_position(gtk.WIN_POS_CENTER)
md.run()
md.destroy()

```

---

### Post by Vaphell on 2010-07-27
huh? it's a basic html navigation
besides, open open office writer and there you can add hyperlinks to other documents and export to HTML

---

### Post by inameiname on 2010-07-27
I see. I've never made one before, that's all. I'll have to figure it out.

---

### Post by Vaphell on 2010-07-27
lol, your solution for this rather trivial problem is quite hardcore, but i envy pygtk skills :) seriously no experience in basic html?
also you can consider putting link to the intro on desktop (though i don't know how to do that when home dir is created), autostart can be annoying and inexperienced user may have trouble with finding the session apps config :)

---

### Post by inameiname on 2010-07-27
Haha, yeah, thanks. I love scripts. I use Nautilus Scripts for all sorts of things. Anyway, no, no experience with html. And I wouldn't know how to do that when home dir is created either. 

It's cool though. The script above works just fine. And it pops up a handy little box, as shown in the attached picture. 

Also, as far as how annoying it'd be at every start up, on text number 10, I put instructions on how to remove the damn thing from the startup programs for those inexperienced folks I wish to give Ubuntu too. :P

---

### Post by skooter1121 on 2010-07-27
You might like this as an alternative. Pretty and looks like it's part of the OS.

notify-send -i "a path to a custom icon" " " "`shuf -n1 "a path to your text file"`"

I use it to show a favorite quote as a bash script to run every hour.
[http://ubuntuforums.org/images/smilies/icon_biggrin.gif](http://ubuntuforums.org/images/smilies/icon_biggrin.gif)
-SK

---

### Post by inameiname on 2010-07-27
That's an interesting idea, to use it through a notification, however one issue with that is there's no way to have the user close it and/or open the next one when they are finished reading it, as it's on a timed display. And with mine, it's only 3 seconds, as opposed to the 10 that's standard, since that's way too long for most notifications. 

Is there any way to make only these notifications last longer? 

Oh, and I do like your quotes idea using notifications. I have a thousand of those in a text file and using that script above, can have one load on startup very easily.

---

### Post by linux18 on 2010-07-27
I'd hate to advertise, but it seems like I can't stop myself.....
I've got my own remastered ubuntu [http://ubuntuforums.org/showthread.php?t=1534408](http://ubuntuforums.org/showthread.php?t=1534408)
this one installs the exact same system as the command-line only option from alternate and server installs, but its a 250MB smaller iso (450Mb instead of 700MB). works with unetbootin and is a great way to get lubuntu without leaving reminants of other DE's while being much faster than the minimal install.

---

### Post by inameiname on 2010-07-27
That's cool and all, but not sure how that fits in with the contents in this posting...

---

### Post by skooter1121 on 2010-07-28
I've been playing around for the last month with some of the notification programs: zenity, gxmessage, notify-send and looked at a few python scripts. (I'm no programmer & new to Linux, since 01/10 and enjoy customizing scripts.)

```
$ notify-send -help
```

notify-send has a few options. -t will let you set the on screen time, where the default will keep longer messages open longer. I've never gotten -u to work!

You could create a launcher on the top panel that would run the script whenever the user wanted another tip.

notify-send is part of the notify-osd which is installed as part of Ubuntu. There is a patch to the the library that will allow more customized features. They have also created a GUI that will let you change things like color and font weight.

Here is the link for info.

http://www.webupd8.org/2010/05/finally-easy-way-to-customize-notify.html"

And the install step by step;

Add the patch repository:
```
     $sudo add-apt-repository ppa:leolik/leolik
```
Patched Notify-OSD
```
     $sudo apt-get update && sudo apt-get upgrade
```
Add the GUI repository:
```
     $sudo add-apt-repository ppa:amandeepgrewal/notifyosdconfig
```
GUI
```
     $sudo apt-get update && sudo apt-get install notifyosdconfig
```

You'll find the NotifyOSD GUI under Applications/Accessories

Here's some fun samples for notify-send.

```
notify-send -i "your custom icon location" "`date +%a` `date +%I:%M` `date +%p`" "`shuf -n1 "your custom text file location"`"
```

```
wget http://www.randomfunfacts.com -O - 2>/dev/null | grep \<strong\> | sed "s;^.*<i>\(.*\)</i>.*$;\1;" | while read TRIVIA; do notify-send -t $((1000+300*`echo -n $TRIVIA | wc -w`)) -i "your custom icon location" "          TRIVIA" "$TRIVIA"; done
```

try this one as a python script:

```
#!/usr/bin/python
# -*- coding: utf-8
# Weather-Notify
# See below for instructions to adapt for your city

import xml.parsers.expat
import urllib
from os import execvp

ignore_elements = [
	'guid',
	'geo:lat',
	'geo:long',
	'link',
	'title',
	'ttl',
	'rss',
	'channel',
	'lastBuildDate',
	'pubDate',
	'width',
	'height',
	'item']
in_element = ""

wdata = {}
ferr = 0
icon = '/usr/share/pixmaps/gnome-question.png'
save_image_filename = "/tmp/weather-notify-temp.gif"

def start_element(name, attrs):
	global in_element, wdata
	in_element += "." + name
	if name not in ignore_elements:
		if (in_element == ".rss.channel.yweather:location"):
			wdata['city'] = attrs['city']
		elif (in_element == ".rss.channel.yweather:units"):
			wdata['units'] = attrs
		elif (in_element == ".rss.channel.yweather:wind"):
			wdata['wind'] = attrs
		elif (in_element == ".rss.channel.yweather:atmosphere"):
			wdata['atmosphere'] = attrs
		elif (in_element == ".rss.channel.yweather:astronomy"):
			wdata['astronomy'] = attrs
		elif (in_element == ".rss.channel.item.yweather:condition"):
			wdata['condition'] = attrs
		else:
			#print 'Start element:', in_element, attrs
			pass

def end_element(name):
	global in_element
	in_element = in_element[:-(name.__len__() + 1)]
	if in_element not in ignore_elements:
		#print 'End element:', in_element + "." + name
		pass

def char_data(data):
	global wdata, ferr
	if in_element not in ignore_elements:
		if (in_element == ".rss.channel.item.description"):
			for line in data.split("\n"):
				if (line != ""):
					for attr in  line.split("\""):
						if attr.count("yimg.com") > 0:
							wdata['image_url'] = attr
		elif (in_element == ".rss.channel.title" and data == "Yahoo! Weather - Error"):
			ferr = 1
		elif (data != "\n" and data != " "):
			#print 'Character data:', repr(data)
			pass

p = xml.parsers.expat.ParserCreate()

p.StartElementHandler = start_element
p.EndElementHandler = end_element
p.CharacterDataHandler = char_data

# go to weather.yahoo.com
# enter your zip code in left search GO
# choose your town from drop down list
# it will refresh with your town
# look at the page source
# find a line like : href="http://weather.yahooapis.com/forecastrss?p=USNJ0107&amp;u=f">
# copy  after p= till &
# replace in next line in same place
# end with &u=c for Celsius &u=f for Fahrenheit

urlfd1 = urllib.urlopen("http://xml.weather.yahoo.com/forecastrss?p=USCA0502&u=f")
p.Parse(urlfd1.read(), 1)

#p.Parse(xwyc, 1)

if (ferr == 1):
	title = "XML fetch error"
	message = "Unable to retrieve weather information"

else:
	title = wdata['city'] + ": " + wdata['condition']['temp'] + u'°' + wdata['units']['temperature'] + " (" + wdata['condition']['text'] + ")"
	message  = "<b>Windspeed:</b>\t" + wdata['wind']['speed'] + " " + wdata['units']['speed'] + "\n"
	message += "<b>Windchill:</b>\t" + wdata['wind']['chill'] + u'°' + wdata['units']['temperature'] + "\n"
	message += "<b>Sunrise:</b>\t\t" +"Sunset:</b>"+ "\t\n" + wdata['astronomy']['sunrise'] + "\t\t" + wdata['astronomy']['sunset'] + "\n"
	message += "<b>Humidity:</b>\t" + wdata['atmosphere']['humidity'] + "%\n"
	message += "<b>Pressure:</b>\t" + wdata['atmosphere']['pressure'] + " " + wdata['units']['pressure'] + "\n"
	message += "<b>Visibility:</b>\t" + wdata['atmosphere']['visibility'] + " " + wdata['units']['distance']
	urlfn, urlhdrs = urllib.urlretrieve(wdata['image_url'], save_image_filename)
	if not urlhdrs.type == "text/html":
		icon = save_image_filename
args = [
	'notify-send',
	'--icon='+icon,
	title,
	message]

execvp("notify-send", args)
```

This one might take a few seconds to run.

```
wget http://www.randominsults.net -O - 2>/dev/null | grep \<strong\> | sed "s;^.*<i>\(.*\)</i>.*$;\1;" | while read INSULT; do notify-send -t $((1000+300*`echo -n $INSULT | wc -w`)) -i "custom icon location" "          INSULT" "$INSULT"; echo $INSULT | espeak; done
```

I've also attached my current formatted quote text file and my customized icon.

Since you appear to be more programming literate than I am, I wonder if you have any suggestions on how to make this script accept file names with spaces or periods. I have sooooo much trouble having scripts accept filenames with spaces.

```
#!/bin/bash

for i in `ls *.avi`;do avidemux2_gtk --load "${i}" --run /home/stephen/.avidemux/custom/XvidSize250.js --save "${i%%.*}"[350m].avi --quit; done
notify-send "Your Conversion Has Completed"

```

I'd be interested in any comments/suggestions.
-SK

---

### Post by inameiname on 2010-07-28
Wow, thanks for all of that. Very cool. I actually like your way of showing random facts and/or quotes or whatever than mine. One question though about the weather one, which I like as well: any way to make it longer than 3 seconds, as that's my current length? I can't seem to figure out where to put the '-t 8000' which I think would be long enough. It just uses the default one. No biggie.

I actually use Webupd8 all the time, as well as omgubuntu, and already installed the GUI and notifyosdconfig. Hence why it's only 3 seconds instead of 10 that's standard. The default was sooooooo long. Your suggestion on making just this script longer is intriguing; I'll have to look into it. 

Oh, and thanks for all the quotes. I'll reciprocate. hehe Enjoy! Basically I just used that first script above, saved in my nautilus-scripts folder, along with the text files, and can look at a random one anytime I like. And this is what I will continue to do, but now I made shell scripts with what you suggested instead of the python scripts I were using for such. 

Finally, as for your question, I'm afraid I don't know how to add the ability to have spaces and periods in filenames in your script. It is an ongoing problem for me as well for a few scripts I've tried to make as well. There was a random music script I had where I tried to figure out the same thing, but ended up getting a new script entirely from somebody that was even better so I gave up on mine. Hehe. All I do know, if it helps and you don't know, is if you add a "\" before a space in a filename it'll read the whole thing. Or add quotes to the entire filename, and it reads the whole thing, whether it has spaces or not. Perhaps if that can be included into it, so it reads whatever is in the quotes, but I wouldn't know how to include that.

---

