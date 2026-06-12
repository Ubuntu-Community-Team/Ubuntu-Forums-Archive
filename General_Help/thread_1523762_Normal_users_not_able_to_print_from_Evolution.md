---
title: "Normal users not able to print from Evolution"
date: 2010-07-04
forum: General Help
---

### Post by toMeloos on 2010-07-04
Hi, I'm facing a very weird issue:

For the last couple of weeks the users in this machine I'm maintaining are unable to print to the printer or to PDF from Evolution. There is no error message, the printer just doesn't do anything and printing to PDF doesn't result in a PDF file.

The users can print from any other application. OpenOffice, Gedit, Evince, etc. is not a problem. Also, printing from Evolution does work for the root user. Started it using 'gksudo evolution' and am not having any printing issues then.

Upgraded from 9.10 to 10.04 but this has not solved the problem. Checked the cups logs and it just reports the tasks as printed successfully.

I'm guessing this is a rights/policy issue but don't know what to check. Any suggestions on what could be wrong here?

---

### Post by philinux on 2010-07-04
Check the file /etc/group

Check that your user is in lpadmin

You can use system>admin>users and groups for this.

---

### Post by toMeloos on 2010-07-04
I've checked, users are in lp and lpadmin.

Besides if they weren't they couldn't have printed from the other applications either. So that wasn't the issue :(

---

### Post by dcstar on 2010-07-04
> **toMeloos said:**
> Hi, I'm facing a very weird issue:

For the last couple of weeks the users in this machine I'm maintaining are unable to print to the printer or to PDF from Evolution. There is no error message, the printer just doesn't do anything and printing to PDF doesn't result in a PDF file.

The users can print from any other application. OpenOffice, Gedit, Evince, etc. is not a problem. Also, printing from Evolution does work for the root user. Started it using 'gksudo evolution' and am not having any printing issues then.

Upgraded from 9.10 to 10.04 but this has not solved the problem. Checked the cups logs and it just reports the tasks as printed successfully.

I'm guessing this is a rights/policy issue but don't know what to check. Any suggestions on what could be wrong here?

Create a fresh user and test again.

---

### Post by philinux on 2010-07-04
> **toMeloos said:**
> I've checked, users are in lp and lpadmin.

Besides if they weren't they couldn't have printed from the other applications either. So that wasn't the issue :(

Run evolution from the terminal and see if any cups related errors when trying to print.

---

