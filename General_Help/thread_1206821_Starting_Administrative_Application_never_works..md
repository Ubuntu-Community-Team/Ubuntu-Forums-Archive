---
title: "Starting Administrative Application never works."
date: 2009-07-07
forum: General Help
---

### Post by l951b951 on 2009-07-07
I'm running Hardy Heron on a compaq Evo N610c laptop; pretty much everything is set to the default out of the box setting.  I only use this computer about 1 time per week, maybe less, so every time I boot it up it has updates waiting.  I updated it on Wednesday night (July 1st) and turned it on today to find more updates waiting.  However, today I'm having an issue getting the updater to work.

I click on the update button on my panel and it starts to work; I click on install all updates and I get the application in my bottom tray that says "Starting Administrative Application", it runs for about 5-10 seconds then disappears.  The updater stays non responsive after this happens.  I restarted the computer and tried again, getting the same thing (never prompted for my admin passward, but locking down my updater while it waited for the admin password).  I restarted the computer and clicked on synaptic package manager, and got the same issue: "Starting Administrative Application" but never prompted for my password.  
Finally I opened a terminal and did sudo synaptic.  After pressing enter there was a 10 second delay, but it did prompt me for my password in terminal, I entered it and used synaptic to install my updates.  When the updates were finished, I was prompted to restart my computer, which I did.

However, even after these updates, I'm still getting the same inability to launch synaptic package manager from the menu bar, I have to use "sudo synaptic" to get past the "Starting Administrative Application".

Any ideas where to start looking?

---

### Post by michy99 on 2009-07-07
Try starting synaptic from the terminal with this command:```
gksudo synaptic
```Post any error message you get.

---

### Post by l951b951 on 2009-07-07
> **michy99 said:**
> Try starting synaptic from the terminal with this command:```
gksudo synaptic
```Post any error message you get.

Doesn't work at all, I get the same behavior: "Starting Administrative Application" then nothing.  terminal also hangs on the command and never brings the prompt back.  

Also, I should have mentioned, I forgot the difference between gksudo and sudo, "sudo synaptic" is bringing up the synaptic gui, I'm not having to do the entire updating process text based, just the launching of synaptic.

---

### Post by michy99 on 2009-07-07
It looks like the problem is with the gksudo command, since using sudo seems to work. (Although it isn't a good idea to use sudo with graphical programs.) Since you didn't get any error messages in the terminal, it's hard to tell what is happening. Maybe there is a clue in a log file somewhere. I still haven't figured out how to use log files yet.

---

### Post by l951b951 on 2009-07-07
Ok, while I was perusing synaptic after opening it with "sudo synaptic" the terminal popped this little gem up for me:

(synaptic:14865): Gtk-CRITICAL **: gtk_tree_view_unref_tree_helper: assertion `node != NULL' failed

is that related to my issue, or another issue entirely?  It popped up after about 5 mins of synaptic being open.

---

### Post by michy99 on 2009-07-07
I found another thread which may or may not be of help:

[http://ubuntuforums.org/showthread.php?t=816708](http://ubuntuforums.org/showthread.php?t=816708)

---

### Post by l951b951 on 2009-07-07
> **michy99 said:**
> I found another thread which may or may not be of help:

[http://ubuntuforums.org/showthread.php?t=816708](http://ubuntuforums.org/showthread.php?t=816708)

The advice from that thread meets the same result.  > You need to go into System > Administration > Software Sources, and uncheck the CD-Rom from the first tab.

Clicking on software services tries to open with "Starting Adminsistrative Application", then fizzles.  However, within synaptic, under settings -> repositories, opens a window called software sources that I believe is the same; however there is no checkbox for CD-Rom installs, just a notice "To install from a CD-ROM or DVD, insert the medium into the drive."

So i'm pretty much stuck in the same place.

---

### Post by michy99 on 2009-07-07
Another thing to look at:

[https://answers.launchpad.net/ubuntu/+question/34350](https://answers.launchpad.net/ubuntu/+question/34350)

---

### Post by l951b951 on 2009-07-07
> **michy99 said:**
> Another thing to look at:

[https://answers.launchpad.net/ubuntu/+question/34350](https://answers.launchpad.net/ubuntu/+question/34350)

I tried the following: > sudo aptitude reinstall gksu
Then restarted my computer to make sure everything was refreshed.

Followed the page down and looked at my etc/hosts/ and my config looked similar, I didn't have the domain attached to the name.

Any other suggestions.

---

### Post by l951b951 on 2009-07-08
Apparently my computer was just sleepy.  Shut it down, packed it up and left it in my laptop bag overnight, just turned it back on (around 24 hours later) and it's working.

So apparently it was just a fluke trying to irritate me.

---

