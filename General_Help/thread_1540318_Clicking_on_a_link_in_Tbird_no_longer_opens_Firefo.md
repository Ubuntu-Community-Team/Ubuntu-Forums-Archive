---
title: "Clicking on a link in Tbird no longer opens Firefox"
date: 2010-07-27
forum: General Help
---

### Post by grr51 on 2010-07-27
Hi,

Since I upgraded to Firefox 3.6.8, when I click on a link in Thunderbird 3.1.1, nothing happens!!  Right-clicking on a link and selecting "Open Link in Browser" does not work either.

Any idea what might be the cause of this annoying problem?

Thanks,

grr51

---

### Post by merike on 2010-07-27
> **grr51 said:**
> Hi,

Since I upgraded to Firefox 3.6.8, when I click on a link in Thunderbird 3.1.1, nothing happens!!  Right-clicking on a link and selecting "Open Link in Browser" does not work either.

Any idea what might be the cause of this annoying problem?

Thanks,

grr51

If you open up preferences attachments tab then what is set for http, https and ftp? Most of the time setting correct executable there will fix it. If not set already try to set these to /usr/bin/firefox

---

### Post by grr51 on 2010-07-27
Merike,

Under Attachments, I only have three entries:
- Mailbox
- File
- Power Point Presentation

How do I add new ones?  I did not find any menu to add new entries.

Grr

---

### Post by grr51 on 2010-07-27
Hi,

I finally found the solution to this problem.
Somehow, when upgrading to Firefox 3.6.8, the default web browser was no longer set to Firefox, but to Custom!

Below is how I fixed it:


[LIST=1]
[*]System -> Preferences -> Preferred Applications
[*]Select the "Internet" tab at the top
[*]Using the pull-down menu, select the web browser as Firefox.  Mine was set as "Custom"
[*]Select the radio button "open link with web browser default"
[*]At the same time, select your default "Mail Reader"
[*]Close
[/LIST]
Regards,

grr51

---

