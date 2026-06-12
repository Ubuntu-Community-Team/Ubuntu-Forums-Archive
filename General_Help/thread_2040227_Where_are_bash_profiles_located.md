---
title: "Where are bash profiles located?"
date: 2012-08-10
forum: General Help
---

### Post by cogset on 2012-08-10
Hi there,I've got a customized second bash profile (in Ubuntu Lucid) that I would like to export on  another Lucid installation (stuff like custom background  image,transparency,font size, etc.),so I'd need to know where are these  settings written and how can I export them on the other  installation-thanks.

---

### Post by papibe on 2012-08-10
Hi cogset.

I'm pretty sure you are referring to gnome-terminal profiles. Aren't you?

gnome-terminal settings are store here:
```
~/.gconf/apps/gnome-terminal/
```
The profiles are stored just a little below:
```
~/.gconf/apps/gnome-terminal/profiles
```
Hope that helps. Let us know how it goes.
Regards.

---

### Post by cogset on 2012-08-10
> **papibe said:**
> Hi cogset.
I'm pretty sure you are referring to gnome-terminal profiles. Aren't you?
.

Yes,that's actually what I was talking about,thank you:after following your hint,I've located the profile that I wanted to export and copied its  **%gconf.xml** file inside the directory of a newly created profile on the 2nd computer (kinda like you would do with Firefox profiles,if you get the analogy:first create  a new profile,then replace  its contents with the files from the old profile you want to export),but,the issue is,this isn't working at all.I'm obviously missing something here.

---

