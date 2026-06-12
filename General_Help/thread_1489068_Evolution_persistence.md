---
title: "Evolution persistence"
date: 2010-05-20
forum: General Help
---

### Post by mozillalives on 2010-05-20
I recently installed 10.04 and setup my email in evolution. I was wondering if there was a way to have it persist after I close the window? I noticed that an alarm and data process still run after I close it, but not the mail functionality. Am I missing a setting somewhere?

---

### Post by dcstar on 2010-05-20
> **mozillalives said:**
> I recently installed 10.04 and setup my email in evolution. I was wondering if there was a way to have it persist after I close the window? I noticed that an alarm and data process still run after I close it, but not the mail functionality. Am I missing a setting somewhere?

If you close the program you close the program - it only works if it is running.

---

### Post by mozillalives on 2010-05-21
I'm well aware that the usual response for a program is to terminate if the window is no longer active. But the program running is not necessarily tied to the windows you see - it all depends upon how the application was designed. Evolution for example, will continue to run small pieces of itself even after you close all windows to run event alarms (if you've configured it so).

I'm simply hoping there's a setting to tell it to continue to check mail even after I closed the windows.

---

### Post by 98cwitr on 2010-05-21
I would like to know this as well...hate having it loaded in the bottom task bar when there is a mail icon in the task pane at the top right. Rhythmbox is persistent as well as Vuze...but not mail.

---

### Post by mozillalives on 2010-05-21
I think I found something that will help [http://www.nongnu.org/mailnotify/](http://www.nongnu.org/mailnotify/) (it's Mail Notification in Ubuntu Software Center or mail-notification in aptitude). You can set it up to run and it will display a small mail icon with an unread count when new messages arrive. 

I don't know how good it is though, I'm just trying it out now. Also it looks like there might be others in the software center, just look for "mail notification".

---

### Post by Bobhuber on 2010-05-21
> **mozillalives said:**
> I recently installed 10.04 and setup my email in evolution. I was wondering if there was a way to have it persist after I close the window? I noticed that an alarm and data process still run after I close it, but not the mail functionality. Am I missing a setting somewhere?
I don't know how much ram you have but I run Thunderbird with Firetray and the Lightning extension for the calendar . You could also try using Alltray if you want to stay with Evolution but you won't have all of the features that Firetray has with the email program.

---

### Post by dcstar on 2010-05-22
> **mozillalives said:**
> I'm well aware that the usual response for a program is to terminate if the window is no longer active. But the program running is not necessarily tied to the windows you see - it all depends upon how the application was designed. Evolution for example, will continue to run small pieces of itself even after you close all windows to run event alarms (if you've configured it so).

I'm simply hoping there's a setting to tell it to continue to check mail even after I closed the windows.

As I stated, if you close Evolution it closes.

The Calendar functions are actually run by the Gnome session which integrates with the Evolution Calendar, but this has nothing whatsoever to do with checking mail.

---

### Post by mozillalives on 2010-05-24
@Bobhuber - thanks for those suggestions. I'll give them a try.

---

