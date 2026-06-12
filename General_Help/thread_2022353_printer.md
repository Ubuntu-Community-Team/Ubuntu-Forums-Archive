---
title: "printer"
date: 2012-07-10
forum: General Help
---

### Post by offgridguy on 2012-07-10
I am unable to get my printer to work with libre office,  my ubuntu is 12.04 version.
I have my printer ie: brother dcp 7030 set as default printer, however no luck when 
I want to print.  The computer says it recognizes the printer and sometimes says
sending data to printer but printer says no data.  Same printer works fine on my  other
computer with windows 7,  all help appreciated.

---

### Post by moore.bryan on 2012-07-10
Can you print a test page within the Printer Settings?

---

### Post by offgridguy on 2012-07-10
Thank's for your interest, I just tried a test page within the printer settings and the result is negative,
The request gets submitted but nothing happens.  Any ideas?

---

### Post by moore.bryan on 2012-07-11
No worries... I've had *many* printer issues over the years and wanted to lend a hand if I could help in any way.

Just a few questions:
[LIST]
[*]How did you add the printer?
[*]Is it directly or network attached?
[*]Have you chacked if thie printer's manufacturer has special Linux drivers available on its website?
[/LIST]

---

### Post by offgridguy on 2012-07-11
I added the printer through the system settings, printing using the tools available.
The printer is directly attached via usb cable.
I haven't checked the manufacturer's website yet, thanks for the suggestion.

---

### Post by moore.bryan on 2012-07-11
Well, step one would be to delete your printer and try re-adding it--which you likely have already done. If you haven't, please do so.

---

### Post by kurt18947 on 2012-07-11
If I may butt in here, Brother has an installer script that has been perfect for me installing printers.  Doesn't help with scanner functions though which are more of a PITA.

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00104](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00104)

The script shows a problem with a missing spool file or folder, forget which but my printers still work and when I check the folder/file is present.

---

### Post by offgridguy on 2012-07-11
I just deleted and re-added the printer.  Everything seems to go fine as to following the prompts
up to the print a test page, where it still does nothing.  I did contact the brother website re;
drivers, linux compatible, am awaiting reply.

---

### Post by offgridguy on 2012-07-11
Thank you for the advice, i downloaded the script but am having trouble installing the printer driver.
In the help section 6 no. 3 it says enter this command to extract the downloaded file,
Command: etc......
I can't see where to enter this command, any  advice?

---

### Post by kurt18947 on 2012-07-11
You don't need to use the CLI to extract the file.  If you find the file with Nautilus and right-click it, you should be able to extract it.  Just remember where you put it:).  The actual script does need to be run from the command line.  You need to do this from an account with sudo or 'administrator' privileges.  I saved the file 'linux-brprinter-installer-1.0.4-1 to Desktop.  I then extracted it and got a file by the same name.  Open a terminal and enter "cd Desktop" then "dir".  You should see the file listed.  At that point you can type in the terminal "sudo bash linux-brprinter-installer-1.0.4-1". (Cheat-hint:  right-click  copy and paste work in terminal)  It should then ask you for the model.  Enter something like "MFC-7030" and yes, letter case does matter.  At that point the script should run, ask for a couple "do you agree?" questions, ask what kind of connection etc. etc.

Why does Brother not have a GUI application for this?  There are a number of different desktops in the various distros.  The above script works in ALL distros and desktops afaik.

---

### Post by offgridguy on 2012-07-11
T

---

### Post by offgridguy on 2012-07-11
I followed through as you laid it out, it seems to have installed, the icons are on my desktop.
Now when I try to print I get the message waiting for printer to become available.  I am not sure
how to make it any more available than it already is.  Any suggestions

---

### Post by kurt18947 on 2012-07-11
> **offgridguy said:**
> I followed through as you laid it out, it seems to have installed, the icons are on my desktop.
Now when I try to print I get the message waiting for printer to become available.  I am not sure
how to make it any more available than it already is.  Any suggestions

I assume you're using Unity?  Gnome-shell's printer icon is less helpful but there's a fix for that.  If you're using anything but gnome shell, there should be a printing icon in the dash or for XFCE/classic on a menu.  Click that and you should get icons for each printer installed.  If there's an icon for the Brother printer you could right-click it then left-click properties.  You'll see things like Settings, Policies, Access Control etc.   You could check under 'Policies' to make sure 'enabled', 'accepting jobs' and 'shared' are all checked.  Make sure access control is set to allow printing for everyone.  I've gotten messages like you're getting when the check boxes in Policies are not checked, or I got an overlaid 'paused' icon.  I have no idea why those options were not checked.

Edit:  I had another thought.  What connection are you using?  The installer will default to USB, even if the printer is on a network.  If you getting a 'paused' message I assume the printer is being seen.

---

### Post by offgridguy on 2012-07-11
Yes the desktop is unity, on the desktop I have brdcp7030pr-2.0.2-,  the software centre says it is installed,  I also have cupswrapperDC7030-2.0.2-1i386.deb on the desktop, when I go to the software
centre it is awaiting installation.  Repeated efforts fail to install.
Rechecked the printer using the Dash and system settings, all appropriate boxes are checked.  Still nothing, example if i type a document using libre office writer, check printer status before printing
it shows Brother DCP-7030 default printer, click print, nothing. No messages , nothing.  I can't pretend to know a lot about computers but configuring a printer was a breeze using Windows 7.
I'm not ready to give up on ubuntu yet though.
Edit; to answer the last question, the printer is connected to the computer with usb cable.

---

### Post by offgridguy on 2012-07-11
Hello again,  I think I may have it this time, went through the entire process to install from the script
over again.  When I printed the test page "VOILA" , tried a sample page again using Abiword and
again it printed.  I really appreciate all the help, thank you very much.  This was a learning curve I 
needed as much as I needed the printer.

---

### Post by kurt18947 on 2012-07-12
Good job!  As with most things the more you do it the easier it gets.

---

### Post by moore.bryan on 2012-07-12
Glad to hear everything worked out for you; sorry I couldn't have more actively helped.

Make sure to use the "thread tools" to mark this as solved.

---

### Post by offgridguy on 2012-07-12
I appreciate your offer to help anyway, thank you. I'm impressed with the ubuntu/ linux community
support, it probably won't be the last time I need it.  Thanks again.

---

### Post by moore.bryan on 2012-07-13
All of us were new to Linux at some point!

Best of luck and happy Ubuntu-ing.

---

### Post by offgridguy on 2012-07-14
Thanks to all for the help.:grin:

---

