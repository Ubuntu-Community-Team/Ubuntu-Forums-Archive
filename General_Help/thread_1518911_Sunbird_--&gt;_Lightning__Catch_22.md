---
title: "Sunbird --&gt; Lightning:  Catch 22"
date: 2010-06-27
forum: General Help
---

### Post by blazemiskulin on 2010-06-27
I run several boxen on Kubuntu, and I always use my laptop (the least critical) to test major upgrades.  When I upgraded to Lucid, I discovered that Sunbird was removed.  This causes a major problem for me, as I use it for 3 separate businesses (my own and client's).

I don't particularly like Lightning, but I'm willing to migrate to it in order to keep my data and functionality.  I'm sure I'll get used to it after a while.

The problem is this:

On my business desktop, I attempted to install the lightning extension so I could migrate my calendars, play with them, and get used to the differences.

The current official lightning extension is only available for Thunderbird 3.x.  So I tried to upgrade Thunderbird.  It won't upgrade until I upgrade to Lucid (I have no clue why, but it won't).  If I upgrade to Lucid, Sunbird will be nuked.

I know that I can record all the locations and logins for the various calendars and recreate them after uprading to Lucid, but that means I have no chance to play with Lightning and find out how it works.

Does anyone have a valid link to a previous version of the Lightning extension that can be installed on Thunderbird 2.x so I can test it out before upgrading?

On a tangential note:  I understand that Sunbird is no longer being developed or supported, but... why in the world would it be *uninstalled* as part of an upgrade?  That's just rude.

---

### Post by SteveDee on 2010-06-28
> **blazemiskulin said:**
> I run several boxen on Kubuntu, and I always use my laptop (the least critical) to test major upgrades.  When I upgraded to Lucid, I discovered that Sunbird was removed.  This causes a major problem for me, as I use it for 3 separate businesses (my own and client's)....

You started by saying that you have already upgraded your laptop to Lucid. If that's the case, why not install the latest Lightning extension to Thunderbird and test your calendars on the laptop? (sorry if I'm missing the point).

You should export your existing calendars in iCalendar format, so they can be simply imported in Lightning.

I've just gone through the same process. If Sunbird is being discontinued, it is better to take the recommended alternative. However, do make sure you are happy with Lucid before making the switch.

---

### Post by blazemiskulin on 2010-06-28
> **SteveDee said:**
> You started by saying that you have already upgraded your laptop to Lucid. If that's the case, why not install the latest Lightning extension to Thunderbird and test your calendars on the laptop? (sorry if I'm missing the point).

The two systems (laptop and desktop) are so radically different.  I've looked at Lightning on the laptop.  It's different enough from Sunbird that I want to test it out on the desktop--where I'm using it in conjunction with half a dozen other programs.  It's not just about the application, it's about the workflow.

---

### Post by Benchrest on 2010-06-28
I have sunbird running on Lucid.  Let me find my notes.

---

### Post by Benchrest on 2010-06-28
first save the sunbird calendar. I saved mine from my jaunty machine as part of backup prior to loading lynx. Mine is 0ojb70qr.default. You will find it in the .mozilla/sunbird folder. Yours will have a similar but different name. I use the same name on both my machines so it's easier to copy back and forth to sync. 
I went to the mozilla site [http://www.mozilla.org/projects/calendar](http://www.mozilla.org/projects/calendar) and downloaded the sunbird program. I used the linux x86,english. Downloaded sunbird-10b1.tar.bz2

The site says this is the last sunbird release and they recommend lightning. But this will give you time to plan.

double click on the file and that starts the extract process. Select your files to go to .mozilla/sunbird folder. after that finishes copy your saved calendar to sunbird and change the profile to look at your calendar.

I moved the whole contents of .mozilla/sunbird to leave it empty before extracting the new

When you edit applications to add it to office, you need to give the full address of the program. mine is /home/userername/.mozilla/sunbird/sunbird

I use mine with alltray. so I have in startup programs 
alltray /home/username/.mozilla/sunbird/sunbird

I also use FG Printers addon with sunbird and there is a new release 0.4.9
Hope this helps.

---

### Post by blazemiskulin on 2010-06-29
@ Benchrest

Thanks.

All my calendars are remote, so I'm not worried about the data. 

There aren't any problems with the manual install?  I've had a few instances in the past where trying to use an old program on an upgraded OS caused problems.  I'm just minorly paranoid.  :)

---

### Post by Benchrest on 2010-06-29
This is not an old program, it is a new release. (its a beta). You have most likely been running release 0.9, this is 1.0b1 . 

The only problem I had was adding it to "applications menu" and "startup applications" I had to insert the full address of the application as I stated. With a normally installed program you don't have to tell where a program is, the system finds it. With a program installed like this you have to give the full address.

---

### Post by blazemiskulin on 2010-06-29
I'm sorry.  I wasn't clear.

I meant running the "old" Sunbird, not Lightning.

---

