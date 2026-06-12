---
title: "startup boot/kernel messages too fast to read"
date: 2012-06-10
forum: General Help
---

### Post by amoun on 2012-06-10
Hi

I have the age old problem of trying to read the messages during start-up. I've seen a few threads on this but to no avail. 

1. There doesn't seem to be a way of paging the screen or accepting each option individually, as there was/is in Windows.

2. Reading all the files in /var/log doesn't get it, as I can see a 'FATAL ERROR' in the messaging but no such thing in the files. In fact the files are hugely different from info shown whilst the kernel is loading etc.

So any help would be appreciated in reading all the text before the GUI kicks in.

Thanks

---

### Post by amoun on 2012-06-20
Bumping as it's been over a week.
Changed title to enhance the problem.
How can I find out what the FATAL ERROR refers to ??

Thanks and apologies for the bump ::redface:

---

### Post by amoun on 2012-08-24
Any ideas on how to pause boot/starup messages so they can be read??

---

### Post by oldfred on 2012-08-24
The same info should be in /var/log/demesg. Use Log File Viewer to review log files.

---

### Post by bogan on 2012-08-24
Hi!,** Amoun**,

Try editing the grub menu script by adding '--verbose text' instead of 'quiet splash' at the end of the 'Linux /boot... line and press 'Crtl+x' to boot.

You could also try adding 'nomodeset', though I doubt that will cure your problem.

[ If necessary, press 'Shift' at the beginning of the boot sequence, to get the grub menu. Highlight the ubuntu entry and press 'e'; the script will be displayed.]

This should show you all the messages and terminate in a tty log-in prompt, from which you can start the GUI with:```
 sudo service lightdm start
```,

Or you can try pressing: 'Crtl+Alt+F1' from the login screen to see if there are any visible messages.   'Crtl+Alt+F7' will return you to the GUI.

Chao!, **bogan.**

---

### Post by amoun on 2012-08-24
Thanks oldfred

The demesg doesn't have references to the messages that flash past at start up,that I am querying, but I have now found how to open all the messages in /var/log via the System Log application, so I will look at the various, nay numerous, logs there and report back.

---

### Post by Fred4D on 2012-10-23
That's what worked for me:

[IMG]http://upload.wikimedia.org/wikipedia/commons/8/8c/Key_break.jpg[/IMG]

---

