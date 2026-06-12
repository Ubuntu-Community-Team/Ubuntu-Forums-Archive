---
title: "Easy Flash Install 64-bit"
date: 2011-05-25
forum: General Help
---

### Post by elliotbeken on 2011-05-25
Hi all i thought i would just post this to maybe help some people with their 64-bit flash in firefox.

I have already written this on my website (elliotbeken.com) but adding it here cant hurt!

1. download the flash file ([http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_2_p3_64bit_linux_111710.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_2_p3_64bit_linux_111710.tar.gz)).

2. extract the libflashplayer.so

3. copy  libflashplayer.so to /home/USER/.mozilla/plugins (if the plugins folder isnt there simply create it! and also to see hidden folders press CTRL + H)

4. restart/close firefox and flash should work !!

hope this helps

---

### Post by .psd on 2011-05-25
As a n00b, I can bet this topic will be viewed by n00bs, who like me had no understanding of how to copy a file to a restricted location. So n00bs, consider this:

Open a terminal, type this to open a file explorer with root access (in other words, browse your files with the ability to copy/paste wherever you want):
```
gksu nautilus
```

Then you can move the file around without spending half the day learning to use the terminal to move a file to a restricted location.

---

### Post by 5149.5 on 2011-05-25
Installing the flashaid plugin and running it is much easier.

---

### Post by oldos2er on 2011-05-25
> **.psd said:**
> As a n00b, I can bet this topic will be viewed by n00bs, who like me had no understanding of how to copy a file to a restricted location. 

/home/user is not a restricted location.

---

### Post by novinick on 2011-05-25
yes , first method works for me for some time now

unpack &&  copy // no sweat
:guitar:

---

### Post by elliotbeken on 2011-05-25
i agree 5149.5 i used to use flash aid but if i can have the same feature without an exter addon all the better..

---

### Post by lovinglinux on 2011-05-25
> **elliotbeken said:**
> i agree 5149.5 i used to use flash aid but if i can have the same feature without an exter addon all the better..

I am the developer of [Flash-Aid]("http://www.webgapps.org/add-ons/flash-aid"), so I am biased, but it allows to install the plugin from Adobe pretty easily. Additionally, it warns you when there is a new Flash version from Adobe Labs, which you don't have if you install it manually. Not to mention the performance tweaks that Flash-Aid applies to your system.

It also allows to install Flash from the repos or copy the plugin from Google Chrome (32bit only).

The latest version of [Flash-Aid]("http://www.webgapps.org/add-ons/flash-aid") has been approved by Mozilla today and it has tons of improvements. Now it has a Wizard Mode, 3 Quick Modes and an Advanced mode. The last one is pretty much like the old version interface. The Quick Modes allows to run the script with default options with only two clicks and the Wizard guides you through the options.

---

### Post by novinick on 2011-05-26
heer heer , nice plugin :popcorn:
was not aware of this plugin , but now i am thanks ;)

is it works with flash square 64 bit ? sry for asking 
[http://labs.adobe.com/technologies/flashplayer10/square/](http://labs.adobe.com/technologies/flashplayer10/square/)

any possibility of suporting archived versions, may come in handy
on xubutu for older laptops or systems to have flash 9 for example  ?
(despite security implications)
[http://kb2.adobe.com/cps/142/tn_14266.html](http://kb2.adobe.com/cps/142/tn_14266.html)

it looks like 
[Flash Player 9.0.280 and higher]("http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp9r280_plus_archive.zip") (21.8 MB) is 21 mb
and 
  [Flash Player 10.1.102.64 and 9.0.289.0]("http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp_10.1.102.64_and_9.0.289.0_archive.zip") (126 MB)
is 126 mb bundle

---

### Post by lovinglinux on 2011-05-26
> **novinick said:**
> is it works with flash square 64 bit

Yes, it installs flash square 64bit by default on 64bit systems.

> **novinick said:**
> any possibility of suporting archived versions, may come in handy
on xubutu for older laptops or systems to have flash 9 for example  ?

Yes. Select the "Advanced Mode", then in the installation option, select "Custom". A new field will be displayed. Type the path to the flash 9 tar.gz file or use the search button. You can also put http link here instead of the file path. So you can put the link to the flash 9 plugin on Adobe's site, as long as the link is to a tar file containing the libflashplayer.so.

---

