---
title: "After upgrade to Lucid, Evolution calendar issue..."
date: 2010-05-04
forum: General Help
---

### Post by WilliamCampbellJr on 2010-05-04
Hi, all...

Just upgraded to Lucid, and noticed that my Evolution dumped my previous Calendar appointments. Additionally, when I try to add a new appointment and save it, I get an error box: "URI not loaded." It will not allow a new appointment.

Any ideas on what might have changed in Evolution in the upgrade? My emails are apparently still arriving as usual, accounts behaving the same. Just can't use the Calendar feature anymore...

Thanks for any ideas...

Oh, and I just noticed that the previously entered appointments are still highlighted in the "Go To" dropdown menu in the toolbar, but when I select the button and "Go to" the date, there is no information, no alarms that were previously set, etc...

And, as I just learned, the Evolution alarm for an appointment I had already set up before the upgrade works, even though I can not find any information in the GUI describing what the alarm was for...  Went to the config for the calendar, and just browsing through it, it seems as if the information is logged there; it's just not making it to the interface...

---

### Post by dcstar on 2010-05-05
> **WilliamCampbellJr said:**
> Hi, all...

Just upgraded to Lucid, and noticed that my Evolution dumped my previous Calendar appointments. Additionally, when I try to add a new appointment and save it, I get an error box: "URI not loaded." It will not allow a new appointment.

Any ideas on what might have changed in Evolution in the upgrade? My emails are apparently still arriving as usual, accounts behaving the same. Just can't use the Calendar feature anymore...

Thanks for any ideas...
........

And you are **sure** that you have selected your Personal Calendar and not another one?

---

### Post by WilliamCampbellJr on 2010-05-06
Yes. I don't have any other calendars. Here's an interesting twist. I thought I had it fixed this way: I changed the name of .evolution to .evolution_old, then restarted Evolution. It created another .evolution folder, and I dragged the old calendar.ics file into the new folder. That seemed to work just fine, until this morning, when I rebooted the computer, the calendar data was gone, as was the address book. Tried the same routine again: threw out the old .evolution, restarted Evolution. I had no file at all for calendar.ics, and yet the newly created Evolution recalled a test appointment I had made in an earlier version. Where is it getting this information, if there is no evolution.ics file to draw from? I can't pull up the old appointment information, and I can't seem to get rid of the new (fake) appointment info, can't even figure out where that info is stored if it creates a new .evolution file every time...

Any ideas?

Thanks

---

### Post by dmaxel on 2010-05-12
I have the same problem, just that I only have calendars set up with Google Calendars through Evolution. It happens occasionally, and I always have to exit Evolution, then start it again, and then most of the time it works again so that I can quickly add/edit the appointment.

---

### Post by itsAfork on 2010-05-28
I am running Lucid, my Google Calendars are setup through my Evolution Calendar, & had a **similar** problem. 

I was entering a new event, with alarms, into the calendar, & when I went to save the new appointment, I received the "URI not loaded" error. I noticed that while I had been entering the details for the new appointment, Evolution had some how (randomly???) lost the connection to all of my Google Calendars. I say the connection was lost because when I first started entering the details all 4 of the different calendar's check boxes were checked, & by the time I was finished & tried to save it, I noticed that all 4 of the check boxes were un-checked. When I tried to re-check the boxes, they would not stay checked.

Closing & re-starting Evolution appears to have resolved the issue.

---

### Post by drorlev on 2010-07-24
> **dmaxel said:**
> I have the same problem, just that I only have calendars set up with Google Calendars through Evolution. It happens occasionally, and I always have to exit Evolution, then start it again, and then most of the time it works again so that I can quickly add/edit the appointment.

Apparently I have the same problem, and thanks to dmaxel note I restarted Evolution and indeed everything went just fine. 

Does anybody know if a bug-call has been submitted?
Does anybody know where such bugs should be submitted (e.g. in GNOME web site or is there a special web site for Evolution)?

Dror

---

### Post by conformist5 on 2011-01-17
Use File --> Quit, not Evolution --> Close.

---

