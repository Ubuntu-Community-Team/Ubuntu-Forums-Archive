---
title: "Can't Remove Skype from Unity Panel"
date: 2012-03-08
forum: General Help
---

### Post by superjudge3 on 2012-03-08
Hello everyone.

I am running Skype on Ubuntu 11.10, but I don't want its appindicator to appear in the upper panel.  I tried seeing if I could remove its entry under desktop -> unity -> panel in dconf editor, but the Skype entry isn't there.

What can I do to fix this?

---

### Post by coldjeanz on 2012-03-08
Are you talking about the ugly green icon at the top? 

I use this to get rid of it:

In terminal:

```
gsettings set com.canonical.Unity.Panel systray-whitelist "['JavaEmbeddedFrame', 'Mumble', 'Wine', 'hp-systray']"
```Log out, log back in.

If you want to add it back the info on this page should help

[http://ubuntuforums.org/showthread.php?t=1861843](http://ubuntuforums.org/showthread.php?t=1861843)

---

### Post by superjudge3 on 2012-03-08
The code you just gave me just modifies the white-list so that Skype isn't part of it anymore.  But Skype currently isn't part of my white-list, and the ugly green icon is still showing.

Thanks for the reply though!

---

### Post by coldjeanz on 2012-03-08
I admit I am no expert I just put that code in and it gets rid of the icon for me, not sure why it isn't working for you. I got it from here

[http://www.omgubuntu.co.uk/2011/04/run-skype-as-a-daemon-and-manage-it-from-empathy-in-ubuntu-11-04/](http://www.omgubuntu.co.uk/2011/04/run-skype-as-a-daemon-and-manage-it-from-empathy-in-ubuntu-11-04/)

---

### Post by superjudge3 on 2012-03-09
I tried your code and it didn't work... the thing is that Skype isn't in the white-list, but its appindicator still is showing (the ugly green thing).

How can I make the ugly green blob go away (without quitting Skype)?

---

### Post by coldjeanz on 2012-03-09
Ok try this

Terminal:

 ```
gsettings get com.canonical.Unity.Panel systray-whitelist
```Then

```
gsettings set com.canonical.Unity.Panel systray-whitelist "['JavaEmbeddedFrame', 'Wine', 'scp-dbus-service', 'Update-notifier', 'Skype']"
```Then run the command I mentioned in the first post. What should happen here is that Skype gets added to the white list and then the command I mentioned earlier will hide it.

But keep in mind without the ugly green blob you may run into some problems, right clicking on the green icon is what gives you all the options associated with skype and if you close your main skype window it becomes impossible to reopen the window without completely ending the process and restarting the program.

---

### Post by superjudge3 on 2012-03-09
I tried your exact code, and the ugly green blob is still there.

I manage my Skype chats and contacts through Empathy, so I don't need the green blob.

Can anyone figure out a solution to this?  Why is it appearing in the panel when it's not on the white-list?

---

### Post by superjudge3 on 2012-03-10
Anyone have a solution?

---

### Post by coldjeanz on 2012-03-11
Dunno what to tell you the method I provided in the link here: [http://www.omgubuntu.co.uk/2011/04/run-skype-as-a-daemon-and-manage-it-from-empathy-in-ubuntu-11-04/](http://www.omgubuntu.co.uk/2011/04/run-skype-as-a-daemon-and-manage-it-from-empathy-in-ubuntu-11-04/)

 is exactly what I used to get rid of it, since I also manage Skype through Empathy.

---

### Post by superjudge3 on 2012-03-11
Your solution would work if it weren't for the fact that Skype somehow can display itself on the panel without needing to be in the white-list.

Thank you for trying to help though.

Does anyone else have any clue as to why this is happening?

---

### Post by coldjeanz on 2012-03-11
When I first installed 11.10 the Skype icon in the panel was not showing for me. Initially I wanted it there so I added it to the whitelist using the codes above, however later I switched to Empathy and didn't need it anymore so I used the other code to remove it from the whitelist.

Are you sure Skype isn't on the whitelist? If you have dconf installed go to desktop > unity > panel and see if Skype is part of the whitelist there and get rid of it if it is.

I'm not really understanding why this would work for me but not you. What method did you use to install Skype on your system?

---

### Post by superjudge3 on 2012-03-11
I used the Ubuntu Software Center.  Trust me when I say that I checked dconf editor over 10 times but Skype wasn't in the white-list.

---

### Post by coldjeanz on 2012-03-11
I think I downloaded Skype straight from their website

[http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/](http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/)

That's the only thing I can think of that would be different. You could try uninstalling it and then downloading the .deb package from there and then redoing the steps from the link mentioned earlier.

---

### Post by superjudge3 on 2012-03-16
Nope, even after uninstalling and downloading the package off of the website, the green blob still shows up on the panel.

This is a problem.  Why is Ubuntu allowing this to occur?

---

### Post by superjudge3 on 2012-03-17
Can anyone help?

---

### Post by erik1001 on 2012-04-17
I have the same problem. I removed it from the whitelist and restarted, but it is still there.

---

