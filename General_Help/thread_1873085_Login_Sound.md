---
title: "Login Sound"
date: 2011-10-31
forum: General Help
---

### Post by JaggedImage on 2011-10-31
I just reinstalled Ubuntu 11.10 on my laptop and I'm not hearing the  login sound which I used to hear. I hear it when I login the Guest  account though and the settings in the Startup Applications is the same  for the Guest account and my account. How can I fix this?

---

### Post by MG&amp;TL on 2011-10-31
Ubuntu, or Lubuntu? The thread is tagged Lu-?


In *U*buntu, you can mute the speakers in your account. Ensure they are not muted at the top in lightdm (login screen), then try it again.

So, login to your account, make sure speakers are ON, logout, lightdm, check bar at top, make sure ON-try again.

---

### Post by lisati on 2011-10-31
Hi, JaggedImage, welcome to the forum.

I've closed your other thread relating to this question, and edited the title of this thread to something that might grab people's attention a bit better. 

Feel free to let us know how you get on with MG&TL's suggestion.

---

### Post by JaggedImage on 2011-10-31
It wasn't muted but I'm still not hearing the login sound. All other sounds, such as music, work as they should. I'm just not hearing the login sound when I log into my account.

---

### Post by MG&amp;TL on 2011-11-01
Are you using Ubuntu or Lubuntu?

---

### Post by JaggedImage on 2011-11-02
I accidentally placed the wrong prefix. It should have been Ubuntu. Can it be changed?

---

### Post by lisati on 2011-11-02
> **JaggedImage said:**
> I accidentally placed the wrong prefix. It should have been Ubuntu. Can it be changed?

Done!

---

### Post by MG&amp;TL on 2011-11-02
No problem, it's just that the procedure is different for Lu- as opposed to U-.

I honestly can't think of any reason that would be. I shall do some googling, but I can't see a reason. What sound card/speakers do you have?

If you don't know, (like me !), look at the ouput of:

```
sudo lshw
```

and post the section under *-multimedia or *-audio or similiar.

Although I think it is probably lightdm, rather than your sound, as your sound plays normally. Lightdm is still relatively new, so it might be a bug.

---

