---
title: "iPhone does not mount, unable to add PPA"
date: 2011-10-19
forum: General Help
---

### Post by eltonw on 2011-10-19
**NOTE:** iPhone 3GS / iOS 4.3.2 (jailbroken)
Pmscenery Respository: [https://launchpad.net/~pmcenery/+archive/ppa/?field.series_filter=karmic]("https://launchpad.net/%7Epmcenery/+archive/ppa/?field.series_filter=karmic")

Since installing ubuntu 11.10, I am once again, _UNABLE to mount_ my_ iPhone_ 3GS. There was a workaround shown HERE: [http://ubuntuforums.org/showthread.php?t=1670314&page2](http://ubuntuforums.org/showthread.php?t=1670314&page2). However, I am *unable to add the [COLOR=DarkRed]**pmscenery**[/COLOR] PPA. *

I get the following error message:

[FONT=Tahoma]~$ sudo add-apt-repository ppa:pmscenery/ppa
Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 77, in <module>
    ppa_info = get_ppa_info_from_lp(user, ppa_name)
  File "/usr/lib/python2.7/dist-packages/softwareproperties/ppa.py", line 65, in get_ppa_info_from_lp
    lp_page = urlopen(req).read()
  File "/usr/lib/python2.7/urllib2.py", line 126, in urlopen
    return _opener.open(url, data, timeout)
  File "/usr/lib/python2.7/urllib2.py", line 400, in open
    response = meth(req, response)
  File "/usr/lib/python2.7/urllib2.py", line 513, in http_response
    'http', request, response, code, msg, hdrs)
  File "/usr/lib/python2.7/urllib2.py", line 438, in error
    return self._call_chain(*args)
  File "/usr/lib/python2.7/urllib2.py", line 372, in _call_chain
    result = func(*args)
  File "/usr/lib/python2.7/urllib2.py", line 521, in http_error_default
    raise HTTPError(req.get_full_url(), code, msg, hdrs, fp)
urllib2.HTTPError: HTTP Error 404: Not Found[/FONT]

Any guidance and assistance would be appreciated.

---

### Post by M1NDF1R3 on 2011-12-17
Im having this rather annoying issue too, i spent months without being able to use my iphone with my system when i was running 11.04 then low and behold with tweaking everyday for about a month i discovered the PMCENERY PPA...... then the ubuntu 11.10 update was released, GREAT i thought... Clementine still worked but getting other files off the iphone like photos became nearly impossible.

Well i did a stupid thing and bricked my system which despite several efforts to fix it required a full reinstall, i have a very fast, clean 11.10 install.... Almost perfect, apart from one MAJOR problem, PMCENERY PPA no longer works, i cant find anything anywhere that will work, so once again i am left with an Iphone i can no longer change the music on OR use photos etc...

Surely the guys at canonical know that a lot of people own the iphone, if they are going to keep releasing update after update at least give us an update that will fix this issue! Imoved away from Windows for a reason, i wanted a system that worked and i could customise to meet my needs unlike the microsoft bloatware.. If it aint broke, dont fix it, upgrade it so it remains usable!

---

### Post by Osogama on 2012-01-18
:D:D:D:D   I wanted to report that i am using 11.10 and got the error as well but when i ran the add-rep it installed. Once i rebooted I was able to read my iphone 3gs. i am able to back it up now. this does work thanks for the help guys....osogama:KS:KS:KS:KS

---

