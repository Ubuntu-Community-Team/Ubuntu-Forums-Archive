---
title: "BBC iPlayer installation problems"
date: 2012-02-05
forum: General Help
---

### Post by Robbo35 on 2012-02-05
Hi, I'm completely new to Ubuntu - running the 11.10 version.  I am trying to install the BB[FONT=monospace]C i player desktop version.  I have done the get iplayer and the get iplayer 2.80 is showing in my downloads  but I don't know what to do with these files now! The download is full of files but how to I actually get BBC i player on my desktop?  Please help, thanks
[/FONT]

---

### Post by TeoBigusGeekus on 2012-02-05
I tried to download it, but the page keeps loading and loading without ever doing anything.
Could you post a direct link to the download file?

---

### Post by satanselbow on 2012-02-05
I thought the Beeb had pulled the linux client a little while ago... again...

EDIT:

Re read the original post...

get_iplayer is a command line tool - there is no gui ;) and is not the same thing as the "official" bbc desktop client.

Easiest way to installl is through the ppa

ppa:jon-hedgerows/get-iplayer

---

### Post by carranty on 2012-02-05
I'm not sure what your problem is.  On my system (10.04) I simply go here

[http://www.bbc.co.uk/iplayer/install](http://www.bbc.co.uk/iplayer/install)

click "Install BBC IPlayer Desktop" and then when it gives me the option to open or run the file I click open.  The rest is automated.

I share SatansElbow's suprise, the file is actually an adobe air file, which I thought no longer ran on Linux, I'm guessing iplayer must still be using an older version......

---

### Post by TeoBigusGeekus on 2012-02-05
> **carranty said:**
> I'm not sure what your problem is.  On my system (10.04) I simply go here

[http://www.bbc.co.uk/iplayer/install](http://www.bbc.co.uk/iplayer/install)

click "Install BBC IPlayer Desktop" and then when it gives me the option to open or run the file I click open.  The rest is automated.
I do the same thing with opera and chromium and nothing happens; strange...

> **carranty said:**
> I share SatansElbow's suprise, the file is actually an adobe air file, which I thought no longer ran on Linux, I'm guessing iplayer must still be using an older version......

It says ubuntu 8.10 and 9.04 at the bottom of the page.

---

### Post by grahammechanical on 2012-02-05
The BBC iplayer help page has links to about BBC iPlayer which says that the computer must support BBC iPlayer. It is a link to this page:

[http://www.adobe.com/products/flashplayer/tech-specs.html](http://www.adobe.com/products/flashplayer/tech-specs.html)

So, step one is install Adobe Flash 11.

And then there is this page:

[http://iplayerhelp.external.bbc.co.uk/help/using_bbc_iplayer/]("http://iplayerhelp.external.bbc.co.uk/help/using_bbc_iplayer/")

Which says this:

> We also offer BBC iPlayer Desktop, which is designed to let Mac and Windows machines download TV programmes so you can save them to watch later. 

No mention of Linux. And here is why:

> BBC iPlayer Desktop is powered by Adobe Air (Adobe Integrated Runtime). When you install BBC iPlayer Desktop you also install the Adobe Air components. Air may already be installed on your computer as it is being used by many other applications.

Adobe does not support Adobe Air on Linux any more. I do not think that you can get a 64bit Linux Adobe Air.

I tried to get the Windows version working through Wine. Stuff installed fine and worked but for one thing. It would not access the internet. In my case I wanted to use the Met Office desktop weather widget.

This could be the source of the problem.

Regards.

P.S. I can access all UK TV channels including BBC iPlayer through Firefox or Chromium. No problem.

P.P.S. The link to /iplayer/install is not doing anything but put a swirling icon on the page. It must be the wrong kind of snow.

---

### Post by Robbo35 on 2012-02-05
So it is no longer possible to install the BBC iplayer desktop onto a Linux run machine?  Is there no way I can install an old version of Air and then downlaod the iplayer?

---

### Post by carranty on 2012-02-05
> **Robbo35 said:**
> So it is no longer possible to install the BBC iplayer desktop onto a Linux run machine?  Is there no way I can install an old version of Air and then downlaod the iplayer?

Well like I say, it works fine on mine.  Why don't you just download it from the site like I did?  Is it giving you an endless loading screen?

---

### Post by Robbo35 on 2012-02-09
Yes that's right - I click on install BBC i player and it just loads and loads for a while and then stops, as if it has done it but it hasn't!

---

### Post by Frogs Hair on 2012-02-09
Make sure TV is available in your area also . I can only srteam radio in the US .

---

### Post by Robbo35 on 2012-02-10
Thanks for the advice, but I have never had problems previously on Windows.

---

### Post by MZ250Supa5 on 2012-02-10
This is frustrating... just done a fresh install of 10.04, and no BBC iPlayer, and it just work... I have the latest Flash plugin for Firefox, but something isn't right, as YouTube doesn't work either.

The Download page for BBC iPlayer is non-functioning, and really shouldn't be there, as it must be confusing a lot of people, especially those new to Linux.

Grrrrrr!

---

### Post by megamonkey on 2012-02-11
It doesn't work for me either, that said get_iplayer is very easy to use when you know how.

Have a look at this vid for an explanation.

[http://www.youtube.com/watch?v=DRmM_dN307M](http://www.youtube.com/watch?v=DRmM_dN307M)

---

### Post by zurga on 2012-02-15
get_iplayer is not to be confused with the BBC iplayer. The latter is not intended for use in Linux environment. I use get_iplayer, and it works just fine for me. It is a command line program, so after installing it you can in a terminal do
[COLOR=Magenta]man get_iplayer[/COLOR]
which will display the manual for the command including many options which you don't initially need. So to start you quickly do something like
[COLOR=Magenta]get_iplayer prisoners[/COLOR]
in a terminal. This will list all the programmes available at the time, with prisoners in their title as below:
[COLOR=Blue]Matches:
523:    Prisoners' Wives - Episode 1, BBC One, Audio Described,Crime,Drama,Guidance,Relationships & Romance,TV, default,audiodescribed
524:    Prisoners' Wives - Episode 2, BBC One, Audio Described,Crime,Drama,Guidance,Relationships & Romance,TV, default,audiodescribed
525:    Prisoners' Wives - Episode 3, BBC One, Audio Described,Crime,Drama,Guidance,Highlights,Popular,Relationships & Romance,TV, default,audiodescribed,

INFO: 3 Matching Programmes[/COLOR]
Note that each programme is associated with a Programme Identifier (PID). If you like to download episode one of Prisoners' Wives, you can do
[COLOR=Magenta]get_iplayer -g 523[/COLOR]
This will download and save a flv file with a clearly identifiable name.
The file can be played with a number of players. If you have installed ffmpeg package it includes a player called ffplay:
[COLOR=Magenta]ffplay filename.flv[/COLOR]
will play the file. Alternatively, if you have installed VLC, which has ffmpeg integrated into it, it also has its own GUI, which you can use in the normal way to play the file.

---

### Post by Robbo35 on 2012-02-24
Thank you Zurga for clearing this up for me.  I think I was getting a bit confused!  I understand the difference now.
 
Cheers

---

