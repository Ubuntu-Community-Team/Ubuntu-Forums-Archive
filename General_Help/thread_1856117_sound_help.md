---
title: "sound help"
date: 2011-10-07
forum: General Help
---

### Post by ericsoderstrom on 2011-10-07
I get sound at the login screen (where I enter username/password)
but once actually logging in, I get no sound =(
This wasn't always the case, the behavior started quite recently. Any idea what's going on?

---

### Post by dreamsR4living on 2011-10-07
Are you using ubuntu 11.10? Last week my sound suddenly stopped working. Found out that it is some kind of bug with PulseAudio's settings which are saved in the Home folder.

After removing the .pulse folder in Home and restarted, the sound worked again. 

Execute the following command in the terminal to remove it;

```
rm -rf ~/.pulse
```

By the way someone else in the Forums is suggesting to remove .pulse-cookie

```
rm -rf ~/.pulse-cookie
```

Hope this helps. And if not, it is a different problem.

---

