---
title: "normal user cant hear sound"
date: 2006-06-06
forum: General Help
---

### Post by niC666 on 2006-06-06
I have upgraded to dapper 6.06 and am trying to get sound to work (amd_64). Incidentally it was not working before on breezy.
My current situation is as follows:
root can play sounds but no other user can, doing a sudo aplay somefile plays the file perfectly whilst a normal user gets:
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_dmix.c:819:(snd_pcm_dmix_open) unable to open slave
aplay: main:544: audio open error: No such device

only root can run alsamixer. 

i have changed the permissions on /dev/snd to no avail. I would really like to fix this because it seems like the answer should be trivial (one user can use the damn thing)

appreciate any help

---

### Post by ctgray on 2006-06-06
Have you tried adding the username to the audio group in /etc/group?

---

### Post by niC666 on 2006-06-06
[QUOTE=ctgray]Have you tried adding the username to the audio group in /etc/group?[/QUOTE]

yes i have, then logged in on a terminal but still no luck.
i see though, if i try play a sound whilst xmms is running as root playing to the sound card the error i get is this instead:
ALSA lib pcm_dmix.c:790:(snd_pcm_dmix_open) unable to create IPC semaphore
aplay: main:544: audio open error: Permission denied

dont know if that helps in any way.. i dont know how alsa works.. looks like it creates this 'default' device as it needs it.

---

### Post by niC666 on 2006-06-07
Ok it works!

hmm after rebooting it now seems to work, not sure if it was adding the user to the audio group or changing the permissions on the devices but rebooting seemed to sort it out.

thanks for the help

---

