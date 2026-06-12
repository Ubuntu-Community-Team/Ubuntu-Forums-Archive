---
title: "Evolution EWS Ubuntu 12.04"
date: 2012-05-09
forum: General Help
---

### Post by Scabby_al on 2012-05-09
Has anyone had any success installing the evolution-ews plugin for Evolution in 12.04? I tried to manually compile it without any luck and the PPA is for 11.10 only.

Thanks!

---

### Post by celluloid on 2012-05-16
Would love to know if you had any luck with this - although with the glaring lack of response, it looks like may be not...

I'm really relying on some sort of decent Exchange compatibility so that I can begin using Ubuntu as my daily driver at work - everything else is fine, except enterprise Exchange support!

---

### Post by Scabby_al on 2012-05-16
I ended up going back to Thunderbird and using Davmail and a few other add-ons to email, bi-directional calendar support, and bi-directional global address list access. Granted I have to run Windows 7 in a VM while I'm at work for a few other apps that I need to use but this is one less thing I need Windows for. 

Thunderbird Add-Ons:
Lightning
Exchange 2007/2010 Calendar and Tasks Provider
Google Contacts - personal use
Inverse SOGo Connector - Exchange address book sync
Provider for Google Calendar - Personal Use
Thunderbird Conversations - Creates a "Gmail-Like" layout in Thunderbird. I use it more for the conversational style grouping than I do the quick reply fields since replying in this fashion formats all Exchange email as plain text. 

If you want to give it a whirl, just give Thunderbird/Davmail a try. If you need a hand setting any of this up, let me know.

On a semi-related note: Why is it possible to have phones and tablets that can support Exchange through Exchange Web Services (EWS) but there isn't a desktop client that can utilize it? I don't *think* there is any reverse engineering needed since this is Microsoft's preferred way to have non Windows Outlook clients access Exchange.

---

### Post by mp035 on 2012-05-21
> **Scabby_al said:**
> Why is it possible to have phones and tablets that can support Exchange through Exchange Web Services (EWS) but there isn't a desktop client that can utilize it? I don't *think* there is any reverse engineering needed since this is Microsoft's preferred way to have non Windows Outlook clients access Exchange.
:KS

I could not agree more!  Seems like such a silly thing to leave out.  OSX can access Exchange too.  A decent Exchange client would make Ubuntu MUCH easier to adopt as a business tool.

I too use davmail, but with evolution.  My only complaint is that when I'm out of the office, it's soooooooooooooo slow.  Hence I would love to try evolution-ews, but my searches are turning up nothing for ubuntu 12.04 and there are several libraries too new to allow me compile the latest version from source..

---

### Post by Scabby_al on 2012-05-21
I'm really surprised this hasn't been addressed sooner given how important Exchange access is to a lot of folks.

---

### Post by mp035 on 2012-05-21
Ok, I've done it.  First of all, credit where it is due, my script is an improvment on the one found here: [http://itworks.hu/2012/03/06/compiling-evolution-ews-for-ubuntu-12-04/]("http://itworks.hu/2012/03/06/compiling-evolution-ews-for-ubuntu-12-04/") by csak.

Copy the following text into a text editor:

```
#!/bin/bash
sudo apt-get install git gnome-common checkinstall gtk-doc-tools evolution-data-server-dev libgtk-3-dev libgconf2-dev libsoup-gnome2.4-dev libedataserver1.2-dev libedataserverui-3.0-dev libebackend1.2-dev libecal1.2-dev libedata-cal1.2-dev libedata-book1.2-dev evolution-dev
sudo rm -r evolution-ews ; git clone http://git.gnome.org/browse/evolution-ews -b gnome-3-2
sed '/\-Wall/ a \
\t-Wno-error=deprecated-declarations \
\t-Wno-missing-field-initializers' evolution-ews/configure.ac |
sed '/AC_SUBST(SOUP_CFLAGS)/ i \
AC_CHECK_LIB(gthread-2.0, g_thread_init)' >evolution-ews/configure.ac.new
mv evolution-ews/configure.ac.new evolution-ews/configure.ac
cd evolution-ews
./autogen.sh --prefix=/usr --disable-maintainer-mode
#sudo checkinstall --pkgname=evolution-ews --pkgversion=3.2 --pkgrelease=git -requires `evolution \(\>\= 3.2\), evolution \(\<\<3.3\)` && sudo mv *.deb ..
make
sudo make install
cd ..
```

Save it in your home folder as build-evolution.sh
open a terminal and type:
```
 chmod a+x build-evolution.sh
./build-evolution.sh
```

Wait for everyting to compile and install, then restart evolution and you should be able to add "Exchange Web Services" accounts to evolution.

The script will leave a directory(folder) called evolution-ews in your home folder.  Once you have confirmed everyting is working properly, you can delete this directory and its contents using your file manager of choice (eg. nautilus).

---

### Post by gamblor01 on 2012-05-23
> **mp035 said:**
> Ok, I've done it.  First of all, credit where it is due, my script is an improvment on the one found here: [http://itworks.hu/2012/03/06/compiling-evolution-ews-for-ubuntu-12-04/]("http://itworks.hu/2012/03/06/compiling-evolution-ews-for-ubuntu-12-04/") by csak.

Copy the following text into a text editor:

```
#!/bin/bash
sudo apt-get install git gnome-common checkinstall gtk-doc-tools evolution-data-server-dev libgtk-3-dev libgconf2-dev libsoup-gnome2.4-dev libedataserver1.2-dev libedataserverui-3.0-dev libebackend1.2-dev libecal1.2-dev libedata-cal1.2-dev libedata-book1.2-dev evolution-dev
sudo rm -r evolution-ews ; git clone http://git.gnome.org/browse/evolution-ews -b gnome-3-2
sed '/\-Wall/ a \
\t-Wno-error=deprecated-declarations \
\t-Wno-missing-field-initializers' evolution-ews/configure.ac |
sed '/AC_SUBST(SOUP_CFLAGS)/ i \
AC_CHECK_LIB(gthread-2.0, g_thread_init)' >evolution-ews/configure.ac.new
mv evolution-ews/configure.ac.new evolution-ews/configure.ac
cd evolution-ews
./autogen.sh --prefix=/usr --disable-maintainer-mode
#sudo checkinstall --pkgname=evolution-ews --pkgversion=3.2 --pkgrelease=git -requires `evolution \(\>\= 3.2\), evolution \(\<\<3.3\)` && sudo mv *.deb ..
make
sudo make install
cd ..
```

Save it in your home folder as build-evolution.sh
open a terminal and type:
```
 chmod a+x build-evolution.sh
./build-evolution.sh
```

Wait for everyting to compile and install, then restart evolution and you should be able to add "Exchange Web Services" accounts to evolution.

The script will leave a directory(folder) called evolution-ews in your home folder.  Once you have confirmed everyting is working properly, you can delete this directory and its contents using your file manager of choice (eg. nautilus).

This is awesome, thank you!  Out of curiosity, have you tried contacting the maintainer of the evolution-ews package?  It looks like the 12.04 build failed on May 5 and nobody is doing anything about it...but you got it to build!

Ideally we could get this built and put into the official repo.  Then folks could just run "apt-get install evolution-ews" and get the binary version directly.  That makes package management (updates and such) much easier to distribute.

In any case, many thanks for this.  I'm currently using Davmail and Thunderbird/Lightning but I wanted to give Evolution a shot.  Script is running as I type so I'm excited to give it a try.

Cheers!

---

### Post by Scabby_al on 2012-05-23
Nice work on the script! Hopefully this plugin will stabilize a bit and make it into the official Evolution build. Last I knew, mail worked but there were some issues with calendar and contacts?

---

### Post by Derek Karpinski on 2012-05-23
> **Scabby_al said:**
> I ended up going back to Thunderbird.......

Thunderbird's lack of ubuntu integration with the panel calendar, and the messaging menu is a deal breaker.  Should've been fixed before they switched from Evolution to Thunderbird.

Thunderbird, IMO is not an 'enterprise' solution.  Evolution is much closer, although it has it's own issues too.

---

### Post by mp035 on 2012-05-23
> **Scabby_al said:**
> Nice work on the script! Hopefully this plugin will stabilize a bit and make it into the official Evolution build. Last I knew, mail worked but there were some issues with calendar and contacts?

Cheers Scabby_al.  You are correct, the calendar is unusable, I am still using DavMail for my calendar, but have switched my mail over to evolution-ews.  

There is a bug with exchange 2007 that prevents you from sending emails with evolution-ews, so I had to patch my copy to work with my employers server.  For anyone looking, there is a thread here:
[https://bugzilla.gnome.org/show_bug.cgi?id=664749]("bugzilla.gnome.org/show_bug.cgi?id=664749")
It has patches attached to comments #8 and #11.  I used the outdated patch in #8 because #11 is too new for evolution 3.2.3

IMO Davmail is a far more stable (and better overall) solution.  As soon as I am back at the office, I will be dumping the ews plugin and switching back to Davmail.  Unfortunately with thousands of emails in my sent and inbox, Davmail is just too slow while connecting remotely.

I hope that someone packages Davmail for ubuntu, with a pretty monochrome icon which is whitelisted for the default notification area.

@Derek, I agree completeley, neither is perfect, but evolution is clearly a superior package.

---

### Post by mp035 on 2012-05-23
> **gamblor01 said:**
> This is awesome, thank you!  Out of curiosity, have you tried contacting the maintainer of the evolution-ews package?  It looks like the 12.04 build failed on May 5 and nobody is doing anything about it...but you got it to build!

Ideally we could get this built and put into the official repo.  Then folks could just run "apt-get install evolution-ews" and get the binary version directly.  That makes package management (updates and such) much easier to distribute.

In any case, many thanks for this.  I'm currently using Davmail and Thunderbird/Lightning but I wanted to give Evolution a shot.  Script is running as I type so I'm excited to give it a try.

Cheers!

Your welcome. :redface: I just improved on csaks work.

I have not tried contacting the maintainer of the package.  If you try, please inform him/her of the patches required to work with Exchange 2007 as that would be approximately half of the servers in operation.

---

### Post by viniciusferrao on 2012-07-08
The script is now broken :(

```

Making install in camel
make[2]: Entering directory `/home/viniciusferrao/evolution-ews/src/camel'
  CC     libcamelews_la-camel-ews-transport.lo
camel-ews-transport.c: In function 'ews_send_to_sync':
camel-ews-transport.c:101:3: error: implicit declaration of function 'camel_ews_settings_get_email' [-Werror=implicit-function-declaration]
camel-ews-transport.c:101:3: error: nested extern declaration of 'camel_ews_settings_get_email' [-Werror=nested-externs]
camel-ews-transport.c:101:45: error: 'settings' undeclared (first use in this function)
camel-ews-transport.c:101:45: note: each undeclared identifier is reported only once for each function it appears in
camel-ews-transport.c: In function 'camel_ews_transport_class_init':
camel-ews-transport.c:140:33: error: 'CAMEL_TYPE_EWS_SETTINGS' undeclared (first use in this function)
cc1: all warnings being treated as errors
make[2]: *** [libcamelews_la-camel-ews-transport.lo] Error 1
make[2]: Leaving directory `/home/viniciusferrao/evolution-ews/src/camel'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/viniciusferrao/evolution-ews/src'
make: *** [install-recursive] Error 1

```

---

### Post by celluloid on 2012-07-16
> **viniciusferrao said:**
> The script is now broken :(

```

Making install in camel
make[2]: Entering directory `/home/viniciusferrao/evolution-ews/src/camel'
  CC     libcamelews_la-camel-ews-transport.lo
camel-ews-transport.c: In function 'ews_send_to_sync':
camel-ews-transport.c:101:3: error: implicit declaration of function 'camel_ews_settings_get_email' [-Werror=implicit-function-declaration]
camel-ews-transport.c:101:3: error: nested extern declaration of 'camel_ews_settings_get_email' [-Werror=nested-externs]
camel-ews-transport.c:101:45: error: 'settings' undeclared (first use in this function)
camel-ews-transport.c:101:45: note: each undeclared identifier is reported only once for each function it appears in
camel-ews-transport.c: In function 'camel_ews_transport_class_init':
camel-ews-transport.c:140:33: error: 'CAMEL_TYPE_EWS_SETTINGS' undeclared (first use in this function)
cc1: all warnings being treated as errors
make[2]: *** [libcamelews_la-camel-ews-transport.lo] Error 1
make[2]: Leaving directory `/home/viniciusferrao/evolution-ews/src/camel'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/viniciusferrao/evolution-ews/src'
make: *** [install-recursive] Error 1

```

Hi,
Were you able to progress past this point?
I'm still unable to find any 12.04 packages and the phurley PPA has not be updated :(

---

### Post by cirdon on 2012-07-24
> **celluloid said:**
> Hi,
Were you able to progress past this point?
I'm still unable to find any 12.04 packages and the phurley PPA has not be updated :(

[FONT=System]If you're willing to upgrade Evolution to 3.4, you can use the [/FONT][FONT=System]stracciatella PPA to get 3.4 and its updated dependencies.

I ran into some bugs with 3.2's EWS plugin, and so I dug around and eventually [COLOR=Navy]_[asked on AskUbuntu]("http://askubuntu.com/questions/167475/evolution-3-4-3-on-12-04")_[/COLOR]. The stracciatella PPA was suggested, so I tried it and, by simply changing the version number in script posted here, I've got Evolution up and running with full EWS support. You can find the details in my AskUbuntu question.
[/FONT]

---

### Post by viniciusferrao on 2012-07-31
> **cirdon said:**
> [FONT=System]If you're willing to upgrade Evolution to 3.4, you can use the [/FONT][FONT=System]stracciatella PPA to get 3.4 and its updated dependencies.

I ran into some bugs with 3.2's EWS plugin, and so I dug around and eventually [COLOR=Navy]_[asked on AskUbuntu]("http://askubuntu.com/questions/167475/evolution-3-4-3-on-12-04")_[/COLOR]. The stracciatella PPA was suggested, so I tried it and, by simply changing the version number in script posted here, I've got Evolution up and running with full EWS support. You can find the details in my AskUbuntu question.
[/FONT]

Cirdon can you please post more information about this? How to set up Evolution 3.4 with 12.04 LTS?

---

### Post by cirdon on 2012-08-03
> **viniciusferrao said:**
> Cirdon can you please post more information about this? How to set up Evolution 3.4 with 12.04 LTS?

In my original comment here, my "asked on AskUbuntu" is a link to the details, but I'll jot down the steps here, too, and do a start-to-finish of setting up Evolution with EWS.


[LIST=1]
[*]In terminal, run ```
sudo apt-add-repository ppa:janvitus/gnomestracciatella
``` . This will add the Stracciatella PPA. **Note**: This is all of the stock Gnome 3 stuff, Ubuntu won't be too happy if you try to just do a mass upgrade (it actively tries to keep you from just upgrading everything).
[*]Run ```
sudo apt-get update
``` to update apt.
[*]Run ```
sudo apt-get install evolution
``` to upgrade Evolution
[LIST=1]
[*] After you've installed Evolution, I recommend disabling the PPA in the Software Source menu, otherwise Ubuntu will complain that it can't upgrade everything, every single time you run the Update Manager.
[/LIST]
 
[*]If you then want EWS, download the script available earlier in this thread.
[*]In the second line of the script, where it says ```
git clone http://git.gnome.org/browse/evolution-ews -b gnome-3-2
```, change it to ```
git clone http://git.gnome.org/browse/evolution-ews -b gnome-3-4

``` (note the change from "gnome-3-2" to "gnome-3-4").
[*]Run the script. It'll go through a bunch of stuff and spit out a wall-o-text, but should install successfully.
[*]Open Evolution, when you go to add email accounts, you should now have an entry along the lines of "Exchange EWS" available. Fill out your Exchange information and you should be good to go!
[/LIST]

---

### Post by dcstar on 2012-08-04
FWIW EWS is in the 12.10 Alpha development release - but if even you install it there is no EWS option for a new mail account.

The version of Evolution in the Alpha is also a development version, so it may be a while until this feature is stable - hopefully when 12.10 goes live (and then it - also hopefully - will be backported to 12.04 LTS).

---

### Post by dcstar on 2012-08-04
Also this thread has a link to a 64-bit EWS deb file for 12.04:

[http://ubuntuforums.org/showpost.php?p=12146254&postcount=2](http://ubuntuforums.org/showpost.php?p=12146254&postcount=2)

I have just installed it on my 12.04 test VM and set it up to a SBS 2011 system I am in the middle of installing and it seems to work well - even linked up the GAL URL automagically!

Hmmm, mail seems ok but I cannot get the GAL list to appear in Contacts. This setup already has a connection to a SBS 2003 box so there may be some conflict issues - others may want to verify that this package works fully for them.

---

### Post by celluloid on 2012-08-06
How do you guys go with setting send/receive times?
I noted that it won't send/receive like Outlook w/ Exchange does and I still need to set a time like with IMAP?

---

### Post by Scabby_al on 2012-08-16
After being away from this thread for a little bit trying several other options and finding myself unhappy with all the results. Davmail works flawlessly but its an absolute memory hog and using Exchange Web App isn't the worst thing in the world but it has it's limitation and integrates with the desktop poorly. 

I grabbed a .deb of Evolution-EWS linked in the post above me and installation went smoothly. I can configure mail without any issues but calendar and contacts still don't work despite having the proper URI. May do some poking around in th emorning but I have been unable to find a fix other than either upgrading to Evolution 3.4 and hoping for the best or using Davmail for calendar, contacts, and GAL.

---

### Post by celluloid on 2012-08-17
> **Scabby_al said:**
> 
I grabbed a .deb of Evolution-EWS linked in the post above me and installation went smoothly. I can configure mail without any issues but calendar and contacts still don't work despite having the proper URI. May do some poking around in th emorning but I have been unable to find a fix other than either upgrading to Evolution 3.4 and hoping for the best or using Davmail for calendar, contacts, and GAL.

Any chance you could give me a run-down on using Davmail? Which client are you using this with?

---

### Post by Scabby_al on 2012-08-17
> **celluloid said:**
> Any chance you could give me a run-down on using Davmail? Which client are you using this with?

I was using Davmail with the latest stable version of Thunderbird 14 and Thunderbird 15 beta along with the following add-ons:

[LIST]
[*]Lightning
[*]Google Calendar Provider
[*]Gmail Conversation View
[/LIST]

I used the Gmail conversation view just to group my mail similar to Gmail / Outlook (got too used to it). The quick replies aren't very useful unless you're just sending plain text replies. 

I used Davmail's iMap function to access my mail and downloaded the messages locally to build a cache for quick mail access.

---

### Post by achmorrison on 2012-08-24
Is there a way to install and activate the evolution-exchange plugin?  It disappeared when I installed evolution 3.4, and now I can't get it to install after having installed the EWS stuff.

---

### Post by cirdon on 2012-08-25
> **achmorrison said:**
> Is there a way to install and activate the evolution-exchange plugin?  It disappeared when I installed evolution 3.4, and now I can't get it to install after having installed the EWS stuff.

See my previous post: [http://ubuntuforums.org/showpost.php?p=12148743&postcount=16](http://ubuntuforums.org/showpost.php?p=12148743&postcount=16)

---

### Post by arune on 2012-09-18
I've tested evolution3.4 and evolution-ews under Ubuntu 12.04 according cirdon. Mail worked but not calendar nor contacts.

I'm going back to evolution-mapi which works better with calendar and contacts but some items in calendar seems to have wrong time somehow, they are off by an hour or two.

---

### Post by dcstar on 2012-09-18
> **arune said:**
> I've tested evolution3.4 and evolution-ews under Ubuntu 12.04 according cirdon. Mail worked but not calendar nor contacts.

I'm going back to evolution-mapi which works better with calendar and contacts but some items in calendar seems to have wrong time somehow, they are off by an hour or two.

Check the Time Zones.

---

### Post by arune on 2012-09-19
How?
Some calendar items are correct and some are not...

---

### Post by dcstar on 2012-09-19
> **arune said:**
> How?
Some calendar items are correct and some are not...

Microsoft Outlook does not seem to strictly follow the rules of the .ics format, and I have found that things that look ok in Outlook are screwed up in other .ics compliant software (like Evolution).

I have seen .ics files that have items with an End time **before** the Start time look ok when imported in Outlook, but totally confuse Evolution (which justifiably expects something to start before it ends).

It could be as simple as the relevant Appointments not having a Time Zone set so Outlook "assumes" something whereas other things don't and require a specific value.

---

### Post by arune on 2012-09-19
I have **attached** an event which I saved as ics from both outlook and evolution. Attached is also a diff in PNG.

Which are the interesting fields?

I originally created the event in outlook as a reoccurring "Appointment", the time should be 14:30. In evolution the event is displayed at 16:30.

Anyway, is there anything to do about this? If I change timezone or similar I guess some other events will be wrong instead?

---

### Post by cirdon on 2012-09-19
> **arune said:**
> I've tested evolution3.4 and evolution-ews under Ubuntu 12.04 according cirdon. Mail worked but not calendar nor contacts.

I'm going back to evolution-mapi which works better with calendar and contacts but some items in calendar seems to have wrong time somehow, they are off by an hour or two.

What version of ** Exchange** are you using? As far as I know, EWS only works with Exchange 2010, and mapi only works with versions previous to 2010.

---

### Post by cirdon on 2012-09-19
One thing I noticed that I missed in my transcription of my AskUbuntu stuff:

Once you set up EWS, you may need to restart evolution-contacts and evolution-calendar (or whatever exactly they're called) by exiting Evolution, then going into system monitor and ending all the other references to Evolution. Then, restart Evolution and your calendar and contacts should work.

---

### Post by dcstar on 2012-09-20
> **arune said:**
> I have **attached** an event which I saved as ics from both outlook and evolution. Attached is also a diff in PNG.

Which are the interesting fields?

I originally created the event in outlook as a reoccurring "Appointment", the time should be 14:30. In evolution the event is displayed at 16:30.

Anyway, is there anything to do about this? If I change timezone or similar I guess some other events will be wrong instead?

In the ICS files there are definition fields stating when the Standard & Daylight Saving dates for the time zone definitions begin:

Evolution: DTSTART:19701028T030000  (year: 1970, month: 10, date: 28, time 3AM)

Outlook:   DTSTART:16011028T030000  (year 1601(!!), month 10 etc. etc.)

I don't know about you, I reckon but giving a Linux system a time definition with the year 1601 may cause some issues!

As far as I can tell the RFC that defines these files assumes that the earliest year defined in them will be 1970:

[https://tools.ietf.org/html/rfc5545#ref-ISO.8601.2004](https://tools.ietf.org/html/rfc5545#ref-ISO.8601.2004)

Anyway, this discussion is now way OT for this thread even if the problem seems to be typical Microsoft bogosity.

---

### Post by arune on 2012-09-20
> **cirdon said:**
> What version of ** Exchange** are you using? As far as I know, EWS only works with Exchange 2010, and mapi only works with versions previous to 2010.

We are running Exchange 2007. 
According to [[COLOR="Blue"]_this_[/COLOR]]("http://www.howtoforge.com/talking-soap-with-exchange") article, Soap/EWS came in Exchange 2007.


[QUOTE=cirdon,12249201]Once you set up EWS, you may need to restart evolution-contacts and evolution-calendar (or whatever exactly they're called) by exiting Evolution, then going into system monitor and ending all the other references to Evolution. Then, restart Evolution and your calendar and contacts should work.[/QUOTE]

Did not do this, will try when I have some time for it.

---

### Post by cirdon on 2012-09-20
> **arune said:**
> We are running Exchange 2007. 
According to [[COLOR="Blue"]_this_[/COLOR]]("http://www.howtoforge.com/talking-soap-with-exchange") article, Soap/EWS came in .

I'm talking about evolution-ews, the plugin, not the Exchange service.

---

### Post by arune on 2012-09-21
Do you mean that evolution-ews only supports Exchange 2010?

Well, maybe if the soap/ews-interface changed so much between 2007 and 2010.

---

### Post by cirdon on 2012-10-09
> **arune said:**
> Do you mean that evolution-ews only supports Exchange 2010?

Well, maybe if the soap/ews-interface changed so much between 2007 and 2010.

I believe I recall seeing changes to the encryption used, so yes, it changed enough.

---

### Post by NSC on 2012-11-12
If You don't want to add additional repositories which updates lots of packages in system from unknown repository, You can compile package for existing evolution version.

Since ubuntu 12.04 uses evolution 2.3.2, You may use evolution-ews plugin version 2.3.2. Sadly, ubuntu default repository doesn't have this package.

You can download right package from evolution site:
[http://projects.gnome.org/evolution/previous.shtml](http://projects.gnome.org/evolution/previous.shtml)

two ways to compile:
automation script:
[http://loginroot.com/evolution-ews-plugin-install-script-for-evolution-3-2-3-on-ubuntu-12-04/](http://loginroot.com/evolution-ews-plugin-install-script-for-evolution-3-2-3-on-ubuntu-12-04/)

manualy compiling:
[http://loginroot.com/adding-ms-exchange-compability-with-evolution-ews-in-ubuntu-12-04/](http://loginroot.com/adding-ms-exchange-compability-with-evolution-ews-in-ubuntu-12-04/)

---

### Post by drpain on 2013-01-24
> **cirdon said:**
> In my original comment here, my "asked on AskUbuntu" is a link to the details, but I'll jot down the steps here, too, and do a start-to-finish of setting up Evolution with EWS.


[LIST=1]
[*]In terminal, run ```
sudo apt-add-repository ppa:janvitus/gnomestracciatella
``` . This will add the Stracciatella PPA. **Note**: This is all of the stock Gnome 3 stuff, Ubuntu won't be too happy if you try to just do a mass upgrade (it actively tries to keep you from just upgrading everything).
[*]Run ```
sudo apt-get update
``` to update apt.
[*]Run ```
sudo apt-get install evolution
``` to upgrade Evolution
[LIST=1]
[*] After you've installed Evolution, I recommend disabling the PPA in the Software Source menu, otherwise Ubuntu will complain that it can't upgrade everything, every single time you run the Update Manager.
[/LIST]
 
[*]If you then want EWS, download the script available earlier in this thread.
[*]In the second line of the script, where it says ```
git clone http://git.gnome.org/browse/evolution-ews -b gnome-3-2
```, change it to ```
git clone http://git.gnome.org/browse/evolution-ews -b gnome-3-4

``` (note the change from "gnome-3-2" to "gnome-3-4").
[*]Run the script. It'll go through a bunch of stuff and spit out a wall-o-text, but should install successfully.
[*]Open Evolution, when you go to add email accounts, you should now have an entry along the lines of "Exchange EWS" available. Fill out your Exchange information and you should be good to go!
[/LIST]



Hi cirdon,

Thank you for the post, I was able to connect to our Exchange Server and everything is pulling over. Thank you for the script and the detailed instructions!

Cheers

---

### Post by xyepblra on 2013-08-09
I followed cirdon's instructions and update process when through nicely and smoothly, but went I entered the host URL (host IP in my case) and clicked "Apply" button, Evolution hang for an hour. I decided to see where it goes finally, but nothing has changed so far. Is what I'm doing wrong?

---

### Post by david_ally on 2013-10-25
Evolution email client does not shutdown, it takes hours to shutdown unless I switch off the PC. How do I ensure proper shutdown of this application?

---

### Post by david_ally on 2013-10-28
I could not get pass this point, what I'm I missing?

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[4]: Leaving directory `/home/david/evolution-ews/src/server'
make[3]: Leaving directory `/home/david/evolution-ews/src/server'
make[2]: Leaving directory `/home/david/evolution-ews/src/server'
Making install in server/tests
make[2]: Entering directory `/home/david/evolution-ews/src/server/tests'
make[3]: Entering directory `/home/david/evolution-ews/src/server/tests'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/david/evolution-ews/src/server/tests'
make[2]: Leaving directory `/home/david/evolution-ews/src/server/tests'
Making install in utils
make[2]: Entering directory `/home/david/evolution-ews/src/utils'
  CC     libewsutils_la-e-ews-query-to-restriction.lo
In file included from /usr/include/evolution-data-server-3.4/libedata-cal/e-cal-backend-sexp.h:28:0,
                 from e-ews-query-to-restriction.c:28:
/usr/include/evolution-data-server-3.4/libedata-cal/e-cal-backend.h:26:35: fatal error: libebackend/e-backend.h: No such file or directory
compilation terminated.
make[2]: *** [libewsutils_la-e-ews-query-to-restriction.lo] Error 1
make[2]: Leaving directory `/home/david/evolution-ews/src/utils'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/david/evolution-ews/src'
make: *** [install-recursive] Error 1

---

### Post by david_ally on 2013-10-28
Hi Cirdon,
Please I need help with this, my Evolution doesn't start again. This is the message I received after going through the process;

installing sv.gmo as /usr/share/locale/sv/LC_MESSAGES/evolution-ews.mo
installing zh_CN.gmo as /usr/share/locale/zh_CN/LC_MESSAGES/evolution-ews.mo
make[1]: Leaving directory `/home/david/evolution-ews/po'
make[1]: Entering directory `/home/david/evolution-ews'
make[2]: Entering directory `/home/david/evolution-ews'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/david/evolution-ews'
make[1]: Leaving directory `/home/david/evolution-ews'
david@david-Latitude-D630:~$ evolution
Xlib:  extension "GLX" missing on display ":0".
Segmentation fault (core dumped)

---

### Post by vivekgs2007 on 2014-08-22
@[**[COLOR=#000000]mp035[/COLOR]**]("http://ubuntuforums.org/member.php?u=251197")

I used you script to run the evotion ews. 

It got some error:

rm: cannot remove `evolution-ews': No such file or directory
remote: Counting objects: 12827, done.
remote: Compressing objects: 100% (5431/5431), done.
remote: Total 12827 (delta 10120), reused 9341 (delta 7378)
Receiving objects: 100% (12827/12827), 3.20 MiB | 10 KiB/s, done.
Resolving deltas: 100% (10120/10120), done.
configure.ac:38: installing `./compile'
configure.ac:113: installing `./config.guess'
configure.ac:113: installing `./config.sub'
configure.ac:3: installing `./install-sh'
configure.ac:3: installing `./missing'
src/account-setup-eplugin/Makefile.am:10: `%'-style pattern rules are a GNU make extension
src/account-setup-eplugin/Makefile.am:16: `%'-style pattern rules are a GNU make extension
src/account-setup-eplugin/Makefile.am:19: `%'-style pattern rules are a GNU make extension
src/account-setup-eplugin/Makefile.am: installing `./depcomp'
src/server/Makefile.am:66: `%'-style pattern rules are a GNU make extension
src/server/Makefile.am:72: pkgconfig_DATA:-$(API_VERSION: non-POSIX variable name
Makefile.am: installing `./INSTALL'
camel-ews-transport.c: In function 'ews_send_to_sync':
camel-ews-transport.c:101:3: error: implicit declaration of function 'camel_ews_settings_get_email' [-Werror=implicit-function-declaration]
camel-ews-transport.c:101:3: error: nested extern declaration of 'camel_ews_settings_get_email' [-Werror=nested-externs]
camel-ews-transport.c:101:45: error: 'settings' undeclared (first use in this function)
camel-ews-transport.c:101:45: note: each undeclared identifier is reported only once for each function it appears in
camel-ews-transport.c: In function 'camel_ews_transport_class_init':
camel-ews-transport.c:140:33: error: 'CAMEL_TYPE_EWS_SETTINGS' undeclared (first use in this function)
cc1: all warnings being treated as errors
make[3]: *** [libcamelews_la-camel-ews-transport.lo] Error 1
make[2]: *** [all-recursive] Error 1
make[1]: *** [all-recursive] Error 1
make: *** [all] Error 2
libtool: install: warning: relinking `libewsutils.la'
camel-ews-transport.c: In function 'ews_send_to_sync':
camel-ews-transport.c:101:3: error: implicit declaration of function 'camel_ews_settings_get_email' [-Werror=implicit-function-declaration]
camel-ews-transport.c:101:3: error: nested extern declaration of 'camel_ews_settings_get_email' [-Werror=nested-externs]
camel-ews-transport.c:101:45: error: 'settings' undeclared (first use in this function)
camel-ews-transport.c:101:45: note: each undeclared identifier is reported only once for each function it appears in
camel-ews-transport.c: In function 'camel_ews_transport_class_init':
camel-ews-transport.c:140:33: error: 'CAMEL_TYPE_EWS_SETTINGS' undeclared (first use in this function)
cc1: all warnings being treated as errors
make[2]: *** [libcamelews_la-camel-ews-transport.lo] Error 1
make[1]: *** [install-recursive] Error 1
make: *** [install-recursive] Error 1

---

### Post by vivekgs2007 on 2014-08-22
Tried with the same steps but got some error. pasting it bellow. please do look it.


remote: Counting objects: 12827, done.
remote: Compressing objects: 100% (5431/5431), done.
remote: Total 12827 (delta 10118), reused 9341 (delta 7378)
Receiving objects: 100% (12827/12827), 3.22 MiB | 24 KiB/s, done.
Resolving deltas: 100% (10118/10118), done.
configure.ac:38: installing `./compile'
configure.ac:113: installing `./config.guess'
configure.ac:113: installing `./config.sub'
configure.ac:3: installing `./install-sh'
configure.ac:3: installing `./missing'
src/account-setup-eplugin/Makefile.am:10: `%'-style pattern rules are a GNU make extension
src/account-setup-eplugin/Makefile.am:16: `%'-style pattern rules are a GNU make extension
src/account-setup-eplugin/Makefile.am:19: `%'-style pattern rules are a GNU make extension
src/account-setup-eplugin/Makefile.am: installing `./depcomp'
src/server/Makefile.am:66: `%'-style pattern rules are a GNU make extension
src/server/Makefile.am:72: pkgconfig_DATA:-$(API_VERSION: non-POSIX variable name
Makefile.am: installing `./INSTALL'
In file included from /usr/include/evolution-data-server-3.4/libedata-cal/e-cal-backend-sexp.h:28:0,
                 from e-ews-query-to-restriction.c:28:
/usr/include/evolution-data-server-3.4/libedata-cal/e-cal-backend.h:26:35: fatal error: libebackend/e-backend.h: No such file or directory
compilation terminated.
make[3]: *** [libewsutils_la-e-ews-query-to-restriction.lo] Error 1
make[2]: *** [all-recursive] Error 1
make[1]: *** [all-recursive] Error 1
make: *** [all] Error 2
In file included from /usr/include/evolution-data-server-3.4/libedata-cal/e-cal-backend-sexp.h:28:0,
                 from e-ews-query-to-restriction.c:28:
/usr/include/evolution-data-server-3.4/libedata-cal/e-cal-backend.h:26:35: fatal error: libebackend/e-backend.h: No such file or directory
compilation terminated.
make[2]: *** [libewsutils_la-e-ews-query-to-restriction.lo] Error 1
make[1]: *** [install-recursive] Error 1
make: *** [install-recursive] Error 1

---

