---
title: "Gnome-Do in Openbox, Folders open in Browser!"
date: 2011-03-12
forum: General Help
---

### Post by migel_wimtore on 2011-03-12
Hi. I rely heavily on Gnome-Do to open folders in Nautilus.

This worked just fine in Ubuntu Desktop. However, in Openbox it opens folders in Chromium.

This is annoying for two reasons:

One, obviously i would like to view the selected folders in Nautilus. 

And, two, i would like to set Firefox 4 as the browser of choice when opening anything via Gnome-Do. It is set as my browser of choice in Preferred Applications.

I have searched for configuration files, but see no entry i could modify, and would not know where to begin writing my own commands.

Can anyone help?

I am sure many people must use Gnome-Do in Openbox. If you are one of them, did you encounter similar issues? If so, how did you fix them?

Thanks.

---

### Post by migel_wimtore on 2011-03-22
Well, i am using debian with openbox now, but the problem persisted. However, i few tweaks later and i found a, tweak free, solution.

So, for anyone else with similar issues potentially reading this, i will explain what fixed the issue for me.

Now, both the "xdg-open" command and folders opened via Gnome-Do open, as they should, in Nautilus and not a web browser.

The solution:

Install "libfile-mimeinfo-perl".

Probably not news to many, but may help some. 

Im pretty sure this should take care of it, however, i had also tried adding a space and a full stop, or that thing that girls have, (ie, " .") after the "x-directory [...] nautilus" and inode/directory [...] nautilus" entries in ~./.local/share/applications/defaults.list, as well as adding "export BROWSER=nautilus &"  to my autostart. 

However i have since undone these changes and Do is still working properly, so i think libfile-mimeinfo-perl alone took care of it.

Sweet!

---

### Post by jockopablo on 2011-05-11
Thankyouthankyouthankyou!  I came here searching for an answer to this problem and your solution worked perfectly!

---

### Post by migel_wimtore on 2011-05-11
Sweet. How do text files open when activated by DO for you?

Leafpad is my preffered general text editor application, however DO opens text files blank.

I use Kupfer as a launcher now, it is faster, however, it doesnt have adjustable depth in folder searches and i would consider moving back to DO.

---

### Post by jockopablo on 2011-05-12
Honestly I'm not familiar with DO.  The problem I was having was when I was selecting "Open in folder" for a Chrome download or when I tried to open my Drobox folders they would both open in Chrome instead of Nautilus.  That was very annoying.

Installing the mimeinfo pack fixed it and now they both open in nautilus, as they should.

---

### Post by migel_wimtore on 2011-05-12
Just out of interest, could you try navigating to a text file in DO and see what happens when you try to open it?

Are you using Geddit?

---

### Post by jockopablo on 2011-05-12
I just checked and I don't even have gnome-do installed.  I haven't modified my base Lubuntu install much.  And I'm a Linux n00b, so I'm afraid I won't be much help to you.

---

### Post by migel_wimtore on 2011-05-12
Oh. Sorry, i misunderstood you. 

Cheers.

---

