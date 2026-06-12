---
title: "no sound alert in Thunderbird or DownThemAll"
date: 2011-06-03
forum: General Help
---

### Post by marstehr on 2011-06-03
I'm running Ubuntu 11.04, Thunderbird and Firefox with DownThemAll on an eeepc 1005ha.

I like Thunderbird to play a .wav sound file when new mail is comming in and DTA to play a sound when the download is complete, unfortunately they keep quiet. Thunderbird is able to give notice via 'Default system sound for new mail'.

DownThemAll doesn't play a sound when downloads are complete, even though 'Play a sound when downloads are complete' is ticket.

Banshee, Skype and the like all do their job. Start Up and other System sounds are playing too.
Anybody out there who has an idea and can help?

:guitar:

---

### Post by metakola on 2011-10-09
I had a similar sound issue with Thunderbird and I found a workaround for it that might be of help to you. I posted it about it recently here:  [http://www.metakola.com/w/guides/workaround-for-thunderbird-alert-sound-problem-in-ubuntu/](http://www.metakola.com/w/guides/workaround-for-thunderbird-alert-sound-problem-in-ubuntu/)

Maybe you can do a similar thing for DownThemAll? I haven't used that add-on in ages, so no idea.

I have the same netbook by the way, it's pretty nice.

---

### Post by Tangomog on 2011-11-12
I had the same problem with Thunderbird and I found the solution in the Ubuntu General Help forum (credit to mike555).

Install the following files (I used synaptic to install them):

Libaudiofile0
Libesd0
esound-common

Thunderbird sound alert now works fine.

With a bit of luck it might sort out DownThemAll as well.

---

### Post by e7a7b7 on 2011-11-28
Thanks, @Tangomog, that worked for me, too.

---

### Post by tomek_wap on 2011-11-28
@[Tangomog]("http://ubuntuforums.org/member.php?u=511534") thnx! That worked for me too. 

OT: Too bad many of those little things we would like to have as standard, need to be installed as an extra - and most of the time it's not so simple - I guess otherwise Linux would be no longer for bit more advanced users, and head towards Windows and OS X.
Sometimes I think that I would need to be a Linux developer in order to know those things...

---

### Post by vange on 2012-02-28
Thank you, it helped me on Oneiric 11.10.

> **Tangomog said:**
> I had the same problem with Thunderbird and I found the solution in the Ubuntu General Help forum (credit to mike555).

Install the following files (I used synaptic to install them):

Libaudiofile0
Libesd0
esound-common

Thunderbird sound alert now works fine.

With a bit of luck it might sort out DownThemAll as well.

---

### Post by marstehr on 2012-05-13
> **Tangomog said:**
> I had the same problem with Thunderbird and I found the solution in the Ubuntu General Help forum (credit to mike555).

Install the following files (I used synaptic to install them):

Libaudiofile0
Libesd0
esound-common

Thunderbird sound alert now works fine.

With a bit of luck it might sort out DownThemAll as well.

Thank you for your answer, those packages were the solution and made TB and DownThemAll playing the desired sound.

I did not reply earlier, because my eeepc passed away and  meanwhile I was using Bodhi Linux on another machine. 
 
I came back to this Forum, because with the upgrade to TB 12 the sound problem came back in a different way. The above packages were and are installed, still notification sound for DownThemAll, but no sound in TB.

If someone knows of a solution, please answer here:
[http://ubuntuforums.org/showthread.php?p=11933516#post11933516](http://ubuntuforums.org/showthread.php?p=11933516#post11933516)

Greetings and may the sound be audible
:guitar:

---

