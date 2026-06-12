---
title: "Firefox/Swiftfox configuring thing"
date: 2009-08-07
forum: General Help
---

### Post by Quirriff on 2009-08-07
I installed Swiftfox today, and it works fine.

Except it didn't translate over the "Ubuntu Firefox modifications" extension.

Which it seems not only adds apt-updating, but more importantly to me, the Gnome integration. So it prompts (For what program I want to use) me whenever I try to run something from the Downloaded files list. Or right Click the file and select "open containing folder".

I've got a similar program, but with Ordinary firefox on my Xubuntu machine.

It's not critical, but it's something I'd like to fix.

---

### Post by theicyj on 2009-08-17
I too have the same problem.  I am always prompted to select a program to use to open a downloaded file, or to "Open containing folder" when right-clicking on a downloaded file.  I am using Ubuntu 9.04 with the latest kernel and Swiftfox 3.5.2

---

### Post by y-lee on 2009-08-17
> **Quirriff said:**
> I installed Swiftfox today, ...
Except it didn't translate over the "Ubuntu Firefox modifications" extension.

Which it seems not only adds apt-updating, but more importantly to me, the Gnome integration. So it prompts (For what program I want to use) me whenever I try to run something from the Downloaded files list. Or right Click the file and select "open containing folder".

I've got a similar program, but with Ordinary firefox on my Xubuntu machine.

It's not critical, but it's something I'd like to fix.

For the record you can fix the apt-updating (I am thinking you mean being able to install debs by clicking on apturl links online) by consulting [help.ubuntu.com/community/AptURL]("https://help.ubuntu.com/community/AptURL"). If modifying firefoxes or SWs [noparse]about:config[/noparse] file is something you need help with post back and I will try to guide you thru the process.

> **theicyj said:**
> I too have the same problem.  I am always prompted to select a program to use to open a downloaded file, or to "Open containing folder" when right-clicking on a downloaded file.  I am using Ubuntu 9.04 with the latest kernel and Swiftfox 3.5.2

The window that pops up should have an option to check saying *remember choice *be sure it is checked and navigate to **/usr/bin** and pick nautilus (assuming you wish to use nautilus to open folders .... if not choose the file manager you wish to use) and click ok and then firefox or swiftweasel should open folders correctly aqfter that. if not feel free to modify the advice given, [Open Containing folders]("http://rubylution.ping.de/articles/2007/09/11/open-containing-folder-in-firefox-under-linux") changing thunar to nautilus (or whatever you wish). if none of that works let us know.

---

