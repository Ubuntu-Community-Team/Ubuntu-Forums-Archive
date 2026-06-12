---
title: "Devede says it can't find mplayer or mencoder?"
date: 2010-08-21
forum: General Help
---

### Post by inameiname on 2010-08-21
A recent update to ffmpeg, in which I've learned was an upgrade to the restricted ffmpeg as opposed to the unrestricted default one that is in the official repos, has now made it unable for me to use mplayer or Devede.

Reading up about this, especially from here: [https://answers.launchpad.net/openshot/+faq/723](https://answers.launchpad.net/openshot/+faq/723), I have learned it's a frequent problem when installing the restricted ffmpeg.

Basically what Devede says at startup is:

```

Cant's find the following programs:

mplayer
mencoder

Devede needs them to work. If you want to use Devede, you must install all of them.

```Using the terminal to open mplayer (or mencoder), I get this error:

mplayer: relocation error: mplayer: symbol codec_wav_tags, version LIBAVFORMAT_52 not defined in file libavformat.so.52 with link time reference

From my research, seems as though the problem lies in libavformat52 not being installed (or removed) and libavformat-extra-52 is installed, which is the same thing, but because it's the restricted version, it is called something different. Anybody know if that is correct?

Also, checking up, libavformat-unstripped-52 isn't installed but available, so should I install that to replace the missing libavformat52, as when I sudo aptitude install libavformat52, it says it conflicts with libavformat-extra-52?

Anybody have any idea? Thanks in advance.

UPDATE:

I installed libavformat-unstripped-52, which didn't conflict with the already installed libavformat-extra-52, just to see if it would basically just replace the missing libavformat52, which conflicted with libavformat-extra-52 and couldn't be installed safely, but after I did, nothing changed. I still get the same error with opening Devede and mplayer (or mencoder) in the terminal. Doh!

---

### Post by inameiname on 2010-08-21
I found this thread with seems to show my exact issue. However, no sure fix was given. Seems as though it's mplayer's version that is unable to handle the newest ffmpeg.

[https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/587203](https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/587203)

---

### Post by inameiname on 2010-08-21
So to all those who may have or have had this issue, here is the fix (or perhaps, a workaround of sorts):

It's the version of 'mencoder' and 'mplayer' that is causing it, which seems to conflict with the latest version of 'ffmpeg' (which was updated in the past few days). So that is what needs to be installed, or 'upgraded'.

I found the latest versions of the two through Launchpad ([https://launchpad.net/~falk-t-j/+archive/lucid/+build/1879607](https://launchpad.net/~falk-t-j/+archive/lucid/+build/1879607)) and once found, I installed. However, not before installing the following, which, despite not being needed with the previous version of 'mencoder' and 'mplayer', these later versions of those two require the following:

sudo apt-get install libdirac-decoder0 libggi2 libggiwmh0

When that is done, I just install 'mencoder' and 'mplayer' deb files, and voila, everything works. I have all the latest, including the latest 'ffmpeg'. Woohoo! Although, oddly enough, one of my PPAs is the culprit for the bad 'mencoder' and 'mplayer' that wouldn't work with the latest 'ffmpeg', so what I then had to do, which you wouldn't have to deal with, I put a hold on those two files using the following, so when the computer was updated, it didn't update those two:

echo "mencoder hold" |sudo dpkg --set-selections
echo "mplayer hold" |sudo dpkg --set-selections

---

### Post by Deadite81 on 2010-08-23
Thanks! I was getting very annoyed and you solved my problem.  I have the same ppa problem as you...VERY Annoying!

---

### Post by inameiname on 2010-08-23
Yeah, it was quite annoying. Actually, the PPA that has the screwy versions of mplayer and mencoder is [http://ppa.launchpad.net/guido-iodice/guiodiclucid/ubuntu/](http://ppa.launchpad.net/guido-iodice/guiodiclucid/ubuntu/), which has 2:1.0-rc3~0guiodic3. And while the problem is indeed mplayer at that version being unable to handle the latest ffmpeg, it is actually the typo in the version number, 2:1.0-rc3~0guiodic3, which has a '-' instead of a '~', so no new versions will ever update it. I actually emailed the package maintainer dude and he said he'd correct it soon.

---

### Post by Deadite81 on 2010-08-23
Yea, using custom PPAs I run into problems like this occasionally, especially with the ones that have lots of updated/alpha/beta packages. Usually shooting an email out to the maintainer solves the problem, as long as it's still being maintained at all! It can also get very confusing sometimes, so I'm glad you did the leg work. I'm not usually so lucky!

---

### Post by inameiname on 2010-08-23
Hehe, indeed. I have well over 30 PPAs, so I really got to figure out quickly what is working and what isn't. :P Actually, this is nothing compared to this one bad PPA update I had in Karmic several months back. I had no clue what was the issue, and it was bad because this one update was keeping me from running and installing a custom Live DVD that I made, so I couldn't back it up. I went from one PPA to another trying to figure out what was the trouble. Took ages. hehe Anyway, fortunately with this one, Guido's PPA is pretty large, and very well maintained, so hopefully it'll get fixed soon.

---

### Post by slumbergod on 2010-08-25
Using the N-Muench ppa to upgrade VLC to 1.1.3 (to eliminate an annoying bug) I discover the ffmpeg required was also no longer compatible with mencoder and mplayer.

Following the advice above, the replacements seem to have fixed the issue. My thanks.

---

### Post by inameiname on 2010-08-26
Glad my experience could help. 

Actually, I can update this to say here is the latest version of mplayer and mencoder, but actually if you add this ppa, you can get mplayer, mencoder, and ffmpeg of the latest version which are made to work for each other:

[https://launchpad.net/~lucid-bleed/+archive/lucidbleed-exp/+build/1921287](https://launchpad.net/~lucid-bleed/+archive/lucidbleed-exp/+build/1921287)

ppa:lucid-bleed/ppa

When that is done, I just install 'mencoder' and 'mplayer' deb files,  and voila, everything works. Then just do this:

echo "mencoder hold" |sudo dpkg --set-selections
echo "mplayer hold" |sudo dpkg --set-selections 	

FYI, if you don't have the PPA:guido-iodice/ppa like I do, and no bad mplayer/mencoder packages wanting to overwrite your latest, you don't need to put a hold on it. So really just add ppa:lucid-bleed/ppa and you will have working versions for it all.

FYI 2, for some reason those three files I needed with the other working version of mplayer aren't required with this one. So if you have them already, you can remove them:

sudo apt-get remove libdirac-decoder0 libggi2 libggiwmh0

---

### Post by Rytron on 2010-08-26
> **inameiname said:**
> So to all those who may have or have had this issue, here is the fix (or perhaps, a workaround of sorts):

It's the version of 'mencoder' and 'mplayer' that is causing it, which seems to conflict with the latest version of 'ffmpeg' (which was updated in the past few days). So that is what needs to be installed, or 'upgraded'.

I found the latest versions of the two through Launchpad ([https://launchpad.net/~falk-t-j/+archive/lucid/+build/1879607](https://launchpad.net/~falk-t-j/+archive/lucid/+build/1879607)) and once found, I installed. However, not before installing the following, which, despite not being needed with the previous version of 'mencoder' and 'mplayer', these later versions of those two require the following:

sudo apt-get install libdirac-decoder0 libggi2 libggiwmh0

When that is done, I just install 'mencoder' and 'mplayer' deb files, and voila, everything works. I have all the latest, including the latest 'ffmpeg'. Woohoo! Although, oddly enough, one of my PPAs is the culprit for the bad 'mencoder' and 'mplayer' that wouldn't work with the latest 'ffmpeg', so what I then had to do, which you wouldn't have to deal with, I put a hold on those two files using the following, so when the computer was updated, it didn't update those two:

echo "mencoder hold" |sudo dpkg --set-selections
echo "mplayer hold" |sudo dpkg --set-selections

Thank you inameiname. Your solution worked a treat. ;)

---

### Post by inameiname on 2010-08-26
Sure. :)

I just don't get why this bug hasn't been fixed, especially as it seems quite a few folks have it.

---

### Post by OsakaWilson on 2010-09-14
"When that is done, I just install 'mencoder' and 'mplayer' deb files"

I got lost here. Where are the "'mencoder' and 'mplayer' deb files" and how do I install them?

---

### Post by mc4man on 2010-09-14
> I just don't get why this bug hasn't been fixed, especially as it seems quite a few folks have it.
Well it's not an ubuntu bug if things break due to using ffmpeg libs from outside sources.

(the ffmpeg in lucid (and medibuntu) hasn't changed since release

---

### Post by Deadite81 on 2010-09-14
> **OsakaWilson said:**
> "When that is done, I just install 'mencoder' and 'mplayer' deb files"

I got lost here. Where are the "'mencoder' and 'mplayer' deb files" and how do I install them?

[https://launchpad.net/~falk-t-j/+archive/lucid/+build/1879607]("https://launchpad.net/%7Efalk-t-j/+archive/lucid/+build/1879607/+files/mencoder_1.0%7Erc3%2B%2Bfinal-0ubuntu3.1_i386.deb")

---

### Post by inameiname on 2010-09-16
Thanks for the links, [Deadite81]("http://ubuntuforums.org/member.php?u=996614"), I was away for a few days to reply.

---

### Post by Deadite81 on 2010-09-16
> **inameiname said:**
> Thanks for the links, [Deadite81]("http://ubuntuforums.org/member.php?u=996614"), I was away for a few days to reply.

Your Welcome.  The original page is here: [https://launchpad.net/~falk-t-j/+archive/lucid/+build/1879607](https://launchpad.net/~falk-t-j/+archive/lucid/+build/1879607)

Since you've used the links I'm going to remove them since they will change with the versions.

---

### Post by inameiname on 2010-09-16
Alrighty.

---

