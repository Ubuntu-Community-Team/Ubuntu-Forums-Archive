---
title: "regexp question"
date: 2011-04-04
forum: General Help
---

### Post by dpastern on 2011-04-04
I have an issue with /etc/bind/services.conf - somewhere in it is just .com.au, amongst the correct entries.  I want to find ONLY that line and remove it, so BIND behaves.  I've spent 90 mins googling and trying a variety of things with no luck.  I do not know sed/awk/regexp, so I am stumped.

Any help appreciated.

Dave

PS issue is on Debian, but should apply to any distro...just putting this out there for anyone smarter than me who knows how to do what I need...

---

### Post by mendhak on 2011-04-04
You could start with a simple command to just search for .com.au

grep .com.au /etc/bind/services.conf

That will search the services.conf file for ".com.au" (without quotes)

Another way - you could also open the file in a text editor.  Press Alt+F2, in the run dialog do

gksu gedit /etc/bind/services.conf

Then in gedit, find that string.

---

### Post by dpastern on 2011-04-04
yeah I tried grep .com.au and it just finds all of the buggers...there's 2800 entries in this services.conf file (not all of them are .com.au, some are other domain types).  

it's a server, so command line only, no GUI.

I couldn't figure out via Google how to search for the shortest line (# of characters).  Tried a few things like awk /^"zone .com.au" /etc/bind/services.conf (don't think that'll work cos of the blank character anyways).

I could manually eyeball all 2800 odd lines, but there *has* to be an easier way.  

Thanks for the reply though.

Dave

---

### Post by nothingspecial on 2011-04-04
grep -x will match exactly that line, ie it will only match a line that is zone .com.au

and not any line with that string in it.

---

### Post by dpastern on 2011-04-04
Didn't know that.  So something like:

grep -x "zone .com.au"

?

I don't think that it'll like the space somehow.  Will try tomorrow when I'm @ work.  Thanks.

Cheers,

Dave

---

### Post by nothingspecial on 2011-04-04
If the line you wish to remove is exactly "zone .com.au" and no other line that you want to keep starts with it then

```
sed -e /^zone\ \.com\.au$/d /etc/bind/services.conf 
``` will get rid of it.

Make a backup first, just in case

---

### Post by Vaphell on 2011-04-04
afaik there is no need to backup when there is no -i switch in sed (change in place)

---

### Post by dpastern on 2011-04-04
Cool, much thanks guys, will try today when I'm @ work.  It's not critical to remove this, it doesn't stop BIND from working, I just don't like seeing uneccessary errors in the syslog!

Dave

---

### Post by dpastern on 2011-04-04
mmm Didn't work :(  It just brings back *all* of the domains with .com.au in them...

This is the format of the services.conf file:

```
zone "domainname.com.au" { type master; file "domainname.com.au"; };
```

If that helps any sed guru?  I've tried for years to learn sed, I just can't wrap my head around it...

Dave

---

### Post by nothingspecial on 2011-04-05
I was under the impression the line you wanted to remove was exactly
```
zone .com.au
```

The -e flag will print what will happen if you do it but not actually do it. The -i flag will do it (if you see what I mean).

For example, see the "zone .com.au" in red, at different points in different lines and the one in green we want to remove?

```
ns@netbook:~$ cat example.txt 
iled
[18213.798659] FAT: Directory bread(block 19143) failed
[18213.798708] FAT: Directory bread(block 19144) failed
[18213.798757] FAT: Directory bread(block 19145) failed
[18213.887424] FAT: Directory [COLOR="Red"]zone .com.au[/COLOR] bread(block 19302) failed
[18213.887478] FAT: Directory bread(block 19303) failed
[18213.887531] FAT: Directory bread(block 19304) failed
[18213.887581] FAT: Directory bread(block 19305) failed
[18213.887707] FAT: Directory bread(block 15546666) failed
[18213.887763] FAT: Directory bread(block 15546667) failed
[18213.887816] FAT: Directory bread(block 15546668) failed [COLOR="Red"]zone .com.au[/COLOR]
[COLOR="Lime"]zone .com.au[/COLOR]
[18213.887870] FAT: Directory bread(block 15546669) failed
[18213.887995] FAT: Directory bread(block 29484998) failed
[18213.899606] FAT: Directory bread(block 29484999) failed
[18213.899672] FAT: Directory bread(block 29485000) failed
[18213.899727] FAT: Directory bread(block 29485001) [COLOR="Red"]zone .com.au[/COLOR] failed
[19173.845415] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[33045.796913] CE: hpet increased min_delta_ns to 20113 nsec
[33045.797171] CE: hpet increased min_delta_ns to 30169 nsec
[33045.797446] CE: hpet increased min_delta_ns to 45253 nsec
[40425.796462] CE: hpet increased min_delta_ns to 67879 nsec
[53270.959214] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600
```

If we do it with the -e flag you can see that the regex will remove the green line

```
ns@netbook:~$ sed -e /^zone\ \.com\.au$/d example.txt 
iled
[18213.798659] FAT: Directory bread(block 19143) failed
[18213.798708] FAT: Directory bread(block 19144) failed
[18213.798757] FAT: Directory bread(block 19145) failed
[18213.887424] FAT: Directory [COLOR="Red"]zone .com.au[/COLOR] bread(block 19302) failed
[18213.887478] FAT: Directory bread(block 19303) failed
[18213.887531] FAT: Directory bread(block 19304) failed
[18213.887581] FAT: Directory bread(block 19305) failed
[18213.887707] FAT: Directory bread(block 15546666) failed
[18213.887763] FAT: Directory bread(block 15546667) failed
[18213.887816] FAT: Directory bread(block 15546668) failed [COLOR="Red"]zone .com.au[/COLOR]
[18213.887870] FAT: Directory bread(block 15546669) failed
[18213.887995] FAT: Directory bread(block 29484998) failed
[18213.899606] FAT: Directory bread(block 29484999) failed
[18213.899672] FAT: Directory bread(block 29485000) failed
[18213.899727] FAT: Directory bread(block 29485001) [COLOR="Red"]zone .com.au[/COLOR] failed
[19173.845415] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[33045.796913] CE: hpet increased min_delta_ns to 20113 nsec
[33045.797171] CE: hpet increased min_delta_ns to 30169 nsec
[33045.797446] CE: hpet increased min_delta_ns to 45253 nsec
[40425.796462] CE: hpet increased min_delta_ns to 67879 nsec
[53270.959214] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600
```

But it is still there

```
ns@netbook:~$ cat example.txt 
iled
[18213.798659] FAT: Directory bread(block 19143) failed
[18213.798708] FAT: Directory bread(block 19144) failed
[18213.798757] FAT: Directory bread(block 19145) failed
[18213.887424] FAT: Directory [COLOR="Red"]zone .com.au[/COLOR] bread(block 19302) failed
[18213.887478] FAT: Directory bread(block 19303) failed
[18213.887531] FAT: Directory bread(block 19304) failed
[18213.887581] FAT: Directory bread(block 19305) failed
[18213.887707] FAT: Directory bread(block 15546666) failed
[18213.887763] FAT: Directory bread(block 15546667) failed
[18213.887816] FAT: Directory bread(block 15546668) failed [COLOR="Red"]zone .com.au[/COLOR]
[COLOR="Lime"]zone .com.au[/COLOR]
[18213.887870] FAT: Directory bread(block 15546669) failed
[18213.887995] FAT: Directory bread(block 29484998) failed
[18213.899606] FAT: Directory bread(block 29484999) failed
[18213.899672] FAT: Directory bread(block 29485000) failed
[18213.899727] FAT: Directory bread(block 29485001) [COLOR="Red"]zone .com.au[/COLOR] failed
[19173.845415] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[33045.796913] CE: hpet increased min_delta_ns to 20113 nsec
[33045.797171] CE: hpet increased min_delta_ns to 30169 nsec
[33045.797446] CE: hpet increased min_delta_ns to 45253 nsec
[40425.796462] CE: hpet increased min_delta_ns to 67879 nsec
[53270.959214] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600
```

With the -i flag it really is gone

```
ns@netbook:~$ sed -i /^zone\ \.com\.au$/d example.txt 
ns@netbook:~$ cat example.txt 
iled
[18213.798659] FAT: Directory bread(block 19143) failed
[18213.798708] FAT: Directory bread(block 19144) failed
[18213.798757] FAT: Directory bread(block 19145) failed
[18213.887424] FAT: Directory [COLOR="Red"]zone .com.au[/COLOR] bread(block 19302) failed
[18213.887478] FAT: Directory bread(block 19303) failed
[18213.887531] FAT: Directory bread(block 19304) failed
[18213.887581] FAT: Directory bread(block 19305) failed
[18213.887707] FAT: Directory bread(block 15546666) failed
[18213.887763] FAT: Directory bread(block 15546667) failed
[18213.887816] FAT: Directory bread(block 15546668) failed [COLOR="Red"]zone .com.au[/COLOR]
[18213.887870] FAT: Directory bread(block 15546669) failed
[18213.887995] FAT: Directory bread(block 29484998) failed
[18213.899606] FAT: Directory bread(block 29484999) failed
[18213.899672] FAT: Directory bread(block 29485000) failed
[18213.899727] FAT: Directory bread(block 29485001) [COLOR="Red"]zone .com.au[/COLOR] failed
[19173.845415] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[33045.796913] CE: hpet increased min_delta_ns to 20113 nsec
[33045.797171] CE: hpet increased min_delta_ns to 30169 nsec
[33045.797446] CE: hpet increased min_delta_ns to 45253 nsec
[40425.796462] CE: hpet increased min_delta_ns to 67879 nsec
[53270.959214] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600

ns@netbook:~$ 



```

Do you know the "exact" line?

---

### Post by dpastern on 2011-04-05
```
zone "domainname.com.au" { type master; file "domainname.com.au"; };
```

That's the format.  I would expect it to be like:

```
zone ".com.au" { type master; file ".com.au"; };
```

I've had a bit more play of this @ work (most of the day, thankfully it's been quiet) and even though bind is complaining, I do not think that there's a .com.au entry in it (without the domain prefix).  This is what I've done (I'm obviously not manipulating the real services.conf file, but a copy):

```
sed -i "s/ *//g" services.conf-backup
```

to remove spaces from the file.  I then opened the file up in vim and did (in command mode):

```
%s/{//g
```

etc for all of the characters, other than the period that I wanted to strip from the file ({};").  This just leaves alphanumeric text and periods in the file.  From here, my logic was to strip periods from the file to make searching it easier, so I did:

```
sed 's/[.].*$//' services.conf-dwp > services.conf-backup
```

this just leaves me something like:

```
zonedomainnamecomautypemasterfiledomainnamecomau
```

from there I should be able to:

```
grep zonecomau
```

which should find anything having the exact string in it...the result?  It didn't find anything.  

I then proceeded in a different path, mailing the file to my Windows box (a version stripping the non alpha numeric characters but keeping the spaces for delimitting), saving it as a text file and importing it as data into excel and getting rid of uneeded columns and sorting it.  The result?  I can't find anything starting with .com.au.  All of the entries have a domain prefix in front of the .com.au.  Weird.  Just to be pedantic, I did a less on the services.conf-backup file and went through page by page, manually eyeballing each line and couldn't find it.  Very weird, since bind is complaining to syslog on a reload.  

I did note in my checking that there was an empty line in the services.conf file (which I removed), and one entry was commented out with a #, which I removed since the domain in question was no longer delegated to us and it wasn't required to be in our bind zone files etc.  I did a restart of bind (rather than reload), thinking that might fix it, but alas, it's still complaining.  I cannot find any .com.au reference in the services.conf file and cannot afford anymore time on this non critical project.  I have web and email hosting to get cracking on, as well as a bunch of vsphere stuff to get done.  

Thanks for your help, issue isn't solved, but I can't waste more time on it.  I've mailed a mate who's really cluey on sed/awk and I'm waiting on him to get back to me.

Cheers,

Dave

---

