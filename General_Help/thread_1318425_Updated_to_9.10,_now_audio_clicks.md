---
title: "Updated to 9.10, now audio clicks"
date: 2009-11-07
forum: General Help
---

### Post by MonsterMaxx on 2009-11-07
Every time the audio changes I get a pop.

In other words, launch a music player, and I get a pop.
In myth, when it starts I get a pop, when I close it I get a pop.  When I change to a different recording I get a pop.

Playback is normal and sounds fine, but this pop on a change is annoying and it never used to do this.

It never used to do this with 9.04.  NO HARDWARE CHANGES, only updated 9.04 to 9.10 via the update.

One clue may be that I installed virtualbox today and it refused to do any audio until I switched it to oss.  Note: it was doing this pop before installing virtualbox, so I'm sure that's not the cause.  Started doing the 'pop' when I did the update to 9.10

I know for a fact I used to be using Alsa.  But with Alsa selected in virtualbox I got nothing.

Could something have switched my audio to oss in the 9.10 update?  If so, how would I change it back to alsa and would this bollix everything else (specifically Myth?)

As always, thanks in advance.

---

### Post by impact on 2009-11-07
> **MonsterMaxx said:**
> Every time the audio changes I get a pop.

In other words, launch a music player, and I get a pop.
In myth, when it starts I get a pop, when I close it I get a pop.  When I change to a different recording I get a pop.

Playback is normal and sounds fine, but this pop on a change is annoying and it never used to do this.

It never used to do this with 9.04.  NO HARDWARE CHANGES, only updated 9.04 to 9.10 via the update.

One clue may be that I installed virtualbox today and it refused to do any audio until I switched it to oss.  Note: it was doing this pop before installing virtualbox, so I'm sure that's not the cause.  Started doing the 'pop' when I did the update to 9.10

I know for a fact I used to be using Alsa.  But with Alsa selected in virtualbox I got nothing.

Could something have switched my audio to oss in the 9.10 update?  If so, how would I change it back to alsa and would this bollix everything else (specifically Myth?)

As always, thanks in advance.

It's the power saving that is shutting down sound hardware after 10 seconds of inactivity and then turning it back on when a sound is to be played.

You probably should file a bug according to this:
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/380892](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/380892)

You can also manually edit /etc/modprobe.d/alsa-base.conf and disable power saving by changing the parameter back to 0: 
options snd-hda-intel power_save=0

That will get rid of the popping sound.

---

### Post by MonsterMaxx on 2009-11-07
seems to have fixed it. thank you.

for those who also hit this, a reboot is needed after editing the file

---

### Post by MonsterMaxx on 2009-11-07
woops, spoke too soon.

now I have no audio anywhere

---

### Post by MonsterMaxx on 2009-11-07
I took out the power_save_controller=N part and rebooted.

Seems to be working for the moment both natively and thru XP in a virtual box.

Will see how long that lasts and update as need be.

---

### Post by tenach on 2009-12-05
> **MonsterMaxx said:**
> I took out the power_save_controller=N part and rebooted.

Seems to be working for the moment both natively and thru XP in a virtual box.

Will see how long that lasts and update as need be.

All sound stopped when I set it to 0.  Commenting it out works like a charm.  Thank you! :popcorn:

---

