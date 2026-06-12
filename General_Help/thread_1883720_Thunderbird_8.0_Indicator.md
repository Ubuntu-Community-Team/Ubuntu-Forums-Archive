---
title: "Thunderbird 8.0 Indicator"
date: 2011-11-19
forum: General Help
---

### Post by Raweed on 2011-11-19
Okay so I have ubuntu 10.04 and dont really feel "evolution" so i've downloaded thunderbird 8.0 and lightning. Ive set it as my 'preferred' mail reader only it doesnt show up in the top bar where the email icon is, the only 2 applications in there are pidgin and gwibber. Is there any way to integrate thunderbird so it is up there and it shows me how many emails ive got etc like it did with evolution? I downloaded the indicator 1.1 but thunderbird says it is not compatible with 8.0, any ideas on how i can do this?

---

### Post by Frogs Hair on 2011-11-19
See the link . [http://www.kabatology.com/03/27/how-to-change-your-default-applications-mail-client-in-a-gnome-desktop/](http://www.kabatology.com/03/27/how-to-change-your-default-applications-mail-client-in-a-gnome-desktop/)

---

### Post by Raweed on 2011-11-19
> **Frogs Hair said:**
> See the link . [http://www.kabatology.com/03/27/how-to-change-your-default-applications-mail-client-in-a-gnome-desktop/](http://www.kabatology.com/03/27/how-to-change-your-default-applications-mail-client-in-a-gnome-desktop/)

I have tried everything on there and there is nothing that puts thunderbird into the mail icon at the top :/

---

### Post by Frogs Hair on 2011-11-19
Other than those instructions and some solved threads using the same method   , I didn't find anything else  I am using 11.10 , but have had 10.04 installed  for 6 months . Thunderbird 7 is the default on 11.10 and 8 won't be used as default until 12.04 which is pre Alpha . That may be why the indicator is incompatible .

---

### Post by pqwoerituytrueiwoq on 2011-11-19
if you are trying to get thunderbird as a "tray" icon
i have been using a addon called "MinimizeToTray revived"

---

### Post by Bobhuber on 2011-11-19
> **Raweed said:**
> Okay so I have ubuntu 10.04 and dont really feel "evolution" so i've downloaded thunderbird 8.0 and lightning. Ive set it as my 'preferred' mail reader only it doesnt show up in the top bar where the email icon is, the only 2 applications in there are pidgin and gwibber. Is there any way to integrate thunderbird so it is up there and it shows me how many emails ive got etc like it did with evolution? I downloaded the indicator 1.1 but thunderbird says it is not compatible with 8.0, any ideas on how i can do this?
I don't use 10.04 anymore but I think this is what you are trying to do.

To set up thunderbird so that it will show up in the  mail notification area

/usr/share/indicators/messages/applications

create a text file called thunderbird with the following single line.

/usr/share/applications/thunderbird.desktop

In order to get mail notifications you will need to use an earlier version of TB probably 7.01 or earlier

---

### Post by Raweed on 2011-11-20
> **Bobhuber said:**
> I don't use 10.04 anymore but I think this is what you are trying to do.

To set up thunderbird so that it will show up in the  mail notification area

/usr/share/indicators/messages/applications

create a text file called thunderbird with the following single line.

/usr/share/applications/thunderbird.desktop

In order to get mail notifications you will need to use an earlier version of TB probably 7.01 or earlier

Yes thank you I found the exact instructions on [http://ubuntugenius.wordpress.com/2010/06/01/email-notification-add-mozilla-thunderbird-to-the-indicator-applet-in-ubuntus-system-tray/](http://ubuntugenius.wordpress.com/2010/06/01/email-notification-add-mozilla-thunderbird-to-the-indicator-applet-in-ubuntus-system-tray/) and it has put it in my mail icon. Is there anyway to downgrade or just remove and install?

---

### Post by Bobhuber on 2011-11-20
I would just remove your downloaded 8.0 and reinstall the system default if you disabled it.

---

### Post by Raweed on 2011-11-20
> **Bobhuber said:**
> I would just remove your downloaded 8.0 and reinstall the system default if you disabled it.

Ok Thanks I'll do that :)

---

