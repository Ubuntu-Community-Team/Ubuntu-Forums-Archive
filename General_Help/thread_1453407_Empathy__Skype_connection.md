---
title: "Empathy / Skype connection?"
date: 2010-04-13
forum: General Help
---

### Post by julianb on 2010-04-13
I thought I heard that the Empathy IM client (or one of the other multi-protocol IM clients?) for Ubuntu would connect to Skype to allow text chat. Is this true?

If so, how do I do it? Do I need to install skype on my system first? 



(I want to accept messages from folks who are on skype in addition to several other instant message services, so I really want to make this work without having to log in to each system separately.)

---

### Post by HermanAB on 2010-04-13
Nope, the Skype protocol is obfuscated and nobody bothered to reverse engineer it yet.

---

### Post by eliasv on 2010-04-22
Actually, skype does provide an API which allows this exact behaviour. It does require you to have skype itself running in the background unfortunately though, but this probably isn't such a massive problem for most people, it does mean that you will have to install skype first though yea.

Check [http://eion.robbmob.com/](http://eion.robbmob.com/) for a download of a plugin for libpurple (used by pidgin / empathy? etc) which interfaces with skype and instructions on how to get it set up with pidgin. I have a feeling that it might be in the repos too - just search for skype or something - but I'm not sure.

I have used this myself so i can vouch for it :). I have only used it with pidgin myself, but I guess it should probably work for other stuff too.

good luck :).

EDIT:

Just installed this myself, the one in the repos doesn't seem to work with empathy in 10.04, and the one from the website depends on pidgin, so if you want to use skype with empathy here is a bug report along with a solution [https://bugs.launchpad.net/ubuntu/+source/pidgin-skype/+bug/567248?comments=all](https://bugs.launchpad.net/ubuntu/+source/pidgin-skype/+bug/567248?comments=all)

---

### Post by krisgesling on 2010-09-20
My debian based nokia n900 has skype integrated with all the other contact methods so it must be possible, unless nokia hasn't released certain components of the maemo sourcecode. I've gotta go do some digging.

---

### Post by tom2652 on 2010-10-29
> **HermanAB said:**
> Nope, the Skype protocol is obfuscated and nobody bothered to reverse engineer it yet.

Actually, several of the multi-protocol IM clients on Windows have & support Skype... Trillian, Pidgin... Skype seems to be the popular IM flavor of the moment with a lot of the geeks @ tech companies I work with.

Actually, I just may have solved my own problem... Pidgin & Instabird are both available for ubuntu, and both support Skype. In fact, it seems, Empathy is one of the few that does not?

---

### Post by paulsomm on 2010-11-03
Yes, it works in Empathy (use it myself under 10.10).  It's not called Skype tho.  Install Skype, then install the pidgin-skype package, start skype, then when you run Empathy the skype plugin shows up as account type "bigbrownchunx-skype-dbus".

Methinks a developer has a sense of humor :)

Note: Skype must run in addition to empathy.

---

### Post by JOZeldenrust on 2010-11-16
> **paulsomm said:**
> Yes, it works in Empathy (use it myself under 10.10).  It's not called Skype tho.  Install Skype, then install the pidgin-skype package, start skype, then when you run Empathy the skype plugin shows up as account type "bigbrownchunx-skype-dbus".

Methinks a developer has a sense of humor :)

Note: Skype must run in addition to empathy.

Everything works fine right up to the moment I enter the account info for my skype account. There's only a single field for the account name, and that's it. There's a button to "log in" but that doesn't seem to do anything.

I'm lost here.

---

### Post by djhenry on 2010-11-17
I have had success with Empathy +Skype on Ubuntu 10.10 following these directions.  I installed the Skype Beta client 2.1.0.81 first and entered just my account name in the Empathy setup.  When I clicked connect, it opened the Skype client and asked permission for the Empathy plugin to use my Skype account.  I then just entered my password in Skype and everything seems happy.

Hope that helps.

---

### Post by cmavr8 on 2010-11-22
I tried many suggestions (described here as well as the bug report) but I still get a "Disconnected - Network error" error in empathy..

Any ideas?

---

### Post by Astrotrain on 2010-12-01
> **cmavr8 said:**
> I tried many suggestions (described here as well as the bug report) but I still get a &quot;Disconnected - Network error&quot; error in empathy..

Any ideas?

 I had the same problem, and I have solved it few minutes ago!  Posible cause may be that you have only 32-bit versions of libskype.so and libskype-dbus.so in usr/lib/purple-2 folder while running 64-bit Ubuntu. At least that was my case.  So I went to [http://eion.robbmob.com/](http://eion.robbmob.com/) , and downloaded 64-bit versions, copied them to usr/lib/purple-2 and it worked like a charm.  :) Hope that helps!

---

### Post by cmavr8 on 2010-12-01
Thanks... it worked for a moment (without sync or skypeout checkbox options enabled) but no more...

Did you overwrite the 32 bit libs or did you just add the 64 bit ones side-by-side?

Thanks

---

### Post by Astrotrain on 2010-12-02
I have only added 64-bit versions, and it all works without a flaw. And btw, I have both SkypeSync and SkypeOut enabled.

---

### Post by sinisterstuf on 2011-01-31
What is the **point** of being able to Skype chat with Empathy if you have to have Skype open all the time?
You'd like a different interface or what? Why not just have Empathy open and Skype open? Same thing!

---

### Post by cmavr8 on 2011-01-31
I prefer one interface for all chat accounts... Also, empathy integrates better than skype to ubuntu.

---

### Post by Astrotrain on 2011-01-31
> **cmavr8 said:**
> I prefer one interface for all chat accounts... Also, empathy integrates better than skype to ubuntu.

That is also my point exactly.

---

### Post by whochismo on 2011-02-03
> **Astrotrain said:**
> I had the same problem, and I have solved it few minutes ago!  Posible cause may be that you have only 32-bit versions of libskype.so and libskype-dbus.so in usr/lib/purple-2 folder while running 64-bit Ubuntu. At least that was my case.  So I went to [http://eion.robbmob.com/](http://eion.robbmob.com/) , and downloaded 64-bit versions, copied them to usr/lib/purple-2 and it worked like a charm.  :) Hope that helps!

For me, I didn't change anything. I still got the same error, and I've tried in two different computers. Should I delete the 32-bit libraries?

---

### Post by Astrotrain on 2011-02-03
> **whochismo said:**
> For me, I didn't change anything. I still got the same error, and I've tried in two different computers. Should I delete the 32-bit libraries?
  Well to be honest, I don`t really know. I haven`t deleted 32-bit libraries, and it all works ok. I have checked it out right this minute, because I usually use Pidgin, but I started Empathy just to make sure something hasn`t changed since last check and everything really works fine, for me at least.

---

### Post by gufide on 2011-02-14
everythings work fine for me but I must run skype with empathy :icon_frown:

---

### Post by dtbaker on 2011-03-28
Worked for me, I just ran:

$ sudo apt-get install pidgin-skype skype skysentials 

then opened skype, then opened pidgin

then in pidgin you "add new account" and select "skype". just enter your username and click login. the skype client will ask for permissions and away you go. 

chat works fine, using it now.

64bit ubuntu 10.10

---

### Post by cmavr8 on 2011-03-29
Works!
Thanks!

---

### Post by Ascurion on 2011-04-23
Thanks a lot for these informations they helped me make it work as well. I'd like to add my experience on this topic using the 64bit version of Ubuntu 11.04 beta 2. It worked for me after downloading the 64bit libraries, as described above, and installing pidgin-skype and skysentials, but only after un-checking "Skypeout Online" under the "Advance" options when adding the account. However, I don't know what did the trick in the end.

---

### Post by luis6268 on 2011-04-23
Nope, the Skype protocol is obfuscated and nobody bothered to reverse engineer it yet.
[URL="http://www.totallyseo.co.uk/"]
[/URL]

---

### Post by aarongc on 2011-06-18
... until now! [http://skype-open-source.blogspot.com/2011/06/skype-protocol-reverse-engineered.html](http://skype-open-source.blogspot.com/2011/06/skype-protocol-reverse-engineered.html)

---

### Post by flipNasty on 2011-06-29
so does this mean we'll see some true empathy/skype integration in the near future?? Maybe with Oneiric?

---

### Post by elzy89 on 2011-08-06
Ah, I'd love to see compatibility in Oneiric. Might stop my little brother moaning. I have transferred my whole family to Ubuntu systems. This is the only complaint I get from my little bro. Little sister moans about flash stuff not being quick enough sometimes but that's flash for you I guess...

---

### Post by calibre45 on 2011-09-06
It works - I can see my contacts, call them, send messages, but i don't receive any messages from them into empathy - they go directly into skype. Is there any solution?

---

### Post by Zvlwab on 2011-09-19
> **calibre45 said:**
> It works - I can see my contacts, call them, send messages, but i don't receive any messages from them into empathy - they go directly into skype. Is there any solution?
I'm having exactly the same problem, I can send messages using Empathy, but I only receive them in skype.

---

### Post by kuvanito on 2011-09-25
you can try imo.im almost every chat client works here

---

### Post by zanfur on 2011-10-03
> **Zvlwab said:**
> I'm having exactly the same problem, I can send messages using Empathy, but I only receive them in skype.

Same in pidgin.  If you're running 64-bit, the pidgin-skype or skype4pidgin packages in the Ubuntu repositories don't work with Skype 2.2.x anymore -- it will send messages but not receive them.

However, if you download the debian package from eion.robbmob.com, it will work just fine.  I've made a new pidgin-skype package including images for skype in empathy that I'll be adding to my PPA in a bit for everyone who uses lucid on up.

---

### Post by berka on 2011-10-07
> **zanfur said:**
> Same in pidgin.  If you're running 64-bit, the pidgin-skype or skype4pidgin packages in the Ubuntu repositories don't work with Skype 2.2.x anymore -- it will send messages but not receive them.

However, if you download the debian package from eion.robbmob.com, it will work just fine.  I've made a new pidgin-skype package including images for skype in empathy that I'll be adding to my PPA in a bit for everyone who uses lucid on up.

Great thanks. I had same problem, this worked like a charm. I don't know if following procedure is needed but anyway...
1) Remove previous entered skype accountin Empathy
2) Remove using for example Synaptics the Ubuntu version of pidgin-skype package 
3) I found the deb package here:
[http://packages.debian.org/sid/amd64/pidgin-skype/download](http://packages.debian.org/sid/amd64/pidgin-skype/download)
4) install:
sudo dpkg -i pidgin-skype_20110407+svn612+dfsg-1.1_amd64.deb
5) Start emphaty and add the skype account again and voila all messages routes to Empathy

If you do not want the Skype indicator in panel use dconf-editor (dconf-tools package and Remove the 'Skype' entry from desktop -> panel whitelist
/Erik

---

### Post by Zvlwab on 2011-10-11
Yay it works! Thanks

Is there any way to remove the skype icon from the system tray? I don't like the new indicator applet.

---

### Post by Jul8 on 2012-02-22
> **Zvlwab said:**
> Yay it works! Thanks

Is there any way to remove the skype icon from the system tray? I don't like the new indicator applet.
true ;o

---

