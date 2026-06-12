---
title: "Firefox and directly Skype calls"
date: 2011-08-29
forum: General Help
---

### Post by ELMIT on 2011-08-29
I use vTiger CRM and it is great! It has the function that you could dial directly through the system via Skype. E.g., it let you add a Skype field and it makes this as a link  
e.g, if I use a Skype user: Skype2me
it makes a link:     skype://Skype2me?call

How can I do that?

Or how can I use it with just a phone number in the web page (as Windows user can)

---

### Post by Habitual on 2011-08-29
[http://forum.skype.com/index.php?showtopic=92761](http://forum.skype.com/index.php?showtopic=92761)

---

### Post by ELMIT on 2011-08-29
Yes, this one I followed till I came to this line:


[http://www.kolmann.at/philipp/linux/skype_..._handler_0.6.py](http://www.kolmann.at/philipp/linux/skype_..._handler_0.6.py)

404 Page not found!

---

### Post by ELMIT on 2011-08-30
I found the action handler 1.0 in py and pl version.

However, it still does not work and gives me:

Firefox doesn't know how to open this address, because the protocol (skype) isn't associated with any program.


I have installed Greasemonkey and I have enabled it
I have installed Skype Linkify for Linux. 
In Firefox I have added 
network.protocol-handler.app.skype      /usr/local/bin/action_handler_1.0.pl
I have chmod +x /usr/local/bin/action_handler_1.0.pl
I have restarted Firefox.
I checked cpan:
install Net::DBus::Skype
Net::DBus::Skype is up to date (0.02).

What do I miss?

---

### Post by Habitual on 2011-08-30
[http://forum.skype.com/index.php?showtopic=90273](http://forum.skype.com/index.php?showtopic=90273)

---

### Post by ELMIT on 2011-08-30
The only thing I learned from that thread was to try it in a terminal window:

/usr/local/bin/skype-action-handler  skype:echo123?call
No running API-capable Skype found at /usr/local/share/perl/5.10.1/Net/DBus/Skype.pm line 43.



???

I use Skype (Beta) 2.2.0.35

---

### Post by ELMIT on 2011-09-14
I tried after I restarted the computer again:

/usr/local/bin/skype-action-handler skype:echo123?call

and the command from the command line worked magically, ... but using it from firefox gives me:

Firefox doesn't know how to open this address, because the protocol (skype) isn't associated with any program.

The link for that phone number was:    skype://+63-2-2225%203322?call



A search for skype in Firefox's about:config  finds me two lines:

greasemonkey.newscript_namespace	user set	string		Skype Linkify for Linux
network.protocol-handler.app.skype	user set	string		/usr/local/bin/action_handler_1.0.pl


changing /usr/local/bin/action_handler_1.0.pl to /usr/local/bin/skype-action-handler AND restart both Skype and firefox did not change it either.

It remains:
Firefox doesn't know how to open this address, because the protocol (skype) isn't associated with any program.

---

### Post by Habitual on 2011-09-14
[http://forum.skype.com/index.php?showtopic=92761](http://forum.skype.com/index.php?showtopic=92761) and
[http://eu.blackpanther.hu/2010/04/working-skype-links/](http://eu.blackpanther.hu/2010/04/working-skype-links/) and
[http://blogs.skype.com/linux/2006/08/making_skype_links_work.html](http://blogs.skype.com/linux/2006/08/making_skype_links_work.html) describe similar processes for adding a skype action handler to the Firefox browser.

You have the code to make the call, now you must tell FF how to handle the protocol (associate the action/link to the handler script.)

* Open Mozilla (Firefox)
* Type about:config in the address-bar to open the configuration editor.
* Use the scroll bar to navigate to the network.protocol&#8230; section.
* Check if the network protocol section includes a network.protocol-handler.app.skype key.
* If a key exists, edit it. If no key exists, create a key by right-clicking on any key and selecting New -> String from the pull-down menu.
* Enter **network.protocol-handler.app.skype** as the key name.
* Enter /usr/local/bin/action_handler_0.6.py as the key value.

Restart FireFox and lets give it a try!

**Your actual /path/file may be different** than "/usr/local/bin/action_handler_0.6.py"

Some pages suggest that GreaseMonkey is to be installed.

Some reading suggests that this works on the Windows platform.
The post from thestudio53 and a comment at [http://blogs.skype.com/linux/2006/08/making_skype_links_work.html](http://blogs.skype.com/linux/2006/08/making_skype_links_work.html) suggests that is can work in Ubuntu 10.10.

I wish I had a "go here, do 1-2-3 and it'll work" answer, but I don't.

Here's a "recent" article on this subject:
[http://mikebeach.org/2011/03/installing-skype-on-ubuntu-or-debian-with-updates-for-skype-urls/](http://mikebeach.org/2011/03/installing-skype-on-ubuntu-or-debian-with-updates-for-skype-urls/)

---

### Post by ELMIT on 2011-09-14
I tried all above, but no go, ...

I can start it from the command line, but I cannot get it to work from Firefox.

about:config just ignors:
network.protocol-handler.app.skype

---

### Post by linuxgeoff on 2011-12-16
I've been around the exact same loop repeatedly.  can call skype from command line, have named the action handler in firefox and get the same error.  I've been around numerous forums and I'm coming to the conclusion that no-one knows how to do this (and, therefore, no one has it working in 11.04/10):( 

Has anyone gotten this to work in 11.x? ( I had it working on earlier versions).  Is the problem in FF, or in ubuntu?

If anyone knows the answer, please help us all out!

---

### Post by deejaylight on 2012-02-20
Hey guys.
I think I found the way.
Here is how I solve the problem

1) list a new .Desktop file in /usr/share/applications/defaults.list by adding the following line:
x-scheme-handler/skype=firefox-skype.desktop

2) create a firefox-skype.desktop file in /usr/share/applications with the following lines:
[Desktop Entry]
Encoding=UTF-8
Name=Skype Action Handler
Comment=Call from Skype
GenericName=Skype Client
Exec=/usr/local/bin/skype-action-handler
Terminal=false
X-MultipleArgs=false
Type=Application
Icon=skype
Categories=Application;Network;
MimeType=x-scheme-handler/skype;

I replaced in firefox about:config -> network.protocol-handler.app.skype to value usr/share/applications/firefox-skype.dedsktop

and when I push the call link from firefox my skype start to call.

Best regards!

---

### Post by linuxgeoff on 2012-02-20
Yes! this is pretty much what I discovered a few weeks again and posted to a couple of forums like [Skype]("http://blogs.skype.com/linux/2006/08/making_skype_links_work.html#more") and netscape, but forgot this one (doh!).  Thanks for posting.

So been using this for a few weeks and it works fine on my machine.  Now if Skype can just release an up to date, stable version for linux.....

Geoff

> **deejaylight said:**
> Hey guys.
I think I found the way.
Here is how I solve the problem

1) list a new .Desktop file in /usr/share/applications/defaults.list by adding the following line:
x-scheme-handler/skype=firefox-skype.desktop

2) create a firefox-skype.desktop file in /usr/share/applications with the following lines:
[Desktop Entry]
Encoding=UTF-8
Name=Skype Action Handler
Comment=Call from Skype
GenericName=Skype Client
Exec=/usr/local/bin/skype-action-handler
Terminal=false
X-MultipleArgs=false
Type=Application
Icon=skype
Categories=Application;Network;
MimeType=x-scheme-handler/skype;

I replaced in firefox about:config -> network.protocol-handler.app.skype to value usr/share/applications/firefox-skype.dedsktop

and when I push the call link from firefox my skype start to call.

Best regards!

---

