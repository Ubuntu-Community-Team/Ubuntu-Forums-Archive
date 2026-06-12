---
title: "Mailwasher Pro 6.54 runs on Maverick (wine)"
date: 2011-01-14
forum: General Help
---

### Post by pabloikba on 2011-01-14
Here is what is working for me:

Install Mailwasher Pro via wine.

Here is the wine configuration:

1. Add Mailwasher Pro as an application
2. Set the Windows Version as WIndows 7
3. Go to the Graphics tab and check only 2 boxes -
        Allow the window manager to decorate the window
        Allow the window manager to control the windows

Next:

Start Mailwasher Pro and register
Go to Tools, Email Accounts (DO NOT import email accounts)
Click Add Account - 
(this next step is important):
Only enter information in the first box (name of the account) - DO NOT enter anything in the box asking for your email address.
Click the Next button and fill-in everything on this page and the Advanced page (if desired).

And, finally, if you've been using Mailwasher Pro on any other computer and have compiled blacklists and white lists, etc., you can import them to be used by your Wine installation by copying the entire Mailwasher Pro folder (in Windows it is in Documents & Settings, User, Application Data, MailwasherPro) and pasting it into Ubuntu and replacing the existing files from your new install (it is in .wine, dosdevices, C:, Users, UserName, Application Data, MailwasherPro).


That's it. Works like a charm. You can even use custom colors from the Options, Display offerings.

Note: I entered 23 email accounts (from all the websites that I manage). I have it running _sequentially_ as opposed to all at one time - no reason except some of the accounts are IMAP with SSL and they sometimes need a little time to shake hands.

---

