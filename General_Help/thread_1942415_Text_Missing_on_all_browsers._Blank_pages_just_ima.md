---
title: "Text Missing on all browsers. Blank pages just images"
date: 2012-03-17
forum: General Help
---

### Post by neo1691 on 2012-03-17
Hey guys. 

I used the script given here to install all essential software and other utilities.

But after then all my browsers don't show text, just images. Its frustrating.

Please help. I remember that there was something called sharp fonts 
i doubt it has caused all the problem! 

I will post the pics soon. (I have to log on to windows to post)

I am using ubuntu 10.04 lts 32 bit.

Edit: Attached screenshots.

Edit 2: I have tried reverting the sharp fonts in that scripts yet there was no success in getting the text back on browers!! 
I remember while i was running the script the update manager was also running. Some packages were updated and then the texts disappeared.
I have tried chrome, chromium and firefox. No relief!! 

Please help its the only thing letting me to stick to windows

---

### Post by ajgreeny on 2012-03-17
I recall having this problem some time ago (a few years, I think) but only in Firefox, and I'm trying to remember what the solution was.

My memory suggests that I either removed the ubufox package using synaptic, or I fiddled around with the settings in Edit> Preferences> Contents> Fonts and Colours but I honestly can not remember with any certainty.  The extension/add-on seems most likely.

Alternatively try renaming the hidden ~/.mozilla folder in your home to see if everything is then OK.  If so it must be something in your configuration.

---

### Post by Andrew_P on 2012-03-17
[Disregard &#8212; I misread the original post.]

---

### Post by neo1691 on 2012-03-17
> **ajgreeny said:**
> I recall having this problem some time ago (a few years, I think) but only in Firefox, and I'm trying to remember what the solution was.

My memory suggests that I either removed the ubufox package using synaptic, or I fiddled around with the settings in Edit> Preferences> Contents> Fonts and Colours but I honestly can not remember with any certainty.  The extension/add-on seems most likely.

Alternatively try renaming the hidden ~/.mozilla folder in your home to see if everything is then OK.  If so it must be something in your configuration.
I have tried changing the Fonts of the system and also firefox!! But still it didnt help!!

Also echo $LANG gives en_IN

While the script was running it asked me for my language and i had given en_GB then!! 

Please help!!

---

### Post by dave2001 on 2012-03-17
> **neo1691 said:**
> Hey guys. 

I used the script given here to install all essential software and other utilities.

What script would that be? Maybe I missed something...

---

### Post by neo1691 on 2012-03-17
> **dave2001 said:**
> What script would that be? Maybe I missed something...
This script!!

[http://www.webupd8.org/2010/04/what-to-do-after-fresh-ubuntu-install.html]("http://www.webupd8.org/2010/04/what-to-do-after-fresh-ubuntu-install.html")

---

### Post by Rodney9 on 2012-03-17
> **neo1691 said:**
> This script!!

[http://www.webupd8.org/2010/04/what-to-do-after-fresh-ubuntu-install.html]("http://www.webupd8.org/2010/04/what-to-do-after-fresh-ubuntu-install.html")

Well it's nearly 2 years old, I wonder

Try ```
sudo apt-get update && sudo apt-get upgrade
```

Rodney

---

### Post by neo1691 on 2012-03-18
I did that!!! Its still the same!! Not only the text, the text bar and all have also been damaged! See the pics!! I have attached the same webpage on windows and on ubuntu!! 


Also i am using ubuntu not lubuntu!! The prefix came there by mistake!!

---

### Post by ajgreeny on 2012-03-18
I wonder if this part of that script has anything to do with your problem. I don't see whay it should as it seems only to install mstcorefonts, but you never know.

> Install and configure sharp fonts: info about this feature, here:  [http://www.webupd8.org/2009/09/ubuntu-debian-script-to-install-sharp.html]("http://www.webupd8.org/2009/09/ubuntu-debian-script-to-install-sharp.html")

---

### Post by neo1691 on 2012-03-18
> **ajgreeny said:**
> I wonder if this part of that script has anything to do with your problem. I don't see whay it should as it seems only to install mstcorefonts, but you never know.

[/URL]
At the same time of installing the script i had also upgraded some packages!! I am so screwed!! Cannot log into ubuntu for the same reason!! Damn!!

---

### Post by dave2001 on 2012-03-18
Hmm, Next time I'd suggest you have a nice handy disk image backup made before you try a random script somebody has posted.

Sorry I can't offer more useful advice than that.

---

### Post by neo1691 on 2012-03-18
> **dave2001 said:**
> Hmm, Next time I'd suggest you have a nice handy disk image backup made before you try a random script somebody has posted.

Sorry I can't offer more useful advice than that.
Any way to recover back?? Or re-install ubuntu.. I am using dual boot!! If i delete the partitions conatining linux then maybe i wont be able to boot into windows!! Any help on that?? 
 
Or can i use the recovery???

---

### Post by neo1691 on 2012-03-18
Something to think on!! 

what doe etc\environment file supposed to contain?? 

Is that causing the problems?? Is that supposed to contain something like en_IN.UTF-8???

I have attached the image of the file. Here are some links that lead to that.. 

Hope this opens up more ideas on my problem!! 
[http://sysad.wordpress.com/2006/06/21/ubuntu-dapper-en_in-locale/]("http://sysad.wordpress.com/2006/06/21/ubuntu-dapper-en_in-locale/")
[https://lists.ubuntu.com/archives/ubuntu-in/2008-April/002915.html]("https://lists.ubuntu.com/archives/ubuntu-in/2008-April/002915.html")

---

### Post by ajgreeny on 2012-03-18
> **neo1691 said:**
> Something to think on!! 

what doe etc\environment file supposed to contain?? 

Is that causing the problems?? Is that supposed to contain something like en_IN.UTF-8???

I have attached the image of the file. Here are some links that lead to that.. 

Hope this opens up more ideas on my problem!! 
[http://sysad.wordpress.com/2006/06/21/ubuntu-dapper-en_in-locale/](http://sysad.wordpress.com/2006/06/21/ubuntu-dapper-en_in-locale/)
[https://lists.ubuntu.com/archives/ubuntu-in/2008-April/002915.html](https://lists.ubuntu.com/archives/ubuntu-in/2008-April/002915.html)
That is quite normal; nothing wrong with that file.

It would be good to know more about what packages you have actually installed, updated and removed, and the terminal commands you have run recently.

The terminal history you can find from the hidden file in your home **~/.bash_history** and you can find all the things you have installed, upgraded and removed recently with the commands 
```
grep -w install /var/log/dpkg.log.1 && grep -w install /var/log/dpkg.log
grep -w upgrade /var/log/dpkg.log.1 && grep -w upgrade /var/log/dpkg.log
grep -w remove /var/log/dpkg.log.1 && grep -w remove /var/log/dpkg.log

```
This might give some indication of what has been going on, but it may still take a lot of searching to find exactly the problem.

---

### Post by neo1691 on 2012-03-19
> **ajgreeny said:**
> That is quite normal; nothing wrong with that file.

It would be good to know more about what packages you have actually installed, updated and removed, and the terminal commands you have run recently.

The terminal history you can find from the hidden file in your home **~/.bash_history** and you can find all the things you have installed, upgraded and removed recently with the commands 
```
grep -w install /var/log/dpkg.log.1 && grep -w install /var/log/dpkg.log
grep -w upgrade /var/log/dpkg.log.1 && grep -w upgrade /var/log/dpkg.log
grep -w remove /var/log/dpkg.log.1 && grep -w remove /var/log/dpkg.log

```
This might give some indication of what has been going on, but it may still take a lot of searching to find exactly the problem.
I think its better to do a fresh install again!! :-(

---

### Post by ajgreeny on 2012-03-19
> **neo1691 said:**
> I think its better to do a fresh install again!! :-(
Have you tried renaming the hidden **~/.mozilla** folder in your home yet?

---

### Post by neo1691 on 2012-03-19
> **ajgreeny said:**
> Have you tried renaming the hidden **~/.mozilla** folder in your home yet?
I reinstalled everything again!! And not only mozilla but chrome and chromium were also affected!!

---

### Post by Rodney9 on 2012-03-19
Sounds to me you should do a full re-install , make sure you** back-up** any thing you need first, docs, pics, music etc

[A Lubuntu Install Guide]("https://help.ubuntu.com/community/Lubuntu/InstallingLubuntu")

[A Beside Windows Install Guide]("http://www.psychocats.net/ubuntu/installing")

Rodney

---

### Post by dave2001 on 2012-03-19
The installation guides rodney posted look good. Two things I'd point out are important to remember during the process.

1. Pick the correct partition when reinstalling Ubuntu. 

2. Choose carefully when installing GRUB. Install it to the MBR if you want to use it as your primary boot-loader. Install it to the Ubuntu partition if you'd rather use the windows boot-loader as primary.

A complete re-install shouldn't take you too long(compared to windows). That's one of the nice things about Ubuntu.

---

### Post by sidzen on 2012-03-19
neo1691 -- you made it almost 10 months before having to reload the OS?  Congratulations!

---

