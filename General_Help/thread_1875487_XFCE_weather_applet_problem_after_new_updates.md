---
title: "XFCE weather applet problem after new updates"
date: 2011-11-04
forum: General Help
---

### Post by DapperMe17 on 2011-11-04
Today's Xubuntu updates killed the XFCE weather applet updates.

The weather applet simply says "no data" after a reboot. 

If I remember correctly, tzdata was one of the updates.

Any ideas?

---

### Post by Toz on 2011-11-04
The license key used to connect to xoap.weather.com has become invalid. See the official bug report: [https://bugzilla.xfce.org/show_bug.cgi?id=8105]("https://bugzilla.xfce.org/show_bug.cgi?id=8105").

EDIT: Here is another link: [http://old.nabble.com/xfce4-weather-plugin-stopped-working-with-%22Invalid-License-Key%22-to32783869.html#a32783884]("http://old.nabble.com/xfce4-weather-plugin-stopped-working-with-%22Invalid-License-Key%22-to32783869.html#a32783884"). 

I had a look at the source code and noticed that the Partner ID and License Key were hard coded. I went to xoap.weather.com, re-registered my own PartnerID and License Key, updated the source with this new information and re-compiled the code. This has got me back up. Hopefully the developers will fix the issue with the ID/Key they use soon.

---

### Post by DapperMe17 on 2011-11-04
Toz,

Thanks for the info!

---

### Post by jsntyyl on 2011-11-05
> **Toz said:**
> The license key used to connect to xoap.weather.com has become invalid. See the official bug report: [https://bugzilla.xfce.org/show_bug.cgi?id=8105]("https://bugzilla.xfce.org/show_bug.cgi?id=8105").

EDIT: Here is another link: [http://old.nabble.com/xfce4-weather-plugin-stopped-working-with-%22Invalid-License-Key%22-to32783869.html#a32783884]("http://old.nabble.com/xfce4-weather-plugin-stopped-working-with-%22Invalid-License-Key%22-to32783869.html#a32783884"). 

I had a look at the source code and noticed that the Partner ID and License Key were hard coded. I went to xoap.weather.com, registered for my own PartnerID and License Key, updated the source with this new information and re-compiled the code. This has got me back up. Hopefully the developers will fix the issue with the ID/Key they use soon.

i met the same problem, can't update the weather, so i searched and found this page, then i followed your step:

1. registe a new account and got a partnerid and license key
2. replace them in /xfce4-weather-plugin-0.7.4/panel-plugin/weather.h with my own

#define PARTNER_ID       "my prartnerid"
#define LICENSE_KEY)     "my license key"

3. ./configure
4  make
5  sudo apt-get remove xfce4-weather-plugin
6  sudo make install

everything is ok, but i can't find the weather plugin in the list of window "add new item" after "sudo make install".

is there anything wrong?

---

### Post by Jose Catre-Vandis on 2011-11-05
Ah, glad it's not just me. Nice work again Toz. I'll wait for Xubuntu to sort itself out, though...:)

---

### Post by Toz on 2011-11-05
> **jsntyyl said:**
> 
everything is ok, but i can't find the weather plugin in the list of window "add new item" after "sudo make install".

is there anything wrong?

Here is how I did it:

1. Install required packages:
```
sudo apt-get install build-essential fakeroot dpkg-dev devscripts cdbs xfce4-panel-dev libxml2-dev libxfcegui4-dev hardening-includes
```

2. Create a folder to develop in:
```
mkdir ~/Development
cd ~/Development
```

3. Get the source:
```
apt-get source xfce4-weather-plugin
```

4. Go to the source directory:
```
cd xfce4-weather-plugin-0.7.4
```

5. Update the version changelog:
```
dch -i
```
...enter comment regarding change and save file

6. Edit the source:
```
leafpad panel-plugin/weather.h
```
...and edit the two define lines with your partner ID and license key:
> 
#define PARTNER_ID       "xxxxxxxxxx"
#define LICENSE_KEY      "yyyyyyyyyyyyyyyy"
...save file.

7. Build the new package:
```
dpkg-buildpackage -rfakeroot -uc -b
```

8. Install the new package:
```
sudo dpkg -i ../xfce4-weather-plugin_0.7.4-1ubuntu1_i386.deb
```

Hope I haven't missed anything. Good luck.

---

### Post by madmack on 2011-11-05
how in the world did you guys obtain the partner_id and license_key by registering? apparently xaop is subscription (read: fees) only.

I went to this website to get my own pair of keys:

[http://www.weather.com/services/xmloap.html](http://www.weather.com/services/xmloap.html)

instead, i got a "magic key" that I can try in their new sandbox trial period.

---

### Post by azertyh on 2011-11-05
> **Toz said:**
> The license key used to connect to xoap.weather.com has become invalid. See the official bug report: [https://bugzilla.xfce.org/show_bug.cgi?id=8105]("https://bugzilla.xfce.org/show_bug.cgi?id=8105").


ok. glad to know that it's a bug. hope that it will be fixed.

---

### Post by Toz on 2011-11-05
> **madmack said:**
> how in the world did you guys obtain the partner_id and license_key by registering? apparently xaop is subscription (read: fees) only.

I went to this website to get my own pair of keys:

[http://www.weather.com/services/xmloap.html](http://www.weather.com/services/xmloap.html)

instead, i got a "magic key" that I can try in their new sandbox trial period.

I had registered there a few years back when I was playing with conky weather scripts. I logged into my account and was asked to re-confirm my profile, which I did, and it still listed my previous subscription information (including my xoap xml feed). I then edited the xfce weather plugin source code with the partner_id and license_key shown there and it worked.

---

### Post by madmack on 2011-11-05
> **Toz said:**
> I had registered there a few years back when I was playing with conky weather scripts. I logged into my account and was asked to re-confirm my profile, which I did, and it still listed my previous subscription information (including my xoap xml feed). I then edited the xfce weather plugin source code with the partner_id and license_key shown there and it worked.

from the conky thread, it looks like weather.com is suspending these free accounts and moving to a new subscription based service.

looks like the xfce devs will have to come up with a new service (wunderground, accuweather.. ) and rewrite their parser if they want to avoid paying the minimum ~$64/month.

meanwhile, i get to live with the "No Data" staring at me in the panel. :(

---

### Post by DapperMe17 on 2011-11-05
Great information from all.

=D>

---

### Post by hwttdz on 2011-11-06
Wouldn't it make sense to point it at the noaa forecasts/conditions, as this is likely where all these sources are getting their information from and it has the upside of being free.

---

### Post by DapperMe17 on 2011-11-06
Agreed.

---

### Post by hwttdz on 2011-11-06
Just to keep my own notes as I go along...
Here are two possible feeds from the noaa, I think the second would be preferable, as it's smaller, but it would also require I know how to read a weather report.  It would make the code easier to write, but harder to understand.  Haven't decided which way is better to go, thoughts?

[http://weather.noaa.gov/pub/data/observations/metar/decoded/KNYC.TXT](http://weather.noaa.gov/pub/data/observations/metar/decoded/KNYC.TXT)
```
NEW YORK CITY CENTRAL PARK, NY, United States (KNYC) 40-47N 073-58W 48M
Nov 06, 2011 - 07:51 AM EST / 2011.11.06 1251 UTC
Wind: Variable at 6 MPH (5 KT):0
Visibility: 10 mile(s):0
Sky conditions: clear
Temperature: 42.1 F (5.6 C)
Dew Point: 28.9 F (-1.7 C)
Relative Humidity: 59%
Pressure (altimeter): 30.56 in. Hg (1034 hPa)
ob: KNYC 061251Z AUTO VRB05KT 10SM CLR 06/M02 A3056 RMK AO2 SLP340 T00561017 TSNO 
cycle: 13
```


[http://weather.noaa.gov/pub/data/observations/metar/stations/KNYC.TXT](http://weather.noaa.gov/pub/data/observations/metar/stations/KNYC.TXT)
```
2011/11/06 12:51
KNYC 061251Z AUTO VRB05KT 10SM CLR 06/M02 A3056 RMK AO2 SLP340 T00561017 TSNO 
```

So that's a date (in gmt)
the vbr05kt is winds variable at 5 knots
CLR is for "Sky conditions: clear"
It's possible that "A3056" -> "Temperature: 42.1 F (5.6 C)" in which case I have no idea what the "A30" is for...

---

### Post by Toz on 2011-11-06
There is also the google weather api: [http://www.google.com/ig/api?weather=central+park,ny]("http://www.google.com/ig/api?weather=central+park,ny").

Here is a bash script to parse the file: [http://forum.unixclubhouse.com/index.php?topic=28.0]("http://forum.unixclubhouse.com/index.php?topic=28.0"). Unfortunately, this won't work for the xfce4-weather-plugin (unless someone changes the code), but it could work for conky.

---

### Post by hwttdz on 2011-11-06
Yeah, I'm parsing the noaa feed for my conky currently.  Libxml makes the xfce applet go around, which on the one hand is a good plan because xml is a convenient way of getting the data but it means that switching over to noaa would be more effort.  I don't think it's going to happen this week.

For the interim you can put this in a genmon applet and at least get the temperature back (which is what I'm mostly after anyways).

```
#!/usr/bin/perl
use strict;
my @conditions=`curl --silent http://weather.noaa.gov/pub/data/observations/metar/decoded/KNYC.TXT 2>&1|grep 'Temperature'`;
for(my $i=0; $i < scalar(@conditions); ++$i)
{
	my $line = lc($conditions[$i]);
	chomp($line);
	$line =~ s/(\w+)/\u\L$1/g;
	$line =~ s/^\.//g;
	$line =~ s/.*:\s+//g;
	$line =~ s/\s+F.*/°F/g;
	print "$line\n";
}
```

And yes that's hacked from something which reads multiple lines if you're wondering about the array-ness.

---

### Post by madmack on 2011-11-06
> **hwttdz said:**
> Yeah, I'm parsing the noaa feed for my conky currently.  Libxml makes the xfce applet go around, which on the one hand is a good plan because xml is a convenient way of getting the data but it means that switching over to noaa would be more effort.  I don't think it's going to happen this week.

For the interim you can put this in a genmon applet and at least get the temperature back (which is what I'm mostly after anyways).

```
#!/usr/bin/perl
use strict;
my @conditions=`curl --silent http://weather.noaa.gov/pub/data/observations/metar/decoded/KNYC.TXT 2>&1|grep 'Temperature'`;
for(my $i=0; $i < scalar(@conditions); ++$i)
{
	my $line = lc($conditions[$i]);
	chomp($line);
	$line =~ s/(\w+)/\u\L$1/g;
	$line =~ s/^\.//g;
	$line =~ s/.*:\s+//g;
	$line =~ s/\s+F.*/°F/g;
	print "$line\n";
}
```

And yes that's hacked from something which reads multiple lines if you're wondering about the array-ness.


I managed to make it output the temp in C.


I'm not exactly the perl regex guru, but thought I'd share what I have.

replace the for loop with this

```

for(my $i=0; $i < scalar(@conditions); ++$i)
{
	my $line = lc($conditions[$i]);
	chomp($line);
	$line =~ s/(\w+)/\u\L$1/g;
	$line =~ s/^\.//g;
	$line =~ s/.*:\s+//g;
	$line =~ s/.*[(]//g;
	$line =~ s/[)]//g;
	print "$line\n";
}

```

---

### Post by hwttdz on 2011-11-06
Because my perl was ugly, if people are going to use this, here's for F
```
#!/usr/bin/perl
use strict;
my $temp=`curl --silent http://weather.noaa.gov/pub/data/observations/metar/decoded/KNYC.TXT 2>&1|grep 'Temperature'`;
chomp($temp);
$temp =~ s/.*:\s+//g; # remove up to the first :
$temp =~ s/\s*F.*/°F/g; # replace one or more spaces followed by F to the end of the line with, °F
print "$temp\n";
```

And for C:
```
#!/usr/bin/perl
use strict;
my $temp=`curl --silent http://weather.noaa.gov/pub/data/observations/metar/decoded/KNYC.TXT 2>&1|grep 'Temperature'`;
chomp($temp);
$temp =~ s/.*\(//g; # remove up to the first (
$temp =~ s/\s*C.*/°C/g; # remove spaces followed by C to the end of the line with °C
print "$temp\n";
```

because I looked at that (being my original code) and had no idea what it was doing.  Dependencies are obviously perl and curl.

---

### Post by gmargo on 2011-11-06
I wrote a quick shell script wrapper around the **weather-util(1)** command to get the temperature for the xfce4-genmon-plugin.
[http://packages.ubuntu.com/oneiric/weather-util](http://packages.ubuntu.com/oneiric/weather-util)

Here's my script for Moffett Field (KNUQ).  Adjust as needed for your local site.
```

#!/bin/sh

# weather-util -i KNUQ
# Current conditions at Moffett Field, CA (KNUQ)
# Last updated Nov 06, 2011 - 11:56 AM EST / 2011.11.06 1656 UTC
#   Temperature: 55.9 F (13.3 C)
#   Relative Humidity: 66%
#   Wind: from the WNW (300 degrees) at 3 MPH (3 KT)
#   Sky conditions: overcast

weather-util -i KNUQ | \
        grep "Temperature:" | \          
        sed 's/.*Temperature: //' | \
        sed 's/^\([-\.0-9]\+ [A-Za-z]\).*/\1/'


```

---

### Post by BobMarleyy on 2011-11-07
Hello everyone,

I also read the bug report:
[https://bugzilla.xfce.org/show_bug.cgi?id=8105](https://bugzilla.xfce.org/show_bug.cgi?id=8105)

Does anyone know some alternative to xfce4-weather-plugin?
It should reside in the panel and show at least the temperature. It should be available for Xubuntu (11.10). It should have a how to install when it involves using scripting/programming, because I am a newbie.

For the time being, I will stare at No Data from the xfce4-weather-plugin, until it is fixed.

It looks like this happened before with xfce4-weather-plugin, see the About section on:
[http://goodies.xfce.org/projects/panel-plugins/xfce4-weather-plugin](http://goodies.xfce.org/projects/panel-plugins/xfce4-weather-plugin)
In addition, xfce4-weather lacks the radar map. Therefore Xubuntu users might want an alternative for the xfce4-weather-plugin.

Cheers,
Bob

---

### Post by jsntyyl on 2011-11-07
> **Toz said:**
> Here is how I did it:

......

7. Build the new package:
```
dpkg-buildpackage -rfakeroot -uc -b
```8. Install the new package:
```
sudo dpkg -i ../xfce4-weather-plugin_0.7.4-1ubuntu1_i386.deb
```Hope I haven't missed anything. Good luck.

em... tried you said, it works again! thank you very much!
but i am confused why the compile doesn't work.

---

### Post by gmargo on 2011-11-07
> **gmargo said:**
> I wrote a quick shell script wrapper around the **weather-util(1)** command to get the temperature for the xfce4-genmon-plugin.


That works but does not restore properly after logout/login.  The **xfce4-genmon-plugin** is happily running, except it no longer displays on the panel.

Killing the plugin doesn't work either - the parent process (**xfce4-panel**) merrily restarts it.

---

### Post by Toz on 2011-11-07
[https://bugzilla.xfce.org/show_bug.cgi?id=7449]("https://bugzilla.xfce.org/show_bug.cgi?id=7449"). There is a patch there is you're the compiling kind.

I found that you could also go to Panel->Panel Preferences->Items tab, open and close the preferences for the applet it will become visible again.

I'm going to have a go at recompiling with the patch.

EDIT: Patching worked. Patch files are: 
1. [http://bugzilla.xfce.org/attachment.cgi?id=3064]("http://bugzilla.xfce.org/attachment.cgi?id=3064")
2. [https://bugzilla.xfce.org/attachment.cgi?id=3464]("https://bugzilla.xfce.org/attachment.cgi?id=3464") (Save as xfce-start.patch)
Put both files in debian/patches and recompile. Source package is xfce4-genmon-applet.

---

### Post by gmargo on 2011-11-07
Thanks Toz, that patch does make xfce4-genmon-plugin work as expected.

---

### Post by DapperMe17 on 2011-11-07
Toz,

Thanks for your time with this!

Does your work fix the xfce-weather-applet as it originally was?

If so, could you break down the final process for those who are simply users, and not coders?

Thanks!

---

### Post by Toz on 2011-11-08
> **DapperMe17 said:**
> Toz,

Thanks for your time with this!

Does your work fix the xfce-weather-applet as it originally was?

If so, could you break down the final process for those who are simply users, and not coders?

Thanks!

Have a look at the official bug report at: [https://bugzilla.xfce.org/show_bug.cgi?id=8105]("https://bugzilla.xfce.org/show_bug.cgi?id=8105"). Post #9 looks like they're going to be using another set of ids and keys. The id and key is posted there if you want to use it (like mine, they still work). You can either wait for that to play out (it really isn't a difficult task for them to fix the applet upstream) or follow the instructions in post #6 of this thread. Unfortunately, those instructions require you to recompile code because the id/key pair is hard-coded.

The real issue, I think, is that the weather channel is going to put an end to all keys and the whole applet will need to be re-written to use another weather service. This may just end up being a temporary solution. The second part of this thread, see post #19, talks about using the xfce4-genmon-applet to connect to and parse the info from another weather service. This applet can be configured to look like and work like the weather applet. Unfortunately, it too has a bug that prevents it from being visible on the panel on restart. There exists a patch to fix that, but again, you need to recompile. There is a bug upstream for this as well.

---

### Post by DapperMe17 on 2011-11-08
Thanks Toz,

I'll take a look at the bug report, or just wait a while for the official fix.

Kudos!
:popcorn:

---

### Post by DapperMe17 on 2011-11-20
Debian has updated their XFCE4 weather plugin. 

Go to [http://packages.debian.org/sid/xfce/xfce4-weather-plugin](http://packages.debian.org/sid/xfce/xfce4-weather-plugin) and download for your architecture.

In Xubuntu, remove the current XFCE weather applet in Synaptic. 

Install the downloaded file. 

Then, add a new weather applet to your panel and configure. 

You'll have a working weather applet until Xfce releases the updated version and it's inserted into the Ubuntu repos. 

:popcorn:

---

### Post by BenB1 on 2011-11-21
> **DapperMe17 said:**
> Debian has updated their XFCE4 weather plugin. 

Go to [http://packages.debian.org/sid/xfce/xfce4-weather-plugin](http://packages.debian.org/sid/xfce/xfce4-weather-plugin) and download for your architecture.

In Xubuntu, remove the current XFCE weather applet in Synaptic. 

Install the downloaded file. 

Then, add a new weather applet to your panel and configure. 

You'll have a working weather applet until Xfce releases the updated version and it's inserted into the Ubuntu repos. 

:popcorn:


**Arggggggghhhhhhh! **Dependency Rage! "Make Hulk Mad, Depend, Depend, Depend .... Hulk Smash!":lolflag:

And getting the libc6 package presents a "it breaks something in ubuntu, dude, sure ya wanna?"

Just as well use Debian for all the dependencies required for something simple. Um, been there done that.
Starting to understand why people fuss about Linux not being as easy as many suggest it to be.

---

### Post by gmargo on 2011-11-21
> **BenB1 said:**
> Hulk Smash!"


Think soothing thoughts Hulk.....  Besides, no one can predict when this license key will expire.  But you can bank on it expiring sometime, as weather.com wants to extract ca$h from you.

The patch itself is trivial and easy to apply and recompile.  See the attached file.

Or, for Oneiric, this fellow has generated a PPA:
[https://launchpad.net/~lordnightcon/+archive/xfce4.8-weather-plugin]("https://launchpad.net/%7Elordnightcon/+archive/xfce4.8-weather-plugin")

---

### Post by KBD47 on 2011-11-23
I removed the weather applet and installed indicator-weather from synaptic package manager and have my weather back again on Xubuntu 11.10.
KBD47

---

### Post by PhilGil on 2011-11-25
A bit late to the party, but I just wanted to thank [hwttdz]("http://ubuntuforums.org/member.php?u=175488") for the generic monitor applet script s/he posted upthread. Works perfectly. Thanks!

---

### Post by brmiller on 2011-12-10
> **jsntyyl said:**
> em... tried you said, it works again! thank you very much!
but i am confused why the compile doesn't work.

Heh... compiling is too hard (yeah, I'm a sw engineer too...)

I just edited /usr/lib/xfce4-weather-plugin/xfce4/panel-plugins/xfce4-weather-plugin using bvi (a hex editor) and replaced the previous partner id and license key with the ones listed in the patch file elsewhere in this thread.  10 seconds and I have weather again.

Brendan

---

### Post by Gammell on 2011-12-21
> **brmiller said:**
> Heh... compiling is too hard (yeah, I'm a sw engineer too...)

I just edited /usr/lib/xfce4-weather-plugin/xfce4/panel-plugins/xfce4-weather-plugin using bvi (a hex editor) and replaced the previous partner id and license key with the ones listed in the patch file elsewhere in this thread.  10 seconds and I have weather again.

Brendan
Thanks! This worked like a charm (once I figured out I wanted "R" mode, and not "I" like in vi).

I used the key found in the patch listed [here]("https://projects.archlinux.org/svntogit/packages.git/commit/trunk?h=packages/xfce4-weather-plugin&id=ea5bc563d6deeeb531a8509da684d36b3ad9a58e")

---

### Post by Marzata on 2011-12-29
xfce4-weather-plugin just got updated. Please, upgrade your systems. Thank you, Xubuntu community!

---

### Post by missmoondog on 2011-12-31
> **Marzata said:**
> xfce4-weather-plugin just got updated. Please, upgrade your systems. Thank you, Xubuntu community!

yes,
it got updated yesterday and that was when i noticed it didn't work! installed on another machine this morning and guess what, it still doesn't work!

4 pages of replies to something as simple as this, sheesh!

never use these kind of applets on my machines, but seeing as how it was the only update i've received in a week, i thought i'd look at it.

it's gone. NEVER to come back!!  :)


> **BenB1 said:**
> **Arggggggghhhhhhh! **Dependency Rage! "Make Hulk Mad, Depend, Depend, Depend .... Hulk Smash!":lolflag:

And getting the libc6 package presents a "it breaks something in ubuntu, dude, sure ya wanna?"

Just as well use Debian for all the dependencies required for something simple. Um, been there done that.
Starting to understand why people fuss about Linux not being as easy as many suggest it to be.


"Starting to understand why people fuss about Linux not being as easy as many suggest it to be."

i've been saying exactly that since the very first time i tried ubuntu way back on 5.04!!

---

### Post by Marzata on 2011-12-31
> **missmoondog said:**
> yes,
it got updated yesterday and that was when i noticed it didn't work! installed on another machine this morning and guess what, it still doesn't work!



It works today. :D

---

### Post by Toz on 2011-12-31
> **missmoondog said:**
> yes,
it got updated yesterday and that was when i noticed it didn't work! installed on another machine this morning and guess what, it still doesn't work!

4 pages of replies to something as simple as this, sheesh!

never use these kind of applets on my machines, but seeing as how it was the only update i've received in a week, i thought i'd look at it.

it's gone. NEVER to come back!!  :)





"Starting to understand why people fuss about Linux not being as easy as many suggest it to be."

i've been saying exactly that since the very first time i tried ubuntu way back on 5.04!!

I think you should direct your concerns to the folks over at weather.com. They are the ones who decided to stop offering the weather feed service as a _free_ service, thus affecting all applications that relied on it. This really isn't a "Linux" problem.

---

### Post by PhilGil on 2011-12-31
I don't completely disagree with the previous posters, Linux can be more fiddly than Windows or Mac. However, in this particular case, the loss of the weather feed hosed all applications that receive their data from weather.com, including Windows and mobile apps.

---

### Post by Marzata on 2011-12-31
Can't they use [http://freemeteo.com/](http://freemeteo.com/) ?

---

### Post by Toz on 2011-12-31
> **Marzata said:**
> Can't they use [http://freemeteo.com/](http://freemeteo.com/) ?

Looks like they're going to use yr.no. See: [https://bugzilla.xfce.org/show_bug.cgi?id=8105]("https://bugzilla.xfce.org/show_bug.cgi?id=8105")

---

### Post by Marzata on 2011-12-31
[http://www.yr.no/](http://www.yr.no/) is great.

---

### Post by rburkartjo on 2012-05-01
or you could just install weather indicator from the ubuntu software center. that is what i did

---

### Post by Marzata on 2012-05-01
[http://goodies.xfce.org/projects/panel-plugins/xfce4-weather-plugin](http://goodies.xfce.org/projects/panel-plugins/xfce4-weather-plugin) works now.

---

### Post by rburkartjo on 2012-05-01
and how do you install and where tks

---

### Post by Marzata on 2012-05-01
Install xfce4-goodies package. Then add "Weather Update" applet to the panel.

---

