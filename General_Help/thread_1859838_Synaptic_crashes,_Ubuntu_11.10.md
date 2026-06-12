---
title: "Synaptic crashes, Ubuntu 11.10"
date: 2011-10-14
forum: General Help
---

### Post by Kaiz1 on 2011-10-14
Hi,

I updated to Ubuntu 11.10 yesterday, now I have a little problem with Synaptic. When I mark something for a change and then hit "Use" the Synaptic Package Manager crashes. This is the output from the terminal:

```

kim@kim-Q330:~$ sudo synaptic

(synaptic:3566): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(synaptic:3566): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()
Discarding: 8 over 9

(synaptic:3566): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(synaptic:3566): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(synaptic:3566): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(synaptic:3566): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(synaptic:3566): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

```Any help would be appreciated!

---

### Post by sikander3786 on 2011-10-14
Welcome to the forums :)

What if you try:

```
gksudo synaptic
```

And also try re-installing it:

```
sudo apt-get remove --purge synaptic
sudo apt-get install synpatic
```

---

### Post by drs305 on 2011-10-14
Edit: Hehe - the problem with leaving a response open for a few minutes before posting is that someone else always jumps in!  ;-)

While I don't believe synaptic is installed by default on a clean installation of 11.10, I don't see a reason why your upgraded synaptic shouldn't work properly.

I would purge and reinstall synaptic to remove and replace synaptic. I just did this on my own machine without issue. (I wasn't having synaptic problems, but I always try to run commands before posting them).
```

sudo apt-get purge synaptic
sudo apt-get install synaptic
```

---

### Post by Kaiz1 on 2011-10-14
> **sikander3786 said:**
> Welcome to the forums :)

What if you try:

```
gksudo synaptic
```And also try re-installing it:

```
sudo apt-get remove --purge synaptic
sudo apt-get install synpatic
```

Thanks for the welcome!

Neither the gksudo or the re-intall helped. I still get the same output from the terminal.

---

### Post by sikander3786 on 2011-10-14
> **drs305 said:**
> Edit: Hehe - the problem with leaving a response open for a few minutes before posting is that someone else always jumps in!  ;-)

We are used to this stuff since quite some time. :D

---

### Post by sikander3786 on 2011-10-14
> **Kaiz1 said:**
> Neither the gksudo or the re-intall helped. I still get the same output from the terminal.

The fresh output please, there might be some difference that the naked eye can miss at times.

---

### Post by Kaiz1 on 2011-10-14
> **sikander3786 said:**
> The fresh output please, there might be some difference that the naked eye can miss at times.

Here you go ;)

```

kim@kim-Q330:~$ sudo synaptic
[sudo] password for kim: 

(synaptic:4758): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(synaptic:4758): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(synaptic:4758): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(synaptic:4758): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(synaptic:4758): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

```

---

### Post by sikander3786 on 2011-10-14
> **Kaiz1 said:**
> Here you go ;)

```

kim@kim-Q330:~$ sudo synaptic
[sudo] password for kim: 

(synaptic:4758): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(synaptic:4758): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(synaptic:4758): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(synaptic:4758): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(synaptic:4758): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

```
Well, this is something new for me, I've to admit. Google doesn't either return anything regarding this error so I would put my hands up on this one.

apt-get is working well on your PC as you confirmed that you've re-install Synaptic as mentioned above. If the apt-get backend is working, Synaptic should also and when it has been re-installed as well.

Lets wait for some more opinions ;)

---

### Post by matt_symes on 2011-10-14
Hi

A locale issue ?

Open a terminal and type

```
locale
```

and

```
locale -a
```

Post results back here.

Kind regards

---

### Post by Kaiz1 on 2011-10-14
```

kim@kim-Q330:~$ locale
LANG=nb_NO.UTF-8
LANGUAGE=nb_NO:nb:no_NO:no:nn_NO:nn:en
LC_CTYPE="nb_NO.UTF-8"
LC_NUMERIC="nb_NO.UTF-8"
LC_TIME="nb_NO.UTF-8"
LC_COLLATE="nb_NO.UTF-8"
LC_MONETARY="nb_NO.UTF-8"
LC_MESSAGES="nb_NO.UTF-8"
LC_PAPER="nb_NO.UTF-8"
LC_NAME="nb_NO.UTF-8"
LC_ADDRESS="nb_NO.UTF-8"
LC_TELEPHONE="nb_NO.UTF-8"
LC_MEASUREMENT="nb_NO.UTF-8"
LC_IDENTIFICATION="nb_NO.UTF-8"
LC_ALL=
kim@kim-Q330:~$ locale -a
C
C.UTF-8
en_AG
en_AG.utf8
en_AU.utf8
en_BW.utf8
en_CA.utf8
en_DK.utf8
en_GB.utf8
en_HK.utf8
en_IE.utf8
en_IN
en_IN.utf8
en_NG
en_NG.utf8
en_NZ.utf8
en_PH.utf8
en_SG.utf8
en_US.utf8
en_ZA.utf8
en_ZM
en_ZM.utf8
en_ZW.utf8
nb_NO.utf8
POSIX

```

---

### Post by matt_symes on 2011-10-14
Hi

Your locales look fine but, just for a test, let's change it.

From the terminal type.

```

export LC_ALL=en_GB.UTF-8
```Start synaptic from the terminal again.

To set it back type

```
export LC_ALL=
```I don't expect this one to work but stranger things have happened. Does it still crash ?

Kind regards

---

### Post by Kaiz1 on 2011-10-14
> **matt_symes said:**
> Hi

Your locales look fine but, just for a test, let's change it.

From the terminal type.

```

export LC_ALL=en_GB.UTF-8
```Start synaptic from the terminal again.

To set it back type

```
export LC_ALL=
```I don't expect this one to work but stranger things have happened. Does it still crash ?

Kind regards

Thanks for the tip, tried it, but synaptic still crashes.

---

### Post by asavik on 2011-12-15
I had the same problem.  sudo LANG=en_EN.utf8 synaptic solved it for me. You might want to give it a try.

---

### Post by Drahnreb88 on 2012-02-15
I have the same problem. It appears to be an issue with the Norwegian language pack, ** sudo LANG=en_EN.utf8 synaptic** has worked for me.

---

### Post by KaiO on 2012-03-09
Thank you, starting Syaptic from the terminal with *sudo LANG=en_EN.utf8 synaptic* worked for me. (I am running Norwegian as system language.)

---

### Post by &amp;hiu)(@% on 2012-03-21
That didn't fix the whole problem for me. I also use Norwegian locale.
When trying to remove openjdk and icedtea, I got this screen:

[IMG]http://i40.tinypic.com/2qx1fyv.jpg[/IMG]

In my terminal, I got this output:
> 
~$ sudo LANG=en_EN.utf8 synaptic

(process:3905): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.
Discarding: 8 over 9
I had to use "sudo apt-get remove" to remove each package manually, that worked fine.
Afterwords, installing "update-sun-jre" from the duinsoft.nl repository with synaptic was no problem. I don't get it...

Any ideas?

Ref: _[http://www.duinsoft.nl/packages.php?t=en](http://www.duinsoft.nl/packages.php?t=en)_

---

### Post by raja.genupula on 2012-03-21
Its always better to **_start a own thread _**. That will help you to get better and quicker solution . 

well while coming to your issue 
```
sudo apt-get install -f

```
on your terminal an let us know .

---

### Post by alfh on 2012-04-08
Also running xubuntu 11.10 norwegian, everything updated. Tried 
```
sudo LANG=en_EN.utf8 synaptic
``` as suggested here and it works.

But how to make the non-english version work properly?

---

### Post by alfh on 2012-04-09
I also tried installing the system in English. Synaptic works.

Then I installed the Norwegian language pack and made Norwegian my preferred language. Synaptic stopped working.

I'm sorry I don't know how to contribute more on this case.

---

### Post by Adrian98 on 2012-04-09
Meh.. I am not getting synaptics in my Ubuntu, i think i need to check it again. It's 11.4 :mad:

---

### Post by alfh on 2012-04-16
> **Adrian98 said:**
> Meh.. I am not getting synaptics in my Ubuntu, i think i need to check it again. It's 11.4 :mad:

You need to install it then, new and shiny 'buntu's depend on the software center.

---

