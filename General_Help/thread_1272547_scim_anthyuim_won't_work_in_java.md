---
title: "scim anthy/uim won't work in java"
date: 2009-09-22
forum: General Help
---

### Post by adari on 2009-09-22
Hey folk! 
So I've just now realized that I can't use Japanese in Java.  It doesn't work in open office, or more importantly, on  KGS go server!  I'm running xubuntu 9.04 on an asus eee pc, and have followed these few guides: 
[http://ubuntuforums.org/showpost.php?p=3676161&postcount=6](http://ubuntuforums.org/showpost.php?p=3676161&postcount=6)
[http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=3100](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=3100)

currently I have: 
- added the scim config file to root user, as one guide suggested
- installed scim bridge, and changed /etc/X11/xinit/xinput.d/scim from:
> GTK_IM_MODULE="xim"
QT_IM_MODULE="xim"
to:
> GTK_IM_MODULE="scim-bridge"
QT_IM_MODULE="scim-bridge"
and also:
> XIM=SCIM
XIM_PROGRAM=" "
[FONT=Verdana]to [/FONT]
> XIM=SCIM
XIM_PROGRAM=/usr/bin/scim
XIM_ARGS=-d
XIM_PROGRAM_SETS_ITSELF_AS_DAEMON=yes

All of this in suggestion of various guides, though to no avail.  Might anyone have an idea of why scim/xim isn't working in java?

---

### Post by Irihapeti on 2009-09-23
Ubuntu, and I assume Xubuntu as well, has a different way of setting up Scim. There's only one configuration file that may need to be edited, and that's mainly for Java (see below).

There are two steps, and the first one may be all that's necessary for 9.04.

They are set out in this post: [http://ubuntuforums.org/showpost.php?p=7956308&postcount=2](http://ubuntuforums.org/showpost.php?p=7956308&postcount=2)

I've discovered since I wrote this that you only need to log out and in again, not reboot, even though the system tells you to.

After this, you should have Scim working in OpenOffice and most other programs. If your locale is en_US.UTF-8, then Scim should be working in Java as well.

If it isn't, you need to edit the file /etc/scim/global . The first line is

```
/SupportedUnicodeLocales = en_US.UTF-8
```

Add a comma to the end of the line, and then your locale, with no space between the comma and your locale name, like this:

```
/SupportedUnicodeLocales = en_US.UTF-8,en_NZ.UTF-8
```

Of course, replace en_NZ.UTF-8 with your locale if it's different.

Then log out and in again and Scim should be working in Java.

---

### Post by adari on 2009-09-23
Hi Irihapeti!

Thank you so much for replying.  The good news is, this partially fixed my problem.  The bad news is, it didn't fix the part that I need.  

Thanks to this command, if x has been restarted, open office works fine.  However, my java go server refuses to allow me to type anything in input unless scim has been exited and restarted.  Once scim is restarted, it no longer works in either open office, or the go server, most likely not anything java.

-adari

---

### Post by Irihapeti on 2009-09-23
I'm not sure what is going on here. It may be that you have encountered a bug with Java. I have used FreeMind quite a bit, also a Java application, and I've discovered that keyboard input can lock up completely under some circumstances. I'm not quite clear what those circumstances are, but I think it may be connected to the autosave feature. However, I've not had lockup problems with other Java apps.

I found this bug [https://bugs.launchpad.net/ubuntu/+source/scim/+bug/66104](https://bugs.launchpad.net/ubuntu/+source/scim/+bug/66104) on Launchpad which might or might not be related to your problem.

There's an alternative iBus input method available in 9.04 which might work better. I haven't used it myself (running 8.04 still) so I have no definite knowledge on that one.

If I find out anything further that might be useful, I'll post again.

---

### Post by Irihapeti on 2009-09-24
Update on iBus:

I remembered I had an install of Ubuntu 9.04 on a 4GB SD card in my EeePC, so I did some experiments.

I found iBus a bit sluggish to use, but that may be because of running from an SD card and also because I have CPU scaling running (to reduce power use when the thing isn't doing anything much). I didn't do a lot of testing, and only with ibus-pinyin. I did notice that the bugs I've seen in certain Java apps seem to have disappeared and iBus generally plays more nicely with Java. It's also easier to set up than Scim is.

The iBus in the official repositories doesn't seem to work properly. Instead, use the ppa repository for the 1.1 version (see [http://code.google.com/p/ibus/wiki/Ubuntu](http://code.google.com/p/ibus/wiki/Ubuntu) for instructions on installing the repository).

---

### Post by adari on 2009-09-24
Hi again!
I was really excited that  someone is trying to make an alternative to scim.  I tried installing iBus by following the website, I left scim installed, but still installed and added anthy for the list on ibus, and created a trigger of alt +` for iBus, and then restarted x.  I couldn't get it it to start, so I unistalled scim, incase there were any conflicts, and then changed the trigger to the standard control + space, and restarted x again.  Unfortunately, I'm still able to get iBus  to input at all so far.   Do you know of any guides, or anything else that needs to be done to make it work?
-adari

---

### Post by adari on 2009-09-24
alright a bit of progress:
found this post: [http://chinesepod.com/community/conversations/post/5398](http://chinesepod.com/community/conversations/post/5398)
So I completely purged everything scim/ibus and even im switch for good measure, then reinstalled ibus and im switch and restarted x.. got nothing, so i typed 
```
im-switch -s ibus
```
Still nothing.. looking further and tweeking preferences.. if I select "always" for "Show language panel," then the little bar letting me choose anthy shows up.. if I choose "when active" then no matter what trigger I set, it won't come up.  Even with "always" selected, I still can't actually use anthy, it just shows me the option for it in an extra icon.  So I guess that means that I can't activate iBus for some reason. 

another interesting note probably xubuntu based: 
applications -> system -> language support 
shows me: [http://i168.photobucket.com/albums/u180/himawariadari/language.jpg](http://i168.photobucket.com/albums/u180/himawariadari/language.jpg) .. no selection of any input method, which I've seen on others.

-adari

---

### Post by adari on 2009-09-24
wondering if this could be the problem:
```
sudo im-switch -v -s ibus
LC_ALL=""
LC_CTYPE=""
LANG="en_US.UTF-8"
LNG="en_US"
You are root user.
No system wide default defined just for locale en_US .
Use "all_ALL" quasi-locale and set IM.
update-alternatives: Cannot find alternative `/etc/X11/xinit/xinput.d/ibus'.

Changed system wide default from default to default.
From the package dependency information requires
  "".
```
Would this be it, and how could I go about fixing it, if so?

---

### Post by Irihapeti on 2009-09-24
im-switch is done WITHOUT sudo. That's probably why you are getting the error - you are using sudo.

You also need the locale, as in 
```
im-switch -z en_UTF-8 -s ibus
```

Make sure you are using the ppa repository for iBus, as the official Ubuntu version of iBus is broken.

---

### Post by adari on 2009-09-25
So I checked everything, and I did have it installed from the repository... completely installed it again and did the 
```
sudo apt-get update
``` 
with the deb in the source list.. it was all installed again, and I restarted x.. it didn't show ibus being installed at all, and when I typed it in terminal, it said infact that it wasn't installed.  I tried just installing ibus-gtk after... but that didn't help either, still no icon, still no ibus.  So I installed it from the repository again.. now ibus shows up on the side again, but still won't go active, and if i type "ibus" in terminal it still gives me: 
> The program 'ibus' is currently not installed.  You can install it by typing:
sudo apt-get install ibus

however, if i type "ibus-setup", then it does give me ibus setup.

---

### Post by Irihapeti on 2009-09-25
I have to admit that I'm stumped. The only thing I can think of - and it's a long shot - is to clean out the current configuration and start again: completely remove both iBus and Scim (as in "sudo apt-get purge scim ibus" and any related lib files), delete the .xinput.d directory in your home directory, and reinstall iBus from the ppa. I suppose you could reinstall the whole OS, but I could understand if it doesn't appeal.

I'm running Ubuntu 9.04 (occasionally) on my EeePC, not Xubuntu, so maybe there's some critical difference?

If I find any new information in my internet travels, I'll post here with an update.

---

### Post by adari on 2009-09-25
good news: after installing ibus-m17n and ibus-table, i can officially type in hiragana! I still can't type kanji though.  To make it type Japanese at all, I need to select anthy with a lower case a (&#12354; symbol instead of a crown with the capital a anthy). So now I need to get kanji working, and I have a working ibus completely!  Does this have anything to do with next input method?

The other good news, is the problem of not being able to type at all in java is gone!  
Bad news:  My problem still technically exists, the font that it types in is a  completely unreadable font of skinny japanese characters.  Any suggestions there?

---

### Post by Irihapeti on 2009-09-25
Glad to hear that you've made some progress!

There's a package "ibus-anthy" in the ppa repository. Have you tried installing that? If it acts like Scim-anthy does, then you should be able to convert hiragana to kanji.

Re the font problem: is this happening only in Java, or elsewhere as well?

---

### Post by adari on 2009-09-25
It doesn't act like scim anthy, it gives me no kanji selection, I can't seem to figure out how to get the kanji to show.  It won't type katakana either, only hiragana.  If I type in my go server, it shows up like: [http://i168.photobucket.com/albums/u180/himawariadari/test.jpg](http://i168.photobucket.com/albums/u180/himawariadari/test.jpg) , which should read "&#12371;&#12428;&#12399;&#12390;&#12377;&#12392;" (which was typed using ibus! yay!)  Interestingly enough, the font seems to show fine in openoffice though.  As openoffice and the go server are the only java based programs I use, I don't know  if it's like this for any other programs, or just kgs.

-adari

---

### Post by adari on 2009-09-25
excellent news kinda:  font now works fine in KGS!  I found out how to configure that, just by hitting the configure button...... kinda bad on my part heh.  Well I still needed ibus either way, since japanese won't type in java at all with scim.. atleast not to my research's content.  So now I just need to figure out how to type kata/kanji with ibus, and all of my problems are solved!
-adari

---

### Post by Irihapeti on 2009-09-25
Great that you have at least a partial answer to your problem, and I hope that the rest of the pieces fall into place for you. If I find out any more, I'll post here. I'm a bit limited by the fact that a lot of the iBus forum posts seem to be in Chinese and I'm only a beginner in that language. :)

---

### Post by Hiroshima on 2009-10-11
Same problem with UIM in Open office.  I see that the orginal "im-switch -z (your_locale) -s scim-bridge" is intended for scim.  Any suggestions for a similar command that would work for UIM?

Thanks in advance, Hiroshima

---

### Post by Irihapeti on 2009-10-11
> **Hiroshima said:**
> Same problem with UIM in Open office.  I see that the orginal "im-switch -z (your_locale) -s scim-bridge" is intended for scim.  Any suggestions for a similar command that would work for UIM?

Look in the directory _/etc/X11/xinit/xinput.d_

If you have installed UIM, you should see a file with a name containing "uim" (or maybe it's just "uim" on its own). Use that name instead of "scim-bridge" in the command.

ie. ```
im-switch -z (your_locale) -s (filename with uim in it)
```

---

### Post by Hiroshima on 2009-10-14
I gave it a try, and it didn't seem to work.  
I've now lent that computer out to someone, so I won't be able to try again for a while, but thank you for the advice.

Hiroshima

---

