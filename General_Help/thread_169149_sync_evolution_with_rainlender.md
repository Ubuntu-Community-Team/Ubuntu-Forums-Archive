---
title: "sync evolution with rainlender?"
date: 2006-05-02
forum: General Help
---

### Post by pongu on 2006-05-02
i realize this is probably either impossible or way out of my league but i thought i'd ask. i'm dual booting xp and ubuntu and trying to find a medium for my calendar. i've used rainlender in windows for a long time and have been pleased. i have a rainlender server set up on a remote computer. i'm new to linux and am still feeling out evolution but was wondering if there's a way to sync it with my rainlender server so i don't have to compare my calendars and update each individually. if not w/ evolution, maybe there's another calendar program in linux that will allow it. any suggestions?

---

### Post by nanotube on 2006-05-02
well, evolution stores its calendar in an ical file, so if you install the rainlendar ical plugin, and direct it to the evolution .ics file, it should be able to display it.

now... of course there is the problem of windows reading the linux partition... maybe there is an option in evolution to specify the path where it stores its .ics file, and put it on some kind of shared fat32 drive that can be accessed from both win and lin.

---

### Post by pongu on 2006-05-02
my laptop dual boots linux and xp. my desktop runs xp and stays on which makes it easier to use as my rainlender server and access w/ my laptop. others in my house use the desktop so setting it up w/ linux in order to have a calendar server isn't really an option (if that's possible). though, i'm not sure evolution supports a calender server anyway.

are you suggesting i create an additional small fat32 partition on my hard drive where i'd store my .ics file? if there was any way at all to convince windows to recognize the linux partition then i'd like to try that first but i understand that's not likely.

---

### Post by nanotube on 2006-05-02
hmm, i dont know what kind of a server the rainlendar server runs - if its a standard ical-based server, then evolution i think should be able to sync to your rainlendar server. but since i have not ever used rainlendar server, i just don't know what format it serves in. but yea, that would be the first thing to try, actually. :)

but yes, my original suggestion was to have a small fat32 partition to store ics. hmm, i think i remember seeing some kind of a driver for windows to read ext2. search google, and you will find it. dont remember if its compatible with ext3, though.

---

