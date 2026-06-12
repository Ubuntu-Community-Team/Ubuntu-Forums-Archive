---
title: "Unity Webapps on 12.04"
date: 2012-07-19
forum: General Help
---

### Post by jasonsmith01 on 2012-07-19
Taking into account this is a feature for 12.10 and that it is still unfinished I thought it would be nice if we could share some experiences for anyone using this on PP. It installed just fine for me via the PPA. I rebooted and it failed to integrate. I logged out and back in and I was able to see a integration dialog or two. I have created a few web apps, Launchpad, Last.Fm and Google Calendar. 

All of the launcher bar icons so far are generic grey question marks, nothing app specific. 

Last.Fm does not integrate with the sound menu. 

I am not getting an integration dialog for many site, such as Facebook, Twitter, Google Reader, Gmail etc. 

I love the feature and am hoping it gets a little bit of backporting into PP. 

Anyone else having any good mileage so far?

[http://www.omgubuntu.co.uk/2012/07/how-to-install-ubuntus-new-web-apps-feature?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29](http://www.omgubuntu.co.uk/2012/07/how-to-install-ubuntus-new-web-apps-feature?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29)

---

### Post by werewolves on 2012-07-20
So far I'm only using it for Gmail (which works great), and Reddit, and I haven't really seen it do much except put an icon in my messages menu.  Will probably try out Google Calendar tonight.

I too get nothing but the grey gears icon in the dash, kind of a bummer.

My biggest question is where do I change things?  If I click "never for this site" on Facebook, how do I change my mind later?  If I decide the Reddit integration isn't that great, how do I turn it off?

---

### Post by jasonsmith01 on 2012-07-20
Yep, I agree. So far there's no way to access any of the functions other than the plugins. No way to delete the webapps or even the whole package. There needs to be some control panel someplace. It's introduced some bugs into Unity from what I can see, hoping they eventually get solved for PP.

---

### Post by werewolves on 2012-07-24
> **werewolves said:**
> My biggest question is where do I change things?  If I click "never for this site" on Facebook, how do I change my mind later?  If I decide the Reddit integration isn't that great, how do I turn it off?

Ran across the answer to this:

Install dconf-tools:
**sudo apt-get install dconf-tools**

Then open Dconf Editor from Dash, navigate to: **com > canonical > unity > webapps** and edit the "allowed domains" value.

---

### Post by jasonsmith01 on 2012-07-24
That's a good find, I wish there was a way to actually uninstall these items as I'm sure they leave something behind no?

I must say though the past few days has had some good updates and most is working nicely now, there's also a good bug list started so things are getting rolling.

---

### Post by jasonsmith01 on 2012-07-24
Okay a new question...

How do you change the address that the new webapp goes to? In my case I have Launchpad taking me to one specific bug, I want it to go someplace else. I'm going to start digging around.

---

### Post by TedinOz on 2012-07-24
For me it is working fine on Chromium for gmail, twitter etc. I also use Firefox from time to time but after an update from Software Updater today for Web Apps package, every time I use Firefox, even though it runs fine, every time I close it I get a crash report. This has only started happening since the update. Anyone else experiencing this?

---

### Post by jasonsmith01 on 2012-07-24
I'm not using Firefox but check the LP bug page [https://bugs.launchpad.net/webapps-applications](https://bugs.launchpad.net/webapps-applications) and see if someone else has reported it. I've added all the ones that I have had including a few extra.

---

### Post by TedinOz on 2012-07-24
> **jasonsmith01 said:**
> I'm not using Firefox but check the LP bug page [https://bugs.launchpad.net/webapps-applications](https://bugs.launchpad.net/webapps-applications) and see if someone else has reported it. I've added all the ones that I have had including a few extra.

Thanks for that. Can't see the problem reported yet so will figure out how to report it as a bug and see where that goes.

---

### Post by Stray Wolf on 2012-07-25
I'm on 12.04 and so far haven't seen any benefit to Web Apps so far. It's a nice idea but functionality isn't there yet. You get a launcher icon for Google or Facebook but you have to open multiple instances of your browser or use tabbed browsing to keep that icon there without locking it to the launcher. I'd rather not have more items on my launcher anyway. I'd prefer integration with the sound and messaging menu but those features don't seem to work. And every time I log back on to my system I get an OSD message that I need to go to system settings > online accounts to grant access to my services because they failed to connect.

---

### Post by jasonsmith01 on 2012-07-25
In it's current state I would agree with you that it doesn't have much of a benefit, however there is lots of potential. My Google Reader webapp integrates with the notification drop down and lists the current unread feeds but the webapp needs to be open. 

My biggest compliant thus far is the lack control you have over the whole project. It creates webapps to specific sites but links to the pages you actually create the webapp on, so if you're not on the root or home page of that site the webapp goes to a page that eventually becomes not so useful. There is no easy way to change that. 

I don't like a cluttered launcher either so I just launch from the dash, it's easy and works well. For something like GReader though it needs to stay running to get the benefits. I would like the icon to actually show the unread count without having it open.

Bottom line, it's not doing anything negative having it installed, the instability bugs have been worked out. I can turn off the notifications easy enough by disabling the browser extensions, I love Ubuntu and all the cool features and this is just another one of them. I am trusting that it will develop into something very useful and I have no problem being a tester.

---

### Post by TedinOz on 2012-07-28
I persevered with it for a while but eventually the bugs got to me and I have removed it. I normally use Google Chrome which doesn't support it so went with Chromium which wasn't a success as it frequently crashed. In Firefox I had to disable the extension to keep the browser stable. Finally I was hit with updates requiring partial upgrades which I am dubious about having had negative un-met dependencies problems back in 11.04 so have decided to wait until it is fully stable in Precise before using it again.

---

### Post by jasonsmith01 on 2012-07-28
How did you remove it? That is something that doesn't look so clear to me. Was thinking of just removing all the packages from Synaptic.

---

### Post by TedinOz on 2012-07-28
> **jasonsmith01 said:**
> How did you remove it? That is something that doesn't look so clear to me. Was thinking of just removing all the packages from Synaptic.

That would work I think but I followed the instructions from here to ensure that the PPA was removed fully and all apps within were restored to their previous versions.

[http://askubuntu.com/questions/165662/how-do-i-install-and-use-ubuntus-web-application-integration?newsletter=1&nlcode=34838%7c7559](http://askubuntu.com/questions/165662/how-do-i-install-and-use-ubuntus-web-application-integration?newsletter=1&nlcode=34838%7c7559)

The commands are ```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:webapps/preview
```

---

### Post by jasonsmith01 on 2012-07-28
Thanks for that, nice to know it can be completely removed. 

I updated through Synaptic which overcame the Partial Upgrade. For some reason Ubuntu's Update Manager didn't want to install one of the signon updates. 

I like the idea of this, it's missing quite a bit to become actually useful though IMO. I'm not a fan of using the actual webapps as I find using the actual browser is easier. It's the desktop integration that I was hoping to get but so far all I'm seeing is notifications in the drop down, and they only work when the webapp is active. 

Not sure if what I'm going to do at this point, I do like to watch things evolve.

---

### Post by TedinOz on 2012-07-28
Yes I'm with you in all you say. Besides, Precise is so far the most stable version I have used and I am enjoying that so don't want to mess with it with something that is not right yet.

---

