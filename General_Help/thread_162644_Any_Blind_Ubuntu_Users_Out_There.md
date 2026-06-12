---
title: "Any Blind Ubuntu Users Out There?"
date: 2006-04-19
forum: General Help
---

### Post by gwilson on 2006-04-19
Moderators, please place this in the most appropriate forum.

I have a friend who has been blind from birth who is into computers. He relies on Windows XP with a third-party software package called JAWS that reads all of the text on the computer monitor to him via the sound card and speakers. He would like to experiment with Ubuntu, and I wondered if there are any blind Ubuntu users who can offer advice on setting up a system he could use. I've experimented with some of the Linux programs for the blind but have not had a lot of success.

Aside from the screen-reading software, he uses a program that converts text to braille and then prints the braille out using an embosser.

Any input would be appreciated.

Glen

---

### Post by henriquemaia on 2006-04-19
Bump!

Bumped this one because I think this is important.

---

### Post by gwilson on 2006-04-20
Bump.  Please respond if you have any info on Linux for the blind.

---

### Post by PapaWiskas on 2006-04-20
I know people dont respond if they dont know how to help, but if anyone has any inkling of somewhere that mr wilson could get some assistance that would be awesome.

I too think this is an important issue.

---

### Post by z_diver on 2006-04-20
[QUOTE=gwilson]He relies on Windows XP with a third-party software package called JAWS that reads all of the text on the computer monitor to him via the sound card and speakers. [/QUOTE]
I don't know how [COLOR="Red"]Gnopernicus[/COLOR] would fare in a direct comparrison with JAWS but it came preinstalled on Dapper so I gave it a shot the other day.  It was able to read text and links located on the screen to me and while looking into the settings, I noticed it also comes with a few braille settings.  Under Startup Mode > Active Components it lists Braille, Magnifier, Speech, and [COLOR="DarkRed"]Braille monitor[/COLOR].  Under the Speech Preferences it has many different voice lists and can be set to pronounce punctuation in different ways.  I did not test any of this though.

If you try it, please do write back and let us know your findings.  BEST OF LUCK!!!

---

### Post by gwilson on 2006-04-21
[QUOTE=z_diver]I don't know how [COLOR="Red"]Gnopernicus[/COLOR] would fare in a direct comparrison with JAWS but it came preinstalled on Dapper so I gave it a shot the other day.  ...
If you try it, please do write back and let us know your findings.  BEST OF LUCK!!![/QUOTE]

I also have Dapper installed with all of the latest updates for everything. I have Gnopernicus installed and assistive technology support activated. I can run Gnopernicus and get the box for setting start-up modes and preferences, but for some reason, I can't get it to read anything, such as an Open Office document.

Yours is working under Dapper, right?  Any hints?

Appreciate the interest you've shown.

GW

---

### Post by gwilson on 2006-04-21
I've also visited the Gnopernicus website and am working through what I've found there.

---

### Post by z_diver on 2006-04-21
[QUOTE=gwilson]
Yours is working under Dapper, right?  Any hints?[/QUOTE]
Not really.  It just works out of the box on my Toshiba m35-s359 laptop.  However, because of your post, I checked how well it works on my little IBM T21 and found that for some reason the sound features of Gnopernicus are disabled.  And at the moment it is not allowing me to turn this on.  I'll look into it further and compare what the differences are between the two installations.  I know I have installed some extra media programs and codecs through a script on the computer that is working.  I'll write back to let you know my findings.

---

### Post by z_diver on 2006-04-21
OK.  I got the IBM working by going to Preferences > Assistive Technologies > and then unchecking/closing and then opening/rechecking the box for "Enable assistive technologies.  Below that there was a note saying the [COLOR="DarkRed"]changes do not take effect[/COLOR] until you log out and then back in.  I checked the screenreader box. and then logged out.  Upon logging in again it is working.  I can use tab to go between active items on the desktop and gnopernicus reads the "tooltips" to me.  Thankfully it seems like the "tooltips" are rather complete.  There were a few issues using the mouse where I had to off the item in question a short distance before tooltips would be read aloud but it seems the tab button is better for navigation anyway because it removes most of the whitespace or "non-clickable" items from the screen.

I can understand the speech OK, and now I realized that there are braille device preferences that list 25 separate braille devices.  Several by Baum, Alvabraille, HandyTech, EcoBraille and one called Brltty's brlapi.

Hope this helps.  By the way, is sound working on your computer?  I guess that would be an "obvious" starting point.

---

### Post by eeried on 2006-04-28
Hello,

Though I am not blind I'm insterested in accessibility and free software for bind or partially blind people.

Perhaps a distro specially made for blind people may help, though its development is rather slow and it's a Live-CD: Oralux [http://oralux.org/](http://oralux.org/)

You can at least use it on your own from scratch -- no need for a sighted friend to help you at all since every step is rendered in speech (you can choose your speech synthesizer).

I think it's an excellent thing that wider accessibilty is taken care of in Dapper even if some stuff doesn't seem to work properly yet.

---

### Post by Henrik on 2006-04-28
Hello,

It is correct that some things are not quite working properly yet, and there are three main reasons for this.

1) The setup is not quite performing as we intended -- I just tested the latest Live CD; with F5 + choice 3. Assistive technology is enabled, but it should also launch on start. Instead you have to go to System -> Preferences -> Assistice Tech and enable the relevant options. You have to then either log out and in or type 'gnopernicus' in a terminal. Obviously our intention is for this to happen automatically -- should be easy ...

2) Speech with gnopernicus works fine in some programs (like gedit) and less well in Firefox and OpenOffice. This is due to lacking AT (assistive technology) support in those applications and should be reported as bugs to those projects. We would appreciate help from the community in testing applications for AT support and nudging upstream projects in the right direction.

3) The gnopernicus screen reader itself has it's limitations in that it's not very good at adapting itself to different applications. This will be much improved by a new gnome screen reader called Orca, currently in development, which is scriptable. The advantage is that it can adapt to the relevant apps and work around difficult UI quirks in host applications. See: [http://live.gnome.org/Orca](http://live.gnome.org/Orca) We are working closely with the Orca team to get the UI ready for Gnome 2.16. Orca can be installed from universe (called gnome-orca), for those who want to experiment.

So, in short we will have some level of AT support for dapper (up from nearly none), suitable for mid-level to experienced computer users. By Edgy Eft it should start being useable by a more general audience.

Again, we could really use some help with testing of AT support in applications. I have posted three Summer of Code projects on this topic, so if there are any tallented students out there with an interest in this, please have a look: [https://wiki.ubuntu.com/GoogleSoC2006](https://wiki.ubuntu.com/GoogleSoC2006) The Accessibility can usually be found at #ubuntu-accessibility or [https://lists.ubuntu.com/mailman/listinfo/ubuntu-accessibility](https://lists.ubuntu.com/mailman/listinfo/ubuntu-accessibility) Feel free to join us :)

---

### Post by michaeljt on 2006-05-02
Hello,

I must admit that I am not blind, but the subject does interest me.  About the first thing that struck me the first time I saw the Ubuntu web page was that accessibility was one of the major points mentioned, and in fact accessibility for blind people was one of the first things I thought of.  It strikes me that it would be a good thing for Ubuntu to add a sub-distribution for blind people to the current trio (with Kubuntu and Edubuntu) - in particular, perhaps, one designed to be usable in pure text mode.  I would have thought that Ubuntu has enough momentum and is respected enough to be able to find third-party funding for that.  In fact, it would mostly be a case of choosing the right software for the base sub-distribution and configuring it correctly, since I think that Linux has most of the software available.

Just as some food for thought, I was recently reading a blind programmer's web site ([http://www.eklhad.net/cli.html](http://www.eklhad.net/cli.html)) in which he praised /bin/ed as being an ideal editor for blind users, since it reduces input and output to the necessary minimum instead of supplying lots of helpful information which is potentially more confusing than helpful to a blind user.  This sort of thing makes me think that tweaking a distribution might not be enough to make it blind-friendly.

---

### Post by dusanyu on 2006-05-04
Bumping again (importent ishue)

I know Dapper suports brale writers (after one of the recent updates i was asked about setting one up.)

While i hate to point at other distros i know OpenSUSE has Exalent Suport for the blind  (Suse has has a option called Blinux sence version 6.3)

info on linux for the blind Links 


Tips and Software for Blind Linux Users
[http://wwwcs.uni-paderborn.de/cs/heiss/blinux/index-en.html](http://wwwcs.uni-paderborn.de/cs/heiss/blinux/index-en.html)

Brass - Braille and Speech Server
[http://www.butenuth.onlinehome.de/blinux/index-en.html](http://www.butenuth.onlinehome.de/blinux/index-en.html)

blinux-newbie (mailinglist)
[http://speech.braille.uwo.ca/mailman/listinfo/blinux-newbie](http://speech.braille.uwo.ca/mailman/listinfo/blinux-newbie)

[http://www.suse.de/~thr/](http://www.suse.de/~thr/) (in german)

hmm prehaps this should lead into yet a Ubuntu branch espeshaly for users with Visual or phiscal imparement. 

we have an idea now all we need is a bunch of talented hackers :)

---

### Post by eeried on 2006-05-04
> Perhaps a distro specially made for blind people may help, though its development is rather slow and it's a Live-CD: Oralux [http://oralux.org/](http://oralux.org/)

So no one has any idea if this distro goes into the right direction?

It could help to start an Ubuntu version for the blind, couldn't it? 

I don't have dsl so I can't download the Oralux CD but if a friend of mine can I'll reprot on what it's like -- though from the point of view of a sighted person ...:-k

---

### Post by Henrik on 2006-05-05
I think the ideal option would be for Oralux to become Ubuntu-based (as Mephis did). They are already based on Debian/Knoppix AFAIK, so it should not be a very big change. 

That way Oralux could be a cutting edge testing ground for new assistive technologies and the more mature ones could make it into Ubuntu main. A blind user could install a system using an Oralux Live CD which would have more comprehensive support, and could then pull in the whole range of Ubuntu packages. Conversely, a system already running Ubuntu could be made more accessible by adding Oralux packages to it.

---

### Post by eeried on 2006-05-05
Sounds like a good idea Henrik, why not talk to the Oralux people -- they're French I think, but not many -- seem to be the two of them mainly. Yes Oralux is based on Knoppix.

Cheers

---

### Post by Henrik on 2006-05-13
The Live CD access features seem to work well now on the latest daily builds [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

I've also but up a brief getting started guide here: [https://wiki.ubuntu.com/Accessibility/doc/StartGuide](https://wiki.ubuntu.com/Accessibility/doc/StartGuide)

Now that we actually have something working, I can also contact the Oralux people (who have had a working but very different system for some time). I took their CD for a spin today, booting up into EmacsSpeak.

---

### Post by eeried on 2006-05-15
Good news, Henrick!

I haven't been able to download oralux yet.

---

### Post by Markp on 2006-06-11
Hi Glen did you get any takers for the blind Ubuntu users. I have a 12 year old blind son who i only getting to terms with the computer now. We have got Jaws and i am about to buy the real program but get a little confused with updates etc. 
I am not sure how to go about all this at the present but my son is a normal school and it is becoming difficult and expensive if we end up with the wrong software. Duxbury is also needed and i am looking to see if this is usable on Ubuntu and if it is available possibly second hand. 
Look forward to an answer oh this is my first time on this sight and it looks superb so far.
Regards
Mark

---

### Post by Henrik on 2006-06-12
Hi Markp,

If he is quite new to computers, you might want to start him off with a non-GUI environment, as there will be less clutter. The best option for that currently is the Oralux distro ([http://oralux.org/)](http://oralux.org/)), which is a Live CD that boots up directly into a speaking environment. 

Our Live CD can be made to start up speaking as well, with Gnopernicus in Gnome (see: [https://wiki.ubuntu.com/Accessibility/doc/StartGuide](https://wiki.ubuntu.com/Accessibility/doc/StartGuide)) Though this feature still has some wrinkles. We are working to improve the Gnome support in this cycle (due in October/November) and may also add non-GUI support.

---

### Post by Markp on 2006-06-12
Hi Hendrik
Just got you message and thanks.I am still getting to terms with the Linux and have not installed it as i am not sure how to. I am getting as much info on blind software before i make up my mind which way to go.
Regards
Markp

---

### Post by djringjr on 2008-02-17
We are also trying to get a keyboard driven distro for the blind!

[http://www.murga-linux.com/puppy/viewtopic.php?t=24571&sid=284fe90df919d1327ce503b6dd35f63b](http://www.murga-linux.com/puppy/viewtopic.php?t=24571&sid=284fe90df919d1327ce503b6dd35f63b)

Any help is requested especially from those who have brailler terminals.

Best

David Ring

---

### Post by eeried on 2008-02-18
What about Oralux, a distro that is already in existence??

---

