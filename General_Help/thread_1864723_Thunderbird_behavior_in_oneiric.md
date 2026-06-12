---
title: "Thunderbird behavior in oneiric"
date: 2011-10-19
forum: General Help
---

### Post by marcb_ro on 2011-10-19
Hi all,

I have two laptops and have recently upgraded Ubuntu on both of them to 11.10 from 11.04.

Due to the fact that Thunderbird is the new default mail client, I have uninstalled evolution (which I have previously been using) on both machines and am now using Thunderbird for emails.

The curious thing is that on one laptop (dell) Thunderbird won't go to background when I close the window, but rather quits (it doesn't show up in the process list anymore). Hence I get no new mail notifications.

On the other machine (asus) Thunderbird does close to background, but I have to close the window two times, i.e. after I click the close button another main window of TB is opened, as can be visually confirmed from the dash (two arrows on the left of the TB icon). It is, however, interesting to note that at this point only one instance of the TB process is listed when issuing the *ps* command in the terminal (yes, I grep the output for TB). When I click on the close button again both windows dissapear and TB is backgrounded - I receive notifications and all.

This is a really strange behavior of TB. Please note that my stringent need is to get TB to close its window and remain in the background so I can receive new mail notifications, as I can, for now, live on with the two-clicks close approach.

Any help would surely be appreciated!

---

### Post by pancongato on 2011-11-15
I have the exact same problem.
I would like that Thunderbird started with system boot on the background so I could get desktop notifications, and to go back to background once closed, just like Gwibber and Telepathy.
Is there a way to achieve this?

---

### Post by marcb_ro on 2011-11-15
I actually found a solution [[COLOR="Blue"]here[/COLOR]]("http://askubuntu.com/questions/67522/closing-thunderbird-to-messaging-menu"). Basically, installing the Thunderbird extension *[[COLOR="blue"]MinimizeToTray revived[/COLOR]]("https://addons.mozilla.org/en-US/thunderbird/addon/minimizetotray-revived/?src=ss")* should do the job.

---

### Post by pancongato on 2011-11-15
That worked like a charm. Thank you.

---

