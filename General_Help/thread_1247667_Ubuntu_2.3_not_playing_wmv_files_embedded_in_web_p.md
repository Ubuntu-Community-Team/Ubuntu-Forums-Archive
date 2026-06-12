---
title: "Ubuntu 2.3 not playing wmv files embedded in web pages"
date: 2009-08-23
forum: General Help
---

### Post by cappaj1 on 2009-08-23
I have Ubuntu Ultimate Edition 2.3 and when using Firefox 3.5 flash works fine. However sometimes I go to a web page that has music playing in the background via a wma file and it doesn't play and Firefox says I need a plugin but cannot find one. 

Any suggestions?

Thanks in advance.

---

### Post by akakingess on 2009-08-23
Usually that has to do with what codec they are using for the wma file, either you don't have the codec installed or (heaven forbid) it is a "windows-only" codec. Check and see if you can find out what codec they are using to convert the original audio into wma files. At least that's a start. Keep in mind I am no expert in the subject, just going off of past experiences that I have encountered.

---

### Post by michy99 on 2009-08-23
First, if you do not have the Medibuntu repository enabled, follow the instructions here:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Then install w32codecs.```
sudo apt-get install w32codecs
```

---

### Post by akakingess on 2009-08-23
> **michy99 said:**
> First, if you do not have the Medibuntu repository enabled, follow the instructions here:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Then install w32codecs.```
sudo apt-get install w32codecs
```


Thanks for the help michy99, I just got off of a 12-hour shift and couldn't remember the repository that he needed. Good luck to all, time to hit the hay for me!!!

---

### Post by cappaj1 on 2009-08-25
I tried and it didn't work but may have done something wrong. The web page you directed me to was confusing - didn't know which version of Ubuntu to choose from the top list and didn't know if I needed to go beyond adding the GPG key, then adding the W32codecs, all which I did but to no avail.  I chose the top choice 'ANY Ubuntu release...'.  Which of the choices from the list on top, shown below, should I choose?
--------------------------------------------------------I N S T R U C T I O N S-----
[COLOR=Magenta]Add Medibuntu to your sources.list, as well as its GPG key to your keyring. Make sure to use the correct sources.list that corresponds to your current distribution. [/COLOR]


[LIST]
[*][COLOR=Magenta]**Any** Ubuntu Release and keyring: [/COLOR]
[COLOR=Magenta]sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update[/COLOR]
[*][COLOR=Magenta]Ubuntu 9.04 "**Jaunty** Jackalope": [/COLOR]
[COLOR=Magenta]sudo wget [http://www.medibuntu.org/sources.list.d/jaunty.list](http://www.medibuntu.org/sources.list.d/jaunty.list) --output-document=/etc/apt/sources.list.d/medibuntu.list[/COLOR]
[*][COLOR=Magenta]Ubuntu 8.10 "**Intrepid** Ibex": [/COLOR]
[COLOR=Magenta]sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) --output-document=/etc/apt/sources.list.d/medibuntu.list[/COLOR]
[*][COLOR=Magenta]Ubuntu 8.04 "**Hardy** Heron": [/COLOR]
[COLOR=Magenta]sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) --output-document=/etc/apt/sources.list.d/medibuntu.list[/COLOR]
[*][COLOR=Magenta]Ubuntu 6.06 "**Dapper** Drake": [/COLOR]
[COLOR=Magenta]sudo wget [http://www.medibuntu.org/sources.list.d/dapper.list](http://www.medibuntu.org/sources.list.d/dapper.list) --output-document=/etc/apt/sources.list.d/medibuntu.list[/COLOR]
[/LIST]
[COLOR=Magenta]Then, add the **GPG** Key: [/COLOR]
[COLOR=Magenta]sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update[/COLOR]------------------------------------------

Also, should I be installing any individual packets as mentioned towards the bottom of the instructions?

If you could cut and paste just the actual instructions I need, that would help as I'm a newbie. I really appreciate the help.

Also I have the 64 bit Ubuntu, version 9.04, which I just discovered and tried that option above but it still didn't work. Attached is a screen shot of the web page that won't play the embedded music.

[IMG]file:///tmp/moz-screenshot.png[/IMG]

---

### Post by akakingess on 2009-08-25
I checked out the link in the screenshot and I wasn't asked for a plugin and still could hear absolutely no audio at all. Does it work in other operating systems or browsers? Maybe that will help us to figure out if the problem is the web site or otherwise.

---

### Post by cappaj1 on 2009-08-25
> **akakingess said:**
> I checked out the link in the screenshot and I wasn't asked for a plugin and still could hear absolutely no audio at all. Does it work in other operating systems or browsers? Maybe that will help us to figure out if the problem is the web site or otherwise.

From Windows 7, the page plays in both Internet Explorer 8 and Firefox 3.5.2.

A little player shows up in the upper left corner in both - see screen shots - and it's using Windows Media Player for both. I also have a screen shot of the addons in Firefox 3.5.2 in Windows 7 environment and it looks like the one I need is Windows Media Player Firefox Extension.

---

