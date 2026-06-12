---
title: "Keyboard After Suspend"
date: 2012-02-08
forum: General Help
---

### Post by Rafterman414 on 2012-02-08
So I am sure many people are aware that on some systems after resuming from Suspend or Sleep mode the keyboard does not function. I ran into this last night on my Ubuntu 11.10 64bit Installation on my Wife's Sony Vaio VGN-CS215J. I just wanted to share a little tip that will hopefully save users from having to do a hard shutdown. What I did was I went to the universal access option (The little person in the circle) in order to bring up the On Screen Keyboard that way I could login and then shutdown the system. After the system came back up I immediately installed an SSH server so I could shutdown remotely in case this happens again.

If this is something the whole world knows already then I apologize, please feel free to file me under last to know.

---

### Post by Frogs Hair on 2012-02-08
Are you able to resume from sleep / suspend using the keyboard ? I dual boot and have always had to resume from sleep by depressing the power button slightly , but restarting is not required . I have never been able to use the keyboard as a device to resume from sleep since using Ubuntu . I think it may be hardware or driver related .

---

### Post by Rafterman414 on 2012-02-08
Oddly enough I can resume by using either the keyboard or the power button, its just Ubuntu that does not recognize the keystrokes. I guess its because the BIOS recognizes the key board input and instructs the system to wake. That makes me think, I might be able to reboot using SysRQ + REISUB if this happens again.

---

