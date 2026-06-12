---
title: "Email Notifications for Gnome &amp; Evolution (or any other mail client)"
date: 2009-12-14
forum: General Help
---

### Post by openxs on 2009-12-14
This is a How-To for making Email Notifications work for Gnome & Evolution (or any other mail client)

It all started when I decided that having Evolution open all the time was a bit annoying. I like Evolution because it integrates well with Google Mail, Contacts & Calendars, as well as all my IMAP mail boxes and my Yahoo POP mailbox. I didn't want to change client. I am using Mail Notification 5.4 [(http://www.nongnu.org/mailnotify/)]("http://www.nongnu.org/mailnotify/") by  Jean-Yves Lefort in Ubuntu Karmic Koala. 

I could have minimised Evolution to the system tray and got mail notifications as they came in by using KDocker [(KDocker tutorial)]("http://www.ridinglinux.org/2007/04/09/minimize-evolution-mail-client-into-system-tray-with-kdocker/") or [AllTray]("https://launchpad.net/alltray") but they didn't do quite what I wanted for one reason or another, for example, compatibility issues with Compiz.

How:

Open Synaptic package Manager and search for "mail-notification", tick both 'mail-notification & mail-notification-evolution' 
or in a terminal, type:

# sudo apt-get install mail-notification mail-notification-evolution

Once this is done, open Evolution and check the plugin is installed and active: Edit > Plugins > Jean-Yves Lefort's Mail Notification (make sure there is a tick next to it).

Now you should find the configuration properties for mail notification on the desktop menu, click: System > Preferences: Mail Notification.

This is where you add your mailboxes, now, this is where things started going wrong and took a bit of working out. I added a mailbox by clicking 'Add', then on the option of 'Mailbox Type' I selected Evolution, obviously...? It didn't work.

Trying to add Evolution in Mail notify gave me the error "Mail Notification can not contact Evolution. Make sure that Evolution is running and that the Evolution Jean-Yves Lefort's Mail Notification plugin is loaded." Both were true and so I tried to fix this problem, I read lots of bug reports and tried various 'fixes' all to no avail. 

Then I thought to myself, why not take Evolution out of the equation until it's needed? So I configured my IMAP & POP accounts directly, OK, it took a bit longer but totally worth it, here's how...

1) Select mailbox type (e.g. IMAP, POP, Gmail...)
2) Fill in the General tab with mail server address, username/email address & password
3) Click TAB called 'Connection' and select Authentication Mechanism.

 **IMPORTANT** 

I changed the drop down menu to Cram-MD5 for mine, but select whatever Authentication method your provider uses, if you don't know, trial and error only takes a few seconds more. If you leave it on 'Autodetect' you will get an error saying 'Unhandled IMAP or POP mailbox (unable to encode Base64: overflowed buffer)' and it won't work. if you have the wrong authentication Mechanism you'll get the same error or it won't connect, straight forward.

4) Select the 'Details' Tab and changed the name of your mailbox if you want to, this is just what your Mailbox is identified as in the list, I called mine by the email address i.e. [email]chris@blahblah.blah[/email]

5) Apply,OK 

...and thats it for that part.

Now send yourself a test email to the address you just configured and you'll get a notification! 

Mail Reader

If you right-click the mail icon, the first option is 'Mail Reader' and when you click it, what's supposed to happen is your Mail Reader (Evolution) opens up so you can read and reply to the email, mine didn't do anything. 

The reason, I found out, was because it was trying to open Thunderbird... I found out by opening a terminal and typing:

# tail -n 0 -f ~/.xsession-errors

Then clicking the 'Mail Reader' option. The output told me thet the 'click' called Thunderbird.

To set the correct Mail Client, on the desktop task bar, click open: System > Preferences > Preferred Applications

Under the Mail Reader section in the 'Command' box, type in Evolution, or the path to Evolution, i.e: 
/usr/bin/evolution

You might want to add options to it, you can check what options are available on the man page:

# man evolution

Finally, close the Preferred Applications dialog and you're done, email notifications without Evolution being open, I hope this helps.

---

### Post by kalyp on 2009-12-16
I just found another solution here:
[http://ubuntuforums.org/showpost.php?p=8243857&postcount=10](http://ubuntuforums.org/showpost.php?p=8243857&postcount=10)
Looks like the Jean-Yves Lefort plugin is installed in the bad directory under karmic.

edit: actually, it doesn't seem to work for me. I'll look later and will update.

---

### Post by openxs on 2009-12-16
> **kalyp said:**
> I just found another solution here:
[http://ubuntuforums.org/showpost.php?p=8243857&postcount=10](http://ubuntuforums.org/showpost.php?p=8243857&postcount=10)
Looks like the Jean-Yves Lefort plugin is installed in the bad directory under karmic.

edit: actually, it doesn't seem to work for me. I'll look later and will update.

Hi, I tried what the fellow in the post you quoted has done. I found that it would only work with Evolution running, which kinda defeated the object for me.

However, as the link you added states, some people may find that they need to copy the plugins from one folder to another if they get installed to the wrong (2.24) folder when they are using Evolution version 2.28. Check to see if the plugins are here:

# ls /usr/lib/evolution/2.24/plugins/

they **should** be here:

# # ls /usr/lib/evolution/2.28/plugins/

The plugins you are looking for are:

org-jylefort-mail-notification.eplug
liborg-jylefort-mail-notification.so

You can copy them to the correct folder with 'cp' or use a symbolic link 'ln -s'

below I have added the symbolic link commands needed. As you can see, it points the plugins to '/usr/lib/evolution/2.28/plugins/'. 

# sudo ln -s /usr/lib/evolution/2.24/plugins/org-jylefort-mail-notification.eplug /usr/lib/evolution/2.28/plugins/
# sudo ln -s /usr/lib/evolution/2.24/plugins/liborg-jylefort-mail-notification.so /usr/lib/evolution/2.28/plugins/ 

** On another note, I have found that when I boot my machine in the morning, Mail notify flashes, showing that it has not connected. I have to right-click the system tray icon and select update, then it connects fine. I suspect that if I made it load last it would sort it out, will try it out when I get a moment. Let us know if you get it working. Atb

---

### Post by kalyp on 2009-12-16
yeah well, that's exactly what the other link says. And I did create the links in 2.28 and the plugin shows up in evolution. But mail-notification still cannot find evolution (actually, it doesn't even launch anymore right now).

Your solution worked though, for 5 min maybe :) don't ask me what's wrong, I haven't had time to look through it, and since mail-notification doesn't work right now, it's not that easy. I'll keep you posted :)

edit: ok, I just don't get it. After letting it try for 30 min (I could see the process but nothing happened), gmail-notifier told me that my IMAP inbox (parameterized just like evolution) was not supported, there's a "EOF" error. BUT I can now directly see evolution (Noo 2 Ubuntoo's method) and it works. So I won't try to undersand and just be happy about it :)

---

### Post by SlugSlug on 2009-12-16
:popcorn:


For me -- this is the best webmail alert

[https://addons.mozilla.org/en-US/firefox/addon/4490](https://addons.mozilla.org/en-US/firefox/addon/4490)

---

### Post by openxs on 2009-12-17
> **kalyp said:**
>  So I won't try to undersand and just be happy about it :)

Fairplay for the update, will be good if they just programmed Evolution to do this small but important thing, it would make so many people happy. If it wasn't for the integration I think I would use Thunderbird, but calendar & contacts are useful. Maybe in the next release :) atb

---

### Post by openxs on 2009-12-17
> **SlugSlug said:**
> :popcorn:


For me -- this is the best webmail alert

[https://addons.mozilla.org/en-US/firefox/addon/4490](https://addons.mozilla.org/en-US/firefox/addon/4490)

Funky plugin for Firefox, I wonder if there are any Chrome addons that do the same, it's my favourite Linux browser now :)

---

### Post by kalyp on 2009-12-17
> **openxs said:**
> Funky plugin for Firefox, I wonder if there are any Chrome addons that do the same, it's my favourite Linux browser now :)

same here :)
I looked yesterday but didn't find any, if you find something let me know!

---

### Post by realbadapple on 2009-12-29
> **openxs said:**
> Fairplay for the update, will be good if they just programmed Evolution to do this small but important thing, it would make so many people happy. If it wasn't for the integration I think I would use Thunderbird, but calendar & contacts are useful. Maybe in the next release :) atb

Evolution has this feature in the evolution-plugins package ( which is installed by default ), but it only works, for me after sending an email from a link on webpage, for example. After that the default plugin works until I log out or shut down. This has been a problem, on Ubuntu, for some time! On fedora, this bug has been squashed for a couple of years! So, I guess that all the monkeying with the default gnome stuff that Ubuntu is doing is causing the problem.:( ](*,)

---

