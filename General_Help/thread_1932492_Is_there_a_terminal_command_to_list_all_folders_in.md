---
title: "Is there a terminal command to list all folders in a directory by size?"
date: 2012-02-27
forum: General Help
---

### Post by Rytron on 2012-02-27
Hi.

Is there a terminal command to list all folders in a directory by size?

I know of **du -h**.

Also, how can I get du to ignore hidden files and folders?

I also want it to ignore sub folders in the output.

Thanks.

---

### Post by cortman on 2012-02-27
```
du -h --max-depth=1
```

As far as excluding hidden folders --exclude='.*' SHOULD work, but I haven't gotten it to yet...

---

### Post by Rytron on 2012-02-28
> **cortman said:**
> ```
du -h --max-depth=1
```

As far as excluding hidden folders --exclude='.*' SHOULD work, but I haven't gotten it to yet...

Hi cortman. It is not listing them in order of size.

---

### Post by plucky on 2012-02-28
Try ```
ls -lhS
``` Use Capital S not lowercase s

---

### Post by Rytron on 2012-02-28
> **plucky said:**
> Try ```
ls -lhS
``` Use Capital S not lowercase s

Hey plucky.

That orders all files in order from largest to smallest. Can you get it to only show and order folders from largest to smallest?

---

### Post by texpat on 2012-02-28
> **Rytron said:**
> Hi cortman. It is not listing them in order of size.

If you do away with the -h option and pipe it into sort..

```
du --max-depth=1 |sort -gr
```

---

### Post by Rytron on 2012-02-28
> **texpat said:**
> If you do away with the -h option and pipe it into sort..

```
du --max-depth=1 |sort -g -r
```

Take a bow.

571012 is showing instead of 558MB. Can it be shown in MB and ordered from largest to smallest? It is currently ordered smallest to largest.

You are nearly there. ;)

Update: I notice that if I use **-h** in your code - it will put 558M then 556M then 545M etc. at the top and 1.8G and 1.4G at the bottom. :confused:

---

### Post by texpat on 2012-02-28
> **Rytron said:**
> Take a bow.

571012 is showing instead of 558MB. Can it be shown in MB and ordered from largest to smallest? It is currently ordered smallest to largest.

You are nearly there. ;)

Update: I notice that if I use **-h** in your code - it will put 558M then 556M then 545M etc. at the top and 1.8G and 1.4G at the bottom. :confused:

That is because the -g option in sort will sort numerically: it only looks at the numbers. It'll only look as far as the numbers go and sort those. It can't tell that 1G is bigger than, say, 2M.

---

### Post by Rytron on 2012-02-28
> **texpat said:**
> That is because the -g option in sort will sort numerically: it only looks at the numbers. It'll only look as far as the numbers go and sort those. It can't tell that 1G is bigger than, say, 2M.

I see.

---

### Post by Khayyam on 2012-02-28
This is one of those times when I say to myself "there has to be a better way than this!" ... so take my "solution" as no more than a lapse into temporary insanity:

```
du --max-depth=0 --exclude='.*' */ | sort -nr |awk '{i=$1/1024; if(i >= 1) printf("%dMB %s\n", i,$2);}'
```

If any direcotory is < 1MB then the results are excluded (otherwise we'd end up with directories of "0MB").

HTH ... khay

---

### Post by Rytron on 2012-02-28
> **Khayyam said:**
> This is one of those times when I say to myself "there has to be a better way than this!" ... so take my "solution" as no more than a lapse into temporary insanity:

```
du --max-depth=0 --exclude='.*' */ | sort -nr |awk '{i=$1/1024; if(i >= 1) printf("%dMB %s\n", i,$2);}'
```

If any direcotory is < 1MB then the results are excluded (otherwise we'd end up with directories of "0MB").

HTH ... khay

Lookin good. The only thing is that it is showing part of the file name. It ignores spaces in names.

---

### Post by Khayyam on 2012-02-28
> **Rytron said:**
> Lookin good. The only thing is that it is showing part of the file name. It ignores spaces in names.

There are no "spaces in names", only\ protected\ spaces. In *nix a "space" is a "special character", and it is this way for a reason.

'awk' uses spaces as a field delimiter and as the above command is manipulating "space delimited fields" how is awk to know that the space in your "file\ name" is to be treated specially? We could have awk use another delimiter but then we could nolonger manipulate the space delimited fields. This is why the use of spaces in filenames is discouraged (though I have to say, this is becoming equally as much encouraged with the advent of OSX, and such like, branded as "*nix" OSes).

This is not some arbitrary rule, its simply a matter of there needing to be some consistant way to indentify an object, resource, or file. If we don't adopt a standard for doing this then "file file file" might be 1, 2 or 3 "files". For your own personal use it doesn't particularly matter, but if you need to provide a consistant means of handling these files (via network protocols, computation, etc) then its important that there is some standardised method of doing so.

There are ways of dealing with files with spaces (quoting, backslash, etc) but if you use them then you should understand that some aspects of the OS will not behave as expected (like your ability to pass data from one command to another as in the case above). There is probably some voodoo that would provide a 'fix' but it'd require getting all the fields into an array ... gah ... I don't even want to think about it.

best ... khay

---

### Post by TeoBigusGeekus on 2012-02-28
My take:
```
du -h --max-depth=1| sort -h
```
ascending sorting

```
du -h --max-depth=1| sort -rh
```
descending sorting

---

### Post by collisionystm on 2012-02-28
I always use...

du -chs * | sort -n


Replace * with the folder/s

---

### Post by Rytron on 2012-02-28
> **TeoBigusGeekus said:**
> My take:
```
du -h --max-depth=1| sort -h
```
ascending sorting

```
du -h --max-depth=1| sort -rh
```
descending sorting

Hi TeoBigusGeekus. Those mix up folders like so:

159M	./xyzdir
1.8G	./abcdir
190M    ./123dir

---

### Post by Rytron on 2012-02-28
My 1st choice code:
```
du --max-depth=1 |sort -gr
```


My 2nd choice code:
```
du -chs * | sort -n
```

---

### Post by Khayyam on 2012-02-28
I think Teo's probably nailed it with the 'sort -h' ... so

```
du -h --max-depth=0 --exclude='.*' */ | sort -rh
```

The '-h' swich must be quite recent as the coreutils I was using (earlier) didn't have that listed on the manpage.

```
% sort --version |head -1
sort (GNU coreutils) 7.1
% ls | sort -h
sort: invalid option -- 'h'
Try `sort --help' for more information.
% ssh other@host.tld
sort --version |head -1 
sort (GNU coreutils) 8.5 <== this version works
```

best ... khay

---

### Post by Khayyam on 2012-02-28
> **Rytron said:**
> My 2nd choice code:
```
du -chs * | sort -n
```

With the '-c' it'll return a directory "total" as -c produces a "grand total" of all directories.

best ... khay

---

### Post by Khayyam on 2012-02-28
> **Rytron said:**
> [..] Those mix up folders like so:

159M    ./xyzdir
1.8G    ./abcdir
190M    ./123dir

Are you sure? ... it seems to order by size here.

```
% cd /usr/share
% du -h --max-depth=0 --exclude='.*' */ | sort -rh 
289M    share/
170M    lib/
41M     bin/
15M     include/
2.7M    sbin/
128K    local/
96K     lib64/
8.0K    games/
4.0K    src/
```

---

### Post by Rytron on 2012-02-28
> **Khayyam said:**
> Are you sure? ... it seems to order by size here.

```
% cd /usr/share
% du -h --max-depth=0 --exclude='.*' */ | sort -rh 
289M    share/
170M    lib/
41M     bin/
15M     include/
2.7M    sbin/
128K    local/
96K     lib64/
8.0K    games/
4.0K    src/
```

I get this:

```
du -h --max-depth=0 --exclude='.*' */ | sort -rh 

sort: invalid option -- 'h'
Try `sort --help' for more information.
```

---

### Post by TeoBigusGeekus on 2012-02-28
> **Rytron said:**
> Hi TeoBigusGeekus. Those mix up folders like so:

159M	./xyzdir
1.8G	./abcdir
190M    ./123dir

No such thing here... (Arch user)
```
0	./.gvfs
4.0K	./BUILDS
4.0K	./.covers
4.0K	./Downloads
4.0K	./.elinks
4.0K	./.fonts.conf.d
4.0K	./.gconfd
4.0K	./.gnome2_private
4.0K	./.pulse
4.0K	./SOURCE
8.0K	./.gphoto
8.0K	./gtk-3.0
8.0K	./.gtodo
8.0K	./.icedteaplugin
8.0K	./.mplayer
12K	./.dbus
12K	./.FontForge
12K	./.gnome
12K	./.netx
16K	./.avidemux
16K	./conky_bitly
16K	./.fltk
16K	./.gnome2
16K	./JavaScript
16K	./.qutecom
32K	./.java
36K	./conky_intellicast
36K	./.pki
44K	./accuweather_conky_modified
44K	./conky_fetchmail
48K	./.subversion
48K	./.swt
48K	./.vim
52K	./.nv
56K	./cfm_script
56K	./.dvdcss
100K	./.mysql
104K	./.mysqlgui
180K	./.adobe
228K	./Accuweather_RSS
244K	./conky_wunderground2
248K	./conky_forecast_nws
264K	./.gconf
340K	./.macromedia
432K	./Accuweather_Conky_Int_ConkyWeatherFont
476K	./accuweather_conky
480K	./.loki
584K	./.gimp-2.6
640K	./.spumux
712K	./.Skype
744K	./.googleearth
764K	./.fontconfig
832K	./.gstreamer-0.10
1.1M	./.teamviewer
1.3M	./accuweather_conky_USA
1.8M	./Accuweather_Conky_USA_Images
1.9M	./Accuweather_Conky_Int_Images
2.1M	./.claws-mail
2.7M	./Conky_WeatherCom
3.3M	./bleachbit-0.9.1
3.4M	./.local
4.6M	./.darcs
5.9M	./.themes
7.5M	./.cache
8.8M	./jpdfbookmarks-2.5.1
9.8M	./.dropbox
11M	./Teo GMail
12M	./Linux_Team_Kastoria-Linux_Lessons
12M	./tbd
13M	./TeoBigusGeekus_Conky_Weather_Scripts_24-2-12
14M	./.thumbnails
16M	./.aMule
16M	./Desktop
18M	./.fonts
19M	./.mozilla
26M	./.eclipse
31M	./.config
40M	./.icons
75M	./ANTI
93M	./google-earth
109M	./&#922;&#917;&#925;&#913;&#922;
158M	./tbd_project
163M	./.thunderbird
177M	./MIUI_Darktremor
178M	./b
256M	./Dropbox
605M	./.opera
767M	./Pictures
1.7G	./Videos
3.2G	./Documents
8.1G	./Music
16G	.
```

EDIT: Using coreutils 8.15-1

---

### Post by Khayyam on 2012-02-28
> **Rytron said:**
> I get this:

```
du -h --max-depth=0 --exclude='.*' */ | sort -rh 

sort: invalid option -- 'h'
Try `sort --help' for more information.
```

Yes, it seem the '-h' switch is something that only recent versions of sort (part of the coreutils package) have. I know it works with coreutils-8.5.

best ... khay

---

### Post by Rytron on 2012-02-28
> **Khayyam said:**
> Yes, it seem the '-h' switch is something that only recent versions of sort (part of the coreutils package) have. I know it works with coreutils-8.5.

best ... khay

Thanks. I am on coreutils_7.4.2.

---

### Post by TeoBigusGeekus on 2012-02-28
Which ubuntu version are you using?
Coreutils 8.5 [came out in April 2010]("http://ftp.gnu.org/gnu/coreutils/")...

EDIT:
> **Rytron said:**
> Thanks. I am on coreutils_7.4.2.
Ay ay ay!!!...

---

### Post by Rytron on 2012-02-28
> **TeoBigusGeekus said:**
> Which ubuntu version are you using?
Coreutils 8.5 [came out in April 2010]("http://ftp.gnu.org/gnu/coreutils/")...

EDIT:

Ay ay ay!!!...

Ubuntu 10.04 Lucid Lynx.

---

### Post by TeoBigusGeekus on 2012-02-28
> **Rytron said:**
> Ubuntu 10.04 Lucid Lynx.

Jeez, I guess these are the advantages of a rolling release; I've been using the -h option in sort for almost 2 years now - I thought it was de facto...

---

### Post by Rytron on 2012-02-28
> **TeoBigusGeekus said:**
> Jeez, I guess these are the advantages of a rolling release; I've been using the -h option in sort for almost 2 years now - I thought it was de facto...

I may upgrade in April. ;)

Just to confirm, the following lists just folders and ignores hidden files+folders?

```
du -h --max-depth=0 --exclude='.*' */ | sort -rh 
```

---

### Post by Khayyam on 2012-02-28
> **Rytron said:**
> Just to confirm, the following lists just folders and ignores hidden files+folders?

```
du -h --max-depth=0 --exclude='.*' */ | sort -rh 
```

Correct ...

---

### Post by Rytron on 2012-02-28
> **Khayyam said:**
> Correct ...

Cheers Khayyam. ;)

I have yet to come across a forum as friendly and helpful as ubuntuforums.

---

### Post by Khayyam on 2012-02-28
> **Rytron said:**
> Cheers Khayyam. I have yet to come across a forum as friendly and helpful as ubuntuforums.

Your welcome ... and Teo (it seems) and I are not even Ubuntu users.

It's should be relatively simple to update coreutils on Lucid Lynx, 'apt-get source coreutils' and then 'debuild' (see man debuild)

HTH ... khay

---

### Post by collisionystm on 2012-02-28
> **Khayyam said:**
> Your welcome ... and Teo (it seems) and I are not even Ubuntu users.

It's should be relatively simple to update coreutils on Lucid Lynx, 'apt-get source coreutils' and then 'debuild' (see man debuild)

HTH ... khay


May I inquire what distro you use?

---

### Post by matt_symes on 2012-02-28
> **collisionystm said:**
> May I inquire what distro you use?

Stab in the dark. Arch and Gentoo ? 

Hello Teo. I hope you are well.

---

### Post by TeoBigusGeekus on 2012-02-28
Hi there Matt!! Still alive...
Hope you're well.

Arch uses the latest coreutils (8.15), by the way; he uses 8.5

---

### Post by Khayyam on 2012-02-28
> **collisionystm said:**
> May I inquire what distro you use?

Ummmm ... for personal use, or in general? I'm a sys admin so I'm familar with, and/or admin, Gentoo, Debian, Redhat, *BSD. In the past I've worked on Solaris, IRIX, and other *nix.

My own machines (all ancient) have Gentoo (one with an install dating back to 2002, but still rolling), mostly its because I can build for really old machines (the PowerPC 604e for instance) and once the install is done it'll roll on for years without too much administration.

I've not had an Ubuntu install but thats more because Ubuntu doesn't really suite my needs, I'm more than happy to recommend it to others though.

best ... khay

---

### Post by Rytron on 2012-02-29
> **Khayyam said:**
> Your welcome ... and Teo (it seems) and I are not even Ubuntu users.

It's should be relatively simple to update coreutils on Lucid Lynx, 'apt-get source coreutils' and then 'debuild' (see man debuild)

HTH ... khay

Hi Khayyam.

Please elaborate.

Do I do this?

```
sudo apt-get source coreutils
```

and then

```
sudo apt-get install debuild
```

---

### Post by Khayyam on 2012-02-29
> **Rytron said:**
> Please elaborate.

Standard disclaimer: I'm not advising you to do this, I am meerly saying that its possible to roll your own package. Any systems admin type work should be performed with your full understanding of what the task involves, and so it would be bad advice for me to tell you to do x then y.

I don't even know if Ubuntu has a "devscripts" package, and how it might differ from Debian in this regard, and not being an Ubuntu user I have't done this and so can't say exactly what you should do, or how it might turn out.

Perhaps someone else here can advise, it might be worth opening another thread on the matter (in the suitable sub-forum).

I've been bitten too many times in situations when simple problems turn into catastrophes due to users not having the level of understanding required to undertake this kind of work, and so I hope you'll understand by disclaimer.

best ... khay

---

### Post by Rytron on 2012-03-01
> **Khayyam said:**
> Standard disclaimer: I'm not advising you to do this, I am meerly saying that its possible to roll your own package. Any systems admin type work should be performed with your full understanding of what the task involves, and so it would be bad advice for me to tell you to do x then y.

I don't even know if Ubuntu has a "devscripts" package, and how it might differ from Debian in this regard, and not being an Ubuntu user I have't done this and so can't say exactly what you should do, or how it might turn out.

Perhaps someone else here can advise, it might be worth opening another thread on the matter (in the suitable sub-forum).

I've been bitten too many times in situations when simple problems turn into catastrophes due to users not having the level of understanding required to undertake this kind of work, and so I hope you'll understand by disclaimer.

best ... khay

No problem, I understand. I will upgrade my Distro soon anyway. Cheers.

---

