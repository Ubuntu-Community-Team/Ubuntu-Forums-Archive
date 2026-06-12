---
title: "The sound work fine for me but not for others account."
date: 2006-06-17
forum: General Help
---

### Post by Braim on 2006-06-17
Hi everyone, 

I've got a little problem and I hope someone would help me :-)

On the 1st June I installed the new ubuntu(I didn't do the upgrade from KUbuntu 5.1).

Since that install I've got a problem with my sound card. I've got 3 different users. A, B, C. On the account A everything works just fine (divX, mp3, gaim...) but when the user B or C connects to his session and try to open an mp3 no sounds come out of the speaker... it says that no sound card is configured. :confused: 

Am I the only one with that problem or what ? Can anyone help me to solve this ? I already tried Google and ... now I'm here :-P 

Thanks in advance for your advice.

Braim

---

### Post by asimon on 2006-06-17
Your users B and C need to be in the audio group. The user which is created during installation is added automatically to it. You can do this via System->Users and Groups. Your users must log out and log in again before any changes to their groups are effective.

---

### Post by Braim on 2006-06-17
Thank you it works :)
(and shame on me not having seen that by myself :oops: :oops: )

---

