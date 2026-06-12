---
title: "Ubuntu 10.10 time keeps changing"
date: 2010-12-02
forum: General Help
---

### Post by altjx on 2010-12-02
I think I selected the wrong time during the installation and now at the top right corner, my time keeps changing back to one hour ahead. Not sure why. I've went into the Preferences of the Time/Date > Time Settings > and set an hour back manually. I check back in 30-45 minutes, it's back another hour ahead. Any idea?

I'm on a Dell Inspiron 1545. I searched the forums for a few threads but none of them were helping me.

---

### Post by mendhak on 2010-12-02
What time zone are you in (real life)?
What time zone did you select during installation?

Do you know if your time is being synced with NTP servers? 

Go to System > Administration > Time & Date 

Click the 'lock' to unlock it.

Then look at the configuration dropdown - is it 'manual' or 'keep synchronized with internet servers'?  You can also change your time zone there. HTH

---

