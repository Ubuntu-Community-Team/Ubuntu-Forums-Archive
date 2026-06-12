---
title: "Firefox 4.0.1 bin issue"
date: 2011-06-15
forum: General Help
---

### Post by oldsoundguy on 2011-06-15
Not sure where to put this problem, so move it if need be.

I am  running 10.04LTS on my main computer and recently installed FF 4.0.1 on it.  In general all is OK, but now and then it goes nutso and locks up the box, requiring a re-boot.
When I select restart or shutdown on the options, I get a popup that "firefox.bin is running and do I want to quit anyway".
Could this be the initial reason for the lock up?  
Inquiring minds want to know how to keep the .bin from running in the first place.
Thanks.

---

### Post by prodigy_ on 2011-06-15
> **oldsoundguy said:**
> firefox.bin is running
You mean **firefox-bin**? It's just firefox executable, nothing wrong here.

---

### Post by oldsoundguy on 2011-06-15
> **prodigy_ said:**
> You mean **firefox-bin**? It's just firefox executable, nothing wrong here.

Then why am I being asked if I want to shut it down when I am forced to reboot because of a hang-up/freeze?
(the real issue is the FREEZE, and I am inclined to think that the running binary may be the cause.)

---

### Post by tredegar on 2011-06-15
I'm also running 10.04, but with FF 3.6.17. As far as I am concerned, everything works.

You need to be aware that although you *can* install newer software on older systems, it is not *guaranteed* to work. My 10.04 repositories say FF 3.6.17 is "the latest" (for this, 10.04), release.

I wonder what would happen if I tried to install FF 4.x on my win98 box in the attic. Something tells me it would not work.

If you want FF 4.x, then install 11.04 (or any other more recent, "cutting edge" distro). It is easy to boot to different linux versions. Then boot and use 11.04, or whatever, when you *need* FF 4.x

You probably do not need to reboot when you run into problems like this, just kill **firefox-bin** or logout and back in again, if you want the slower option. Rebooting is slowest of all, and *sooooo* windows.

Hope this helps.

---

### Post by prodigy_ on 2011-06-15
> **oldsoundguy said:**
> Then why am I being asked if I want to shut it down when I am forced to reboot because of a hang-up/freeze?
Because it doesn't exit gracefully when Gnome asks it to. And after you confirm reboot firefox process is simply killed.

> (the real issue is the FREEZE, and I am inclined to think that the running binary may be the cause.)
Very likely so. But without running it you won't be able to use FF. You can revert to 3.6.x or switch to another browser or provide more info for further investigation. Does it happen on specific sites or randomly? Does only FF freeze or something else too? Did you update addons after installing FF4?

Also have a look at memory usage. FF often has memory leaks. Sometimes they are caused by misbehaving addons.

---

### Post by oldsoundguy on 2011-06-15
I used the Ubuntuzilla method of installing FF 4.0.1 .. and yes the earlier version of FF worked just fine in 10.04, but I have FF 4.0.1 on all of the other 6 computers in the place and found that shifting back to 3.x on this ONE box felt clunky as buttons are in different places. 

I know this will get worked out, but tossed the question out just in case someone had stumbled across an answer.

I can live with the occasional re-boot to clean things up .. just that it should not be needed that often.

---

### Post by lovinglinux on 2011-06-15
> **oldsoundguy said:**
> I used the Ubuntuzilla method of installing FF 4.0.1 .. and yes the earlier version of FF worked just fine in 10.04, but I have FF 4.0.1 on all of the other 6 computers in the place and found that shifting back to 3.x on this ONE box felt clunky as buttons are in different places. 

I know this will get worked out, but tossed the question out just in case someone had stumbled across an answer.

I can live with the occasional re-boot to clean things up .. just that it should not be needed that often.

Ubuntuzilla is no longer under development. Remove it, then use a mozillateam ppa to install Firefox 4 or 5. See the [Firefox 4,5 & Beyond Mega Thread]("http://ubuntuforums.org/showthread.php?t=1712247") for instructions.

After that, [create a new Firefox user profile]("http://www.webgapps.org/tutorials/firefox/general/profiles-and-backups") and test if the problem persists. 

Also observe when the browser freezes in order to determine if it happens on particular web pages. It could be a plugin causing the crash.

Do you have the latest driver for your video card installed?

---

### Post by oldsoundguy on 2011-06-15
lovinglinux, thanks .. done now, will see what shakes out.  Noticed it seemed to happen when I launched Thunderbird from the task bar and then attempt to reduce it back to the bar.
And, yes, latest working version of the NVida driver package.
This is not an old (very) box .. it is a 3.4 hyperthreaded with 4gb of ram.  No other OS .. a stand alone.

---

### Post by lovinglinux on 2011-06-15
> **oldsoundguy said:**
> lovinglinux, thanks .. done now, will see what shakes out.  Noticed it seemed to happen when I launched Thunderbird from the task bar and then attempt to reduce it back to the bar.
And, yes, latest working version of the NVida driver package.
This is not an old (very) box .. it is a 3.4 hyperthreaded with 4gb of ram.  No other OS .. a stand alone.

I am not sure if it will help, because Firefox and Thunderbird doesn't depend on xulrunner package anymore, but I have seen some reports of problems being solved after installing xulrunner-2.0.

Anyway, if the problem occurs during maximizing/minimizing operations, then I suppose it must be related to video driver or xulrunner or both.

---

