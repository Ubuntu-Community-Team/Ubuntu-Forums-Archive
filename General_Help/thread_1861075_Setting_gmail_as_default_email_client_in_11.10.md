---
title: "Setting gmail as default email client in 11.10"
date: 2011-10-15
forum: General Help
---

### Post by gpw797 on 2011-10-15
Looks like prior fixes don't work in 11.10 anybody have a fix? Why the heck isn't this a standard option now?

---

### Post by haqking on 2011-10-15
> **gpw797 said:**
> Looks like prior fixes don't work in 11.10 anybody have a fix? Why the heck isn't this a standard option now?

because not everyone uses gmail.

What is your problem ? you are trying to set it as default in thunderbird or you have installed evolution and trying to set it as default.

Be more specific

---

### Post by Prince Valiant on 2011-10-15
I think that gpw797 is referring to this: [http://www.howtogeek.com/howto/ubuntu/set-gmail-as-default-mail-client-in-ubuntu/](http://www.howtogeek.com/howto/ubuntu/set-gmail-as-default-mail-client-in-ubuntu/) .

The difficulty is that there is no way to add one's own options: all that can be done is to choose from the installed applications (e.g Thunderbird).  What we (I think) would both like to do is have the default mail app button in the Unity dash point to gmail.com.  At least, that's what I want; and the phrasing in the title of gpw797's post is the same as in the articles describing what I just mentioned.  

I don't know (yet) how to fix this.  :-D

-Val

---

### Post by gpw797 on 2011-10-15
> **haqking said:**
> because not everyone uses gmail.

What is your problem ? you are trying to set it as default in thunderbird or you have installed evolution and trying to set it as default.

Be more specific

more specific > want to set gmail as default email client so when you click mailto etc.. it opens up gmail in web interface not a separate email client.

---

### Post by gpw797 on 2011-10-15
Correct...


> **Prince Valiant said:**
> I think that gpw797 is referring to this: [http://www.howtogeek.com/howto/ubuntu/set-gmail-as-default-mail-client-in-ubuntu/](http://www.howtogeek.com/howto/ubuntu/set-gmail-as-default-mail-client-in-ubuntu/) .

The difficulty is that there is no way to add one's own options: all that can be done is to choose from the installed applications (e.g Thunderbird).  What we (I think) would both like to do is have the default mail app button in the Unity dash point to gmail.com.  At least, that's what I want; and the phrasing in the title of gpw797's post is the same as in the articles describing what I just mentioned.  

I don't know (yet) how to fix this.  :-D

-Val

---

### Post by Prince Valiant on 2011-10-15
Here's a workaround; it's not very elegant and will disable the convenient use of Thunderbird.
Go to the website I referenced, as you'll need the code provided there.  Now, run nautilus as root: Alt+F2, then type 

```
gksu nautilus
```

go to user-->share-->applications, within the nautilus window that opens.  

Find the Thunderbird application shortcut.  Right-click, and open it's properties.  This is where you need the website info.  Get the string that launches the shell script (/home/geek/open_mailto.sh %s), edit it for your username, and put it into the command line in the Thunderbird preferences window, instead of the command that launches Thunderbird (this is why Thunderbird won't work conveniently).  

I changed the icon as well; I just Googled a gmail icon to go instead of the Thunderbird icon (click on the icon in the preferences box).  

Now, download and follow the instructions on the site for placing the shell script.  I edited the script to open my inbox with chrome; my changes are below.  

```

#!/bin/sh

google-chrome https://mail.google.com/mail/u/0/#inbox
```

Note that you launch Chrome with the command 'google-chrome', not 'chrome'.

I didn't care to have mailto links work, so I didn't try to achieve that.  If you want that, it'll take some more finagling.  :-D

Have fun!
-Val

P.S. If that helps, please change your thread to say [SOLVED].  :-D

---

### Post by markbl on 2011-10-19
> **gpw797 said:**
> Looks like prior fixes don't work in 11.10 anybody have a fix? Why the heck isn't this a standard option now?

Why the heck has Ubuntu removed the "Custom" option? This constant dumbing down at the expense of usability is really peeving me.

And they really should have added a gmail option by now anyhow, as the OP says.

---

### Post by wildkiev on 2011-11-15
sudo apt-get install gnome-gmail

That'll add Gmail as an option in system-info ;-)
expanding on the [SOLVED] answer in [http://ubuntuforums.org/showthread.php?t=1390756](http://ubuntuforums.org/showthread.php?t=1390756)

---

### Post by epicwiki on 2011-12-06
> **gpw797 said:**
> Looks like prior fixes don't work in 11.10 anybody have a fix? Why the heck isn't this a standard option now?

install gnome 3, then look for a package called gnome-gmail, that will have you sorted

---

### Post by rajohns08 on 2012-01-25
once installed go to applicatons > system tools > system settings > system info

---

### Post by phaemon on 2012-07-03
In unity:

sudo apt-get install gnome-gmail

Then go to System Settings...Details...Default Applications

Choose gnome-gmail as your default email.

This *really* should be in the mainstream; I believe Google Mail is quite popular now... :?

---

### Post by bkline on 2012-10-12
> **wildkiev said:**
> sudo apt-get install gnome-gmail

That'll add Gmail as an option in system-info ;-)
expanding on the [SOLVED] answer in [http://ubuntuforums.org/showthread.php?t=1390756](http://ubuntuforums.org/showthread.php?t=1390756)

Is there a comparable solution for xfce4?

---

### Post by JonPaul on 2013-03-25
In Firefox - Edit/Preferences/Applications Mailto: allows you to set gmail. Then when you click on mail link brings up a gmail compose window.

---

### Post by bkline on 2013-03-25
> **JonPaul said:**
> In Firefox - Edit/Preferences/Applications Mailto: allows you to set gmail. Then when you click on mail link brings up a gmail compose window.

Thanks, but that only works for links encountered in Firefox.  This thread is discussing a system-wide solution, in which all well-behaved apps do what you want when following mailto links.

---

