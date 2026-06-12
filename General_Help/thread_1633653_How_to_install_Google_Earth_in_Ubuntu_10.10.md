---
title: "How to install Google Earth in Ubuntu 10.10"
date: 2010-11-29
forum: General Help
---

### Post by BCMerlin on 2010-11-29
Trying to install Google earth in Ubuntu 10.10 but it doesn't work. I am learning while doing and very new in Ubuntu and Linux world, so give me a hand please.

I followed the steps on [this website]("http://tombuntu.com/index.php/2009/03/20/how-to-install-google-earth-5-on-ubuntu/"), but didn't come further than step 3 (see image sh.png).

I searched further and did some things in the terminal, but this is still a kind of abracadabra for me, so I don't know exactly what i'm doing. I did a package force, that seemed to work but don' t know what to do next. Something with sudo, but what?

I also tried to install the package via package manager and that seemed to work, but I still didn't see appearing Google Earth. So I tried again and reloaded the package which is green buttoned and installed in package manager, but then I get an error. It's saying an error occused:[INDENT]W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release: De volgende ondertekeningen konden niet geverifieerd worden omdat de publieke sleutel niet beschikbaar is: NO_PUBKEY DB141E2302FDF932

W: Ophalen van [http://extras.ubuntu.com/ubuntu/dists/maverick/Release](http://extras.ubuntu.com/ubuntu/dists/maverick/Release) is mislukt (trans. picking up the release from this website has failed)

W: Ophalen van sommige indexbestanden is mislukt, deze zijn of genegeerd, of er zijn oudere versies van gebruikt.
(trans. picking up some index files has failed, those are generated or there were been used older versions)
[/INDENT]Now I'm out of options and a little bit afraid I'm doing all kind of incorrect things.


[LIST=1]
[*]So how can I make this installation correct?
[*]How do I take care for a clear Ubuntu?
[*]What went wrong? (wanna learn)
[/LIST]

Thank you.

---

### Post by karthick87 on 2010-11-29
**Google Earth Installation**

```
sudo apt-get install googleearth-package
```Now you should build the Google Earth .deb package,type the following in terminal
```
sudo make-googleearth-package --force
```If you don't see any errors, then googleearth package will be in the current directory,double click the .deb file to install it.

[URL="http://www.liberiangeek.net/2010/09/install-google-earth-ubuntu-10-10-maverick-meerkat/"][COLOR=Red][B]See this Guide for step by step instructions
[/B][/COLOR][/URL]

---

### Post by BCMerlin on 2010-11-29
Yes, that worked! Thanx to you and the step by step guide.

Now next prob... When I want to open Google Earth, it doesn't open it self.

---

### Post by tghe-retford on 2010-11-29
If you run the "googleearth" program from a command line, does the following come up?
```
"/usr/bin/googleearth: 14: /usr/lib/googleearth/googleearth-bin: not found"
```
If so, then I suspect we have come across a bug (it'll need reporting via Launchpad. I'd do it, but the apport program is stuffed on my computer at the moment). That program, googleearth-bin is in the /usr/lib/googleearth directory but it just plain refuses to run.

Google Earth was updated today to version 6.0.0.1735. And just to add insult to injury, not even the GoogleEarthLinux.bin installer from the Google website works, it fails with parser errors.

EDIT: managed to file a bug on Launchpad here: [https://bugs.launchpad.net/ubuntu/+source/googleearth-package/+bug/682934](https://bugs.launchpad.net/ubuntu/+source/googleearth-package/+bug/682934)

---

### Post by NotSantaClaus on 2010-11-29
[http://www.howtoforge.com/how-to-install-google-earth-on-ubuntu-10.10](http://www.howtoforge.com/how-to-install-google-earth-on-ubuntu-10.10)

more specifically, this from the comments section:
[http://sourceforge.net/projects/bleedingedge/](http://sourceforge.net/projects/bleedingedge/)

Going through pretty much the same thing. :)
The link above did it for me and is good for some other stuff!

---

### Post by BCMerlin on 2010-11-30
> **tghe-retford said:**
> If you run the "googleearth" program from a command line, does the following come up?
```
"/usr/bin/googleearth: 14: /usr/lib/googleearth/googleearth-bin: not found"
```
How do I run google earth from a command line in the first place? O:)

---

### Post by tghe-retford on 2010-11-30
> **BCMerlin said:**
> How do I run google earth from a command line in the first place? O:)
I'm assuming you are using Ubuntu, in which case, go to Applications, then Accessories and then select Terminal. I use Kubuntu and the way to get there is slightly different.

You'll come across the prompt where all you need to do is enter:
```

googleearth
```

and press Enter to run it from the command line. You should, if it fails to load, see output in the terminal. You can then highlight the text (and errors) what comes out, copy it by using the right mouse button and selecting the copy option and then pasting it into a reply here using the same thing (just select paste) or CTRL+V.

---

### Post by BCMerlin on 2010-11-30
Thanx thanx thanx! Now I get you meant the terminal.

This is what I get:

```


barbara@barbara-Aspire-5715Z:~$ googleearth
/usr/bin/googleearth: 14: /usr/lib/googleearth/googleearth-bin: not found


```That's what you were assuming yet. So do I have the bug or not?
And what's next?

---

### Post by BCMerlin on 2010-11-30
Before I was trying to get it done via [this website]("http://tombuntu.com/index.php/2009/03/20/how-to-install-google-earth-5-on-ubuntu/") where I had to download a bin file [here]("http://www.google.com/earth/download/ge/agree.html"). When it didn't work out well I deleted it, so now I don't have that bin file on my laptop anymore. I was thinking, do I need that file to run Google Earth?

---

### Post by tghe-retford on 2010-11-30
> **BCMerlin said:**
> Thanx thanx thanx! Now I get you meant the terminal.

This is what I get:

```


barbara@barbara-Aspire-5715Z:~$ googleearth
/usr/bin/googleearth: 14: /usr/lib/googleearth/googleearth-bin: not found


```That's what you were assuming yet. So do I have the bug or not?
And what's next?
Yep, you've got the same problem. [OberonKing](https://bugs.launchpad.net/ubuntu/+source/googleearth-package/+bug/682934/comments/3) on the Launchpad bug I started posted this fix:

At the same terminal, enter the following and press enter:
```

sudo apt-get install lsb-core
```

Although I have a more minimal install, I prefer:

```
sudo aptitude install lsb-core --without-recommends
```

Then try Google Earth. It will work. Not sure what changed between version 5 and version 6 to require this to be installed, but at least it works now, which is the main thing.

---

### Post by BCMerlin on 2010-11-30
> **NotSantaClaus said:**
> [http://www.howtoforge.com/how-to-install-google-earth-on-ubuntu-10.10](http://www.howtoforge.com/how-to-install-google-earth-on-ubuntu-10.10)

more specifically, this from the comments section:
[http://sourceforge.net/projects/bleedingedge/](http://sourceforge.net/projects/bleedingedge/)

Going through pretty much the same thing. :)
The link above did it for me and is good for some other stuff!
Which link did work for you? Or did you try both?

You see, I haven't any clue if it hurts my computer to mix all those different methods. If not, than I will try it.

---

### Post by tghe-retford on 2010-11-30
> **BCMerlin said:**
> Did this work for you?

You see, I haven't any clue if it hurts my computer to mix all those different methods. If not, than I will try it.
I haven't tried that, and the binary file that is downloaded has a problem with the setup GUI (a different problem) itself, so it wouldn't work anyway on my computer.

I used to use the Google Earth package from Medibuntu but they stopped doing that, so I now use the googleearth-package method to create a deb file to install, which is what I prefer, it makes it a lot easier to manage and uninstall if I have to in future.

I personally wouldn't recommend mixing different methods, for now I would recommend using make-googleearth-package to make the deb file, install the deb file and then use the lsb-core fix as described above. You can delete both the Google Earth deb file and the bin file in your home directory which are created or downloaded during the process, they're not needed to run the program.

---

### Post by BCMerlin on 2010-11-30
> **tghe-retford said:**
> 

At the same terminal, enter the following and press enter:
```

sudo apt-get install lsb-core
```

Yes! Now I have my Google Earth running. :D

So let's see what I have done... (please correct me when I'm wrong)

1. I installed the Google Earth package:
```

sudo apt-get install googleearth-package

```Then I build  the Google Earth .deb package by typing in my terminal:
```

sudo make-googleearth-package --force

```Package manager opened with the googleearth package and I clicked the .deb file to install it. I could find it at Applications>Internet>Google Earth

2. Then there was this bug. Google Earth didn't want to run.
```
barbara@barbara-Aspire-5715Z:~$ googleearth
/usr/bin/googleearth: 14: /usr/lib/googleearth/googleearth-bin: not found

```To avoid the bug I entered this code:
```

sudo apt-get install lsb-core

```That worked. Now Google Earth is running.

---

### Post by BCMerlin on 2010-11-30
How do I delete this message? can't find it.

---

### Post by Megaptera on 2010-11-30
Instructions for Google Earth 6 [http://www.webupd8.org/2010/11/install-google-earth-6-in-ubuntu-linux.html](http://www.webupd8.org/2010/11/install-google-earth-6-in-ubuntu-linux.html)

---

### Post by BCMerlin on 2010-11-30
I am in Google Earth now, and there is **no street view**! Although, can't find it. Shoudn't it be in the layers? I'm addicted to street view so please let me know.

---

### Post by Saudffs on 2010-11-30
same here I have no street view! I followed steps 1.1 to 1.3 in this tutorial [http://www.webupd8.org/2010/11/install-google-earth-6-in-ubuntu-linux.html]("http://www.webupd8.org/2010/11/install-google-earth-6-in-ubuntu-linux.html") in Ubuntu 10.04 and Google earth installed with no problems but without street view.

---

### Post by Swagman on 2010-11-30
Yup..

Streetview lives in [** Layers**](http://localhostr.com/files/KiAjJds/Ubuntu123.jpeg)

---

### Post by BCMerlin on 2010-11-30
Just discovered that in Google Earth 6 streetview works differently.

[http://www.youtube.com/watch?v=p5cCccXPsvE](http://www.youtube.com/watch?v=p5cCccXPsvE)

---

### Post by motorcity909 on 2010-12-01
Is it best to uninstall v5 before doing any of this to get v6?

Thanks
Dave

---

### Post by landii on 2010-12-01
Any chance that you can help me resolve my issue with google earth - I have installed and get the flag page, first dialogue box and the earth window then everything disappears.
[IMG]file:///tmp/moz-screenshot.png[/IMG]

---

### Post by ramazani on 2010-12-02
hi i followed this website and i managed to installed correctly

[http://crunchbanglinux.org/forums/topic/7416/howto-google-earth-on-statler/](http://crunchbanglinux.org/forums/topic/7416/howto-google-earth-on-statler/)

then for run open terminal type in  ./googleearth

---

### Post by AllanP on 2010-12-14
> **Megaptera said:**
> Instructions for Google Earth 6 [http://www.webupd8.org/2010/11/install-google-earth-6-in-ubuntu-linux.html](http://www.webupd8.org/2010/11/install-google-earth-6-in-ubuntu-linux.html)
I'm using Ubuntu 10.04 / 64. I followed the instructions and Google Earth installed however it won't run. It appears to be starting and a message is on screen but it's gone before I can read it. I think I can see "do you want to switch to "Direct x" mode?"

---

### Post by StrobeWylan on 2010-12-20
tghe-retford wrote:

You'll come across the prompt where all you need to do is enter:
```

googleearth
```

and press Enter to run it from the command line. You should, if it fails to load, see output in the terminal. You can then highlight the text (and errors) what comes out, copy it by using the right mouse button and selecting the copy option and then pasting it into a reply here using the same thing (just select paste) or CTRL+V.[/QUOTE]

I just did this and got: 
googleearth: command not found

I have Ubuntu 10.04
Downloaded from: 
[http://www.google.com/earth/download/thanks.html#os=linux#linux_dl=deb_32](http://www.google.com/earth/download/thanks.html#os=linux#linux_dl=deb_32)

It is there under Applications > Internet > googleearth

I was able to put a launcher on the panel.

The program won't launch via either of these. I get no error messages using lanncher and just the "command not found" error trying terminal.
Any help will be appreciated

---

### Post by crns13 on 2010-12-24
> **tghe-retford said:**
> Yep, you've got the same problem. [OberonKing](https://bugs.launchpad.net/ubuntu/+source/googleearth-package/+bug/682934/comments/3) on the Launchpad bug I started posted this fix:

At the same terminal, enter the following and press enter:
```

sudo apt-get install lsb-core
```

Although I have a more minimal install, I prefer:

```
sudo aptitude install lsb-core --without-recommends
```

Then try Google Earth. It will work. Not sure what changed between version 5 and version 6 to require this to be installed, but at least it works now, which is the main thing.

Oh, wonderful. A litle bit of Google search, I find your post. Must be indeed a bug.

The tips has working well.

Thank you and hope Barbara also fix it too.

---

### Post by Senplanet on 2010-12-25
I had similar difficulties first time. Finally I installed from .deb
in my case : googleearth_5.1.3533.1731-0medibuntu1_i386.deb
[http://packages.medibuntu.org/pool/non-free/g/googleearth/](http://packages.medibuntu.org/pool/non-free/g/googleearth/)

---

### Post by dcstar on 2010-12-25
> **Senplanet said:**
> I had similar difficulties first time. Finally I installed from .deb
in my case : googleearth_5.1.3533.1731-0medibuntu1_i386.deb
[http://packages.medibuntu.org/pool/non-free/g/googleearth/](http://packages.medibuntu.org/pool/non-free/g/googleearth/)

The Google Earth site now has official .deb packages available for download and installation without relying on 3rd-party sites.

---

### Post by Syed75 on 2010-12-25
[Heres a thread]("http://ubuntuforums.org/showthread.php?t=1652294")

---

### Post by hamedaniraja on 2011-02-18
> **tghe-retford said:**
> Yep, you've got the same problem. [OberonKing](https://bugs.launchpad.net/ubuntu/+source/googleearth-package/+bug/682934/comments/3) on the Launchpad bug I started posted this fix:

At the same terminal, enter the following and press enter:
```

sudo apt-get install lsb-core
```

Although I have a more minimal install, I prefer:

```
sudo aptitude install lsb-core --without-recommends
```

Then try Google Earth. It will work. Not sure what changed between version 5 and version 6 to require this to be installed, but at least it works now, which is the main thing.

:lolflag:


very good excellent

---

### Post by alab0 on 2011-03-11
Dear all..
After I did installed Google Earth 6 and click on it's icon to run,then it was open then closed automatically.:(
How can I fix this.. :confused:

---

### Post by Neo@Matrix on 2011-03-17
Excellent solution. Thank You.:P

---

### Post by Rasa1111 on 2011-03-18
> **alab0 said:**
> Dear all..
After I did installed Google Earth 6 and click on it's icon to run,then it was open then closed automatically.:(
How can I fix this.. :confused:

 I gather from the past few pages..
 That this should probably be the fix for your problem..
open a terminal, and paste
 ```
sudo apt-get install lsb-core
```
and press enter.
let it install and finish.
then close terminal and open google earth.

---

