---
title: "How to make your desktop look like Mac OS X"
date: 2011-03-05
forum: General Help
---

### Post by Spyderkid on 2011-03-05
[COLOR="Blue"][SIZE="3"]It's very simple indeed to make your desktop look like Mac OSx, 
just folow these very simple instructions...

open a terminal by going to Applications > accessories > Terminal 

then paste and press enter each of these lines one at a time.[/SIZE][/COLOR]

```

wget https://downloads.sourceforge.net/project/macbuntu/macbuntu-10.10/v2.3/Macbuntu-10.10.tar.gz -O /tmp/Macbuntu-10.10.tar.gz
tar xzvf /tmp/Macbuntu-10.10.tar.gz -C /tmp
cd /tmp/Macbuntu-10.10/
./install.sh

```

[COLOR="Blue"][SIZE="3"]Then it will ask you questions answer with y(for yes) and n(for no)[/SIZE][/COLOR]

[SIZE="3"][COLOR="Red"]To un-install enter these using the same method:
```

cd /tmp/Macbuntu-10.10/
./uninstall.sh

``` [/COLOR][/SIZE]

---

### Post by RisingFalcon on 2011-03-05
Yah just got it installed yesterday.Saw that somewhere.Its totally awesome.Cant even imagine that in Windows

---

### Post by mmsmc on 2011-03-05
will this affect any futuer updates, and is there any known bugs with this?

---

### Post by RisingFalcon on 2011-03-05
Nopes.I am surprised to see me not even finding A bug

---

### Post by Spyderkid on 2011-03-05
There a no bugs (or at least so little bugs that it seems as if there are none) known, and it doesn't affect any future updates

---

### Post by mmsmc on 2011-03-05
thanks guys, this is amazing

---

### Post by tommywright on 2011-03-05
I want to try this.. but can your easily reverse it back to what you had before?

---

### Post by tommywright on 2011-03-05
didn't read carefully.  :P  sorry

---

### Post by RisingFalcon on 2011-03-05
Also to mention, After you open the install.sh via terminal, it will ask you various questions.Answer them with Y/n depending upon your wants :).

---

### Post by Spyderkid on 2011-03-05
edited according to your post RisingFlacon, i forgot to mention the Y/n stuff

---

### Post by vivek.pandey on 2011-03-05
i mtried as you said in the very first command i am getting an error..ca someone help

vivek@NEO:~$ wget [https://downloads.sourceforge.net/project/macbuntu/macbuntu-10.10/v2.3/Macbuntu-10.10.tar.gz](https://downloads.sourceforge.net/project/macbuntu/macbuntu-10.10/v2.3/Macbuntu-10.10.tar.gz) -O /tmp/Macbuntu-10.10.tar.gz
--2011-03-06 03:00:19--  [https://downloads.sourceforge.net/project/macbuntu/macbuntu-10.10/v2.3/Macbuntu-10.10.tar.gz](https://downloads.sourceforge.net/project/macbuntu/macbuntu-10.10/v2.3/Macbuntu-10.10.tar.gz)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://nchc.dl.sourceforge.net/project/macbuntu/macbuntu-10.10/v2.3/Macbuntu-10.10.tar.gz](http://nchc.dl.sourceforge.net/project/macbuntu/macbuntu-10.10/v2.3/Macbuntu-10.10.tar.gz) [following]
Error parsing proxy URL [http://localhost:4001](http://localhost:4001) : Bad port number.
vivek@NEO:~$

---

### Post by elliotn on 2011-03-05
old news

---

### Post by vivek.pandey on 2011-03-05
> **elliotn said:**
> old news

what?

---

### Post by towheedm on 2011-03-05
Ok so I just tried this.  Great theme if that's what a MacOS looks like.  However when I uninstalled it, two things it did not restore:
1.  The startup plymouth theme.  I needed to manually do an update-initramfs.
2.  I previously changed the computer icon in the login window of gdm.  It did not restore my icon, but the original icon.

Otherwise great.

---

### Post by Timmer1240 on 2011-03-06
Check out my mac look

---

### Post by mmsmc on 2011-03-06
how do you get those stats on the right? heres mine!

---

### Post by Timmer1240 on 2011-03-06
[http://www.techdrivein.com/2011/02/6-awesome-conky-configs-that-just-works.html](http://www.techdrivein.com/2011/02/6-awesome-conky-configs-that-just-works.html) go here it tells you what to do to get it

---

### Post by blueridgedog on 2011-03-06
> **mmsmc said:**
> how do you get those stats on the right?

Looks like Conky.

[http://conky.sourceforge.net/screenshots.html](http://conky.sourceforge.net/screenshots.html)

---

### Post by Timmer1240 on 2011-03-06
I love Linux you can make it look however you want!Ive got another user account set up to look like windows7 in case company comes and wants to use the computer they dont know the difference.

---

### Post by Timmer1240 on 2011-03-06
Heres my windows 7 look

---

### Post by purezwater on 2011-03-06
ermm...i already install ,but i found that after install i cant open the ubuntu software manager,anyone got the same problem ?

---

### Post by Timmer1240 on 2011-03-06
I never used a script to make mine look like a mac its just an Icon set Cairo dock conky and some fedora wallpaper!

---

### Post by purezwater on 2011-03-06
means i do the wrong thing already ?.....:confused::confused:

---

### Post by mmsmc on 2011-03-06
explain exactly what you did, make sure you dont have synaptic open as well, you cant have synaptic and software center open at same time

---

### Post by purezwater on 2011-03-07
ok ,can top pls explain further about "synaptic" cause i already mention in my post ,i am a newbie ...=-=...please lead me how to solve the problem and keep my mac theme please .

---

### Post by mmsmc on 2011-03-07
lets wait until tommorow, more people will be on to help

---

### Post by towheedm on 2011-03-07
Synaptic is the GUI Package Manager.  Packages are basically what you would download to install applications or programs or anything else for that matter.  The Software Sources tells the Package Manager where it can find those package, on the web or even locally on your PC.

Open a terminal, (Accessories > Terminal).  Enter gksudo synaptic and enter your password when prompted.  Does it open this way?

---

### Post by Spyderkid on 2011-03-07
This pack is basicly what you said Timmer1240 it just has a script to do it all for you

---

### Post by RisingFalcon on 2011-03-07
Try it with the Compiz Wobbly effect.It looks so darn cool yeh

---

### Post by Spyderkid on 2011-03-07
The "wobbly effect" (wobbly windows) is all included in this auto script from the package and all the windows borders backgrounds etc

---

### Post by towheedm on 2011-03-07
Does anyone knows what font is used for the text in the titlebar?  It looks like it's embossed?

---

### Post by Timmer1240 on 2011-03-07
I usually just piece together my theme or look by tweaking everything myself I dont like the window buttons on the left and I dont like the mac window boarders so I dont need all that jazz and yes i got wobbly windows.

---

### Post by MacintoshLover on 2011-03-07
AWN screwed up for me, so I switched to Docky. It looked fine with the skin. BTW, AWN is the dock included with this skin.

---

### Post by MacintoshLover on 2011-03-07
> **Spyderkid said:**
> Windows exists purely for Linux users to laugh atI love your signature!

---

### Post by Spyderkid on 2011-03-19
[EDIT] Screenshot attachments added

---

### Post by RobotoidHuman on 2011-03-23
Just installed... btw, how to change login screen Icon...? the current (default) icon is Mac icon (not macbuntu)... i want to use ubuntu icon... Thanks :)

---

### Post by Spyderkid on 2011-03-23
to change the login icon use ubuntu tweak program which was installed in the macbuntu change

---

### Post by son_of_a_beach77 on 2011-03-24
Nice!! But is it possible to make this
[IMG]http://images.maketecheasier.com/2009/10/secrets-installation.jpg[/IMG]
this is a dialog window
And this
[IMG]http://www.switchingtomac.com/wp-content/uploads/2010/11/OS-X-Parental-Controls.png[/IMG]
I think everybody know the unlock button some where in settings but in osx its a lock picture)

---

### Post by dazman19 on 2011-03-24
got a few very minor errors but works on Debian Squeeze 6.0 amd64

---

### Post by Spyderkid on 2011-03-24
son_of_a_beach777 I'm sorry but I don't quite understand your question?

and whats the top screenshot about and what are your questions? sorry...

---

### Post by blueridgedog on 2011-03-24
He/She is pointing out the small lock icon used to unlock super user permission on OS X and suggesting that that be used...I think.

---

### Post by Bender09 on 2011-03-29
I cannot get mine to uninstall. I followed the instructions correctly and went to the tmp folder and the macbuntu-10.10 isn't there. HOW do i uninstall.. thx

---

### Post by Spyderkid on 2011-03-30
go into file manager go to where ever the macbuntu folder is. it should be in your homefolder or downloads.... (where ever you extracted it) go into it and double click on uninstall.sh and click run in terminal.


Alternitavly go to appearance and click on Ambiance

---

### Post by lanetherif on 2011-03-30
By the way when it uninstalls, it resets your all your customizations to defaults, not to the ones when it was installed...

---

